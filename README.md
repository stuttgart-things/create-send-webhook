stuttgart-things/create-send-webhook
=======================================

configure and send customized webhooks to targets like MS TEAMS (supports connector cards).

install this role
-----------------

copy the following and paste it on your ansible host to install the roles:
```
cat <<EOF > /tmp/requirements.yaml
roles:
- src: git@codehub.sva.de:Lab/stuttgart-things/supporting-roles/create-send-webhook.git
  scm: git
collections:
- name: community.general
  version: 1.2.0
EOF
ansible-galaxy install -r /tmp/requirements.yaml --force
ansible-galaxy collection install -r /tmp/requirements.yaml -f
rm -rf /tmp/requirements.yaml
```

Example Playbook
----------------

```
---
- hosts: "{{ target_host | default('localhost') }}"

  vars:
    summary_text: "App notification text"
    msteams_url: "https://outlook.office.com/webhook/GUID/IncomingWebhook/GUID/GUID"
    card_title: "title for connector card"
    act_image: "https://.../.jpg"
    act_title: "activity title"
    act_subtitle: "activity subtitle"
    act_text: "activity text"
    link_name: "text for link"
    link_url: "http://..."

  roles:
    - create-send-webhook
```

Playbook execution (example)
-----------------------------

```
ansible-playbook create-send-webhook.yaml -vv
```

Role history
----------------
| date  | who | changelog |
|---|---|---|
|2020-11-02  | Christian Müller | intial commit for this role in codehub / initialy needed for rancher-things automation

License
-------

BSD

Author Information
------------------

Christian Müller (christian.mueller@sva.de), SVA GmbH, 11/2020
