# Ansible Role: litestream

[![CircleCI](https://circleci.com/gh/mtlynch/ansible-role-litestream.svg?style=svg)](https://circleci.com/gh/mtlynch/ansible-role-litestream)
[![License](http://img.shields.io/:license-mit-blue.svg?style=flat-square)](LICENSE)

## Overview

Ansible role to install and configure Litestream. Currently, it's limited to just file paths as replica locations.

## Role Variables

See [defaults/main.yml](https://github.com/mtlynch/ansible-role-litestream/blob/master/defaults/main.yml) for full list:

```yaml
litestream_version: "0.3.5"
litestream_db_path: null
litestream_replica_file_path: null
litestream_config_file_owner: null
litestream_config_file_group: null
litestream_config_file_mode: "0640"
litestream_service_enabled: no
litestream_service_state: null
```

## Dependencies

None

## Example Playbook

The example below configures litestream to replicate a SQLite database at `/some/source/db.sqlite3` to a backup path at `/mnt/backup/db`.

### `example.yml`

```yaml
- hosts: litestream
  roles:
    - role: ansible-role-litestream
      vars:
        litestream_db_path: "/some/source/db.sqlite3"
        litestream_replica_file_path: "/mnt/backup/db"
        litestream_config_file_mode: "0640"
        litestream_service_enabled: yes
        litestream_service_state: started
```

### Running Example Playbook

```bash
ansible-galaxy install git+https://github.com/mtlynch/ansible-role-litestream.git
ansible-playbook example.yml
```

## License

MIT

## Author Information

This role was created in 2021 by [Michael Lynch](http://mtlynch.io).
