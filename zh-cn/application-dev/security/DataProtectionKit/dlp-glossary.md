# Data Protection Kit术语
<!--Kit: Data Protection Kit-->
<!--Subsystem: Security-->
<!--Owner: @winnieHuYu-->
<!--Designer: @QRF-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->

## D

### Data Loss Prevention (DLP)；数据防泄漏

系统提供的系统级数据防泄漏解决方案，提供跨设备的文件权限管理、加密存储、授权访问等能力。通过DLP技术，可以保护敏感文件的安全性，防止数据泄漏。

### DLP File；DLP文件

经过数据防泄漏加密保护的权限受控文件，扩展名为.dlp。仅授权列表内的用户可以打开，授权分为完全控制权限和只读权限，系统会根据授权策略限制用户对文件的操作权限。

### DLP Sandbox；DLP沙箱

用于打开DLP文件的隔离运行环境。当打开DLP文件时自动安装沙箱，关闭DLP文件时自动卸载沙箱。沙箱环境提供应用隔离和数据保护，防止DLP文件中的敏感数据泄漏到非受控环境。

## F

### Filesystem in Userspace (FUSE)；用户空间文件系统

用于管理DLP文件的虚拟文件系统。通过FUSE技术创建链接文件，实现对DLP文件的透明访问和管理。对链接文件的读写操作会同步到DLP文件，提供便捷的文件操作接口。