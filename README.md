# ansible_tutorial

<https://www.youtube.com/watch?v=3RiVKs8GHYQ&list=PLT98CRl2KxKEUHie1m24-wkyHpEsa4Y70&index=1&pp=iAQB>

## Commands explained

Test Ansible is working

```ansible all --key-file ~/.ssh/ansible -i inventory -m ping```

List all of the hosts in the inventory

```ansible all --list-hosts```

Gather facts about your hosts

```ansible all -m gather_facts```

Tell ansible to use sudo (become)

```ansible all -m apt -a update_cache=true --become --ask-become-pass```

Install a package via the apt module

```ansible all -m apt -a name=vim-nox --become --ask-become-pass```

Install a package via the apt module, and also make sure it’s the latest version available

```ansible all -m apt -a "name=snapd state=latest" --become --ask-become-pass```

Upgrade all the package updates that are available

```ansible all -m apt -a upgrade=dist --become --ask-become-pass```

Run the playbook

```ansible-playbook --ask-become-pass install_apache.yml```
