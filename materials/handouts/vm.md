# Setting up a Virtual Machine

This guide walks you through setting up a Virtual Machine to run class code with.

First, download the Ubuntu ISO here: <https://releases.ubuntu.com/jammy/ubuntu-22.04.1-desktop-amd64.iso>

## Windows

Download VMware Workstation Player here: <https://www.vmware.com/products/workstation-player/workstation-player-evaluation.html>[^1]

Run the installer. If requested to restart, do so and run the installer again.

If you have an international keyboard, you might want to check "Enhanced Keyboard Driver". Other than that you can just keep clicking "Next", "Install", then "Finish".

Open VMware Player, click "Install a New Virtual Machine", choose "Installer disc image file" and select the Ubuntu ISO you downloaded earlier. Enter your name, username and password. The default machine name and disk size are fine. When prompted, install VMware Tools for Linux.

Once Ubuntu is installed, install updates and restart the VM if prompted.

If you find the VM or other programs on your host system running very sluggishly, you might want to reconfigure the CPU/RAM allocation.

## Mac

Download VMware Fusion here: <https://www.vmware.com/products/fusion/fusion-evaluation.html>[^1]

Choose Fusion 12 Player (not Fusion 12 Pro, that puts you on a 30-day trial). You will need to create an account and register for a Personal Use License.

Open VMware Fusion. Click the "+" sign at the top, and click "New".

Drag the Ubuntu ISO from Finder into "Install from disc or image". Complete the installation.

Once Ubuntu is installed, install updates and restart the VM if prompted.

If you find the VM or other programs on your host system running very sluggishly, you might want to reconfigure the CPU/RAM allocation.

[^1]: MIT offers pro versions of VMware software [here](https://ist.mit.edu/vmware). Consider downloading the VMware software from there instead!
