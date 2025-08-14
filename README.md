onkf.proxmox_ve
===============

This role does basic configuration of a proxmox virtual environment node:
* proxmox ve and ceph repository choice
* microcode installation

Requirements
------------

* Proxmox VE 9 (is checked via `Debian 13` conditional)

Role Variables
--------------

| name              | type     | default           | optional | comment                                                                              |
| ---               | ---      | ---               | ---      | ---                                                                                  |
| `pve_repository`  | `string` | `no-subscription` | yes      | which pve repository to use. valid repos: `enterprise`, `no-subscrption` and `test`  |
| `ceph_repository` | `string` | `no-subscription` | yes      | which ceph repository to use. valid repos: `enterprise`, `no-subscrption` and `test` |
| `ceph_version`    | `string` | `squid`           | yes      | which ceph version to use. valid versions: `squid`                                   |

Dependencies
------------

/

Notes
-----

### repository settings

We use the recommendations from [Proxmox Package Repositories](https://pve.proxmox.com/wiki/Package_Repositories) to configure our repos.
Therefore we take full control of `/etc/apt/sources.list`.

Additionally the following files will be written

* `/etc/apt/sources.list.d/ceph.list` and
* `/etc/apt/sources.list.d/pve-enterprise.list`

Example Playbook
----------------

    - hosts: servers
      roles:
         - onkf.proxmox_ve

License
-------

MIT

Author Information
------------------

Gregor Michels <gregor@brainpeach.de>
