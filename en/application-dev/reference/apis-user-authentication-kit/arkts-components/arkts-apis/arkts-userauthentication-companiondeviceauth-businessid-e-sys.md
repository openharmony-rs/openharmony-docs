# BusinessId (System API)

Enumerates service IDs. A service ID uniquely identifies a service scenario supported by the companion device. The service scenarios supported by different companion devices vary according to the authentication security. For example, executing voice commands without screen unlocking.

The companion device relationships of different service IDs are independent of each other and do not interfere with each other. They can be added, deleted, and authenticated independently.

Currently, the services of the companion device module include the default services of OpenHarmony, screen unlocking, application unlocking, and identity authentication before voice commands are executed on the lock screen.

Adding services has requirements on the scenarios supported by the server device. For example, the multi-screen collaboration service requires that the server device support the agency authentication scenario.

**Since:** 23

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.

## DEFAULT

```TypeScript
DEFAULT = 0
```

Default service ID. It is system-defined and used for basic authentication scenarios.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.

## VENDOR_BEGIN

```TypeScript
VENDOR_BEGIN = 10000
```

Start value of the vendor-defined service ID. The vendor can extend service IDs based on this value. The actual value must be greater than or equal to 10000 to avoid conflicts with the reserved system values [0-9999].

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.
