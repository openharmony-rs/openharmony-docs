# @ohos.file.volumeManager (Volume Management) (System API)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @ning-jingyou-->
<!--Designer: @renguang1116; @wang_zhangjun-->
<!--Tester: @zsyztt; @yue-ye2; @fuwei-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=41c4cfa70d889e724ef4595936fcf122837f23cc translatedAt=2026-11-04T04:32:26.931Z pushedAt=2026-11-04T10:12:33.500Z nl=1 -->

This module provides functions for querying and managing volume devices and disk devices, including querying volume device information and disk device information, mounting, unmounting, and ejecting volume devices, erasing volume devices, creating, deleting, and formatting partitions on disk devices, querying partition tables, formatting volume devices, and burning optical discs (including creating ISO images, burning data, verifying burned data, and querying operation progress).

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

  | Type                               | Description                       |
  | ---------------------------------- | -------------------------- |
  | Promise&lt;[Volume](#volume)[]&gt; | Promise object, returns information about all currently available volume devices. |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID | Error Message |
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
    // Obtain the information about all volume devices.
  }).catch((error: BusinessError) => {
    console.error(`Failed to getAllVolumes. Code: ${error.code}, message: ${error.message}`);
  });
  ```

## volumemanager.getAllVolumes

getAllVolumes(callback: AsyncCallback&lt;Array&lt;Volume&gt;&gt;): void

Obtains information about all volumes of this external storage device. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.STORAGE_MANAGER

**System capability**: SystemCapability.FileManagement.StorageService.Volume

**Parameters**

  | Name   | Type                                              | Mandatory | Description                                 |
  | -------- | ------------------------------------------------- | ---- | ------------------------------------ |
  | callback | AsyncCallback&lt;[Volume](#volume)[]&gt; | Yes   | Callback after getting all currently available volume device information. |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID | Error Message |
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
    if (error) {
      console.error(`getAllVolumes failed, code is: ${error.code}, message is: ${error.message}`);
      return;
    }
    // Obtain the information of all volume devices.
  });
  ```

## volumemanager.mount

mount(volumeId: string): Promise&lt;void&gt;

Mount the specified volume device. Only when in the unmounted state can a volume device be mounted. This API uses a promise to return the result asynchronously.

Currently only supports mounting volume devices with the following file systems:

vfat, exfat, and ntfs.

Supported since API version 26.0.0 for ext4.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MOUNT_UNMOUNT_MANAGER

**System capability**: SystemCapability.FileManagement.StorageService.Volume

**Parameters**

  | Name   | Type   | Mandatory | Description |
  | -------- | ------ | ---- | ---- |
  | volumeId | string | Yes   | Volume device ID, in the format of vol-{major device number}-{minor device number}. The volume device ID changes with the card insertion order. Do not cache it for reuse. |

**Return value**

  | Type                   | Description       |
  | ---------------------- | ---------- |
  | Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID | Error Message |
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
  // Obtain volumeId through getAllVolumes().
  let volumeId: string = "";
  volumeManager.mount(volumeId).then(() => {
    // Callback after the specified volume device is mounted successfully.
  }).catch((error: BusinessError) => {
    console.error(`Failed to mount. Code: ${error.code}, message: ${error.message}`);
  });
  ```

## volumemanager.mount

mount(volumeId: string, callback:AsyncCallback&lt;void&gt;):void

Mount the specified volume device. Only a volume device in the unmounted state can be mounted. This API uses an asynchronous callback.

Currently only supports mounting volume devices with the following file systems:

vfat, exfat, and ntfs.

Supported since API version 26.0.0 for ext4.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MOUNT_UNMOUNT_MANAGER

**System capability**: SystemCapability.FileManagement.StorageService.Volume

**Parameters**

  | Name   | Type                                  | Mandatory | Description                 |
  | -------- | ------------------------------------- | ---- | -------------------- |
  | volumeId | string                                | Yes   | Volume device ID, in the format of vol-{major device number}-{minor device number}. The volume device ID changes with the card insertion order. Do not cache it for reuse.                 |
  | callback | AsyncCallback&lt;void&gt; | Yes   | Callback after the specified volume device is mounted. |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID | Error Message |
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
  // Obtain volumeId through getAllVolumes().
  let volumeId: string = "";
  volumeManager.mount(volumeId, (error: BusinessError) => {
    if (error) {
      console.error(`mount failed, code is: ${error.code}, message is: ${error.message}`);
      return;
    }
    // Callback after the specified volume device is mounted successfully.
  });
  ```

## volumemanager.unmount

unmount(volumeId: string): Promise&lt;void&gt;

Unmounts a volume. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MOUNT_UNMOUNT_MANAGER

**System capability**: SystemCapability.FileManagement.StorageService.Volume

**Parameters**

  | Name     | Type   | Mandatory | Description |
  | -------- | ------ | --------- | ----------- |
  | volumeId | string | Yes       | Volume device ID, in the format of vol-{major device number}-{minor device number}. The volume device ID changes with the card insertion order. Do not cache it for reuse. |

