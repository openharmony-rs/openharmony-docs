# DlpAtomicPermissionType

```TypeScript
export enum DlpAtomicPermissionType
```

Enumerates atomic permissions for DLP files, including user operation and application permission control. This enumeration supports bitwise OR operations to combine multiple permissions.

**Since:** 26.1.0

<!--Device-dlpPermission-export enum DlpAtomicPermissionType--><!--Device-dlpPermission-export enum DlpAtomicPermissionType-End-->

**System capability:** SystemCapability.Security.DataLossPrevention

## ATOMIC_APP_PERMISSION

```TypeScript
ATOMIC_APP_PERMISSION = 0x20
```

Atomic permission to allow sandbox applications to access system services that are otherwise restricted. When accessing a DLP file, the system creates an isolated sandbox clone of the application that inherits data, configuration, and permissions from the original application. This flag enables the sandbox to access system services within the inherited permissions. For example, if the original application does not have the use Bluetooth permission, the sandbox application cannot call Bluetooth-related APIs even with this flag enabled. Specifically, the following permissions are covered:  
- access Internet, set Wi-Fi configuration, set Wi-Fi information, and manage Wi-Fi hotspot permissions.  
- use Bluetooth, manage Bluetooth, access Bluetooth, and discover Bluetooth permissions.  
- access NearLink and manage NearLink permissions.  
- use cloud common service, use cloud backup service, use cloud drive service, cloud file sync, and  
cloud file sync manager permissions.  
- send messages, receive SMS, receive MMS, and receive WAP message permissions.  
- write audio, write document, write image/video, and write media permissions.  
- read/write download directory, read/write desktop directory, and read/write documents directory permissions.  
- write whole calendar permission.  
- proxy authorization URI permission.  
- file access manager permission.  
- distributed data sync permission.  
- NFC tag permission.

This permission can be combined with other atomic permissions using bitwise OR operation. see [DLP Service Development](../../../security/DataProtectionKit/dlp-guidelines.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-DlpAtomicPermissionType-ATOMIC_APP_PERMISSION = 0x20--><!--Device-DlpAtomicPermissionType-ATOMIC_APP_PERMISSION = 0x20-End-->

**System capability:** SystemCapability.Security.DataLossPrevention

## ATOMIC_COPY

```TypeScript
ATOMIC_COPY = 0x04
```

Atomic permission to copy file content.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-DlpAtomicPermissionType-ATOMIC_COPY = 0x04--><!--Device-DlpAtomicPermissionType-ATOMIC_COPY = 0x04-End-->

**System capability:** SystemCapability.Security.DataLossPrevention

## ATOMIC_EDIT

```TypeScript
ATOMIC_EDIT = 0x02
```

Atomic permission to edit files.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-DlpAtomicPermissionType-ATOMIC_EDIT = 0x02--><!--Device-DlpAtomicPermissionType-ATOMIC_EDIT = 0x02-End-->

**System capability:** SystemCapability.Security.DataLossPrevention

## ATOMIC_PRINT

```TypeScript
ATOMIC_PRINT = 0x10
```

Atomic permission to print files.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-DlpAtomicPermissionType-ATOMIC_PRINT = 0x10--><!--Device-DlpAtomicPermissionType-ATOMIC_PRINT = 0x10-End-->

**System capability:** SystemCapability.Security.DataLossPrevention

## ATOMIC_READ

```TypeScript
ATOMIC_READ = 0x01
```

Atomic permission to read files.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-DlpAtomicPermissionType-ATOMIC_READ = 0x01--><!--Device-DlpAtomicPermissionType-ATOMIC_READ = 0x01-End-->

**System capability:** SystemCapability.Security.DataLossPrevention

## ATOMIC_SCREENSHOT

```TypeScript
ATOMIC_SCREENSHOT = 0x08
```

Atomic permission to take file screenshots.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-DlpAtomicPermissionType-ATOMIC_SCREENSHOT = 0x08--><!--Device-DlpAtomicPermissionType-ATOMIC_SCREENSHOT = 0x08-End-->

**System capability:** SystemCapability.Security.DataLossPrevention
