# Android file transfer to Linux

https://wiki.archlinux.org/title/android#Transferring_files

On the phone, select USB preferences to "File transfer" or "MTP" or something like that
sudo pacman -S android-file-transfer
mkdir ~/mnt
aft-mtp-mount ~/mnt
Then navigate to ~/mnt.
