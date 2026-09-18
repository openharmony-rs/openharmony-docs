# DeviceIdType (System API)

Enumerates device ID types. They are used to define the device service identifier type. System-defined types and vendor-defined types are supported.

**Since:** 23

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.

## UNIFIED_DEVICE_ID

```TypeScript
UNIFIED_DEVICE_ID = 1
```

Unified device ID. It is a system-defined device service ID type, used for unified device identification across devices.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.

## VENDOR_BEGIN

```TypeScript
VENDOR_BEGIN = 10000
```

Start value of the vendor-defined device ID type. The vendor can extend device ID types based on this value. The actual value must be greater than or equal to 10000 to avoid conflicts with the reserved system values [1-9999].

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.
