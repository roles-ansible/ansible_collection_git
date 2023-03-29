 Ansible Collection - l3d.git
============================

This is the Ansible Collection l3d.git.
Here are all our ansible roles for installing git server.

## Roles in l3d.git
- [l3d.git.gitea](https://github.com/roles-ansible/ansible_role_gitea.git) - Ansible role to install gitea or forgejo git server

## Using this Collection
You can install the collection using ansible-galaxy by running:
```bash
ansible-galaxy collection install l3d.git
```

Or you could clone this collection in your local ansible project as ``collections/ansible_collections/l3d/git/``.

You can also list a collection in ``requirements.yml``:
```yaml
---
collections:
  - name: l3d.git
```

## Include roles in your playbook
Example Playbook using the l3d.git.gitea role:
```yaml
---
- name: "Install forgejo git server from collection l3d.git"
  hosts: git.example.com
  roles:
    - {role: l3d.git.gitea, tags: forgejo}
  vars:
    # Here we assume we are behind a reverse proxy that will
    # handle https for us, so we bind on localhost:3000 using HTTP
    # see https://docs.gitea.io/en-us/reverse-proxies/#nginx
    gitea_fqdn: 'git.example.com'
    gitea_root_url: 'https://git.example.com'
    gitea_protocol: http
    gitea_start_ssh: true
    gitea_fork: 'forgejo'
```
