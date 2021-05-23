#  BjoernCFischer.unifi-controller

An ansible role to install and configure [Ubiquiti Unifi Controller](https://www.ubnt.com/enterprise/software/)

## History

The role was forked from [nephelaiio's unifi-controller role](https://github.com/nephelaiio/ansible-role-unifi-controller/). 

__2021-05-24__

Changes for improved Raspberry Pi support:
  * System's mongodb service is stopped and disabled
  * [Workaround](https://community.ui.com/questions/UniFi-controller-cant-connect-to-MongoDB-if-localhost-is-1/a403a2ee-b5f5-430a-834e-21045f35054f) for systems with IPv6 localhost (::1) is applied

No unit tests were changed.

## Role Variables

Please refer to the [defaults file](/defaults/main.yml) for an up to date list of input parameters

## Example Playbook

Unifi installation on regular x86_64 hardware

```
- hosts: unifi
  roles:
     - role: unifi-controller
```

Unifi installation on raspberry pi
```
- hosts: unifi
  roles:
     - role: unifi-controller
  vars:
    unifi_java_packages: openjdk-8-jre-headless
    unifi_java_home: /usr/lib/jvm/java-8-openjdk-armhf/jre
```

## Testing

Please make sure your environment has [docker](https://www.docker.com) installed in order to run role validation tests. Additional python dependencies are listed in the [requirements file](https://github.com/nephelaiio/ansible-role-requirements/blob/master/requirements.txt)

Role is tested against the following distributions (docker images):
  * Ubuntu Focal
  * Ubuntu Bionic

You can test the role directly from sources using command ` molecule test `

## License

This project is licensed under the terms of the [MIT License](/LICENSE)
