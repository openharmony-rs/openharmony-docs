# BundleInfoGetFlag

```TypeScript
export enum BundleInfoGetFlag
```

Enumerates the bundle flags, which indicate the type of bundle information to obtain.

**Since:** 23

<!--Device-bundleManager-export enum BundleInfoGetFlag--><!--Device-bundleManager-export enum BundleInfoGetFlag-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## DEFAULT

```TypeScript
DEFAULT = 0
```

Obtains the default bundle information, excluding **applicationInfo** and **signatureInfo**.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-BundleInfoGetFlag-DEFAULT = 0--><!--Device-BundleInfoGetFlag-DEFAULT = 0-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## WITH_APPLICATION_ICON_INFO

```TypeScript
WITH_APPLICATION_ICON_INFO = 1 << 2
```

Obtains the default bundle information and **applicationInfo** (including **iconData**).

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-BundleInfoGetFlag-WITH_APPLICATION_ICON_INFO = 1 << 2--><!--Device-BundleInfoGetFlag-WITH_APPLICATION_ICON_INFO = 1 << 2-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## WITH_APPLICATION_INFO

```TypeScript
WITH_APPLICATION_INFO = 1 << 0
```

Obtains the default bundle information and **applicationInfo** (excluding **iconData**).

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-BundleInfoGetFlag-WITH_APPLICATION_INFO = 1 << 0--><!--Device-BundleInfoGetFlag-WITH_APPLICATION_INFO = 1 << 0-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## WITH_SIGNATURE_INFO

```TypeScript
WITH_SIGNATURE_INFO = 1 << 1
```

Obtains the default bundle information and **signatureInfo**.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-BundleInfoGetFlag-WITH_SIGNATURE_INFO = 1 << 1--><!--Device-BundleInfoGetFlag-WITH_SIGNATURE_INFO = 1 << 1-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager
