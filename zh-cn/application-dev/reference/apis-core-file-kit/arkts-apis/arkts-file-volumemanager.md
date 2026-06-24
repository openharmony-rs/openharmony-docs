# @ohos.file.volumeManager

该模块提供卷设备、磁盘设备查询和管理的相关功能：包括查询卷设备信息，对卷设备的挂载卸载、对磁盘设备分区以及卷设备的格式化等功能。

**起始版本：** 9

**系统能力：** SystemCapability.FileManagement.StorageService.Volume

**系统接口：** 此接口为系统接口。

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[format](arkts-corefile-volumemanager-format-f-sys.md#format-1) | 对指定卷设备进行格式化，使用callback异步回调。当前仅支持vfat和exfat两种文件系统类型的格式化，只有处于卸载状态的<br/>卷设备可以进行格式化，格式化后卷设备的uuid、挂载路径和卷设备描述均会发生变化。<br/> |
| <!--DelRow-->[format](arkts-corefile-volumemanager-format-f-sys.md#format-2) | 对指定卷设备进行格式化，使用Promise异步回调。当前仅支持vfat和exfat两种文件系统类型的格式化，只有处于卸载状态的<br/>卷设备可以进行格式化，格式化后卷设备的uuid、挂载路径和卷设备描述均会发生变化。<br/> |
| <!--DelRow-->[getAllVolumes](arkts-corefile-volumemanager-getallvolumes-f-sys.md#getAllVolumes-1) | 获取当前外置存储中所有卷设备信息，使用callback异步回调。<br/> |
| <!--DelRow-->[getAllVolumes](arkts-corefile-volumemanager-getallvolumes-f-sys.md#getAllVolumes-2) | 获取当前外置存储中所有卷设备信息，使用Promise异步回调。<br/> |
| <!--DelRow-->[getVolumeById](arkts-corefile-volumemanager-getvolumebyid-f-sys.md#getVolumeById-1) | 通过指定卷设备id获得卷设备信息，使用callback异步回调。<br/> |
| <!--DelRow-->[getVolumeById](arkts-corefile-volumemanager-getvolumebyid-f-sys.md#getVolumeById-2) | 通过卷设备id获得指定卷设备信息，使用Promise异步回调。<br/> |
| <!--DelRow-->[getVolumeByUuid](arkts-corefile-volumemanager-getvolumebyuuid-f-sys.md#getVolumeByUuid-1) | 通过卷设备uuid获得指定卷设备信息，使用callback异步回调。<br/> |
| <!--DelRow-->[getVolumeByUuid](arkts-corefile-volumemanager-getvolumebyuuid-f-sys.md#getVolumeByUuid-2) | 通过卷设备uuid获得指定卷设备信息，使用Promise异步回调。<br/> |
| <!--DelRow-->[mount](arkts-corefile-volumemanager-mount-f-sys.md#mount-1) | 挂载指定卷设备，使用callback异步回调。当前仅支持vfat、exfat以及ntfs三种文件系统的卷设备挂载。<br/> |
| <!--DelRow-->[mount](arkts-corefile-volumemanager-mount-f-sys.md#mount-2) | 挂载指定卷设备，使用Promise异步回调。当前仅支持vfat、exfat以及ntfs三种文件系统的卷设备挂载。<br/> |
| <!--DelRow-->[partition](arkts-corefile-volumemanager-partition-f-sys.md#partition-1) | 对磁盘进行分区，使用callback异步回调。当前仅支持将磁盘设备重新分区为一个分区，系统是支持读取多分区的磁盘设备。<br/>不支持对光盘进行分区。<br/> |
| <!--DelRow-->[partition](arkts-corefile-volumemanager-partition-f-sys.md#partition-2) | 对磁盘设备进行分区，使用Promise异步回调。当前仅支持将磁盘设备重新分区为一个分区，系统是支持读取多分区的磁盘设备。<br/>不支持对光盘进行分区。<br/> |
| <!--DelRow-->[setVolumeDescription](arkts-corefile-volumemanager-setvolumedescription-f-sys.md#setVolumeDescription-1) | 修改指定卷设备描述，使用callback异步回调。当前仅支持修改ntfs和exfat两种文件系统类型的设备描述，<br/>只有处于卸载状态的卷设备可以修改设备描述。<br/> |
| <!--DelRow-->[setVolumeDescription](arkts-corefile-volumemanager-setvolumedescription-f-sys.md#setVolumeDescription-2) | 修改指定卷设备描述，使用Promise异步回调。当前仅支持修改ntfs和exfat两种文件系统类型的设备描述，<br/>只有处于卸载状态的卷设备可以修改设备描述。<br/> |
| <!--DelRow-->[unmount](arkts-corefile-volumemanager-unmount-f-sys.md#unmount-1) | 卸载指定卷设备，使用callback异步回调。<br/> |
| <!--DelRow-->[unmount](arkts-corefile-volumemanager-unmount-f-sys.md#unmount-2) | 卸载指定卷设备，使用Promise异步回调。<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| <!--DelRow-->[Volume](arkts-corefile-volumemanager-volume-i-sys.md) | 获取所有卷。<br/> |

