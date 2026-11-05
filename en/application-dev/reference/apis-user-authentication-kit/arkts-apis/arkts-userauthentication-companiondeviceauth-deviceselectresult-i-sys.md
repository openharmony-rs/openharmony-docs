# DeviceSelectResult (System API)

```TypeScript
interface DeviceSelectResult
```

Returns the result of companion device selection. It is used to return the device information and extended context selected by the user in the device selection callback.

**Since:** 23

<!--Device-companionDeviceAuth-interface DeviceSelectResult--><!--Device-companionDeviceAuth-interface DeviceSelectResult-End-->

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

Device information list. It contains the business identifier information of the devices selected by the user. Each **DeviceKey** contains the device ID type, device ID, device user ID, and device sub-identity credential ID. The system performs subsequent template addition or authentication operations based on this information.

**Type:** [DeviceKey](arkts-userauthentication-companiondeviceauth-devicekey-i-sys.md)[]

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-DeviceSelectResult-deviceKeys: DeviceKey[]--><!--Device-DeviceSelectResult-deviceKeys: DeviceKey[]-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.

## selectionContext

```TypeScript
selectionContext?: Uint8Array
```

Device selection context. Carries extended information in JSON format (the specific fields are defined by the service party), which can be used to pass additional parameters during device selection. If this field is not provided, it is empty by default and carries no extended information.

**Type:** Uint8Array

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-DeviceSelectResult-selectionContext?: Uint8Array--><!--Device-DeviceSelectResult-selectionContext?: Uint8Array-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.
