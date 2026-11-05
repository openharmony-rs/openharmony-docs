# BusinessId (System API)

```TypeScript
enum BusinessId
```

Enumerates business IDs. A business ID uniquely identifies a business scenario supported by the companion device. The business scenarios supported by different companion devices vary according to the authentication security. For example, executing voice commands without screen unlocking.

The companion device relationships of different business IDs are independent of each other and do not interfere with each other. They can be added, deleted, and authenticated independently.

The current services of the companion device module include business scenarios such as screen lock unlocking, app lock unlocking, and identity authentication before voice commands are executed on the lock screen.

Adding services has requirements on the scenarios supported by the server device. For example, the multi-screen collaboration service requires that the server device support the agency authentication scenario.

**Since:** 23

<!--Device-companionDeviceAuth-enum BusinessId--><!--Device-companionDeviceAuth-enum BusinessId-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.

## DEFAULT

```TypeScript
DEFAULT = 0
```

Default business ID. A system-preset default business used for basic Companion Device authentication scenarios.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-BusinessId-DEFAULT = 0--><!--Device-BusinessId-DEFAULT = 0-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.

## VENDOR_BEGIN

```TypeScript
VENDOR_BEGIN = 10000
```

Starting value of vendor-defined business IDs. Vendors can define extended business IDs based on this value. The actual value must be greater than or equal to 10000 to avoid conflicts with system-reserved values [0-9999].

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-BusinessId-VENDOR_BEGIN = 10000--><!--Device-BusinessId-VENDOR_BEGIN = 10000-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.
