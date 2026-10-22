# Phansible Role: ZooKeeper

[![CI](https://github.com/phansible/role-zookeeper/actions/workflows/ci.yml/badge.svg)](https://github.com/phansible/role-zookeeper/actions/workflows/ci.yml)

An Ansible Role that installs [ZooKeeper](https://zookeeper.apache.org/) on Ubuntu and Debian specifically created with [Phansible](http://phansible.com/) in mind.

## Requirements

- Ubuntu 22.04, 24.04, 26.04 or Debian 12, 13 (x86_64)
- Ansible >= 2.15

ZooKeeper is installed from the official Apache release tarball (verified against its published SHA-512) and runs on the distro's default OpenJDK as a systemd service. The C client library and headers come from the distro's `libzookeeper-mt-dev` package.

## Role Variables

| Variable | Default | Description |
| --- | --- | --- |
| `zookeeper_version` | `3.9.6` | ZooKeeper release to install. |
| `zookeeper_port` | `'2181'` | Client port written to `zoo.cfg`. |
| `zookeeper_filename` | `apache-zookeeper-{{ zookeeper_version }}-bin` | Release archive name, also the directory created under `/opt`. |
| `zookeeper_filename_extension` | `.tar.gz` | Release archive extension. |
| `zookeeper_path` | `/opt/zookeeper` | Symlink pointing at the installed release. |
| `zookeeper_user` | `zookeeper` | System user that owns and runs ZooKeeper. |
| `zookeeper_var_path` | `/var/zookeeper` | Holds `zoo.cfg` and `logback.xml`; data lives in `{{ zookeeper_var_path }}/data`. |
| `zookeeper_url` | `https://archive.apache.org/dist/zookeeper` | Where the archive and its `.sha512` are downloaded from. |

## Dependencies

None.

## Example Playbook

```yaml
- hosts: all
  become: yes
  roles:
    - role-zookeeper
```

## License

This role is released under the terms of the license specified in the repository or if not specified, under the [MIT license](https://raw.githubusercontent.com/phansible/role-zookeeper/master/LICENSE).

## Author Information

This role was created in 2015 by [The Phansible Team & Contributors](https://github.com/phansible/role-zookeeper/graphs/contributors), credits go also to [Jeff Geerling](http://jeffgeerling.com/), author of [Ansible for DevOps](http://ansiblefordevops.com/) and source of inspiration.
