# DeviceEncryptionStatus (System API)

Represents the file system encryption status.

**Since:** 11

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { securityManager } from '@kit.MDMKit';
```

## isEncrypted

```TypeScript
isEncrypted: boolean
```

Whether the file system of the device is encrypted.

The value **true** means the file system of the device is encrypted; the value **false** means the opposite.

**Type:** boolean

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**System API:** This is a system API.
