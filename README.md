# Ansible Role: sshd

Set up a secure config for OpenSSH Server

* Change the sshd port
* Disable SSH version 1
* Disable root login

## Requirements

* 执行本role之前请确认已经添加了除了root以外拥有管理权限的用户.
* 如果不更改sshd的端口,请将`sshd_setup_firewall`设置为false,否则防火墙设置会报错.

## Role Variables

###  `defaults/main.yml`
*default lower priority variables for this role*

* `sshd_port: 22`
* `sshd_use_dns: no`
* `sshd_gssapi_authentication: no`
* `sshd_security: false`
* `sshd_protocol: 2`
* `sshd_permit_root_login: no`
* `sshd_password_authentication: yes`
* `sshd_setup_firewall: true`

###  `vars/RedHat.yml`
The variables for RedHat/CentOS

* `sshd_config_path: /etc/ssh/sshd_config`
* `sshd_service_name: sshd`

## Dependencies

None.

## Example Playbook

    - name: update SSH configuration to be more secure
      hosts: servers
      vars:
        sshd_port: 22
        sshd_security: true              # enabled sshd security configure
        sshd_setup_firewall: false        # if not change the sshd port
      roles:
        - sshd

## License

MIT / BSD

## Author Information

z
