# Destroy data on a filesystem by wiping first and last sectors
## Wipe the first 1GB
```
dd if=/dev/zero of=/dev/sdX bs=1M count=1024
```
## Wipe the last 1MB
Some RAID configuration data might be present at the end of the disk, thus existing the need to delete this data, before reusing the disk
```
DISK="/dev/sde"
SIZE=$(sudo blockdev --getsize64 ${DISK})
dd if=/dev/zero of=${DISK} bs=1M seek=$((SIZE / 1048576 - 1024)) count=1024 conv=fsync status=progress
```

Depending on your Linux distro, you might have to use `--getsz` instead of `--getsize` as a parameter for `blockdev`. Check `man blockdev` before running the above commands!
