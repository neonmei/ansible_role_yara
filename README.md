ansible_role_yara
=========

This role installs [yara](https://github.com/VirusTotal/yara).

Requirements
------------

Role has no external dependencies. Required build packages can be managed through `yara_build_deps_install` and `yara_build_deps_postrm`.

Role Variables
--------------

Most are self-explanatory, like `yara_version`, but I'll add notes on the not-so-evident ones:

**Installation**:

`yara_install_method`: At the moment only `source` is supported, but in the future I may add support for packages (for Windows, these are provided).

`yara_build_deps_postrm`: Setting to `true` removes build time dependencies. This may be desired on a server that uses Yara and doesn't want to leave `gcc` available.

`yara_src_dest_postrm`: Removes source tree after successful build and installation. Setting to `true` breaks idempotency.

`yara_build_prefix`: It's `/usr/local` by default, so yara will be at `/usr/local/bin/yara`. Remember to have that directory in `$PATH` or change prefix to `/usr`

**Connectivity**

`yara_src_proxy`: Sets a proxy for get_url for connectivity-restricted scenarios. See [Ansible documentation](https://docs.ansible.com/ansible/latest/user_guide/playbooks_environment.html#setting-the-remote-environment-in-a-task) for more information.

`yara_src_url`: If requirements are pulling sources from a private network, this should be updated.

`yara_src_checksum`: If version/url is updated, this should be updated too.


Dependencies
------------

None.

License
-------

GPLv3.