**Return value**

  | Type                   | Description       |
  | ---------------------- | ----------------- |
  | Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID | Error Message |
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
  // Obtain volumeId through getAllVolumes().
  let volumeId: string = "";
  volumeManager.unmount(volumeId).then(() => {
    // Callback invoked after the specified volume device is unmounted successfully.
  }).catch((error: BusinessError) => {
    console.error(`Failed to unmount. Code: ${error.code}, message: ${error.message}`);
  });
  ```

## volumemanager.unmount

unmount(volumeId: string, callback: AsyncCallback&lt;void&gt;): void

Unmounts a volume. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MOUNT_UNMOUNT_MANAGER

**System capability**: SystemCapability.FileManagement.StorageService.Volume

**Parameters**

  | Name   | Type                                  | Mandatory | Description                 |
  | -------- | ------------------------------------- | ---- | -------------------- |
  | volumeId | string                                | Yes   | Volume device ID, in the format of vol-{major device number}-{minor device number}. The volume device ID changes with the card insertion order. Do not cache it for reuse.                 |
  | callback | AsyncCallback&lt;void&gt; | Yes   | Callback after the specified volume device is unmounted. |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID | Error Message |
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
  // Obtain the volumeId through getAllVolumes().
  let volumeId: string = "";
  volumeManager.unmount(volumeId, (error: BusinessError) => {
    if (error) {
      console.error(`unmount failed, code is: ${error.code}, message is: ${error.message}`);
      return;
    }
    // Callback invoked after the specified volume device is unmounted successfully.
  });
  ```

## volumemanager.getVolumeByUuid

getVolumeByUuid(uuid: string): Promise&lt;Volume&gt;

Obtains information about a volume based on the universally unique identifier (UUID). This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.STORAGE_MANAGER

**System capability**: SystemCapability.FileManagement.StorageService.Volume

**Parameters**

  | Name   | Type   | Mandatory | Description |
  | -------- | ------ | ---- | ---- |
  | uuid | string | Yes   | UUID of the volume device. The UUID of the volume device does not change with the card insertion order, but will change after formatting. |

