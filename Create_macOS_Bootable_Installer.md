# Create macOS Bootable Installer

0. On macOS System only 仅用于macOS系统

1. Download Target version from AppStore 从AppStore下载目标版本的macOS安装包
https://support.apple.com/en-us/102662

## USB Key U盘驱动器

2. 插入16GB以上的U盘 Connect the USB flash drive directly to your Mac.

3. 打开终端 Open Terminal, which is in the Utilities folder of your Applications folder.

4. 根据不同版本 输入下列指令 Depending on which macOS you downloaded, enter one of the following commands in Terminal. Each command assumes that the installer is in your Applications folder, and your USB flash drive is named MyVolume. If it has a different name, rename it or replace MyVolume in the command as needed.
https://support.apple.com/en-us/101578
  e.g. macOS 12 Monterey 

  `sudo /Applications/Install\ macOS\ Monterey.app/Contents/Resources/createinstallmedia --volume /Volumes/MyUSBVolume`

## ISO File

2. 创建16GB以上的磁盘镜像 Create a disk image DMG file buy issuing the following command:

  `sudo hdiutil create -o /tmp/Monterey -size 16500m -volname Monterey -layout SPUD -fs HFS+J`

3. 挂载该镜像 Mount the created DMG disk image as follows:

  `sudo hdiutil attach /tmp/Monterey.dmg -noverify -mountpoint /Volumes/Monterey`

4. 根据不同版本 输入下列指令 Depending on which macOS you downloaded, enter one of the following commands in Terminal. Each command assumes that the installer is in your Applications folder, and your USB flash drive is named MyVolume. If it has a different name, rename it or replace MyVolume in the command as needed.
https://support.apple.com/en-us/101578
  e.g. macOS 12 Monterey 

  `sudo /Applications/Install\ macOS\ Monterey.app/Contents/Resources/createinstallmedia --volume /Volumes/Monterey`

5. 移除该镜像 When createinstallmedia has finished, next you can unmount the volume you just created:

  `sudo hdiutil detach /volumes/Install\ macOS\ Monterey`

6. 转换dmg文件为cdr Now we convert the DMG disk image file to an ISO disk image file (technically a CDR file but it’s the same as an iso)
   `sudo hdiutil convert /tmp/Monterey.dmg -format UDTO -o ~/Desktop/Monterey.cdr`
