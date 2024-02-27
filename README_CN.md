# 硬盘克隆问题详细描述

## 硬件信息

- 电脑型号： 戴尔外星人Alienware M15 R7
- Windows版本：Windows 11 Pro, 版本 22H2, OS构建版本 22621.3007
- 硬盘信息：（已经向dell官方人员证实都可以在此电脑上兼容）
  - 原始硬盘 2tb：[adata xpg 2tb ssds](https://www.adata.com/us/xpg/830)
  - 新硬盘 4tb：[fanxiang S880 4TB](https://www.amazon.ca/fanxiang-S880-Internal-Solid-State/dp/B0C6DL33T5

## 操作详细过程【此电脑的日常使用都没有任何问题，我只想请教现在的克隆问题】

1. **硬件准备**：电脑配备两个M.2 SSD硬盘位。原始硬盘（2TB，含OS和一切软件）位于硬盘位1，购买的新硬盘（4TB）安装在硬盘位2。
2. **硬盘初始化**：安装结束后开机，启动电脑后，右键Windows logo，通过`磁盘管理`（Disk Management）工具看到两块硬盘。对新硬盘 自动弹出，进行GPT初始化，然后显示整条黑色“为分配”，格式化后显示为整条黑色，“未分配”空间。
3. **分区和格式化**：在新硬盘的未分配空间上右键，选择新建简单卷，按提示完成分区并格式化，新硬盘被分配盘符（D: 盘），并显示为蓝色。接下来去File Explorer下This PC下查看，可以看到新硬盘的使用大小情况，已经可以对他进行操控。
4. **克隆准备**：使用`Macrium Reflect Free Edition`软件 [我的下载地址](https://www.majorgeeks.com/files/details/macrium_reflect_free_edition.html) 进行克隆，选择原始2TB硬盘作为克隆源盘（Source），4TB硬盘作为目标盘（Destination）。
5. **克隆操作**：接下来，在克隆过程前，在目标盘 位置旁边有一个：先清除目标硬盘上的所有分区操作，然后开始克隆（有一个16MB的分区，和一个3.8tb的第二个整个分区，清楚完毕后，只剩下单独一个3.8tb的分区，是我的E盘名称）。克隆任务开始，与此同时，此页面软件设置为克隆后“关机”的操作。（这是我的第二次自行操作，因为我第一次没有这样设置，很多人也有问题，我在想我是不是也是这里有错，因此再跟着试一次）。
6. **启动尝试**：克隆完成并自动关机后，我物理上移除了原2TB硬盘，此时只有4tb的ssd与电脑连接。尝试仅用4TB硬盘启动，3s后，遇到[此蓝屏错误](blue_screen_standalone_new_ssd.jpg)，无法成功启动。
7. **自行问题诊断**：通过BIOS检查，点击boot sequence，发现已经将新硬盘被设置为启动序列首位，但是缺少`Boot Management`程序。将原硬盘重新安装后，系统能够正常启动，然后我在bios中可以看到boot management在所有的sequence中的第一个。当两块硬盘都链接在电脑上时候，无论在bios boot sequence里面我如何排列两块盘的顺序，亦或是我即使将老2tb盘删除掉，只要老盘还连接着，都是从老盘进入系统，这也可以从File Explorer下This PC下查看，老盘C盘有一个Windows的LOGO，代表这是boot os的盘。

## Notes/笔记：

1. 已经于2024年2月26日晚上更新了最新的BIOS版本，由alienware电脑自动执行。
2. [照片1，在msinfo32命令，在cmd下查看](msinfo32_ssd1.jpg)
3. [照片2，通用信息，在msinfo32命令，在cmd下查看](msinfo32_general.jpg)
4. [在克隆完成之后，选择关机的选项](choose_to_shut_down_after_cloned.jpg)
5. [当两个ssd都连接的时候的bios -> boot sequence选项，可以看到“Windows Boot Manager在一个](two_ssds_connected.PNG)
6. [现在的win下的disk management情况，截图](disk_management_right_now.png)

## 遇到的问题

- 克隆后的新硬盘无法作为启动盘使用，显示[此蓝屏错误](blue_screen_standalone_new_ssd.jpg)。

- 在BIOS中缺少对新硬盘的`Boot Management`选项，这可能是启动失败的原因。但我不知道如何添加它，以及为什么会缺少，我已经按照完整的克隆顺序来做了。

  

## 寻求您的帮助🙇‍🙏

- 如何解决新硬盘无法启动的问题，特别是在克隆硬盘后确保能够从新硬盘启动的解决方案。
- 是否存在步骤遗漏或操作错误，需要专业意见和指导。