**Return value**

  | Type                               | Description                       |
  | ---------------------------------- | -------------------------- |
  | Promise&lt;[Volume](#volume)&gt; | Promise object, returns the volume device information corresponding to the specified UUID. |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID | Error Message |
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
  // Obtain the volume device information through getAllVolumes() to get the UUID.
  let uuid: string = "";
  volumeManager.getVolumeByUuid(uuid).then((volume: volumeManager.Volume) => {
    console.info("getVolumeByUuid successfully:" + JSON.stringify(volume));
  }).catch((error: BusinessError) => {
    console.error(`Failed to getVolumeByUuid. Code: ${error.code}, message: ${error.message}`);
  });
  ```

## volumemanager.getVolumeByUuid

getVolumeByUuid(uuid: string, callback: AsyncCallback&lt;Volume&gt;): void

Obtains information about a volume based on the UUID. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.STORAGE_MANAGER

**System capability**: SystemCapability.FileManagement.StorageService.Volume

**Parameters**

  | Name    | Type                                                 | Mandatory | Description                 |
  | -------- | ------------------------------------------------ | ---- | -------------------- |
  | uuid | string                                                 | Yes   | UUID of the volume device. The UUID of the volume device does not change with the card insertion order, but will change after formatting.                 |
  | callback | AsyncCallback&lt;[Volume](#volume)&gt;  | Yes   | Callback after obtaining the volume device information. |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID | Error Message |
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
  // Obtain the uuid through the getAllVolumes() API to get the volume device information.
  let uuid: string = "";
  volumeManager.getVolumeByUuid(uuid, (error: BusinessError, volume: volumeManager.Volume) => {
    if (error) {
      console.error(`getVolumeByUuid failed, code is: ${error.code}, message is: ${error.message}`);
      return;
    }
    // Obtain the volume device information.
  });
  ```

## volumemanager.getVolumeById

getVolumeById(volumeId: string): Promise&lt;Volume&gt;

Obtains information about a volume based on the volume ID. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.STORAGE_MANAGER

**System capability**: SystemCapability.FileManagement.StorageService.Volume

**Parameters**

  | Name    | Type    | Mandatory  | Description |
  | -------- | ------ | ---- | ---- |
  | volumeId | string | Yes   | Volume device ID, in the format of vol-{major device number}-{minor device number}. The volume device ID changes with the card insertion order. Do not cache it for reuse. |

**Return value**

  | Type                               | Description                       |
  | ---------------------------------- | -------------------------- |
  | Promise&lt;[Volume](#volume)&gt; | Promise object, which returns the volume device information corresponding to the specified volumeId. |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID | Error Message |
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
  // Obtain volumeId through getAllVolumes().
  let volumeId: string = "";
  volumeManager.getVolumeById(volumeId).then((volume: volumeManager.Volume) => {
    console.info("getVolumeById successfully:" + JSON.stringify(volume));
  }).catch((error: BusinessError) => {
    console.error(`Failed to getVolumeById. Code: ${error.code}, message: ${error.message}`);
  });
  ```

## volumemanager.getVolumeById

getVolumeById(volumeId: string, callback: AsyncCallback&lt;Volume&gt;): void

Obtains information about a volume based on the volume ID. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.STORAGE_MANAGER

**System capability**: SystemCapability.FileManagement.StorageService.Volume

**Parameters**

  | Name   | Type                      | Mandatory | Description                          |
  | -------- | ------------------------- | ---- | ----------------------------- |
  | volumeId | string                    | Yes   | Volume device ID, in the format of vol-{major device number}-{minor device number}. The volume device ID changes with the card insertion order. Do not cache it for reuse.                |
  | callback | AsyncCallback&lt;[Volume](#volume)&gt; | Yes   | Callback after obtaining the volume device information.  |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID | Error Message |
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
  // Obtain volumeId through getAllVolumes().
  let volumeId: string = "";
  volumeManager.getVolumeById(volumeId, (error: BusinessError, volume: volumeManager.Volume) => {
    if (error) {
      console.error(`getVolumeById failed, code is: ${error.code}, message is: ${error.message}`);
      return;
    }
    // Obtain the volume device information.
  });
  ```

## volumemanager.setVolumeDescription

setVolumeDescription(uuid: string, description: string): Promise&lt;void&gt;

Sets volume description. This API uses a promise to return the result. Currently, only the device descriptions of NTFS and exFAT file systems can be modified, and only for volume devices in the unmounted state.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MOUNT_UNMOUNT_MANAGER

**System capability**: SystemCapability.FileManagement.StorageService.Volume

**Parameters**

  | Name     | Type   | Mandatory | Description |
  | --------- | ------ | ---- | ---- |
  | uuid      | string | Yes   | UUID of the volume device. The UUID of the volume device does not change with the card insertion order, but will change after formatting. |
  | description | string | Yes   | Volume device description. |

**Return value**

  | Type                    | Description                       |
  | ---------------------- | -------------------------- |
  | Promise&lt;void&gt; | Promise that returns no value.                  |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID | Error Message |
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
  // Obtain the uuid from the volume device information returned by getAllVolumes().
  let uuid: string = "";
  let description: string = "";
  volumeManager.setVolumeDescription(uuid, description).then(() => {
    console.info("setVolumeDescription successfully");
  }).catch((error: BusinessError) => {
    console.error(`Failed to setVolumeDescription. Code: ${error.code}, message: ${error.message}`);
  });
  ```

## volumemanager.setVolumeDescription

setVolumeDescription(uuid: string, description: string, callback: AsyncCallback&lt;void&gt;): void

Sets volume description. This API uses an asynchronous callback to return the result. Currently, only the device descriptions of NTFS and exFAT file systems can be modified, and only for volume devices in the unmounted state.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MOUNT_UNMOUNT_MANAGER

**System capability**: SystemCapability.FileManagement.StorageService.Volume

**Parameters**

  | Name      | Type                                     | Mandatory | Description              |
  | ---------- | --------------------------------------- | ---- | ---------------- |
  | uuid       | string                                  | Yes   | UUID of the volume device. The UUID of the volume device does not change with the card insertion order, but will change after formatting.            |
  | description | string                                 | Yes   | Volume device description.            |
  | callback   | AsyncCallback&lt;void&gt;   | Yes   | Callback after setting the volume description. |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID | Error Message |
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
  // Obtain the volume device information through getAllVolumes() to get the uuid.
  let uuid: string = "";
  let description: string = "";
  volumeManager.setVolumeDescription(uuid, description, (error: BusinessError) => {
    if (error) {
      console.error(`setVolumeDescription failed, code is: ${error.code}, message is: ${error.message}`);
      return;
    }
    // Callback invoked when the volume device description is set successfully.
  });
  ```

## volumemanager.format

format(volumeId: string, fsType: string): Promise&lt;void&gt;

Formats the specified volume device. This API uses a promise to return the result asynchronously.

Currently, only the following file system types are supported for formatting:

vfat and exfat.

Formatting of the ext4 file system is supported since API version 26.0.0.

Only a volume device in the unmounted state can be formatted. After formatting, the UUID, mount path, and description of the volume device will change.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MOUNT_FORMAT_MANAGER

**System capability**: SystemCapability.FileManagement.StorageService.Volume

**Parameters**

  | Name       | Type   | Mandatory | Description |
  | ----------- | ------ | ---- | ---- |
  | volumeId    | string | Yes   | Volume device ID, in the format of vol-{major device number}-{minor device number}. The volume device must be in the unmounted state; otherwise, error code 13600005 is returned. The volume device ID changes with the card insertion order. Do not cache it for reuse. |
  | fsType    | string | Yes   | File system type. Currently, vfat and exfat are supported.<br>**Note**: ext4 is supported since API version 26.0.0. |

**Return value**

  | Type                   | Description       |
  | ---------------------- | ---------- |
  | Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID | Error Message |
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
  // Obtain the volumeId through getAllVolumes().
  let volumeId: string = "";
  let fsType: string = "";
  volumeManager.format(volumeId, fsType).then(() => {
    console.info("format successfully");
  }).catch((error: BusinessError) => {
    console.error(`Failed to format. Code: ${error.code}, message: ${error.message}`);
  });
  ```

## volumemanager.format

format(volumeId: string, fsType: string, callback: AsyncCallback&lt;void&gt;): void

Formats the specified volume device. This API uses an asynchronous callback to return the result.

Currently, only the following file system types are supported for formatting:

vfat and exfat.

Formatting of the ext4 file system is supported since API version 26.0.0.

Only a volume device in the unmounted state can be formatted. After formatting, the UUID, mount path, and description of the volume device will change.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MOUNT_FORMAT_MANAGER

**System capability**: SystemCapability.FileManagement.StorageService.Volume

**Parameters**

  | Name   | Type                      | Mandatory | Description                          |
  | -------- | ------------------------- | ---- | ----------------------------- |
  | volumeId | string                    | Yes   | Volume device ID, in the format of vol-{major device number}-{minor device number}. The volume device must be in the unmounted state; otherwise, error code 13600005 is returned. The volume device ID changes with the card insertion order. Do not cache it for reuse.                |
  | fsType    | string | Yes   | File system type. Currently, vfat and exfat are supported.<br>**Note**: ext4 is supported since API version 26.0.0. |
  | callback | AsyncCallback&lt;void&gt;  | Yes   | Callback after the specified volume device is formatted.  |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID | Error Message |
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
  // Obtain volumeId through getAllVolumes().
  let volumeId: string = "";
  let fsType: string = "";
  volumeManager.format(volumeId, fsType, (error: BusinessError) => {
    if (error) {
      console.error(`format failed, code is: ${error.code}, message is: ${error.message}`);
      return;
    }
    // Callback invoked when the specified volume device is formatted successfully.
  });
  ```

## volumemanager.partition

partition(diskId: string, type: number): Promise&lt;void&gt;

Partitions a disk. This API uses a promise to return the result. Currently, this API can repartition a disk into only one partition. The system supports access to disks that already have multiple partitions. Partitioning optical discs is not supported.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MOUNT_FORMAT_MANAGER

**System capability**: SystemCapability.FileManagement.StorageService.Volume

**Parameters**

  | Name       | Type   | Mandatory | Description |
  | ----------- | ------ | ---- | ---- |
  | diskId    | string | Yes   | ID of the disk device to which the volume device belongs, in the format disk-{major device number}-{minor device number}. |
  | type      | number | Yes   | Partition type, used to specify the partitioning method. Currently, only 0 is supported, which means repartitioning the disk into one partition.    |

**Return value**

  | Type                      | Description                       |
  | --------------------- | ----------------------- |
  | Promise&lt;void&gt;   | Promise that returns no value.              |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID | Error Message |
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
  // Obtain diskId through getAllDisks().
  let diskId: string = "";
  let type: number = 0;
  volumeManager.partition(diskId, type).then(() => {
    console.info("partition successfully");
  }).catch((error: BusinessError) => {
    console.error(`Failed to partition. Code: ${error.code}, message: ${error.message}`);
  });
  ```

## volumemanager.partition

partition(diskId: string, type: number, callback: AsyncCallback&lt;void&gt;): void

Partitions a disk device. This API uses an asynchronous callback to return the result. Currently, this API can partition a disk device into only one partition. The system supports access to disks that already have multiple partitions. Partitioning optical discs is not supported.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MOUNT_FORMAT_MANAGER

**System capability**: SystemCapability.FileManagement.StorageService.Volume

**Parameters**

  | Name      | Type                                   | Mandatory | Description              |
  | -------- | --------------------------------------- | ---- | ---------------- |
  | diskId   | string                                  | Yes   | ID of the disk device to which the volume device belongs, in the format disk-{major device number}-{minor device number}.      |
  | type     | number                                  | Yes   | Partition type, used to specify the partitioning method. Currently, only 0 is supported, which means repartitioning the disk into one partition.          |
  | callback | AsyncCallback&lt;void&gt;   | Yes   | Callback invoked after the disk device is partitioned.      |

**Error codes**

For details about the error codes, see [File Management Error Codes](errorcode-filemanagement.md).

| ID | Error Message |
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
  // Obtain diskId through getAllDisks().
  let diskId: string = "";
  let type: number = 0;
  volumeManager.partition(diskId, type, (error: BusinessError) => {
    if (error) {
      console.error(`partition failed, code is: ${error.code}, message is: ${error.message}`);
      return;
    }
    // Callback after the disk device is partitioned successfully.
  });
  ```

## VerifyType

Enumerates the verification types of burn data.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.FileManagement.StorageService.Volume

**System API**: This is a system API.

| Name         | Value    | Description                 |
| ----------- | ------- | -------------------- |
| KEY_DATA    | 0       | Key data verification type.     |
| FULL_DATA   | 1       | Full data verification type.     |

## volumemanager.erase

erase(volumeId: string): Promise&lt;void&gt;

Erases data on the specified volume device. This API uses a promise to return the result asynchronously. It applies to scenarios where data on a volume device needs to be completely cleared, for example, erasing data before rewriting an optical disc. The erase operation clears all data on the volume device. Only a volume device in the unmounted state can be erased.

**Since:** 26.0.0

**Required permissions**: ohos.permission.MOUNT_UNMOUNT_MANAGER

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.FileManagement.StorageService.Volume

**System API**: This is a system API.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | ------ | ---- | ---- |
| volumeId | string | Yes | Volume device ID, in the format of vol-{major device number}-{minor device number}. The volume device ID changes with the card insertion order. Do not cache it for reuse. |

**Return value**

| Type | Description |
| ---------------------- | ---------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 13600001 | IPC error. |
| 13600002 | Not supported filesystem. |
| 13600010 | The input parameter is invalid. |
| 13600026 | Erase operation failed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain volumeId through getAllVolumes().
let volumeId: string = "";
volumeManager.erase(volumeId).then(() => {
  console.info("erase successfully.");
}).catch((error: BusinessError) => {
  console.error(`Failed to erase. Code: ${error.code}, message: ${error.message}`);
});
```

## volumemanager.eject

eject(diskId: string): Promise&lt;void&gt;

Ejects the specified disk device and its associated volume devices. This API uses an asynchronous callback to return the result.

**Since:** 26.0.0

**Required permissions**: ohos.permission.MOUNT_UNMOUNT_MANAGER

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.FileManagement.StorageService.Volume

**System API**: This is a system API.

**Parameters**

| Name   | Type   | Mandatory | Description |
| -------- | ------ | ---- | ---- |
| diskId | string | Yes | ID of the disk device to which the volume device belongs, in the format disk-{major device number}-{minor device number}. |

**Return value**

| Type                   | Description       |
| ---------------------- | ---------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 13600001 | IPC error. |
| 13600002 | Not supported filesystem. |
| 13600027 | Eject operation failed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain diskId through getAllDisks().
let diskId: string = "";
volumeManager.eject(diskId).then(() => {
  console.info("eject successfully.");
}).catch((error: BusinessError) => {
  console.error(`Failed to eject. Code: ${error.code}, message: ${error.message}`);
});
```

## volumemanager.createIsoImage

createIsoImage(volumeId: string, filePath: string): Promise&lt;void&gt;

Creates an ISO image file from the specified volume device. This API uses a promise to return the result asynchronously.

**Since:** 26.0.0

**Required permissions**: ohos.permission.MOUNT_UNMOUNT_MANAGER

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.FileManagement.StorageService.Volume

**System API**: This is a system API.

**Parameters**

| Name   | Type   | Mandatory | Description |
| -------- | ------ | ---- | ---- |
| volumeId | string | Yes   | Volume device ID, in the format of vol-{major device number}-{minor device number}. The volume device ID changes with the card insertion order. Do not cache it for reuse. |
| filePath | string | Yes   | Path for saving the ISO image file. |

**Return value**

| Type                   | Description       |
| ---------------------- | ---------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 13600001 | IPC error. |
| 13600002 | Not supported filesystem. |
| 13600005 | Incorrect volume state. |
| 13600010 | The input parameter is invalid. |
| 13600024 | Empty disc. |
| 13600025 | Failed to write the ISO file. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain volumeId through getAllVolumes().
let volumeId: string = "";
let filePath: string = "";
volumeManager.createIsoImage(volumeId, filePath).then(() => {
  console.info("createIsoImage successfully.");
}).catch((error: BusinessError) => {
  console.error(`Failed to createIsoImage. Code: ${error.code}, message: ${error.message}`);
});
```

## volumemanager.burn

burn(volumeId: string, want: Want): Promise&lt;void&gt;

Burns data to the specified volume device. This API uses a promise to return the result asynchronously.

**Since:** 26.0.0

**Required permissions**: ohos.permission.MOUNT_UNMOUNT_MANAGER

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.FileManagement.StorageService.Volume

**System API**: This is a system API.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | ------ | ---- | ---- |
| volumeId | string | Yes | Volume device ID, in the format of vol-{major device number}-{minor device number}. The volume device ID changes with the card insertion order. Do not cache it for reuse. |
| want | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes | Want information for starting the ability. |

**Return value**

| Type | Description |
| ---------------------- | ---------- |
| Promise&lt;void&gt; | Promise that returns no value. |
 
**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 13600001 | IPC error. |
| 13600002 | Not supported filesystem. |
| 13600010 | The input parameter is invalid. |
| 13600028 | Burn operation failed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

import { Want } from '@kit.AbilityKit';
// Obtain volumeId through getAllVolumes().
let volumeId: string = "";
let want: Want = {
  parameters: {
    diskName: "MyDisc",
    burnPath: "/data/storage/el2/base/files/burn_data",
    isIsoImage: false,
    burnSpeed: 0,
    fsType: "ISO9660"
  }
};
volumeManager.burn(volumeId, want).then(() => {
  console.info("burn successfully.");
}).catch((error: BusinessError) => {
  console.error(`Failed to burn. Code: ${error.code}, message: ${error.message}`);
});
```

## volumemanager.getOpProcess

getOpProcess(volumeId: string): Promise&lt;number&gt;

Obtains the burning operation progress of the specified volume device's optical drive, using a Promise asynchronous callback. After calling the burn API to write data to the disc, you can use this API to obtain the burning progress.

**Since:** 26.0.0

**Required permissions**: ohos.permission.MOUNT_UNMOUNT_MANAGER

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.FileManagement.StorageService.Volume

**System API**: This is a system API.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | ------ | ---- | ---- |
| volumeId | string | Yes | Volume device ID, in the format of vol-{major device number}-{minor device number}. The volume device ID changes with the card insertion order. Do not cache it for reuse. |

**Return value**

| Type | Description |
| ---------------------- | ---------- |
| Promise&lt;number&gt; | Promise object, which returns the progress of the current operation. The progress value is an integer ranging from 0 to 100. |

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 13600001 | IPC error. |
| 13600002 | Not supported filesystem. |
| 13600010 | The input parameter is invalid. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain volumeId through getAllVolumes().
let volumeId: string = "";
volumeManager.getOpProcess(volumeId).then((progress: number) => {
  console.info("getOpProcess successfully, progress:" + progress);
}).catch((error: BusinessError) => {
  console.error(`Failed to getOpProcess. Code: ${error.code}, message: ${error.message}`);
});
```

## volumemanager.verifyBurnData

verifyBurnData(volumeId: string, verType: VerifyType): Promise&lt;void&gt;

Verifies the burn data of the specified volume device. This API uses a promise to return the result asynchronously.

**Since:** 26.0.0

**Required permissions**: ohos.permission.MOUNT_UNMOUNT_MANAGER

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.FileManagement.StorageService.Volume

**System API**: This is a system API.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | ------ | ---- | ---- |
| volumeId | string | Yes | Volume device ID. |
| verType | [VerifyType](#verifytype) | Yes | Verification type of the burn data. |

**Return value**

| Type | Description |
| ---------------------- | ---------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 13600001 | IPC error. |
| 13600002 | Not supported filesystem. |
| 13600010 | The input parameter is invalid. |
| 13600030 | Verification failed. |

**Example**

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

## volumemanager.getAllDisks

getAllDisks(): Promise&lt;Array&lt;Disk&gt;&gt;

Obtains information about all disk devices in the current external storage. This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions**: ohos.permission.MOUNT_UNMOUNT_MANAGER

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.FileManagement.StorageService.Volume

**System API**: This is a system API.

**Return value**

| Type                   | Description       |
| ---------------------- | ---------- |
| Promise&lt;Array&lt;[Disk](#disk)&gt;&gt; | Promise object, which returns the device information of all disks. |

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 13600001 | IPC error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

volumeManager.getAllDisks().then((disks: Array<volumeManager.Disk>) => {
  console.info("getAllDisks successfully:" + JSON.stringify(disks));
}).catch((error: BusinessError) => {
  console.error(`getAllDisks failed with error, code is: ${error.code}, message is: ${error.message}`);
});
```

## volumemanager.getDiskById

getDiskById(diskId: string): Promise&lt;Disk&gt;

Obtains the specified disk device information by disk device ID. This API uses a promise to return the result asynchronously.

**Since:** 26.0.0

**Required permissions**: ohos.permission.MOUNT_UNMOUNT_MANAGER

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.FileManagement.StorageService.Volume

**System API**: This is a system API.

**Parameters**

| Name   | Type   | Mandatory | Description |
| -------- | ------ | ---- | ---- |
| diskId | string | Yes   | Disk device ID, in the format of disk-{major device number}-{minor device number}. |

**Return value**

| Type                   | Description       |
| ---------------------- | ---------- |
| Promise&lt;[Disk](#disk)&gt; | Promise object that returns the device information of the specified disk. |

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 13600001 | IPC error. |
| 13600008 | No such object. |
| 13600010 | The input parameter is invalid. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain the diskId through getAllDisks().
let diskId: string = "";
volumeManager.getDiskById(diskId).then((disk: volumeManager.Disk) => {
  console.info("getDiskById successfully:" + JSON.stringify(disk));
}).catch((error: BusinessError) => {
  console.error(`getDiskById failed with error, code is: ${error.code}, message is: ${error.message}`);
});
```

## volumemanager.getPartitionTable

getPartitionTable(diskId: string): Promise&lt;PartitionTableInfo&gt;

Obtains the partition table information of the specified disk device by disk device ID. This API uses a promise to return the result asynchronously.

**Since:** 26.0.0

**Required permissions**: ohos.permission.MOUNT_FORMAT_MANAGER

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.FileManagement.StorageService.Volume

**System API**: This is a system API.

**Parameters**

| Name   | Type   | Mandatory | Description |
| -------- | ------ | ---- | ---- |
| diskId | string | Yes   | Disk device ID, in the format of disk-{major device number}-{minor device number}. |

**Return value**

| Type                   | Description       |
| ---------------------- | ---------- |
| Promise&lt;[PartitionTableInfo](#partitiontableinfo)&gt; | Promise object that returns the partition table information of the specified disk device. |

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 13600001 | IPC error. |
| 13600008 | No such object. |
| 13600010 | The input parameter is invalid. |
| 13600021 | Get partition table failed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain diskId through getAllDisks().
let diskId: string = "";
volumeManager.getPartitionTable(diskId).then((partitionTableInfo: volumeManager.PartitionTableInfo) => {
  console.info("getPartitionTable successfully:" + JSON.stringify(partitionTableInfo));
}).catch((error: BusinessError) => {
  console.error(`getPartitionTable failed with error, code is: ${error.code}, message is: ${error.message}`);
});
```

## volumemanager.createPartition

createPartition(diskId: string, params: PartitionParams): Promise&lt;void&gt;

Creates a partition on the specified disk device. Partitioning an optical disc is not supported. This API uses an asynchronous callback.

**Since:** 26.0.0

**Required permissions**: ohos.permission.MOUNT_FORMAT_MANAGER

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.FileManagement.StorageService.Volume

**System API**: This is a system API.

**Parameters**

| Name   | Type   | Mandatory | Description |
| -------- | ------ | ---- | ---- |
| diskId | string | Yes   | Disk device ID, in the format of disk-{major device number}-{minor device number}. |
| params | [PartitionParams](#partitionparams) | Yes   | Partition creation parameters. |

**Return value**

| Type                   | Description       |
| ---------------------- | ---------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 13600001 | IPC error. |
| 13600002 | Not supported filesystem. |
| 13600005 | Incorrect volume state. |
| 13600008 | No such object. |
| 13600010 | The input parameter is invalid. |
| 13600022 | Create partition failed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain diskId through the getAllDisks() API.
let diskId: string = "";
let params: volumeManager.PartitionParams = {
  partitionNum: 1,
  startSector: 2048,
  endSector: 1024000,
  typeCode: "ext4"
};
volumeManager.createPartition(diskId, params).then(() => {
  console.info("createPartition successfully.");
}).catch((error: BusinessError) => {
  console.error(`createPartition failed with error, code is: ${error.code}, message is: ${error.message}`);
});
```

## volumemanager.deletePartition

deletePartition(diskId: string, partitionNum: number): Promise&lt;void&gt;

Deletes the specified partition on the specified disk device. Partitioning an optical disc is not supported. This API uses an asynchronous callback to return the result.

**Since:** 26.0.0

**Required permissions**: ohos.permission.MOUNT_FORMAT_MANAGER

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.FileManagement.StorageService.Volume

**System API**: This is a system API.

**Parameters**

| Name   | Type   | Mandatory | Description |
| -------- | ------ | ---- | ---- |
| diskId | string | Yes   | Disk device ID, in the format of disk-{major device number}-{minor device number}. |
| partitionNum | number | Yes   | Partition number. |

**Return value**

| Type                   | Description       |
| ---------------------- | ---------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 13600001 | IPC error. |
| 13600005 | Incorrect volume state. |
| 13600008 | No such object. |
| 13600010 | The input parameter is invalid. |
| 13600023 | Delete partition failed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain diskId through the getAllDisks() API.
let diskId: string = "";
let partitionNum: number = 1;
volumeManager.deletePartition(diskId, partitionNum).then(() => {
  console.info("deletePartition successfully.");
}).catch((error: BusinessError) => {
  console.error(`deletePartition failed with error, code is: ${error.code}, message is: ${error.message}`);
});
```

## volumemanager.formatPartition

formatPartition(diskId: string, partitionNum: number, params: FormatParams): Promise&lt;void&gt;

Formats the specified partition of the specified disk device. Ensure that the related volume device is in the unmounted state. This API uses an asynchronous callback to return the result.

**Since:** 26.0.0

**Required permissions**: ohos.permission.MOUNT_FORMAT_MANAGER

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.FileManagement.StorageService.Volume

**System API**: This is a system API.

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | ------ | ---- | ---- |
| diskId | string | Yes | Disk device ID, in the format of disk-{major device number}-{minor device number}. |
| partitionNum | number | Yes | Partition number. |
| params | [FormatParams](#formatparams) | Yes | Formatting parameters. |

**Return value**

| Type | Description |
| ---------------------- | ---------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the following error codes, see [Universal Error Codes](../errorcode-universal.md) and [File Management Error Codes](errorcode-filemanagement.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission verification failed. |
| 202 | The caller is not a system application. |
| 13600001 | IPC error. |
| 13600002 | Not supported filesystem. |
| 13600005 | Incorrect volume state. |
| 13600008 | No such object. |
| 13600010 | The input parameter is invalid. |
| 13600032 | Format partition failed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain diskId through the getAllDisks() API.
let diskId: string = "";
let partitionNum: number = 1;
let params: volumeManager.FormatParams = {
  fsType: "ext4",
  quickFormat: true,
  volumeName: "myVolume"
};
volumeManager.formatPartition(diskId, partitionNum, params).then(() => {
  console.info("formatPartition successfully.");
}).catch((error: BusinessError) => {
  console.error(`formatPartition failed with error, code is: ${error.code}, message is: ${error.message}`);
});
``` 

## Volume

Volume information details.

### Properties

**System API**: This is a system API.

**System capability**: SystemCapability.FileManagement.StorageService.Volume

| Name         | Type    | Read-Only   | Optional   | Description                 |
| ----------- | ------- | ------- | ----- | -------------------- |
| id          | string  | No | No | Volume ID, in the vol-{Major device number}-{Minor device number} format. The major device number distinguishes devices of different types. The minor device number distinguishes multiple devices of the same type. The volume ID changes with the card insertion order.                 |
| uuid        | string  | No | No | The volume UUID is a universally unique identifier of the volume device. It does not change with the card insertion order, but formatting the volume device changes its UUID.               |
| diskId      | string  | No | No | ID of the disk to which the volume device belongs. A disk can have one or more volume devices. The disk ID is in the disk-{Major device number}-{Minor device number} format, which is similar to the volume ID format and follows the {Major device number}-{Minor device number} naming rule.        |
| description | string  | No | No | Volume device description. Formatting the volume device changes its description.           |
| removable   | boolean | No | No | Whether the volume device is removable. Currently only removable storage devices can be queried. The value true means removable, and false means non-removable. |
| state       | number  | No | No | Volume status.<br>**0**: The volume is unmounted.<br> **1**: The volume is being checked.<br> **2**: The volume is mounted.<br> **3**: The volume is being ejected.          |
| path        | string  | No | No | Mount path of the volume device, generally /mnt/data/external/{uuid}. Formatting the volume device changes the mount path.         |
| fsType<sup>12+</sup>        | string  | No | No | File system type, including ext2, vfat, ntfs, and so on.<br>**Note**: Since API version 24, ISO9660 and UDF are also supported.      |
| partitionNum   | number  | No | Yes | Partition number of the volume device. If this parameter is omitted, no partition number information is available.<br>**Initial version:** 26.0.0<br>**Model constraint**: This API can be used only in the stage model.         |
| extraInfo   | string  | No | Yes | Extended information of the volume device, including additional attribute data of the device. The specific content varies with the device type. This is an optional field. If it does not exist, there is no extended information.<br>**Initial version:** 26.0.0<br>**Model constraint**: This API can be used only in the stage model.         |

## DiskType

Enumerates the disk types.


**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.FileManagement.StorageService.Volume

**System API**: This is a system API.

| Name         | Value    | Description                 |
| ----------- | ------- | -------------------- |
| SD_CARD     | 1       | SD card type.     |
| USB_FLASH   | 2       | USB flash drive type.     |
| CD_DVD_BD   | 3       | Optical disc type.     |
| DATA_DISK_SSD | 4       | SSD data disk type.     |
| DATA_DISK_HDD | 5       | HDD data disk type.     |
| DVR_USB  | 6       | DVR USB drive type.     |
| UNKNOWN_DISK_TYPE | 255       | Unknown disk type.     |

## Disk

Disk information details.

### Properties

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.FileManagement.StorageService.Volume

**System API**: This is a system API.

| Name         | Type    | Read-Only   | Optional   | Description                 |
| ----------- | ------- | ------- | ----- | -------------------- |
| diskId      | string  | No | No | Disk device ID, in the format of disk-{major device number}-{minor device number}.                 |
| sizeBytes   | number  | No | No | Total size of the disk, in bytes.               |
| diskType    | [DiskType](#disktype) | No | No | Disk type.        |
| removable   | boolean | No | No | Whether the disk is removable. The value true means removable, and false means non-removable. The default value is true.           |
| volumeIds   | Array&lt;string&gt; | No | No | Array of volume device IDs contained in the disk. A disk can contain one or more volume devices.         |
| extraInfo   | string  | No | No | Extended information of the disk device, including additional attribute data of the disk. The specific content varies with the device type.         |

## PartitionInfo

Partition information details.

### Properties

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.FileManagement.StorageService.Volume

**System API**: This is a system API.

| Name | Type | Read-Only | Optional | Description |
| ----------- | ------- | ------- | ----- | -------------------- |
| partitionNum | number | No | No | Partition number. |
| diskId | string | No | No | Disk device ID, in the format of disk-{major device number}-{minor device number}. |
| startSector | number | No | No | Start sector number of the partition. |
| endSector | number | No | No | End sector number of the partition. |
| sizeBytes | number | No | No | Total size of the partition, in bytes. |
| fsType | string | No | No | File system type. Currently supported formats are ext4, vfat, exfat, ntfs, f2fs, and hmfs. |

## PartitionTableInfo

Partition table information details.

### Properties

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.FileManagement.StorageService.Volume

**System API**: This is a system API.

| Name         | Type    | Read-Only   | Optional   | Description                 |
| ----------- | ------- | ------- | ----- | -------------------- |
| diskId      | string  | No | No | Disk device ID, in the format of disk-{major device number}-{minor device number}.                 |
| tableType   | string  | No | No | Partition table type, such as gpt or mbr.               |
| partitionCount | number  | No | No | Number of partitions.        |
| totalSector | number  | No | No | Total number of sectors.           |
| sectorSize  | number  | No | No | Size of each sector, in bytes.         |
| alignSector | number  | No | No | Sector number on which partition alignment is based, used to ensure that the partition start position is aligned with the physical sector boundary.         |
| partitions  | Array&lt;[PartitionInfo](#partitioninfo)&gt; | No | No | Array of partition information.         |

## PartitionParams

Parameters required for creating a partition on the specified disk.

### Properties

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.FileManagement.StorageService.Volume

**System API**: This is a system API.

| Name | Type | Read-Only | Optional | Description |
| ----------- | ------- | ------- | ----- | -------------------- |
| partitionNum | number | No | No | Partition number. |
| startSector | number | No | No | Start sector number of the partition. |
| endSector | number | No | No | End sector number of the partition. |
| typeCode | string | No | No | File system code. Currently supported formats are ext4, vfat, exfat, ntfs, f2fs, and hmfs. |

## FormatParams

Parameters required for formatting a specified partition.

### Properties

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.FileManagement.StorageService.Volume

**System API**: This is a system API.

| Name | Type | Read-Only | Optional | Description |
| ----------- | ------- | ------- | ----- | -------------------- |
| fsType | string | No | No | File system type. Currently supports formatting to ext4, vfat, and exfat. |
| quickFormat | boolean | No | Yes | Whether to perform quick format. Currently only quick format is supported, so this parameter only supports passing true. Passing false returns an invalid parameter error, error code 13600010. The default value is true. |
| volumeName | string | No | Yes | Volume name after formatting. If not passed, an empty string is used as the volume name by default. |