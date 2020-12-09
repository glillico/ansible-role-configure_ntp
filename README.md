# Ansible Role : configure_ntp

[![CI](https://github.com/glillico/ansible-role-configure_ntp/workflows/CI/badge.svg)](https://github.com/glillico/ansible-role-configure_ntp/actions?query=workflow%3ACI)

This role installs and configures either `ntp` or `chrony` on RedHat and Debian based systems.

***NOTE:***<br>
The ntp package cannot be installed on a RedHat 8 based system using the standard repositories, as there is no package available.

## Requirements

None.

## Role Variables

### defaults/main.yml
|Variable|Description|
|---|:---|
|cntp_servers|A list of time servers to use.|

### vars/Debian.yml
|Variable|Description|
|---|:---|
|__cntp_ntp_service_name|The name of the ntp service.<br>(Options: ntp, chrony).|
|__cntp_ntp_package_name|The name of the ntp package.<br>(Options: ntp, chrony).|
|__cntp_configuration_file|Full path and name of the ntp service configuration file.<br>(Options: ntp:/etc/ntp.conf, chrony:/etc/chrony/chrony.conf).|
|cntp_driftfile|Full path and name of the ntp service drift file.<br>(Options: ntp:/var/lib/ntp/ntp.drift, chrony:/var/lib/chrony/chrony.drift).|
|cntp_leapseconds|Full path and name of the ntp service leap seconds file.<br>(Options: /usr/share/zoneinfo/leap-seconds.list).<br>**This applies to ntp only.**|
|cntp_keysfile|Full path and name of the ntp service configuration file.<br>(Options: /etc/chrony/chrony.keys).<br>**This applies to chrony only.**|

### vars/RedHat.yml
|Variable|Description|
|---|:---|
|__cntp_ntp_service_name|The name of the ntp service.<br>(Options: ntpd, chronyd).|
|__cntp_ntp_package_name|The name of the ntp package.<br>(Options: ntp, chrony).|
|__cntp_configuration_file|Full path and name of the ntp service configuration file.<br>(Options: ntp:/etc/ntp.conf, chrony:/etc/chrony.conf).|
|cntp_driftfile|Full path and name of the ntp service drift file.<br>(Options: ntp:/var/lib/ntp/drift, chrony:/var/lib/chrony/drift).|
|cntp_leapseconds|Full path and name of the ntp service leap seconds file.<br>(Options: /usr/share/zoneinfo/leapseconds).<br>**This applies to ntp only.**|
|cntp_keysfile|Full path and name of the ntp service configuration file.<br>(Options: /etc/chrony.keys).<br>**This applies to chrony only.**|

### vars/RedHat-8.yml
|Variable|Description|
|---|:---|
|__cntp_ntp_service_name|The name of the ntp service.<br>(Options: chronyd).|
|__cntp_ntp_package_name|The name of the ntp package.<br>(Options: chrony).|
|__cntp_configuration_file|Full path and name of the ntp service configuration file.<br>(Options: /etc/chrony.conf).|
|cntp_driftfile|Full path and name of the ntp service drift file.<br>(Options: /var/lib/chrony/drift).|
|cntp_keysfile|Full path and name of the ntp service configuration file.<br>(Options: /etc/chrony.keys).|

## Dependencies

None.

## Example Playbook

    - hosts: servers
      vars_files:
        - vars/main.yml
      roles:
        - glillico.configure_ntp

## License

MIT

## Author Information

Created in 2020 by Graham Lillico.
