# BundleFlag

```TypeScript
enum BundleFlag
```

Enumerates the bundle flags, which indicate the type of bundle information to obtain.

**Since:** 9

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## GET_BUNDLE_INFO_OF_ANY_USER

```TypeScript
GET_BUNDLE_INFO_OF_ANY_USER = 0x00002000
```

Used to obtain the bundle information of an application installed by any user. It must be used together with **GET_BUNDLE_INFO_WITH_APPLICATION**. It is valid only in the [getBundleInfo](arkts-ability-bundlemanager-getbundleinfo-f.md) and [getAllBundleInfo](arkts-ability-bundlemanager-getallbundleinfo-f-sys.md) APIs.

**System API**: This flag can be used only in system APIs.

**Since:** 12

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## GET_BUNDLE_INFO_EXCLUDE_CLONE

```TypeScript
GET_BUNDLE_INFO_EXCLUDE_CLONE = 0x00004000
```

Used to obtain the bundle information of a main application (excluding its clones). It is valid only in the [getAllBundleInfo](arkts-ability-bundlemanager-getallbundleinfo-f-sys.md) API.

**System API**: This flag can be used only in system APIs.

**Since:** 12

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## GET_BUNDLE_INFO_WITH_CLOUD_KIT

```TypeScript
GET_BUNDLE_INFO_WITH_CLOUD_KIT = 0x00008000
```

Used to obtain the bundle information of an application that has device-cloud file synchronization or device- cloud structured data synchronization enabled. It is valid only in the [getAllBundleInfo](arkts-ability-bundlemanager-getallbundleinfo-f-sys.md) API.

**System API**: This flag can be used only in system APIs.

**Since:** 20

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## GET_BUNDLE_INFO_WITH_COMMON_CLONE

```TypeScript
GET_BUNDLE_INFO_WITH_COMMON_CLONE = 0x00080000
```

Used to obtain the bundle information of common app clones (appIndex: 1-5). It is valid only in the [getAllAppCloneBundleInfo](arkts-ability-bundlemanager-getallappclonebundleinfo-f-sys.md) API.

**System API**: This flag can be used only in system APIs.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## GET_BUNDLE_INFO_WITH_SANDBOX_CLONE

```TypeScript
GET_BUNDLE_INFO_WITH_SANDBOX_CLONE = 0x00100000
```

Used to obtain the bundle information of sandbox app clones (appIndex: 2000-3000). It is valid only in the [getAllAppCloneBundleInfo](arkts-ability-bundlemanager-getallappclonebundleinfo-f-sys.md) API.

**System API**: This flag can be used only in system APIs.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## GET_BUNDLE_INFO_OF_ALL_DEVICE_MODE

```TypeScript
GET_BUNDLE_INFO_OF_ALL_DEVICE_MODE = 0x00200000
```

Used to obtain the bundle information of an application installed by any device. It is valid only in the [getAllAppCloneBundleInfo](arkts-ability-bundlemanager-getallappclonebundleinfo-f-sys.md) and [getAllBundleInfo](arkts-ability-bundlemanager-getallbundleinfo-f-sys.md) and [getAllBundleInfoInstances](arkts-ability-bundlemanager-getallbundleinfoinstances-f-sys.md) APIs.

**System API**: This flag can be used only in system APIs.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.
