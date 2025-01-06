---
title: Install Debian 12 on Dell Wyse 3040 Thin-Client
description: Learn how to install Debian 12 on the Dell Wyse 3040 Thin Client to
  create a reliable and flexible operating system for your projects.
---

# Install Debian 12 on Dell Wyse 3040 Thin-Client
This guide will walk you through the process of installing Debian 12, ensuring a
reliable and flexible operating system for your projects.  

## Download Debian 12
Download the latest Debian 12 image for your Dell Wyse 3040 Thin Client from the
official Debian website.

- [Debian 12.8.0 (Bookworm) Netinst ISO](https://cdimage.debian.org/debian-cd/current/amd64/iso-cd/debian-12.8.0-amd64-netinst.iso)

## Create a Bootable USB Drive
Create a bootable USB drive using the downloaded Debian 12 image. You can use
tools like [Rufus](https://rufus.ie/) on Windows or `dd` on Linux/Mac to write
the image to the USB drive.

### Using dd on Linux/Mac
1. Identify the USB drive using `lsblk` or `diskutil list`.
2. Unmount the USB drive with `umount /dev/sdX` or `diskutil unmountDisk
   /dev/diskX`.
3. Write the Debian 12 image to the USB drive using `dd`. Replace `/dev/sdX` or
   `/dev/diskX` with your USB drive identifier.
   ```bash
   sudo dd bs=4M if=debian-12.8.0-amd64-netinst.iso of=/dev/sdX; sync
   ```
4. Eject the USB drive with `eject /dev/sdX` or `diskutil eject /dev/diskX` on
   Mac.

## BIOS/UEFI Settings to Boot from USB Drive
Before installing Debian 12 on your Dell Wyse 3040 Thin Client, you need to
change the BIOS/UEFI settings to boot from the USB drive.

1. Insert the bootable USB drive into your Dell Wyse 3040 Thin Client.
2. Power on your Dell Wyse 3040 Thin Client.
3. Press the `F2` key repeatedly during boot to enter the BIOS/UEFI settings.
4. Navigate to the `General > Boot Sequence` tab using the arrow keys.
5. Enable the USB Storage Boot option. (In my case, it was `UEFI: SanDisk Cruzer
   Micro 8.02, Partition 1`.)
6. Change the boot order to prioritize the USB drive.
7. Click `Apply` and `Exit` to save the changes and reboot.

<figure markdown="span">
    ![Dell Wyse 3040 BIOS/UEFI Settings](img/dell-wyse-3040-bios-uefi-settings.png)
    <figcaption>Dell Wyse 3040 BIOS/UEFI Settings</figcaption>
</figure>

## Boot from USB Drive and Install Debian 12
1. Your Dell Wyse 3040 Thin Client should now boot from the USB drive.
2. Choose the `Graphical Install` option to start the Debian 12 installation
   process with a graphical interface.
   ![Debian 12 Graphical Install](img/debian-12-graphical-install.png)
3. Choose your preferred language, location, and keyboard layout.
4. Enter the hostname for your Dell Wyse 3040 Thin Client. (In my case, I used
   `dell-mainsail`.)
   ![Debian 12 Hostname](img/debian-12-hostname.png)
5. Enter the domain name if required. (You can leave it blank if not needed.)
   ![Debian 12 Domain Name](img/debian-12-domain-name.png)
6. Set the root password for your Dell Wyse 3040 Thin Client.
   ![Debian 12 Root Password](img/debian-12-root-password.png)
7. Create a new user account for your Dell Wyse 3040 Thin Client and type in the
   friendly name for the user. (In my case, I created a user named `klipper`.)
   ![Debian 12 User Account](img/debian-12-user-account.png)
8. Set the username for the new user account. (Just press `Enter` to use the
   same username as the friendly name.)
   ![Debian 12 Username](img/debian-12-username.png)
9. Set the password for the new user account.
   ![Debian 12 User Password](img/debian-12-user-password.png)
10. The next step is the Disk partitioning. This will be a little bit tricky
    because of the limited internal storage of the Dell Wyse 3040 Thin Client.
    In the first step, you need to choose `Guided - use entire disk` for a simple
    pre partitioning setup.
    ![Debian 12 Disk Partitioning](img/debian-12-disk-partitioning.png)
11. Select the disk to partition. (In my case, it was
    `MMC/SD Card #1 (mmcblk0) - 7.8 GB MMC H8G4A?`.)
    ![Debian 12 Disk Selection](img/debian-12-disk-selection.png)
12. Choose the partitioning scheme. (I selected `All files in one partition
    (recommended for new users)` for simplicity.)
    ![Debian 12 Partitioning Scheme](img/debian-12-partitioning-scheme.png)
13. Now, you will see a summary of the disk partitioning. Here we need to make
    some changes to optimize the storage usage. Select the `ESP` partition and
    press `Enter`.
    ![Debian 12 Disk Summary](img/debian-12-disk-summary-before.png)
14. Delete the `ESP` partition by selecting `Delete the partition` and then
    `Delete`.
    ![Debian 12 Delete ESP Partition](img/debian-12-delete-esp-partition.png)
15. Repeat the same process for all other partitions, until you have only free
    space left.
    ![Debian 12 Disk Summary After Deletion](img/debian-12-disk-summary-free.png)
16. Select the free space and press `Enter`, then choose `Create a new
    partition` to create a new partition.
    ![Debian 12 Create New Partition](img/debian-12-create-new-partition1.png)
17. Choose the partition size for the first partition. Here we will create a 
    small partition for the boot files. I choose `100M` for the boot partition.
    ![Debian 12 Partition Size](img/debian-12-create-new-partition2.png)
18. In the next step, choose the partition location. Select `Beginning` to
    create the partition at the beginning of the free space.
    ![Debian 12 Partition Location](img/debian-12-create-new-partition3.png)
19. Now you have to set the first partition. This will be the boot partition.
    Use the following settings:
    - Name: EFI
    - Use as: EFI System Partition
    - Bootable flag: on
    After setting the partition, press `Done setting up the partition`.
    ![Debian 12 Partition Type](img/debian-12-create-new-partition-EFI.png)
20. Now, you will see the new partition created. Select the free space again
    and create a new partition for the root filesystem. Choose `Create a new
    partition` and set the partition size. I used the remaining space for the
    root partition. Then you should see a summary of the disk partitioning for
    the root partition.
    ![Debian 12 Create New Partition](img/debian-12-create-new-partition-root.png)
21. At least, select `Done setting up the partition` to finish the disk
    partitioning. If it looks like the following image, you can continue with
    the installation with the `Finish partitioning and write changes to disk`.
    ![Debian 12 Disk Summary After Partitioning](img/debian-12-disk-summary-after.png)
22. In the next step, you will get a warning, that you have not created a swap
    partition. You can select `No` to continue without a swap partition.
    ![Debian 12 Swap Partition](img/debian-12-swap-partition.png)
23. Confirm the changes to write the partitioning to the disk.
    ![Debian 12 Write Changes to Disk](img/debian-12-write-changes.png)
24. After the partitioning is completed, the installation of the base system
    will start. At some point, you will be asked to configure the package
    manager location. Choose your preferred Debian archive mirror.
    ![Debian 12 Package Manager](img/debian-12-package-manager.png)
25. In the next step, you can choose the Debian archive mirror itself.
    ![Debian 12 Archive Mirror](img/debian-12-archive-mirror.png)
26. The last step to configure the package manager is to set the HTTP proxy
    information. You can leave it blank if you don't use a proxy.
    ![Debian 12 HTTP Proxy](img/debian-12-http-proxy.png)
27. Configure the popularity-contest package if you want to participate in the
    Debian user experience improvement program. (I chose `No`.)
    ![Debian 12 Popularity Contest](img/debian-12-popularity-contest.png)
28. Choose the software to install. I deselected all options except for the `SSH
    server` and `standard system utilities`.
    ![Debian 12 Software Selection](img/debian-12-software-selection.png)
29. The installation of the base system will continue. After the installation is
    complete, you will see this Display.  
    IMPORTANT: Do not reboot your system yet. You need to install the bootloader
    manually.
    ![Debian 12 Base System Installation](img/debian-12-base-system-installation-complete.png)
30. To install the bootloader, click on `Go Back`, then select `Execute a shell`
    and click `Continue`.
    ![Debian 12 Execute a Shell](img/debian-12-execute-shell.png)
31. Before you see the shell, you will see this dialog. Click `Continue` to
    proceed.
    ![Debian 12 Execute a Shell Warning](img/debian-12-execute-shell-warning.png)
32. The shell will open. Type the following commands to check the disk name to
    mount the EFI partition.
    ```bash
    mkdir /mnt/boot
    mount /dev/mmcblk0p1 /mnt/boot
    mkdir /mnt/boot/EFI/BOOT
    touch /mnt/boot/EFI/BOOT/BOOTX64.EFI
    exit
    ```
    ![Debian 12 Shell Commands](img/debian-12-shell-commands.png)
33. With a last click on `Continue`, the installation will be completed. Now you
    the system will reboot.
34. Remove the USB drive from your Dell Wyse 3040 Thin Client.
35. During the boot up, you should hit `F2` again to enter the BIOS/UEFI
    settings and change the boot order to boot from the internal storage.
36. Enter the BIOS/UEFI settings and navigate to the `General > Boot Sequence`
    tab. Enable the Boot Sequence `debian` and change the boot order to
    prioritize it to the top.
    ![Dell Wyse 3040 Boot Sequence](img/dell-wyse-3040-boot-sequence.png)
37. Save the changes with `Apply` and `Exit` to reboot your Dell Wyse 3040 Thin
    Client.
38. Debian 12 should now boot from the internal storage of your Dell Wyse 3040
    Thin Client and you should see the console login screen.
    ![Debian 12 Desktop](img/debian-12-console-login.png)
39. Congratulations! You have successfully installed Debian 12 on your Dell Wyse
    3040 Thin Client.

## Additional Steps
After installing Debian 12 on your Dell Wyse 3040 Thin Client, you can further
customize the system to suit your needs. Here are some additional steps you can
take:

### Install sudo and Add User to sudo Group
1. Log in to your Dell Wyse 3040 Thin Client with the root account you created
   during the installation.
2. Install the `sudo` package using the following command:
   ```bash
   apt update
   apt install sudo
   ```
3. Add your user account to the `sudo` group to grant administrative privileges:
   ```bash
    usermod -aG sudo your_username
    ```

After completing these steps, you can log in with your user account via SSH and
perform administrative tasks using `sudo`.

### Reduce Boot Time with changing wait time in GRUB
Open the `/etc/default/grub` file with a text editor and change the
`GRUB_TIMEOUT` value to `1`. This will reduce the boot time significantly.

```bash
sudo nano /etc/default/grub
```

Change the following line:
```bash
GRUB_TIMEOUT=5
```
to
```bash
GRUB_TIMEOUT=1
```

Save the file and update the GRUB configuration with the following command:
```bash
sudo update-grub
```

### Fix issue with reboot and shutdown
The Dell Wyse 3040 Thin Client has an issue with HSUART DMA, which can cause
problems during reboot and shutdown. To fix this issue, you have to add some
lines to `/etc/modprobe.d/blacklist.conf`. To do this, open the file with a text
editor:
```bash
sudo nano /etc/modprobe.d/blacklist.conf
```
and add the following lines:
```
blacklist dw_dmac_core
install dw_dmac /bin/true
install dw_dmac_core /bin/true
```
Save the file with `Ctrl + S` and exit the editor with `Ctrl + X`.
To apply the changes, you have to execute the following command:
```bash
sudo update-initramfs -u
```

Now you can shut down and reboot the system without any issues. To test the
changes, you can execute the following command:
```bash
sudo poweroff
```
after the system is powered off, you can start it again with a press on the
power button.

## References
- [Debian Wiki for Dell Wyse 3040](https://wiki.debian.org/InstallingDebianOn/Dell/Wyse%203040)
- [Intel Atom Cherry Trail CPU issue](https://github.com/up-board/up-community/wiki/Ubuntu_20.04#hang-on-shutdown-or-reboot-for-up-board)

