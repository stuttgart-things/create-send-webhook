stuttgart-things/create-send-webhook
=======================================

configure and send customized webhooks to targets like MS TEAMS (supports connector cards).

<details><summary>ROLE INSTALLATION</summary>

installs role and all of it's dependencies w/:

```bash
cat <<EOF > /tmp/requirements.yaml
roles:
- src: https://github.com/stuttgart-things/create-send-webhook.git
  scm: git
collections:
- name: community.general
  version: 8.6.0
EOF

ansible-galaxy install -r /tmp/requirements.yaml --force
ansible-galaxy collection install -r /tmp/requirements.yaml -f
rm -rf /tmp/requirements.yaml
```

</details>

<details><summary>EXAMPLE INVENTORY</summary>

```bash
cat <<EOF > inventory
[appserver]
1.2.3.4 ansible_user=sthings
EOF
```

</details>

<details><summary>EXAMPLE PLAYBOOK - BASIC DOCKER AND DOCKER COMPOSE INSTALLATION</summary>

```yaml
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

</details>

<details><summary>EXAMPLE EXECUTION</summary>

```bash
ansible-playbook create-send-webhook.yaml -vv
```

```bash
ansible-playbook create-send-webhook.yaml -e send_to_homerun=true -vv
```

</details>


## License
<details><summary>LICENSE</summary>

Copyright 2020 patrick hermann.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
</details>

Role history
----------------
| date  | who | changelog |
|---|---|---|
|2024-24-05  | Andre Ebert | incremented webhook version, removed tasks with missing config
|2020-11-02  | Christian Müller | intial commit for this role in codehub / initialy needed for rancher-things automation



Author Information
------------------

```yaml
Andre Ebert (andre.ebert@sva.de), 05/2024

Christian Müller (christian.mueller@sva.de), SVA GmbH, 11/2020
```
