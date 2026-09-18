# SelectPurpose (System API)

Selects the purpose of the companion device.

**Since:** 23

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.

## SELECT_ADD_DEVICE

```TypeScript
SELECT_ADD_DEVICE = 1
```

Selects a companion device to which the template is to be added. Specifically, the purpose of the current operation is to select a device for adding a new authentication template. The system returns a list of devices suitable for adding a template.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.

## SELECT_AUTH_DEVICE

```TypeScript
SELECT_AUTH_DEVICE = 2
```

Selects the companion device that provides the authentication capability. Specifically, the purpose of the current operation is to select a device that has a registered template for authentication. The system returns a list of devices that have the authentication capability.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.

## VENDOR_BEGIN

```TypeScript
VENDOR_BEGIN = 10000
```

Start value of the vendor-defined selection purpose. The vendor can extend the selection purpose based on this value. The actual value must be greater than or equal to 10000 to avoid conflicts with the reserved system values [0-9999].

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.
