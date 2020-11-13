# Ansible Role: raid

Configures software raid devices and mounts them.
If any disks or raid devices are detected on the target host, the config defined by that element in `raid_arrays` will be skipped

## Requirements

Any disks passed through role variables must be present, the role will deliberately fail otherwise.

## Role variables

`raid_array`: list of dictionaries containing the required configs
 The role will create a filesystem on the device it creates

## Example Raid Array
```yaml
raid_arrays:
  - device: /dev/md0 (req. raid device to create)
    disks: (req. list of disks to add to the array)
      - /dev/sdb
      - /dev/sdc
    level: 1 (req. Raid level, supports anything mdadm supports)
    layout: fX (opt. no default)
    filesystem: xfs (opt. def xfs filesystem to create on the device)
    filesystem_opts: (opt. default omit)
    mountpoint: /mnt/raid (req. where to mount it)
    mount_opts: (opt. default omit)
```
