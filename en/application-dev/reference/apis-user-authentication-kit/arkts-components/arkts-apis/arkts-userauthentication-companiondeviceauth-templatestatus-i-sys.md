# TemplateStatus (System API)

Describes the complete status information about a registered companion device authentication template, including the template ID, data confirmation status, validity, user ID, time when the template is added, supported services, and associated device status.

**Since:** 23

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { companionDeviceAuth } from '@kit.UserAuthenticationKit';
```

## addedTime

```TypeScript
addedTime: Date
```

Template adding time. Timestamp when the template is created. The value is a Unix timestamp, that is, the number of milliseconds elapsed since 00:00:00 on January 1, 1970.

**Type:** Date

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.

## deviceStatus

```TypeScript
deviceStatus: DeviceStatus
```

Device status information. It specifies the current status of the companion device associated with the template, including the online status and device name.

**Type:** [DeviceStatus](arkts-userauthentication-companiondeviceauth-devicestatus-i-sys.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.

## enabledBusinessIds

```TypeScript
enabledBusinessIds: number[]
```

List of supported service IDs. It specifies the service scenarios where the template is enabled. You can update the service scenarios by calling the [updateEnabledBusinessIds](arkts-userauthentication-companiondeviceauth-updateenabledbusinessids-f-sys.md) API.

**Type:** number[]

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.

## isConfirmed

```TypeScript
isConfirmed: boolean
```

Data confirmation status. The value **true** indicates that the data is real-time data and has been confirmed and synchronized with the device. The value **false** indicates that the data is cached data, which may be different from the actual device status.

**Type:** boolean

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.

## isValid

```TypeScript
isValid: boolean
```

Template validity. The value **true** indicates that the template is valid and can be used for authentication. The value **false** indicates that the template is invalid, may have been deleted or expired, and cannot be used for authentication.

**Type:** boolean

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.

## localUserId

```TypeScript
localUserId: number
```

Local user ID. It specifies the user ID associated with the template on the primary device. The value is a positive integer greater than or equal to 0.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.

## templateId

```TypeScript
templateId: Uint8Array
```

Template ID. Unique ID of a companion device authentication template, which is used to specify the target template when the service scope is updated or the authentication status is subscribed to.

**Type:** Uint8Array

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.
