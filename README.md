### 如何您愿意帮助我，也可以阅读[此markdown的中文版本](README_CN.md)！感激不尽
----
# Detailed Description of Disk Cloning Issue [`English version`]

## Hardware Information

- Computer Model: Dell Alienware M15 R7
- Windows Version: Windows 11 Pro, Version 22H2, OS Build 22621.3007
- Disk Information: (Confirmed by official Dell personnel to be compatible with this computer)
  - Original 2TB Disk: [adata xpg 2tb ssds](https://www.adata.com/us/xpg/830)
  - New 4TB Disk: [fanxiang S880 4TB](https://www.amazon.ca/fanxiang-S880-Internal-Solid-State/dp/B0C6DL33T5)

## Detailed Operation Process 【This computer has no issues with daily use; I am only seeking advice on the current cloning issue】

1. **Hardware Preparation**: The computer is equipped with two M.2 SSD slots. The original disk (2TB, containing OS and all software) is installed in slot 1, and the newly purchased disk (4TB) is installed in slot 2.
2. **Disk Initialization**: After installation and booting up the computer, right-click on the Windows logo and see both disks through the `Disk Management` tool. The new disk automatically prompted for GPT initialization, then showed as a whole black "Unallocated" space. After formatting, it displayed as unallocated space.
3. **Partitioning and Formatting**: Right-clicked on the unallocated space of the new disk, chose to create a new simple volume, followed the prompts to complete partitioning and formatting. The new disk was assigned a drive letter (D:), and appeared blue. Next, under File Explorer's This PC, the new disk's usage size could be seen, and it was ready for use.
4. **Cloning Preparation**: Used `Macrium Reflect Free Edition` software [My download link](https://www.majorgeeks.com/files/details/macrium_reflect_free_edition.html) for cloning, selecting the original 2TB disk as the source and the 4TB disk as the destination.
5. **Cloning Operation**: Before starting the cloning process, there was an option next to the target disk to clear all partitions on the target disk, then start cloning (a 16MB partition and a second entire 3.8TB partition were cleared, leaving only a single 3.8TB partition, my E: drive). The cloning task began, and the software was set to shut down the computer after cloning. (This was my second attempt at doing it myself, as many people had issues and I wondered if I also made a mistake here, so I tried again).
6. **Boot Attempt**: After cloning and automatic shutdown, I physically removed the original 2TB disk, leaving only the 4TB SSD connected to the computer. Attempted to boot with only the 4TB disk, but 3 seconds later, encountered [this blue screen error](blue_screen_standalone_new_ssd.jpg) and failed to boot.
7. **Self-Diagnosis**: Checked in BIOS under boot sequence, found the new disk was set as the first in the boot sequence, but lacked the `Boot Management` program. Reinstalling the original disk allowed the system to boot normally, and I could see the boot management in the first place of all sequences in BIOS. When both disks were connected, regardless of how I arranged the order of the two disks in the BIOS boot sequence, or even if I removed the old 2TB disk, as long as the old disk was still connected, it booted from the old disk. This could also be seen in File Explorer under This PC, where the old C: drive had a Windows logo, indicating it was the boot OS disk.

## Notes/Update Notes:

1. Updated to the latest BIOS version on the night of February 26, 2024, executed automatically by the Alienware computer.
2. [Photo 1, viewing under the msinfo32 command in cmd](msinfo32_ssd1.jpg)
3. [Photo 2, general information, under the msinfo32 command in cmd](msinfo32_general.jpg)
4. [Option selected to shut down after cloning was completed](choose_to_shut_down_after_cloned.jpg)
5. [BIOS -> boot sequence options when both SSDs are connected, showing “Windows Boot Manager” in one](two_ssds_connected.PNG)
6. [Current state of disk management in Windows, screenshot](disk_management_right_now.png)

## Encountered Issues

- The newly cloned disk fails to boot, displaying [this blue screen error](blue_screen_standalone_new_ssd.jpg).

- The BIOS lacks the `Boot Management`[the second row in this pic](two_ssds_connected.PNG) option for the new disk, which might be the reason for the boot failure. I'm unsure how to add it or why it is missing, even though I followed the complete cloning process.

## Seeking Your Help 🙇‍🙏

- How to resolve the issue of the new disk not booting, especially looking for solutions to ensure booting from the new disk after cloning.
- Wondering if any steps were missed or errors made, in need of professional advice and guidance.
