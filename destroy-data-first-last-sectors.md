# Destroy data on a filesystem by wiping first and last sectors
## Wipe the first 1GB
```
dd if=/dev/zero of=/dev/sdX bs=1M count=1024
```
## Wipe the last 1MB
Some RAID configuration data might be present at the end of the disk, thus existing the need to delete this data, before reusing the disk
```
dd bs=1M if=/dev/zero of=/dev/sdX count=1024 seek=$((`blockdev --getsz /dev/sdX` - 1024))
```
