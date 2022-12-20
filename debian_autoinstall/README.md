# Debian Autoinstall .iso Generator

The basic goal here is to genereate a preseeded unattended/self-installing .iso image.
Similar to/inspired by [ansible-role-ubuntu\_autoinstall](https://github.com/notthebee/ansible-role-ubuntu_autoinstall) but currently standalone.
The install is somewhat minimal since the expectation is that it will be completed later by another ansible workflow.

Caveat: These are baby steps with Debian and Ansible, which is good for flushing out the "things I didn't realize I didn't know" :)

## Use
```
ansible-playbook -i main.yml
```

The `preseed.cfg` is generated from a template based off [example-preseed.txt](https://www.debian.org/releases/bullseye/example-preseed.txt).
The necessary variables should be in `config.yml` (see `example.config.yml`)

*NOTE* Repartitions and wipes the disk (`/dev/sda`)

## TODO
- Add ssh key
- Figure out the partitioning
- Step 2, preserve `/home` or other persistent partitions
- Clean up temporary extracted image
- Details of UEFI and boot menu
- Better config/support multiple hosts
