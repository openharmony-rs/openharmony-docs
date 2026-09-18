# BundleInfoGetFlag

Enumerates the bundle flags, which indicate the type of bundle information to obtain.

**Since:** 23

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## DEFAULT

```TypeScript
DEFAULT = 0
```

Obtains the default bundle information, excluding **applicationInfo** and **signatureInfo**.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## WITH_APPLICATION_INFO

```TypeScript
WITH_APPLICATION_INFO = 1 << 0
```

Obtains the default bundle information and **applicationInfo** (excluding **iconData**).

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## WITH_SIGNATURE_INFO

```TypeScript
WITH_SIGNATURE_INFO = 1 << 1
```

Obtains the default bundle information and **signatureInfo**.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## WITH_APPLICATION_ICON_INFO

```TypeScript
WITH_APPLICATION_ICON_INFO = 1 << 2
```

Obtains the default bundle information and **applicationInfo** (including **iconData**).

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager
