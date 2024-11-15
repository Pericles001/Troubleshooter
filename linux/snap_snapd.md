# Installing and Configuring Snapd on Arch Linux

This guide provides step-by-step instructions to install and configure Snapd on Arch Linux.

---

## 1. Install Snapd

To install Snapd, use the following `pacman` command:

\`\`\`bash
sudo pacman -S snapd
\`\`\`

---

## 2. Activate the Snapd Service

Enable the Snapd service so it starts immediately and on each boot:

\`\`\`bash
sudo systemctl enable --now snapd.socket
\`\`\`

---

## 3. Create a Symbolic Link for Snap

For Snap to function properly, create a symbolic link to the Snapd directory:

\`\`\`bash
sudo ln -s /var/lib/snapd/snap /snap
\`\`\`

---

## 4. Test the Installation

To confirm that Snapd is working correctly, install a test package, such as `hello-world`:

\`\`\`bash
sudo snap install hello-world
\`\`\`

If the installation is successful, Snapd is ready to use.

---

## Additional Notes

- **Snapd Socket**: The `snapd.socket` is a systemd unit that enables Snap's communication service. Running this command with `enable --now` ensures Snapd will activate immediately and on startup.
- **Symbolic Link**: The symbolic link allows `snap` commands to access the required directory directly, ensuring smooth operation on Arch Linux.
