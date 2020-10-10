# Ansible Role: Time Capsule

Sets up `samba` for use as a Time Capsule with Mac OS X.

## Requirements

Only tested with Fedora 32.

Note that this role will completely overwrite any existing configuration for `samba`.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

* `timecapsule_username` (default: "simon")
  Username for logging into the network share.
  This user will also be created on the OS to set the filesystem permissions.

* `timecapsule_password` (default: "supersecret")
  Password for logging into the network share.
  This password is only used for the network share.

* `timecapsule_folder` (default: "/timecapsule")
  Folder that is used to store the network share data.

* `timecapsule_share_name` (default: "TimeMachine")
  Name of the network share

## Example Playbook

    - hosts: servers
      roles:
         - role: simonkrenger.timecapsule
           vars:
             timecapsule_username: "simon"
             timecapsule_password: "evenmoresecret"
             timecapsule_folder: "/timecapsule"
             timecapsule_share_name: "TimeMachine"

After deploying this role, connect to the network share using the following address using "Connect to server" in Finder:

```
smb://simon@<IP-of-your-machine>/TimeMachine
```

After connecting, this share can then be used as a Time Machine Disk.

## License

MIT

## Author Information

This role was created in 2020 by [Simon Krenger](https://www.krenger.ch).