# AppDistributionType (System API)

```TypeScript
export enum AppDistributionType
```

Identifies an application's [HarmonyAppProvision Configuration File](../../../security/app-provision-structure.md).

**Since:** 12

<!--Device-bundleManager-export enum AppDistributionType--><!--Device-bundleManager-export enum AppDistributionType-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## APP_GALLERY

```TypeScript
APP_GALLERY = 1
```

Application installed from AppGallery.

**Since:** 12

<!--Device-AppDistributionType-APP_GALLERY = 1--><!--Device-AppDistributionType-APP_GALLERY = 1-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## CROWDTESTING

```TypeScript
CROWDTESTING = 6
```

Application under crowdtesting, which is distributed by AppGallery to a limited number of users and come with a set expiration date. When the system detects that the validity period of the application expires, it prompts the user to update to the release version available on AppGallery.

**Since:** 12

<!--Device-AppDistributionType-CROWDTESTING = 6--><!--Device-AppDistributionType-CROWDTESTING = 6-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## ENTERPRISE

```TypeScript
ENTERPRISE = 2
```

Enterprise application that can be installed on personal devices.

**Since:** 12

<!--Device-AppDistributionType-ENTERPRISE = 2--><!--Device-AppDistributionType-ENTERPRISE = 2-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## ENTERPRISE_MDM

```TypeScript
ENTERPRISE_MDM = 4
```

Enterprise MDM application that can be installed only on enterprise devices. To install a common enterprise application, you must have [adminManager.enableAdmin](../../../reference/apis-mdm-kit/js-apis-enterprise-adminManager-sys.md#adminmanagerenableadmin) activated.

**Since:** 12

<!--Device-AppDistributionType-ENTERPRISE_MDM = 4--><!--Device-AppDistributionType-ENTERPRISE_MDM = 4-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## ENTERPRISE_NORMAL

```TypeScript
ENTERPRISE_NORMAL = 3
```

Common enterprise application that can be installed on enterprise devices only through an enterprise mobile device management (MDM) application.

**Since:** 12

<!--Device-AppDistributionType-ENTERPRISE_NORMAL = 3--><!--Device-AppDistributionType-ENTERPRISE_NORMAL = 3-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## NONE

```TypeScript
NONE = 7
```

Other.

**Since:** 12

<!--Device-AppDistributionType-NONE = 7--><!--Device-AppDistributionType-NONE = 7-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## OS_INTEGRATION

```TypeScript
OS_INTEGRATION = 5
```

Preinstalled system application.

**Since:** 12

<!--Device-AppDistributionType-OS_INTEGRATION = 5--><!--Device-AppDistributionType-OS_INTEGRATION = 5-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.
