# AppDistributionType (System API)

Enumerates the application [distribution types](../../../security/app-provision-structure.md).

**Since:** 12

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## APP_GALLERY

```TypeScript
APP_GALLERY = 1
```

Application installed from AppGallery.

**Since:** 12

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## ENTERPRISE

```TypeScript
ENTERPRISE = 2
```

Enterprise application that can be installed on personal devices.

**Since:** 12

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## ENTERPRISE_NORMAL

```TypeScript
ENTERPRISE_NORMAL = 3
```

Common enterprise application that can be installed on enterprise devices only through an enterprise mobile device management (MDM) application.

**Since:** 12

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## ENTERPRISE_MDM

```TypeScript
ENTERPRISE_MDM = 4
```

Enterprise MDM application that can be installed only on enterprise devices. To install a common enterprise application, you must have [administrator privileges](../../apis-mdm-kit/arkts-apis/arkts-mdm-adminmanager-enableadmin-f-sys.md).

**Since:** 12

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## OS_INTEGRATION

```TypeScript
OS_INTEGRATION = 5
```

Preinstalled system application.

**Since:** 12

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## CROWDTESTING

```TypeScript
CROWDTESTING = 6
```

Application under crowdtesting, which is distributed by AppGallery to a limited number of users and come with a set expiration date. When the system detects that the validity period of the application expires, it prompts the user to update to the release version available on AppGallery.

**Since:** 12

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## NONE

```TypeScript
NONE = 7
```

Other.

**Since:** 12

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.
