# @ohos.file.volumeManager (卷管理)(系统接口)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @ning-jingyou-->
<!--Designer: @renguang1116; @wang_zhangjun-->
<!--Tester: @zsyztt; @yue-ye2; @fuwei-->
<!--Adviser: @jinqiuheng-->

该模块提供卷设备、磁盘设备查询和管理的相关功能：包括查询卷设备信息，对卷设备的挂载卸载、对磁盘设备分区以及卷设备的格式化等功能。

> **说明：**
>
> - 本模块首批接口从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> - 本模块为系统接口。

## 导入模块

```ts
import { volumeManager } from '@kit.CoreFileKit';
```

## volumemanager.getAllVolumes

getAllVolumes(): Promise&lt;Array&lt;Volume&gt;&gt;

获取当前外置存储中所有卷设备信息，使用Promise异步回调。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.STORAGE_MANAGER

**系统能力**：SystemCapability.FileManagement.StorageService.Volume

**返回值：**

  | 类型                               | 说明                       |
  | ---------------------------------- | -------------------------- |
  | Promise&lt;[Volume](#volume)[]&gt; | Promise对象，返回当前所有可获得的卷设备信息。 |

**错误码：**

以下错误码的详细介绍请参见[文件管理错误码](errorcode-filemanagement.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: Mandatory parameters are left unspecified. |
| 13600001 | IPC error. |
| 13900042 | Unknown error. |

**示例：**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  volumeManager.getAllVolumes().then((volumes: Array<volumeManager.Volume>) => {
    // do something with volumes, which is an array
  }).catch((error: BusinessError) => {
    console.error("getAllVolumes failed");
  });
  ```

## volumemanager.getAllVolumes

getAllVolumes(callback: AsyncCallback&lt;Array&lt;Volume&gt;&gt;): void

获取当前外置存储中所有卷设备信息，使用callback异步回调。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.STORAGE_MANAGER

**系统能力**：SystemCapability.FileManagement.StorageService.Volume

**参数：**

  | 参数名   | 类型                                              | 必填 | 说明                                 |
  | -------- | ------------------------------------------------- | ---- | ------------------------------------ |
  | callback | AsyncCallback&lt;[Volume](#volume)[]&gt; | 是   | 获取当前所有可获得的卷设备信息之后的回调。 |

**错误码：**

以下错误码的详细介绍请参见[文件管理错误码](errorcode-filemanagement.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: Mandatory parameters are left unspecified. |
| 13600001 | IPC error. |
| 13900042 | Unknown error. |

**示例：**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  volumeManager.getAllVolumes((error: BusinessError, volumes: Array<volumeManager.Volume>) => {
    // do something
  });
  ```

## volumemanager.mount

mount(volumeId: string): Promise&lt;void&gt;

挂载指定卷设备，使用Promise异步回调。

当前仅支持以下文件系统的卷设备挂载：

vfat、exfat及ntfs。

从API版本26.0.0开始支持ext4。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.MOUNT_UNMOUNT_MANAGER

**系统能力**：SystemCapability.FileManagement.StorageService.Volume

**参数：**

  | 参数名   | 类型   | 必填 | 说明 |
  | -------- | ------ | ---- | ---- |
  | volumeId | string | 是   | 卷设备id。 |

**返回值：**

  | 类型                   | 说明       |
  | ---------------------- | ---------- |
  | Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[文件管理错误码](errorcode-filemanagement.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 13600001 | IPC error. |
| 13600002 | Not supported filesystem. |
| 13600003 | Failed to mount. |
| 13600005 | Incorrect volume state. |
| 13600008 | No such object. |
| 13900042 | Unknown error. |

**示例：**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let volumeId: string = "";
  volumeManager.mount(volumeId).then(() => {
    // do something
  }).catch((error: BusinessError) => {
    console.error("mount failed");
  });
  ```

## volumemanager.mount

mount(volumeId: string, callback:AsyncCallback&lt;void&gt;):void

挂载指定卷设备，使用callback异步回调。

当前仅支持以下文件系统的卷设备挂载：

vfat、exfat及ntfs。

从API版本26.0.0开始支持ext4。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.MOUNT_UNMOUNT_MANAGER

**系统能力**：SystemCapability.FileManagement.StorageService.Volume

**参数：**

  | 参数名   | 类型                                  | 必填 | 说明                 |
  | -------- | ------------------------------------- | ---- | -------------------- |
  | volumeId | string                                | 是   | 卷设备id。                 |
  | callback | AsyncCallback&lt;void&gt; | 是   | 挂载指定卷设备之后的回调。 |

**错误码：**

以下错误码的详细介绍请参见[文件管理错误码](errorcode-filemanagement.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 13600001 | IPC error. |
| 13600002 | Not supported filesystem. |
| 13600003 | Failed to mount. |
| 13600005 | Incorrect volume state. |
| 13600008 | No such object. |
| 13900042 | Unknown error. |

**示例：**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let volumeId: string = "";
  volumeManager.mount(volumeId, (error: BusinessError) => {
    // do something
  });
  ```

## volumemanager.unmount

unmount(volumeId: string): Promise&lt;void&gt;

卸载指定卷设备，使用Promise异步回调。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.MOUNT_UNMOUNT_MANAGER

**系统能力**：SystemCapability.FileManagement.StorageService.Volume

**参数：**

  | 参数名   | 类型   | 必填 | 说明 |
  | -------- | ------ | ---- | ---- |
  | volumeId | string | 是   | 卷设备id。 |

**返回值：**

  | 类型                   | 说明       |
  | ---------------------- | ---------- |
  | Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[文件管理错误码](errorcode-filemanagement.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 13600001 | IPC error. |
| 13600002 | Not supported filesystem. |
| 13600004 | Failed to unmount. |
| 13600005 | Incorrect volume state. |
| 13600008 | No such object. |
| 13900042 | Unknown error. |

**示例：**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let volumeId: string = "";
  volumeManager.unmount(volumeId).then(() => {
    // do something
  }).catch((error: BusinessError) => {
    console.error("mount failed");
  });
  ```

## volumemanager.unmount

unmount(volumeId: string, callback: AsyncCallback&lt;void&gt;): void

卸载指定卷设备，使用callback异步回调。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.MOUNT_UNMOUNT_MANAGER

**系统能力**：SystemCapability.FileManagement.StorageService.Volume

**参数：**

  | 参数名   | 类型                                  | 必填 | 说明                 |
  | -------- | ------------------------------------- | ---- | -------------------- |
  | volumeId | string                                | 是   | 卷设备id。                 |
  | callback | AsyncCallback&lt;void&gt; | 是   | 卸载指定卷设备之后的回调。 |

**错误码：**

以下错误码的详细介绍请参见[文件管理错误码](errorcode-filemanagement.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 13600001 | IPC error. |
| 13600002 | Not supported filesystem. |
| 13600004 | Failed to unmount. |
| 13600005 | Incorrect volume state. |
| 13600008 | No such object. |
| 13900042 | Unknown error. |

**示例：**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let volumeId: string = "";
  volumeManager.unmount(volumeId, (error: BusinessError) => {
    // do something
  });
  ```

## volumemanager.getVolumeByUuid

getVolumeByUuid(uuid: string): Promise&lt;Volume&gt;

通过卷设备uuid获得指定卷设备信息，使用Promise异步回调。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.STORAGE_MANAGER

**系统能力**：SystemCapability.FileManagement.StorageService.Volume

**参数：**

  | 参数名   | 类型   | 必填 | 说明 |
  | -------- | ------ | ---- | ---- |
  | uuid | string | 是   | 卷设备uuid。 |

**返回值：**

  | 类型                               | 说明                       |
  | ---------------------------------- | -------------------------- |
  | Promise&lt;[Volume](#volume)&gt; | Promise对象，返回当前uuid的卷设备信息。 |

**错误码：**

以下错误码的详细介绍请参见[文件管理错误码](errorcode-filemanagement.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 13600001 | IPC error. |
| 13600008 | No such object. |
| 13900042 | Unknown error. |

**示例：**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let uuid: string = "";
  volumeManager.getVolumeByUuid(uuid).then((volume: volumeManager.Volume) => {
    console.info("getVolumeByUuid successfully:" + JSON.stringify(volume));
  }).catch((error: BusinessError) => {
    console.error("getVolumeByUuid failed with error:" + JSON.stringify(error));
  });
  ```

## volumemanager.getVolumeByUuid

getVolumeByUuid(uuid: string, callback: AsyncCallback&lt;Volume&gt;): void

通过卷设备uuid获得指定卷设备信息，使用callback异步回调。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.STORAGE_MANAGER

**系统能力**：SystemCapability.FileManagement.StorageService.Volume

**参数：**

  | 参数名    | 类型                                                 | 必填 | 说明                 |
  | -------- | ------------------------------------------------ | ---- | -------------------- |
  | uuid | string                                                 | 是   | 卷设备uuid。                 |
  | callback | AsyncCallback&lt;[Volume](#volume)&gt;  | 是   | 获取卷设备信息之后的回调。 |

**错误码：**

以下错误码的详细介绍请参见[文件管理错误码](errorcode-filemanagement.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 13600001 | IPC error. |
| 13600008 | No such object. |
| 13900042 | Unknown error. |

**示例：**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let uuid: string = "";
  volumeManager.getVolumeByUuid(uuid, (error: BusinessError, volume: volumeManager.Volume) => {
    // do something    
  });
  ```

## volumemanager.getVolumeById

getVolumeById(volumeId: string): Promise&lt;Volume&gt;

通过卷设备id获得指定卷设备信息，使用Promise异步回调。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.STORAGE_MANAGER

**系统能力**：SystemCapability.FileManagement.StorageService.Volume

**参数：**

  | 参数名    | 类型    | 必填  | 说明 |
  | -------- | ------ | ---- | ---- |
  | volumeId | string | 是   | 卷设备id。 |

**返回值：**

  | 类型                               | 说明                       |
  | ---------------------------------- | -------------------------- |
  | Promise&lt;[Volume](#volume)&gt; | Promise对象，返回当前id的卷设备信息。 |

**错误码：**

以下错误码的详细介绍请参见[文件管理错误码](errorcode-filemanagement.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 13600001 | IPC error. |
| 13600008 | No such object. |
| 13900042 | Unknown error. |

**示例：**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let volumeId: string = "";
  volumeManager.getVolumeById(volumeId).then((volume: volumeManager.Volume) => {
    console.info("getVolumeById successfully:" + JSON.stringify(volume));
  }).catch((error: BusinessError) => {
    console.error("getVolumeById failed with error:" + JSON.stringify(error));
  });
  ```

## volumemanager.getVolumeById

getVolumeById(volumeId: string, callback: AsyncCallback&lt;Volume&gt;): void

通过指定卷设备id获得卷设备信息，使用callback异步回调。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.STORAGE_MANAGER

**系统能力**：SystemCapability.FileManagement.StorageService.Volume

**参数：**

  | 参数名   | 类型                      | 必填 | 说明                          |
  | -------- | ------------------------- | ---- | ----------------------------- |
  | volumeId | string                    | 是   | 卷设备id。                |
  | callback | AsyncCallback&lt;[Volume](#volume)&gt; | 是   | 获取卷设备信息之后的回调。  |

**错误码：**

以下错误码的详细介绍请参见[文件管理错误码](errorcode-filemanagement.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 13600001 | IPC error. |
| 13600008 | No such object. |
| 13900042 | Unknown error. |

**示例：**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let volumeId: string = "";
  volumeManager.getVolumeById(volumeId, (error: BusinessError, volume: volumeManager.Volume) => {
    // do something    
  });
  ```

## volumemanager.setVolumeDescription

setVolumeDescription(uuid: string, description: string): Promise&lt;void&gt;

修改指定卷设备描述，使用Promise异步回调。当前仅支持修改ntfs和exfat两种文件系统类型的设备描述，只有处于卸载状态的卷设备可以修改设备描述。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.MOUNT_UNMOUNT_MANAGER

**系统能力**：SystemCapability.FileManagement.StorageService.Volume

**参数：**

  | 参数名     | 类型   | 必填 | 说明 |
  | --------- | ------ | ---- | ---- |
  | uuid      | string | 是   | 卷设备uuid。 |
  | description | string | 是   | 卷设备描述。 |

**返回值：**

  | 类型                    | 说明                       |
  | ---------------------- | -------------------------- |
  | Promise&lt;void&gt; | 无返回结果的Promise对象。                  |

**错误码：**

以下错误码的详细介绍请参见[文件管理错误码](errorcode-filemanagement.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 13600001 | IPC error. |
| 13600002 | Not supported filesystem. |
| 13600005 | Incorrect volume state. |
| 13600008 | No such object. |
| 13900042 | Unknown error. |

**示例：**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let uuid: string = "";
  let description: string = "";
  volumeManager.setVolumeDescription(uuid, description).then(() => {
    console.info("setVolumeDescription successfully");
  }).catch((error: BusinessError) => {
    console.error("setVolumeDescription failed with error:" + JSON.stringify(error));
  });
  ```

## volumemanager.setVolumeDescription

setVolumeDescription(uuid: string, description: string, callback: AsyncCallback&lt;void&gt;): void

修改指定卷设备描述，使用callback异步回调。当前仅支持修改ntfs和exfat两种文件系统类型的设备描述，只有处于卸载状态的卷设备可以修改设备描述。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.MOUNT_UNMOUNT_MANAGER

**系统能力**：SystemCapability.FileManagement.StorageService.Volume

**参数：**

  | 参数名      | 类型                                     | 必填 | 说明              |
  | ---------- | --------------------------------------- | ---- | ---------------- |
  | uuid       | string                                  | 是   | 卷设备uuid。            |
  | description | string                                 | 是   | 卷设备描述。            |
  | callback   | AsyncCallback&lt;void&gt;   | 是   | 设置卷描述之后的回调。 |

**错误码：**

以下错误码的详细介绍请参见[文件管理错误码](errorcode-filemanagement.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 13600001 | IPC error. |
| 13600002 | Not supported filesystem. |
| 13600005 | Incorrect volume state. |
| 13600008 | No such object. |
| 13900042 | Unknown error. |

**示例：**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let uuid: string = "";
  let description: string = "";
  volumeManager.setVolumeDescription(uuid, description, (error: BusinessError) => {
    // do something    
  });
  ```

## volumemanager.format

format(volumeId: string, fsType: string): Promise&lt;void&gt;

对指定卷设备进行格式化，使用Promise异步回调。

当前仅支持以下文件系统类型的格式化：

vfat和exfat。

从API版本26.0.0开始支持ext4文件系统的格式化。

只有处于卸载状态的卷设备可以进行格式化，格式化后卷设备的uuid、挂载路径和卷设备描述均会发生变化。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.MOUNT_FORMAT_MANAGER

**系统能力**：SystemCapability.FileManagement.StorageService.Volume

**参数：**

  | 参数名       | 类型   | 必填 | 说明 |
  | ----------- | ------ | ---- | ---- |
  | volumeId    | string | 是   | 卷设备id。 |
  | fsType    | string | 是   | 文件系统类型（vfat或者exfat）。 |

**返回值：**

  | 类型                   | 说明       |
  | ---------------------- | ---------- |
  | Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[文件管理错误码](errorcode-filemanagement.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 13600001 | IPC error. |
| 13600002 | Not supported filesystem. |
| 13600005 | Incorrect volume state. |
| 13600008 | No such object. |
| 13900042 | Unknown error. |

**示例：**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let volumeId: string = "";
  let fsType: string = "";
  volumeManager.format(volumeId, fsType).then(() => {
    console.info("format successfully");
  }).catch((error: BusinessError) => {
    console.error("format failed with error:" + JSON.stringify(error));
  });
  ```

## volumemanager.format

format(volumeId: string, fsType: string, callback: AsyncCallback&lt;void&gt;): void

对指定卷设备进行格式化，使用callback异步回调。

当前仅支持以下文件系统类型的格式化：

vfat和exfat。

从API版本26.0.0开始支持ext4文件系统的格式化。

只有处于卸载状态的卷设备可以进行格式化，格式化后卷设备的uuid、挂载路径和卷设备描述均会发生变化。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.MOUNT_FORMAT_MANAGER

**系统能力**：SystemCapability.FileManagement.StorageService.Volume

**参数：**

  | 参数名   | 类型                      | 必填 | 说明                          |
  | -------- | ------------------------- | ---- | ----------------------------- |
  | volumeId | string                    | 是   | 卷设备id。                |
  | fsType    | string | 是   | 文件系统类型(vfat或者exfat)。 |
  | callback | AsyncCallback&lt;void&gt;  | 是   | 对指定卷设备格式化后的回调。  |

**错误码：**

以下错误码的详细介绍请参见[文件管理错误码](errorcode-filemanagement.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 13600001 | IPC error. |
| 13600002 | Not supported filesystem. |
| 13600005 | Incorrect volume state. |
| 13600008 | No such object. |
| 13900042 | Unknown error. |

**示例：**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let volumeId: string = "";
  let fsType: string = "";
  volumeManager.format(volumeId, fsType, (error: BusinessError) => {
    // do something    
  });
  ```

## volumemanager.partition

partition(diskId: string, type: number): Promise&lt;void&gt;

对磁盘设备进行分区，使用Promise异步回调。当前仅支持将磁盘设备重新分区为一个分区，系统是支持读取多分区的磁盘设备。不支持对光盘进行分区。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.MOUNT_FORMAT_MANAGER

**系统能力**：SystemCapability.FileManagement.StorageService.Volume

**参数：**

  | 参数名       | 类型   | 必填 | 说明 |
  | ----------- | ------ | ---- | ---- |
  | diskId    | string | 是   | 卷设备所属的磁盘设备id。 |
  | type      | number | 是   | 分区类型。    |

**返回值：**

  | 类型                      | 说明                       |
  | --------------------- | ----------------------- |
  | Promise&lt;void&gt;   | 无返回结果的Promise对象。              |

**错误码：**

以下错误码的详细介绍请参见[文件管理错误码](errorcode-filemanagement.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 13600001 | IPC error. |
| 13600008 | No such object. |
| 13900042 | Unknown error. |

**示例：**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let diskId: string = "";
  let type: number = 0;
  volumeManager.partition(diskId, type).then(() => {
    console.info("partition successfully");
  }).catch((error: BusinessError) => {
    console.error("partition failed with error:" + JSON.stringify(error));
  });
  ```

## volumemanager.partition

partition(diskId: string, type: number, callback: AsyncCallback&lt;void&gt;): void

对磁盘进行分区，使用callback异步回调。当前仅支持将磁盘设备重新分区为一个分区，系统是支持读取多分区的磁盘设备。不支持对光盘进行分区。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.MOUNT_FORMAT_MANAGER

**系统能力**：SystemCapability.FileManagement.StorageService.Volume

**参数：**

  | 参数名      | 类型                                   | 必填 | 说明              |
  | -------- | --------------------------------------- | ---- | ---------------- |
  | diskId   | string                                  | 是   | 卷设备所属的磁盘id。      |
  | type     | number                                  | 是   | 分区类型。          |
  | callback | AsyncCallback&lt;void&gt;   | 是   | 对磁盘设备进行分区。      |

**错误码：**

以下错误码的详细介绍请参见[文件管理错误码](errorcode-filemanagement.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 13600001 | IPC error. |
| 13600008 | No such object. |
| 13900042 | Unknown error. |

**示例：**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let diskId: string = "";
  let type: number = 0;
  volumeManager.partition(diskId, type, (error: BusinessError) => {
    // do something    
  });
  ```

## VerifyType

刻录数据校验类型的枚举。

**起始版本**：26.0.0

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.FileManagement.StorageService.Volume

**系统接口**：此接口为系统接口。

| 名称         | 值    | 说明                 |
| ----------- | ------- | -------------------- |
| KEY_DATA    | 0       | 关键数据校验类型。     |
| FULL_DATA   | 1       | 全量数据校验类型。     |

## volumemanager.erase

erase(volumeId: string): Promise&lt;void&gt;

擦除指定卷设备，使用Promise异步回调。

**起始版本**：26.0.0

**需要权限**：ohos.permission.MOUNT_UNMOUNT_MANAGER

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.FileManagement.StorageService.Volume

**系统接口**：此接口为系统接口。

**参数：**

| 参数名   | 类型   | 必填 | 说明 |
| -------- | ------ | ---- | ---- |
| volumeId | string | 是   | 卷设备id。 |

**返回值：**

| 类型                   | 说明       |
| ---------------------- | ---------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[文件管理错误码](errorcode-filemanagement.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 13600001 | IPC error. |
| 13600005 | Incorrect volume state. |
| 13600008 | No such object. |
| 13600023 | Disc not erasable. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let volumeId: string = "";
volumeManager.erase(volumeId).then(() => {
  console.info("erase successfully.");
}).catch((error: BusinessError) => {
  console.error("erase failed with error:" + JSON.stringify(error));
});
```

## volumemanager.eject

eject(volumeId: string): Promise&lt;void&gt;

弹出指定卷设备，使用Promise异步回调。

**起始版本**：26.0.0

**需要权限**：ohos.permission.MOUNT_UNMOUNT_MANAGER

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.FileManagement.StorageService.Volume

**系统接口**：此接口为系统接口。

**参数：**

| 参数名   | 类型   | 必填 | 说明 |
| -------- | ------ | ---- | ---- |
| volumeId | string | 是   | 卷设备id。 |

**返回值：**

| 类型                   | 说明       |
| ---------------------- | ---------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[文件管理错误码](errorcode-filemanagement.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 13600001 | IPC error. |
| 13600005 | Incorrect volume state. |
| 13600008 | No such object. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let volumeId: string = "";
volumeManager.eject(volumeId).then(() => {
  console.info("eject successfully.");
}).catch((error: BusinessError) => {
  console.error("eject failed with error:" + JSON.stringify(error));
});
```

## volumemanager.createIsoImage

createIsoImage(volumeId: string, filePath: string): Promise&lt;void&gt;

从指定卷设备创建ISO镜像文件，使用Promise异步回调。

**起始版本**：26.0.0

**需要权限**：ohos.permission.MOUNT_UNMOUNT_MANAGER

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.FileManagement.StorageService.Volume

**系统接口**：此接口为系统接口。

**参数：**

| 参数名   | 类型   | 必填 | 说明 |
| -------- | ------ | ---- | ---- |
| volumeId | string | 是   | 卷设备id。 |
| filePath | string | 是   | ISO镜像文件的保存路径。 |

**返回值：**

| 类型                   | 说明       |
| ---------------------- | ---------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[文件管理错误码](errorcode-filemanagement.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 13600001 | IPC error. |
| 13600005 | Incorrect volume state. |
| 13600008 | No such object. |
| 13600024 | Empty disc. |
| 13600025 | Failed to write the ISO file. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let volumeId: string = "";
let filePath: string = "";
volumeManager.createIsoImage(volumeId, filePath).then(() => {
  console.info("createIsoImage successfully.");
}).catch((error: BusinessError) => {
  console.error("createIsoImage failed with error:" + JSON.stringify(error));
});
```

## volumemanager.burn

burn(volumeId: string, want: Want): Promise&lt;void&gt;

向指定卷设备刻录数据，使用Promise异步回调。

**起始版本**：26.0.0

**需要权限**：ohos.permission.MOUNT_UNMOUNT_MANAGER

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.FileManagement.StorageService.Volume

**系统接口**：此接口为系统接口。

**参数：**

| 参数名   | 类型   | 必填 | 说明 |
| -------- | ------ | ---- | ---- |
| volumeId | string | 是   | 卷设备id。 |
| want | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | 是   | 启动Ability的Want信息。 |

**返回值：**

| 类型                   | 说明       |
| ---------------------- | ---------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |
 
**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[文件管理错误码](errorcode-filemanagement.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 13600001 | IPC error. |
| 13600005 | Incorrect volume state. |
| 13600008 | No such object. |
| 13600026 | Insufficient disc space. |
| 13600027 | Source data not found. |
| 13600028 | Burn operation failed. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

import { Want } from '@kit.AbilityKit';
let volumeId: string = "";
let want: Want = {
  diskName: "MyDisc",
  burnPath: "/data/storage/el2/base/files/burn_data",
  isIsoImage: false,
  burnSpeed: 0,
  fsType: "ISO9660",
  isIncBurnSupport: true
};
volumeManager.burn(volumeId, want).then(() => {
  console.info("burn successfully.");
}).catch((error: BusinessError) => {
  console.error("burn failed with error:" + JSON.stringify(error));
});
```

## volumemanager.getOpProcess

getOpProcess(volumeId: string): Promise&lt;number&gt;

获取指定卷设备的操作进度，使用Promise异步回调。

**起始版本**：26.0.0

**需要权限**：ohos.permission.MOUNT_UNMOUNT_MANAGER

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.FileManagement.StorageService.Volume

**系统接口**：此接口为系统接口。

**参数：**

| 参数名   | 类型   | 必填 | 说明 |
| -------- | ------ | ---- | ---- |
| volumeId | string | 是   | 卷设备id。 |

**返回值：**

| 类型                   | 说明       |
| ---------------------- | ---------- |
| Promise&lt;number&gt; | Promise对象，返回光驱刻录操作进度，进度值为0-100的整数。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[文件管理错误码](errorcode-filemanagement.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 13600001 | IPC error. |
| 13600008 | No such object. |
| 13600029 | No ongoing operation. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let volumeId: string = "";
volumeManager.getOpProcess(volumeId).then((progress: number) => {
  console.info("getOpProcess successfully, progress:" + progress);
}).catch((error: BusinessError) => {
  console.error("getOpProcess failed with error:" + JSON.stringify(error));
});
```

## volumemanager.verifyBurnData

verifyBurnData(volumeId: string, verType: VerifyType): Promise&lt;void&gt;

校验指定卷设备的刻录数据，使用Promise异步回调。

**起始版本**：26.0.0

**需要权限**：ohos.permission.MOUNT_UNMOUNT_MANAGER

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.FileManagement.StorageService.Volume

**系统接口**：此接口为系统接口。

**参数：**

| 参数名   | 类型   | 必填 | 说明 |
| -------- | ------ | ---- | ---- |
| volumeId | string | 是   | 卷设备id。 |
| verType | [VerifyType](#verifytype) | 是   | 刻录数据的校验类型。 |

**返回值：**

| 类型                   | 说明       |
| ---------------------- | ---------- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[文件管理错误码](errorcode-filemanagement.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 13600001 | IPC error. |
| 13600005 | Incorrect volume state. |
| 13600008 | No such object. |
| 13600030 | Verification failed. |
| 13600031 | Data mismatch. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let volumeId: string = "";
let verType: volumeManager.VerifyType = volumeManager.VerifyType.KEY_DATA;
volumeManager.verifyBurnData(volumeId, verType).then(() => {
  console.info("verifyBurnData successfully.");
}).catch((error: BusinessError) => {
  console.error("verifyBurnData failed with error:" + JSON.stringify(error));
});
```

## Volume

**系统接口**：此接口为系统接口。

**系统能力**：以下各项对应的系统能力均为SystemCapability.FileManagement.StorageService.Volume。

### 属性

| 名称         | 类型    | 只读   | 可选   | 说明                 |
| ----------- | ------- | ------- | ----- | -------------------- |
| id          | string  | 否 | 否 | 卷设备ID的格式为vol-{主设备号}-{次设备号}，主设备号用来区分不同种类的设备，次设备号用来区分同一类型的多个设备，卷设备ID会随着插卡顺序不同而变化。                 |
| uuid        | string  | 否 | 否 | 卷设备uuid是卷设备的通用唯一识别码，不会随着插卡顺序变化而变化，但是卷设备的格式化会改变卷设备的uuid。               |
| diskId      | string  | 否 | 否 | 卷设备所属的磁盘ID，一个磁盘可以有一个或者多个卷设备。磁盘设备ID的格式为disk-{主设备号}-{次设备号}，与卷设备ID相似。        |
| description | string  | 否 | 否 | 卷设备描述。           |
| removable   | boolean | 否 | 否 | 表示卷设备是否可移除，当前仅支持可移除存储设备。true为可移除；false为不可移除。 |
| state       | number  | 否 | 否 | 卷设备状态标识：<br>0：卸载状态 UNMOUNTED。<br> 1：检查状态 CHECKING。<br> 2：挂载状态 MOUNTED。<br> 3：正在弹出状态 EJECTING。          |
| path        | string  | 否 | 否 | 卷设备的挂载地址，一般为/mnt/data/external/{uuid}。         |
| fsType<sup>12+</sup>        | string  | 否 | 否 | 文件系统的类型，常见有ext2、vfat、NTFS等。<br>**说明**：从API version 24开始，支持ISO9660、UDF。      |
| extraInfo   | string  | 否 | 是 | 卷设备的扩展信息。<br>**起始版本：** 26.0.0<br>**模型约束**：此接口仅可在Stage模型下使用。         |