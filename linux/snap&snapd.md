## INSTALL SNAPD
- sudo pacman -S snapd

## ACTIVATE SERVICE
- sudo systemctl enable --now snapd.socket
## SYMBOLIC LINK (SNAP)
- ln -s /var/lib/snapd/snap /snap
## TEST
- sudo snap install hello-world