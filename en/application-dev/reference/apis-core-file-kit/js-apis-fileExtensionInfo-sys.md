# @ohos.file.fileExtensionInfo (User File Extension Information) (System API)

The **fileExtensionInfo** module defines attributes in **RootInfo** and **FileInfo** of the user file access and management module.

>**NOTE**
>
>- The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>- The APIs provided by this module are system APIs.

## Modules to Import

```ts
import fileExtensionInfo from '@ohos.file.fileExtensionInfo';
```

## fileExtensionInfo.DeviceType

Defines the values of **deviceType** used in **RootInfo**.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.FileManagement.UserFileService

| Name| Value| Description|
| ----- | ------ | ------ |
| DEVICE_LOCAL_DISK | 1 | Local disk.|
| DEVICE_SHARED_DISK | 2 | Shared disk.|
| DEVICE_SHARED_TERMINAL | 3 | Distributed network device.|
| DEVICE_NETWORK_NEIGHBORHOODS | 4 | Network neighbor device.|
| DEVICE_EXTERNAL_MTP | 5 | MTP device.|
| DEVICE_EXTERNAL_USB | 6 | USB device.|
| DEVICE_EXTERNAL_CLOUD | 7 | Cloud disk.|

## fileExtensionInfo.DeviceFlag

Defines the values of **deviceFlags** used in **RootInfo**. **deviceFlags** is used to determine whether a capability is available through the AND operation.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.FileManagement.UserFileService

### Properties

  | Name| Type  | Read-Only| Optional| Description    |
  | ------ | ------ | ---- | ---- | -------- |
  | SUPPORTS_READ   | number | No  | No  | The device supports read.|
  | SUPPORTS_WRITE   | number | No  | No  | The device supports write.|

## fileExtensionInfo.DocumentFlag

Defines the values of **mode** used in **FileInfo**.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.FileManagement.UserFileService

### Properties

  | Name| Type  | Read-Only| Optional| Description    |
  | ------ | ------ | ---- | ---- | -------- |
  | REPRESENTS_FILE   | number | No  | No  | File.|
  | REPRESENTS_DIR   | number | No  | No  | Directory.|
  | SUPPORTS_READ   | number | No  | No  | This file is readable.|
  | SUPPORTS_WRITE   | number | No  | No  | This file is writable.|
  
