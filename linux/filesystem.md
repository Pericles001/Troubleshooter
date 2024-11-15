## How to Check and Repair Filesystem

The `fsck` (file system consistency check) command is used to check and repair inconsistencies in file systems.

### Steps to Check and Repair a Filesystem

1. **Identify the Filesystem**: Determine the device name of the filesystem you want to check. For example, `/dev/sda6`.

2. **Unmount the Filesystem**: Before running `fsck`, ensure the filesystem is unmounted to avoid data corruption.
   ```bash
   sudo umount /dev/sda6