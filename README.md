# GA_970A_DS3P_Fix
_How to fix USB 2.0, USB 3.0 and Ethernet issues on Linux for Gigabyte GA 970A DS3P AM3+ motherboard._

1. Enter in the __UEFI BIOS SETUP__ by pressing **Delete** key when you computer start

2. In Peripherals tab, enable "IOMMU Controller"

3. Press **F10** and select YES to save this setting.

4. Boot your Linux distro's in UEFI Mode

5. Open a terminal as root (or prefix by sudo) and type :
```bash
nano /etc/default/grub
```

6. For line `GRUB_CMDLINE_LINUX=""` add *iommu=soft* in the empty quotes like this :
```bash
GRUB_CMDLINE_LINUX="iommu=soft"
```

7. Save the file with **CTRL+X** and type **Y** then press **Enter**

8. Apply your new grub configuration  (still as root) : 
```bash
grub2-mkconfig -o /boot/grub2/grub.cfg
```

9. Reboot

10. Go again in the __UEFI BIOS SETUP__, in Peripherals tab, now disable "IOMMU Controller", press **F10** and select YES.

11. Now GNU/Linux should work fine on your cheap Gigabyte AM3+ Motherboard !

## Sources :
<https://ubuntuforums.org/showthread.php?t=2188370>

<https://forums.opensuse.org/showthread.php/477980-grub2-update-grub>

<https://forum.level1techs.com/t/trouble-with-the-ga-970a-ds3p-motherboard/73185>
