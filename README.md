# Gitea Ansible role

Ansible role to install gitea.

## Example usage

We have taken a simple approach where the app.ini must be
defined entirely when the role is used. This is a bit
verbose, but is very flexible and reduces needing to define
100's of variables to build up `app.ini`.

```
- name: Git server
  hosts: git3
  become: yes
  roles:
    - { role: users, tags: users }
    - role: gitea
      tags: gitea
      gitea_app_ini: |
        APP_NAME = XYZ Git Server
        RUN_USER = git
        RUN_MODE = prod

        [security]
        INTERNAL_TOKEN = eyJhbJIUzIInR5cCI6IkpXVCJ9.eyJuYmYiOjE1NTIzMzA3Mzl9.H5ErUKo1nZkpOgbUzy5Ra15RkyXlUqTokYZYmFgXJvc
        INSTALL_LOCK   = true
        SECRET_KEY     = IoTyXO79oTz9eZncj2KJwhwX7ilKe1TGiTCqYa4wqQRGBhcTYkP

        [database]
        DB_TYPE  = sqlite3
        HOST     = 127.0.0.1:3306
        NAME     = gitea
```
