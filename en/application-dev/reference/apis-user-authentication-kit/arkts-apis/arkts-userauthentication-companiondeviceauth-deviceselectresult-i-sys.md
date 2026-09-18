# DeviceSelectResult (System API)

Returns the result of companion device selection. It is used to return the device information and extended context selected by the user in the device selection callback.

**Since:** 23

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { companionDeviceAuth } from '@kit.UserAuthenticationKit';
```

## deviceKeys

```TypeScript
deviceKeys: DeviceKey[]
```

Device information list. It contains the device service identifier information selected by the user. Each **DeviceKey** contains the device ID type, device ID, device user ID, and device sub-profile ID. The system will perform subsequent operations such as adding a template or performing authentication based on this information.

**Type:** [DeviceKey](arkts-userauthentication-companiondeviceauth-devicekey-i-sys.md)[]

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.

## selectionContext

```TypeScript
selectionContext?: Uint8Array
```

Device selection context. It carries extension information in JSON format and can be used to pass additional parameters in the device selection process, such as authentication configuration and service scenario identifier.

**Type:** Uint8Array

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.
