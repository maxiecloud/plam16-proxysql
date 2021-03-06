PerconaLive Amsterdam 2016 - ProxySQL Tutorial
===

## Overview
Files for proxysql tutorial at PLAM16

## Dependencies

- Docker
- Ansible (_version:_ 2.1.0+)
- [ProxySQL Ansible modules](https://github.com/bmildren/proxysql_ansible_modules)
    - Create a symlink in the ansible directory `library` to the ansible plugins previously copied

```bash
$ ls -l ansible/library
lrwxr-xr-x  1 dtest  staff  43 Sep 14 20:51 ansible/library -> /Users/dtest/devel/proxysql_ansible_modules
```
- Bash

## Setup

- Connect as root: `sudo su -`
- Change directory: `cd ~/dba/admin/dev/plam16-proxysql`
- Run `./run_proxy.sh`
- If that command fails for failed connecting to MySQL, run: `cd ansible && time ansible-playbook -i inventory setup.yml`
- Connect to ProxySQL Admin interface: `./mysql -h proxy-admin`
- Connect to ProxySQL SQL interface: `./mysql -h proxy-sql`
- Connect to hosts used for rewrite and failover demonstrations
    - master: `./mysql -h master`
    - slave: `./mysql -h slave`
- Connect to hosts used for mirroring demonstration
    - MySQL A (5.6): `./mysql -h mysqla`
    - MySQL B (5.7): `./mysql -h mysqlb`
