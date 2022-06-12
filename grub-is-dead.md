
# Let the GRUB Die Already

**2022-06-08**

Another pack of critical CVEs in GRUB [has arrived](https://lists.gnu.org/archive/html/grub-devel/2022-06/msg00035.html). The same class of vulnerabilities as in the years [2020](https://www.openwall.com/lists/oss-security/2020/07/29/3) and [2021](https://ubuntu.com//blog/grub2-secure-boot-bypass-2021) ‒ a UEFI Secure Boot bypass. Literally, the worst thing that could happen to a bootloader.

Stop raping the corpse already, guys! You don't need GRUB in the absolute most scenarios. Its only killer feature is modules to open fully-encrypted disks with `/boot` within. If your threat model does not include an attacker with physical access to the device being able to modify *initramfs* to contain malicious code to steal your FDE password ‒ just forget about it and store everything in the *EFI system partition* (the one usually mounted at `/boot/EFI`). If it does - implement Secure Boot [the right way](https://wiki.archlinux.org/title/Unified_Extensible_Firmware_Interface/Secure_Boot#Implementing_Secure_Boot
), without a bootloader at all.

Seriously, what else should happen for distro maintainers to stop including GRUB by default? A silent data corruption?

By the way, you can create multi-boot USB flash drives without GRUB too. [Ventoy](https://github.com/ventoy/Ventoy) allows booting from an ISO image on a disk seamlessly. Or even IMG/VHD(x) images, even from NTFS/UDF/XFS/ext partitions! Not so long ago, the only option to boot ISO images from a filesystem was to buy a [special flash drive](https://isostick.com/) with hardware emulation.
