### Step-by-Step Guide to Extend the Root Partition

This guide outlines the process to extend the root partition by creating a new partition, configuring it for LVM, and resizing the filesystem.

---

1.  **Create a New Partition with Free Space**

    Use `parted` to create a new partition in the free space on your disk.

    \`\`\`bash
    sudo parted /dev/sda
    (parted) mkpart primary 37.6GB 137.6GB
    (parted) print   # Confirm the new partition is created
    (parted) quit
    \`\`\`

    - **Note**: Adjust the start and end points (`37.6GB` and `137.6GB`) based on the available free space on your disk.

2.  **Format the New Partition as a Physical Volume (PV)**

    Format the newly created partition for use with Logical Volume Management (LVM).

    \`\`\`bash
    sudo pvcreate /dev/sda4   # Assuming /dev/sda4 is the new partition
    \`\`\`

3.  **Extend the Volume Group (VG)**

    Add the new physical volume to your existing volume group (e.g., `ubuntu--vg`).

    \`\`\`bash
    sudo vgextend ubuntu--vg /dev/sda4
    \`\`\`

4.  **Extend the Logical Volume (LV)**

    Increase the size of the logical volume. Here, we’re expanding it to a total of 100GB.

    \`\`\`bash
    sudo lvextend -L 100G /dev/ubuntu--vg/ubuntu--lv
    \`\`\`

    - **Note**: Replace `100G` with your desired total size or specify `-l +100%FREE` to use all available free space in the volume group.

5.  **Resize the Filesystem**

    Adjust the filesystem to occupy the newly allocated space in the logical volume.

    \`\`\`bash
    sudo resize2fs /dev/ubuntu--vg/ubuntu--lv
    \`\`\`

6.  **Verify the New Size**

    Confirm that the root filesystem has been resized successfully.

    \`\`\`bash
    df -h /
    \`\`\`

    - **Output**: This command displays the updated size and usage of the root partition.

---

### Additional Notes

- **Physical Volume (PV)**: This is a partition or disk configured for use with LVM. The `pvcreate` command prepares the partition for inclusion in a volume group.
- **Volume Group (VG)**: A volume group aggregates physical volumes, making it easier to manage and resize storage.
- **Logical Volume (LV)**: Logical volumes are like partitions within a volume group and can be resized to add more storage as needed.

By following these steps, you can successfully extend your root partition and allocate more storage to the filesystem.
