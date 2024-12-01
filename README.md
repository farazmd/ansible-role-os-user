# Ansible Role OS User
Helps to create and manage OS users


## Role Variables

The role takes 2 main variables `user_groups` and `users`.

The `user_groups` is a list that consits of group info to create groups in OS.
```yaml
user_groups:
  - group_name: "name of the group"
    gid: "group id to use (optional)"
    system: "true or false"
    state: "present or absent"
```

The `users` variable is a list that consists of user info.
```yaml
users:
  - username: "user name to create"
    state: "present or absent"
    additional_groups: 
      - test # Additional groups to add to this user
    create_home: "true or false" # To create a home directory
    is_system: "true or false" # To create a system user
    add_sudo: "true or false" # To add user to sudoers
    authorized_key: "Public key to add to .ssh/authorized_keys file" # To add SSH public key 
```

## Example Playbook

```yaml
- hosts: servers
  roles:
    - ansible-role-os-user
```