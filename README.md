# Ansible Role: quaded.bootstrap

Auxiliary role for other quaded.* roles.

This role: 
- Creates users (for your's apps defined in other roles)
- Import your's local ssh public key
- Sets timezone and install ntp chrony (see `defaults/main.yml`)
- Change ssh port (if it changed in `ssh_port` variable)
- Adds epel repo

---

**Example Playbook (only mandatory variables)**
```
- hosts: my-server.com
  roles:
    - role: quaded.bootstrap
  vars:
    users:
    - username: user1
    - username: user2
```
Creates 2 users with homes `/home/user1` and `/home/user2`.

**More detailed example**
```
- hosts: my-server.com
  roles:
    - role: quaded.bootstrap
  vars:
    users:
    - username: user1
    - username: user2
    ssh_port: 8022
    system_timezone: "UTC"
    install_ntp: False
    install_firewalld: True
    add_epel_repo: False
```
But better to set this global variables in the `roles/quaded.bootstrap/vars/main.yml` or `host_vars/` to better look of your's `main.yml`.

---

## Supported OS
- CentOS/RHEL (7,8)
- Ubuntu (16.04/18.04/19.10)
- Debian (8,9,10)