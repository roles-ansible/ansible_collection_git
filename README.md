[![collection l3d.git](https://ansible.l3d.space/svg/l3d.git_ansible-collection_collection.svg)](https://galaxy.ansible.com/ui/repo/published/l3d/git/)
[![Maintainance](https://ansible.l3d.space/svg/l3d.git_maintainance_collection.svg)](https://ansible.l3d.space/#l3d.git)
[![License](https://ansible.l3d.space/svg/l3d.git_license_collection.svg)](LICENSE)

 Ansible Collection - l3d.git
============================

This is the Ansible Collection ``l3d.git``.
Here are all our ansible roles for installing git server.

## Ansible Roles in l3d.git
- [![l3d.git.gitea](https://ansible.l3d.space/svg/l3d.git.gitea_ansible-role.svg)](https://github.com/roles-ansible/ansible_role_gitea.git) - Ansible role to install gitea or forgejo git server
- [![l3d.git.forgejo_runner](https://ansible.l3d.space/svg/l3d.git.forgejo_runner_ansible-role.svg)](https://github.com/roles-ansible/ansible_role_forgeo_runner.git) - Ansible role to install forgejo runner

## Using this Collection
You can install the collection using ansible-galaxy by running:
```bash
ansible-galaxy collection install l3d.git:1.1.3
```

Remember you can to Upgrade to the latest version of the l3d.git collection using the ``--upgrade`` parameter:
```bash
ansible-galaxy collection install l3d.git --upgrade
```


Or you could clone this collection in your local ansible project for example to ``collections/ansible_collections/l3d/git/``. Make sure you checkout [git submodules](https://git-scm.com/docs/git-submodule) too. Example:
```
# Clone git Repo with submodules to specified path
git clone --recursive https://github.com/roles-ansible/ansible_collection_git.git collections/ansible_collections/l3d/git/

# change directory
cd collections/ansible_collections/l3d/git/

# optionally init git submodules
git submodule update --init --recursive

# optionally install all requirements
ansible-galaxy collection install -r requirements.yml --upgrade
```

You can also list a collection in ``requirements.yml``:
```yaml
---
collections:
  - name: l3d.git
    version: ">=1.1.3"
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

## Requirements
The roles in this collection using the ``ansible.builtin`` and ``community.general`` ansible Collections. To download the latest forgejo/gitea release we use json_query. This requires ``jmespath`` to be available.

### Example Requirements Installation:
```bash
# galaxy requirements
ansible-galaxy collection install -r requirements.yml --upgrade

# pip requirements
pip install -r requirements.txt
```
