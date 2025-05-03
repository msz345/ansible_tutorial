# ansible_tutorial

<https://www.youtube.com/watch?v=3RiVKs8GHYQ&list=PLT98CRl2KxKEUHie1m24-wkyHpEsa4Y70&index=1&pp=iAQB>

## Commands explained

Test Ansible is working

```bash
ansible all --key-file ~/.ssh/ansible -i inventory -m ping
```

List all of the hosts in the inventory

```bash
ansible all --list-hosts
```

Gather facts about your hosts

```bash
ansible all -m gather_facts
```

Tell ansible to use sudo (become)

```bash
ansible all -m apt -a update_cache=true --become --ask-become-pass
```

Install a package via the apt module

```bash
ansible all -m apt -a name=vim-nox --become --ask-become-pass
```

Install a package via the apt module, and also make sure it’s the latest version available

```bash
ansible all -m apt -a "name=snapd state=latest" --become --ask-become-pass
```

Upgrade all the package updates that are available

```bash
ansible all -m apt -a upgrade=dist --become --ask-become-pass
```

Run the playbook

```bash
ansible-playbook --ask-become-pass install_apache.yml
```

List the available tags in a playbook

```bash
ansible-playbook --list-tags site.yml
```

Examples of running a playbook but targeting specific tags

```bash
ansible-playbook --tags db --ask-become-pass site.yml
ansible-playbook --tags centos --ask-become-pass site.yml
ansible-playbook --tags apache --ask-become-pass site.yml
```

Run bootstrap playbook to setup mandatory user, then run site playbook to setup all servers.

```bash
ansible-playbook --ask-become-pass ./playbooks/bootstrap.yml
ansible-playbook site.yml
```
