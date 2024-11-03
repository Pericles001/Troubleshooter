### Step-by-Step Guide to Extend the Root Partition

1.  **Create a New Partition with Free Space**: Use `parted` to create a new partition in the free space.

    bash

    Copy code

    `sudo parted /dev/sda
    (parted) mkpart primary 37.6GB 137.6GB
    (parted) print  # Confirm the new partition is created
    (parted) quit`

2.  **Format the New Partition as a Physical Volume (PV)**: Format the new partition for LVM use.

    bash

    Copy code

    `sudo pvcreate /dev/sda4  # Assuming /dev/sda4 is the newly created partition`

3.  **Extend the Volume Group (VG)**: Add the new physical volume to your existing volume group (`ubuntu--vg`).

    bash

    Copy code

    `sudo vgextend ubuntu--vg /dev/sda4`

4.  **Extend the Logical Volume (LV)**: Increase the size of the logical volume to 100GB.

    bash

    Copy code

    `sudo lvextend -L 100G /dev/ubuntu--vg/ubuntu--lv`

5.  **Resize the Filesystem**: Resize the filesystem to use the newly allocated space.

    bash

    Copy code

    `sudo resize2fs /dev/ubuntu--vg/ubuntu--lv`

6.  **Verify the New Size**: After completing the steps, verify the new size.

    bash

    Copy code

    `df -h /`