Docker Role
=========

This role installs docker on a host with basic configuration : 

- Docker group is created
- Docker users are added to the group
- `/etc/docker/daemon.json` with user-defined configuration is created
- Docker service is started and enabled

Requirements
------------

- [Ansible](https://www.ansible.com/) - Ansible must be installed to execute the playbook.

Role Variables
--------------

| Variable | Description | Default |
|----------|-------------|---------|
| `docker_users` | List of users to add to the docker group | `[]` |
| `docker_daemon_config` | Dictionary of configuration to add to `/etc/docker/daemon.json` | `{}` |

Dependencies
------------

None.

Example Playbook
----------------

File `inventory/hosts_vars/host` for server example :

```yaml
docker_users:
  - user1
  - user2
docker_daemon_config: |
  "no-new-privileges": true,
  "debug": true
```

Playbook example : 
```
- hosts: servers
  roles:
    - docker
```

License
-------

BSD
