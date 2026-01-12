# @ohos.file.volumeManager (Volume Management) (System API)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @wang_zhangjun; @gzhuangzhuang-->
<!--Designer: @wang_zhangjun; @gzhuangzhuang; @renguang1116-->
<!--Tester: @liuhonggang123; @yue-ye2; @juxiaopang-->
<!--Adviser: @jinqiuheng-->

The **volumeManager** module provides APIs for querying and managing volumes and disks, including querying volume information, mounting or unmounting a volume, partitioning a disk, and formatting a volume.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The APIs provided by this module are system APIs.

## Modules to Import

```ts
import { volumeManager } from '@kit.CoreFileKit';
```

## volumemanager.getAllVolumes

getAllVolumes(): Promise&lt;Array&lt;Volume&gt;&gt;

Obtains information about all volumes of this external storage device. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.STORAGE_MANAGER

**System capability**: SystemCapability.FileManagement.StorageService.Volume

**Return value**

  | Type                              | Description                      |
  | ---------------------------------- | -------------------------- |
  | Promise&lt;[Volume](#volume)[]&gt; | Promise used to return the information about all available volume devices.|

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message|
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: Mandatory parameters are left unspecified. |
| 13600001 | IPC error. |
| 13900042 | Unknown error. |

**Example**

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

Obtains information about all volumes of this external storage device. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.STORAGE_MANAGER

**System capability**: SystemCapability.FileManagement.StorageService.Volume

**Parameters**

  | Name  | Type                                             | Mandatory| Description                                |
  | -------- | ------------------------------------------------- | ---- | ------------------------------------ |
  | callback | AsyncCallback&lt;[Volume](#volume)[]&gt; | Yes  | Callback used to return information about all available volumes.|

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message|
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: Mandatory parameters are left unspecified. |
| 13600001 | IPC error. |
| 13900042 | Unknown error. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  volumeManager.getAllVolumes((error: BusinessError, volumes: Array<volumeManager.Volume>) => {
    // Do something.
  });
  ```

## volumemanager.mount

mount(volumeId: string): Promise&lt;void&gt;

Mounts a volume. This API uses a promise to return the result. Currently, only the FAT, exFAT, and NTFS file systems are supported.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MOUNT_UNMOUNT_MANAGER

**System capability**: SystemCapability.FileManagement.StorageService.Volume

**Parameters**

  | Name  | Type  | Mandatory| Description|
  | -------- | ------ | ---- | ---- |
  | volumeId | string | Yes  | Volume ID.|

**Return value**

  | Type                  | Description      |
  | ---------------------- | ---------- |
  | Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message|
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

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let volumeId: string = "";
  volumeManager.mount(volumeId).then(() => {
    // Do something.
  }).catch((error: BusinessError) => {
    console.error("mount failed");
  });
  ```

## volumemanager.mount

mount(volumeId: string, callback:AsyncCallback&lt;void&gt;):void

Mounts a volume. This API uses an asynchronous callback to return the result. Currently, only the FAT, exFAT, and NTFS file systems are supported.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MOUNT_UNMOUNT_MANAGER

**System capability**: SystemCapability.FileManagement.StorageService.Volume

**Parameters**

  | Name  | Type                                 | Mandatory| Description                |
  | -------- | ------------------------------------- | ---- | -------------------- |
  | volumeId | string                                | Yes  | Volume ID.                |
  | callback | AsyncCallback&lt;void&gt; | Yes  | Callback invoked when the specified volume is mounted.|

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message|
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

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let volumeId: string = "";
  volumeManager.mount(volumeId, (error: BusinessError) => {
    // Do something.
  });
  ```

## volumemanager.unmount

unmount(volumeId: string): Promise&lt;void&gt;

Unmounts a volume. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MOUNT_UNMOUNT_MANAGER

**System capability**: SystemCapability.FileManagement.StorageService.Volume

**Parameters**

  | Name  | Type  | Mandatory| Description|
  | -------- | ------ | ---- | ---- |
  | volumeId | string | Yes  | Volume ID.|

**Return value**

  | Type                  | Description      |
  | ---------------------- | ---------- |
  | Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message|
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

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let volumeId: string = "";
  volumeManager.unmount(volumeId).then(() => {
    // Do something.
  }).catch((error: BusinessError) => {
    console.error("mount failed");
  });
  ```

## volumemanager.unmount

unmount(volumeId: string, callback: AsyncCallback&lt;void&gt;): void

Unmounts a volume. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MOUNT_UNMOUNT_MANAGER

**System capability**: SystemCapability.FileManagement.StorageService.Volume

**Parameters**

  | Name  | Type                                 | Mandatory| Description                |
  | -------- | ------------------------------------- | ---- | -------------------- |
  | volumeId | string                                | Yes  | Volume ID.                |
  | callback | AsyncCallback&lt;void&gt; | Yes  | Callback invoked when the specified volume is unmounted.|

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message|
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

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let volumeId: string = "";
  volumeManager.unmount(volumeId, (error: BusinessError) => {
    // Do something.
  });
  ```

## volumemanager.getVolumeByUuid

getVolumeByUuid(uuid: string): Promise&lt;Volume&gt;

Obtains information about a volume based on the universally unique identifier (UUID). This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.STORAGE_MANAGER

**System capability**: SystemCapability.FileManagement.StorageService.Volume

**Parameters**

  | Name  | Type  | Mandatory| Description|
  | -------- | ------ | ---- | ---- |
  | uuid | string | Yes  | UUID of the volume.|

**Return value**

  | Type                              | Description                      |
  | ---------------------------------- | -------------------------- |
  | Promise&lt;[Volume](#volume)&gt; | Promise used to return the volume information of the current UUID.|

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message|
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 13600001 | IPC error. |
| 13600008 | No such object. |
| 13900042 | Unknown error. |

**Example**

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

Obtains information about a volume based on the UUID. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.STORAGE_MANAGER

**System capability**: SystemCapability.FileManagement.StorageService.Volume

**Parameters**

  | Name   | Type                                                | Mandatory| Description                |
  | -------- | ------------------------------------------------ | ---- | -------------------- |
  | uuid | string                                                 | Yes  | UUID of the volume.                |
  | callback | AsyncCallback&lt;[Volume](#volume)&gt;  | Yes  | Callback used to return the volume information obtained.|

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message|
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 13600001 | IPC error. |
| 13600008 | No such object. |
| 13900042 | Unknown error. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let uuid: string = "";
  volumeManager.getVolumeByUuid(uuid, (error: BusinessError, volume: volumeManager.Volume) => {
    // Do something.   
  });
  ```

## volumemanager.getVolumeById

getVolumeById(volumeId: string): Promise&lt;Volume&gt;

Obtains information about a volume based on the volume ID. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.STORAGE_MANAGER

**System capability**: SystemCapability.FileManagement.StorageService.Volume

**Parameters**

  | Name   | Type   | Mandatory | Description|
  | -------- | ------ | ---- | ---- |
  | volumeId | string | Yes  | Volume ID.|

**Return value**

  | Type                              | Description                      |
  | ---------------------------------- | -------------------------- |
  | Promise&lt;[Volume](#volume)&gt; | Promise used to return the volume information of the current ID.|

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message|
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 13600001 | IPC error. |
| 13600008 | No such object. |
| 13900042 | Unknown error. |

**Example**

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

Obtains information about a volume based on the volume ID. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.STORAGE_MANAGER

**System capability**: SystemCapability.FileManagement.StorageService.Volume

**Parameters**

  | Name  | Type                     | Mandatory| Description                         |
  | -------- | ------------------------- | ---- | ----------------------------- |
  | volumeId | string                    | Yes  | Volume ID.               |
  | callback | AsyncCallback&lt;[Volume](#volume)&gt; | Yes  | Callback used to return the volume information obtained. |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message|
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 13600001 | IPC error. |
| 13600008 | No such object. |
| 13900042 | Unknown error. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let volumeId: string = "";
  volumeManager.getVolumeById(volumeId, (error: BusinessError, volume: volumeManager.Volume) => {
    // Do something.   
  });
  ```

## volumemanager.setVolumeDescription

setVolumeDescription(uuid: string, description: string): Promise&lt;void&gt;

Sets volume description. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MOUNT_UNMOUNT_MANAGER

**System capability**: SystemCapability.FileManagement.StorageService.Volume

**Parameters**

  | Name    | Type  | Mandatory| Description|
  | --------- | ------ | ---- | ---- |
  | uuid      | string | Yes  | UUID of the volume.|
  | description | string | Yes  | Description of the volume.|

**Return value**

  | Type                   | Description                      |
  | ---------------------- | -------------------------- |
  | Promise&lt;void&gt; | Promise that returns no value.                 |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message|
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 13600001 | IPC error. |
| 13600002 | Not supported filesystem. |
| 13600005 | Incorrect volume state. |
| 13600008 | No such object. |
| 13900042 | Unknown error. |

**Example**

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

Sets volume description. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MOUNT_UNMOUNT_MANAGER

**System capability**: SystemCapability.FileManagement.StorageService.Volume

**Parameters**

  | Name     | Type                                    | Mandatory| Description             |
  | ---------- | --------------------------------------- | ---- | ---------------- |
  | uuid       | string                                  | Yes  | UUID of the volume.           |
  | description | string                                 | Yes  | Description of the volume.           |
  | callback   | AsyncCallback&lt;void&gt;   | Yes  | Callback invoked after the volume description is set.|

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message|
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 13600001 | IPC error. |
| 13600002 | Not supported filesystem. |
| 13600005 | Incorrect volume state. |
| 13600008 | No such object. |
| 13900042 | Unknown error. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let uuid: string = "";
  let description: string = "";
  volumeManager.setVolumeDescription(uuid, description, (error: BusinessError) => {
    // Do something.   
  });
  ```

## volumemanager.format

format(volumeId: string, fsType: string): Promise&lt;void&gt;

Formats a volume. This API uses a promise to return the result. Currently, only the virtual file allocation table (VFAT) and exFAT file systems are supported. Only unmounted volumes can be formatted. After a volume is formatted, the UUID, mounting path, and description of the volume will change.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MOUNT_FORMAT_MANAGER

**System capability**: SystemCapability.FileManagement.StorageService.Volume

**Parameters**

  | Name      | Type  | Mandatory| Description|
  | ----------- | ------ | ---- | ---- |
  | volumeId    | string | Yes  | Volume ID.|
  | fsType    | string | Yes  | File system type, which can be VFAT or exFAT.|

**Return value**

  | Type                  | Description      |
  | ---------------------- | ---------- |
  | Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message|
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 13600001 | IPC error. |
| 13600002 | Not supported filesystem. |
| 13600005 | Incorrect volume state. |
| 13600008 | No such object. |
| 13900042 | Unknown error. |

**Example**

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

Formats a volume. This API uses an asynchronous callback to return the result. Currently, only the VFAT and exFAT file systems are supported. Only unmounted volumes can be formatted. After a volume is formatted, the UUID, mounting path, and description of the volume will change.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MOUNT_FORMAT_MANAGER

**System capability**: SystemCapability.FileManagement.StorageService.Volume

**Parameters**

  | Name  | Type                     | Mandatory| Description                         |
  | -------- | ------------------------- | ---- | ----------------------------- |
  | volumeId | string                    | Yes  | Volume ID.               |
  | fsType    | string | Yes  | File system type, which can be VFAT or exFAT.|
  | callback | AsyncCallback&lt;void&gt;  | Yes  | Callback that returns no value. |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message|
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 13600001 | IPC error. |
| 13600002 | Not supported filesystem. |
| 13600005 | Incorrect volume state. |
| 13600008 | No such object. |
| 13900042 | Unknown error. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let volumeId: string = "";
  let fsType: string = "";
  volumeManager.format(volumeId, fsType, (error: BusinessError) => {
    // Do something.   
  });
  ```

## volumemanager.partition

partition(diskId: string, type: number): Promise&lt;void&gt;

Partitions a disk. This API uses a promise to return the result. The system supports access to multi-partition disks. Currently, this API can partition a disk into only one partition.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MOUNT_FORMAT_MANAGER

**System capability**: SystemCapability.FileManagement.StorageService.Volume

**Parameters**

  | Name      | Type  | Mandatory| Description|
  | ----------- | ------ | ---- | ---- |
  | diskId    | string | Yes  | ID of the disk to partition.|
  | type      | number | Yes  | Partition type.   |

**Return value**

  | Type                     | Description                      |
   | --------------------- | ----------------------- |
  | Promise&lt;void&gt;   | Promise that returns no value.             |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message|
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 13600001 | IPC error. |
| 13600008 | No such object. |
| 13900042 | Unknown error. |

**Example**

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

Partitions a disk. This API uses a callback to return the result. The system supports access to multi-partition disks. Currently, this API can partition a disk into only one partition.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MOUNT_FORMAT_MANAGER

**System capability**: SystemCapability.FileManagement.StorageService.Volume

**Parameters**

  | Name     | Type                                  | Mandatory| Description             |
  | -------- | --------------------------------------- | ---- | ---------------- |
  | diskId   | string                                  | Yes  | ID of the disk to partition.     |
  | type     | number                                  | Yes  | Partition type.         |
  | callback | AsyncCallback&lt;void&gt;   | Yes  | Callback that returns no value.     |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID| Error Message|
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 401 | The input parameter is invalid. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 13600001 | IPC error. |
| 13600008 | No such object. |
| 13900042 | Unknown error. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let diskId: string = "";
  let type: number = 0;
  volumeManager.partition(diskId, type, (error: BusinessError) => {
    // Do something.   
  });
  ```

## Volume

**System API**: This is a system API.

**System capability**: SystemCapability.FileManagement.StorageService.Volume

### Attributes

| Name        | Type   | Read-Only  | Optional  | Description                |
| ----------- | ------- | ------- | ----- | -------------------- |
| id          | string  | No| No| Volume ID, in the vol-{Primary device ID}-{Secondary device ID} format. The primary device IDs identify devices of different types. The secondary device IDs identify different devices of the same type. The volume IDs vary depending on the card insertion sequence.                |
| uuid        | string  | No| No| Volume UUID, which uniquely identifies a volume irrespective of the card insertion sequence. However, the UUID of a volume will change after the volume is formatted.              |
| diskId      | string  | No| No| ID of the disk to which the volume belongs. A disk can have one or more volumes. The disk ID is in the disk-{Primary device ID}-{Secondary device ID} format, which is similar to the volume ID.       |
| description | string  | No| No| Description of the volume.          |
| removable   | boolean | No| No| Whether the volume can be removed. Currently, only removable storage devices are supported. The value **true** means the device can be removed; the value **false** means the opposite.|
| state       | number  | No| No| Volume status.<br>**0**: The volume is unmounted.<br> **1**: The volume is being checked.<br> **2**: The volume is mounted.<br> **3**: The volume is being ejected.         |
| path        | string  | No| No| Path of the volume mounted. Generally, the path is **/mnt/data/external/{uuid}**.        |
| fsType<sup>12+</sup>        | string  | No| No| File system type. Common file systems are **ext2**, **vfat**, and **NTFS**.      |
