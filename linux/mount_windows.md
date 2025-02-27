## How to check and mount a windows partition on linux OS(/dev/nvme0n1p5 is an example)

- sudo ntfsfix /dev/nvme0n1p5

__Check if Windows was properly shut down__

- sudo mount -t ntfs-3g /dev/nvme0n1p5 /mnt

__Mount partition manually__

- mkdir -p ~/windows_data
sudo mount -t ntfs-3g /dev/nvme0n1p5 ~/windows_data

__Optional: create a folder in the home directory to mount the partition__