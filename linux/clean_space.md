## commands to clean space on arch linux systems

# Vacuum journals
sudo journalctl --vacuum-size=500M && sudo journalctl --vacuum-time=7d

# Remove all uninstalled packages
sudo paccache -rvuk0

# Remove old installed packages, leave 3
sudo paccache -rvk3

# Clean yay cache
yay -Sc -a

# Clean pamac build cache
pamac clean -bv

# Clean temporary build files
rm -rf ~/{.bundle,.cargo,.cmake,.dotnet,.electron,.electron-gyp,.gem,.gradle,.lazarus,.node-gyp,.npm,.nuget,.nvm,.racket,.rustup,.stack,.yarn} || true
rm -rf ~/.cache/{electron,electron-builder,go-build,node-gyp,pip,yarn} || true
sudo rm -rf ~/go || true

# Find files not owned by any package
sudo lostfiles


#Remove orphaned libraries
pamac remove --orphans
#clean cache
pamac clean --build-files
# Clean kioexec cache
rm --recursive ~/.cache/kioexec/krun/*