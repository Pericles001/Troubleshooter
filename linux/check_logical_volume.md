-   **Check Existing Volume Groups**: Run the following command to list all volume groups on your system:

    bash

    Copy code

    `sudo vgdisplay`

    This command will display the available volume groups. Look for the name of the volume group that your root filesystem (`/`) is part of.

    -   **Check Logical Volumes**: If a volume group is found, list the logical volumes within it to confirm the root filesystem setup:

    bash

    Copy code

    `sudo lvdisplay`