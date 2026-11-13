# @ohos.file.volumeManager (卷管理)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @ning-jingyou-->
<!--Designer: @renguang1116-->
<!--Tester: @zsyztt; @fuwei-->
<!--Adviser: @jinqiuheng-->

该模块提供外置存储磁盘设备和卷设备信息查询的相关功能，包括获取外置存储物理磁盘信息和外置存储卷设备信息等。适用于外置存储设备管理、存储空间查询等场景，帮助开发者获取外置存储设备的磁盘和卷设备详情。

**起始版本**：9

## 导入模块

```ts
import { volumeManager } from '@kit.CoreFileKit';
```

## volumeManager.getExternalDiskInfos

getExternalDiskInfos(): Promise&lt;Array&lt;ExternalDiskInfo&gt;&gt;

获取所有外置存储物理磁盘信息。使用Promise异步回调。

**起始版本**：26.0.1

**需要权限**：ohos.permission.GET_STORAGE_VOLUME_INFO

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.FileManagement.StorageService.Volume

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;Array&lt;[ExternalDiskInfo](#externaldiskinfo)&gt;&gt; | Promise对象，返回外置存储物理磁盘信息列表。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[文件管理错误码](errorcode-filemanagement.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. |
| 13600001 | IPC error. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

volumeManager.getExternalDiskInfos().then((disks: Array<volumeManager.ExternalDiskInfo>) => {
  console.info("getExternalDiskInfos successfully:" + JSON.stringify(disks));
}).catch((error: BusinessError) => {
  console.error(`Failed to getExternalDiskInfos. Code: ${error.code}, message: ${error.message}`);
});
```

## volumeManager.getExternalVolumeInfos

getExternalVolumeInfos(): Promise&lt;Array&lt;ExternalVolumeInfo&gt;&gt;

获取所有外置存储卷设备信息。使用Promise异步回调。

**起始版本**：26.0.1

**需要权限**：ohos.permission.GET_STORAGE_VOLUME_INFO

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.FileManagement.StorageService.Volume

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;Array&lt;[ExternalVolumeInfo](#externalvolumeinfo)&gt;&gt; | Promise对象，返回外置存储卷设备信息列表。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[文件管理错误码](errorcode-filemanagement.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. |
| 13600001 | IPC error. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

volumeManager.getExternalVolumeInfos().then((volumes: Array<volumeManager.ExternalVolumeInfo>) => {
  console.info("getExternalVolumeInfos successfully:" + JSON.stringify(volumes));
}).catch((error: BusinessError) => {
  console.error(`Failed to getExternalVolumeInfos. Code: ${error.code}, message: ${error.message}`);
});
```

## volumeManager.getLocalDiskInfos

getLocalDiskInfos(): Promise&lt;Array&lt;LocalDiskInfo&gt;&gt;

获取所有本地磁盘的硬件信息。使用Promise异步回调。

**起始版本**：26.1.0

**需要权限**：ohos.permission.GET_STORAGE_VOLUME_INFO

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.FileManagement.StorageService.Volume

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;Array&lt;[LocalDiskInfo](#localdiskinfo)&gt;&gt; | Promise对象，返回本地磁盘硬件信息列表。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[文件管理错误码](errorcode-filemanagement.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. |
| 13600001 | IPC error. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

volumeManager.getLocalDiskInfos().then((disks: Array<volumeManager.LocalDiskInfo>) => {
  console.info("getLocalDiskInfos successfully:" + JSON.stringify(disks));
}).catch((error: BusinessError) => {
  console.error(`Failed to getLocalDiskInfos. Code: ${error.code}, message: ${error.message}`);
});
```

## volumeManager.getDiskSerialNumber

getDiskSerialNumber(sysPath: string): Promise&lt;string&gt;

获取指定磁盘的序列号。使用Promise异步回调。

**起始版本**：26.1.0

**需要权限**：ohos.permission.ACCESS_DISK_PHY_INFO

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.FileManagement.StorageService.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| sysPath | string | 是 | 磁盘设备节点的物理路径，如/sys/block/nvme0n1。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;string&gt; | Promise对象，返回磁盘序列号。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[文件管理错误码](errorcode-filemanagement.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. |
| 13600001 | IPC error. |
| 13900042 | Unknown error. The sysPath is invalid or the disk does not exist. |
| 13600002 | The file system is not supported. |
| 13600008 | The object does not exist. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let sysPath: string = "/sys/block/nvme0n1";
volumeManager.getDiskSerialNumber(sysPath).then((serial: string) => {
  console.info("getDiskSerialNumber successfully:" + serial);
}).catch((error: BusinessError) => {
  console.error(`Failed to getDiskSerialNumber. Code: ${error.code}, message: ${error.message}`);
});
```

## volumeManager.getDiskPowerCycleCount

getDiskPowerCycleCount(sysPath: string): Promise&lt;number&gt;

获取指定磁盘自出厂以来的完整启停次数。使用Promise异步回调。

如果读取失败（如SATA HDD不支持），返回0。

**起始版本**：26.1.0

**需要权限**：ohos.permission.ENTERPRISE_MANAGE_DISK

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.FileManagement.StorageService.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| sysPath | string | 是 | 磁盘设备节点的物理路径，如/sys/block/nvme0n1。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;number&gt; | Promise对象，返回磁盘启停次数。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[文件管理错误码](errorcode-filemanagement.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. |
| 13600001 | IPC error. |
| 13900042 | Unknown error. The sysPath is invalid or the disk does not exist. |
| 13600002 | The file system is not supported. |
| 13600008 | The object does not exist. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let sysPath: string = "/sys/block/nvme0n1";
volumeManager.getDiskPowerCycleCount(sysPath).then((count: number) => {
  console.info("getDiskPowerCycleCount successfully:" + count);
}).catch((error: BusinessError) => {
  console.error(`Failed to getDiskPowerCycleCount. Code: ${error.code}, message: ${error.message}`);
});
```

## volumeManager.getDiskPowerOnHours

getDiskPowerOnHours(sysPath: string): Promise&lt;number&gt;

获取指定磁盘自出厂以来的总通电时长。使用Promise异步回调。

如果读取失败（如SATA HDD不支持），返回0。

**起始版本**：26.1.0

**需要权限**：ohos.permission.ENTERPRISE_MANAGE_DISK

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.FileManagement.StorageService.Volume

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| sysPath | string | 是 | 磁盘设备节点的物理路径，如/sys/block/nvme0n1。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise&lt;number&gt; | Promise对象，返回磁盘通电时长。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[文件管理错误码](errorcode-filemanagement.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. |
| 13600001 | IPC error. |
| 13900042 | Unknown error. The sysPath is invalid or the disk does not exist. |
| 13600002 | The file system is not supported. |
| 13600008 | The object does not exist. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let sysPath: string = "/sys/block/nvme0n1";
volumeManager.getDiskPowerOnHours(sysPath).then((hours: number) => {
  console.info("getDiskPowerOnHours successfully:" + hours);
}).catch((error: BusinessError) => {
  console.error(`Failed to getDiskPowerOnHours. Code: ${error.code}, message: ${error.message}`);
});
```

## ExternalDiskInfo

外置磁盘信息。

**起始版本**：26.0.1

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.FileManagement.StorageService.Volume

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| diskId | string | 否 | 否 | 磁盘设备ID，格式为disk-{主设备号}-{次设备号}，如disk-8-0。 |
| diskType | number | 否 | 否 | 磁盘设备类型：<br>1：SD卡。<br>2：U盘。<br>3：光盘（CD/DVD/BD）。<br>值为整数。 |
| volumeIds | Array&lt;string&gt; | 否 | 否 | 磁盘上的卷设备ID列表。一个磁盘可以包含多个卷设备，如["vol-8-1", "vol-8-2"]。 |
| vendorId | number | 否 | 否 | USB设备的厂商ID，由USB-IF分配，用于标识设备制造商。值为整数。 |
| productId | number | 否 | 否 | USB设备的产品ID，由制造商分配，用于标识具体产品型号。值为整数。 |

## ExternalVolumeInfo

外置卷设备信息。

**起始版本**：26.0.1

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.FileManagement.StorageService.Volume

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| volumeId | string | 否 | 否 | 卷设备ID，格式为vol-{主设备号}-{次设备号}，如vol-8-1。 |
| uuid | string | 否 | 否 | 卷设备uuid，是卷设备的通用唯一识别码，不会随着插卡顺序变化而变化，但是卷设备的格式化会改变卷设备的uuid，如3C16-F61F。 |
| diskId | string | 否 | 否 | 卷设备所属的磁盘ID。一个磁盘可以有一个或多个卷设备。磁盘设备ID的格式为disk-{主设备号}-{次设备号}，如disk-8-0。 |
| description | string | 否 | 否 | 卷设备描述。卷设备的格式化会改变卷设备描述，如"MyUSB"。 |
| state | number | 否 | 否 | 卷设备状态：<br>0：卸载状态。<br>1：检查状态。<br>2：挂载状态。<br>3：正在弹出状态。<br>值为整数。 |
| totalSize | number | 否 | 否 | 卷设备总大小。单位：Byte。 |
| freeSize | number | 否 | 否 | 卷设备可用大小。单位：Byte。 |
| path | string | 否 | 否 | 卷设备的挂载地址，一般为/mnt/data/external/{uuid}。卷设备的格式化会改变挂载路径。 |
| fsType | string | 否 | 否 | 文件系统类型。常见的文件系统有fat32、ntfs、exfat、ext4、udf和iso9660。 |

## LocalDiskInfo

本地磁盘硬件信息。

**起始版本**：26.1.0

**系统能力**：SystemCapability.FileManagement.StorageService.Volume

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| sysPath | string | 否 | 否 | 磁盘设备节点的物理路径，如/sys/block/nvme0n1。 |
| model | string | 否 | 否 | 磁盘型号，由厂商定义。 |
| description | string | 否 | 否 | 磁盘描述信息，与model字段取值相同。 |
| size | number | 否 | 否 | 磁盘总空间大小。单位：Byte。 |
| mediaType | number | 否 | 否 | 磁盘介质类型：<br>1：SSD（固态硬盘）。<br>2：HDD（机械硬盘）。<br>255：未知。<br>值为整数。 |
| state | string | 否 | 否 | 磁盘运行状态，取值包括"live"、"connecting"、"resetting"、"dead"。 |
