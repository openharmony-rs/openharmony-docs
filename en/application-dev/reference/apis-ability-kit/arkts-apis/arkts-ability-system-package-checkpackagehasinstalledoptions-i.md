# CheckPackageHasInstalledOptions

```TypeScript
export interface CheckPackageHasInstalledOptions
```


> **NOTE:** 
> 
> This API has been supported since API version 3 and deprecated since API version 9.
> Defines the options used for checking whether a bundle has been installed.

**Since:** 3

**Deprecated since:** 9

<!--Device-unnamed-export interface CheckPackageHasInstalledOptions--><!--Device-unnamed-export interface CheckPackageHasInstalledOptions-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## Modules to Import

```TypeScript
import { Package, CheckPackageHasInstalledOptions, CheckPackageHasInstalledResponse } from '@kit.AbilityKit';
```

## complete

```TypeScript
complete?: () => void
```

Called when API call is complete.

**Since:** 3

**Deprecated since:** 9

<!--Device-CheckPackageHasInstalledOptions-complete?: () => void--><!--Device-CheckPackageHasInstalledOptions-complete?: () => void-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

## fail

```TypeScript
fail?: (data: any, code: number) => void
```

Called when API call has failed.

**Since:** 3

**Deprecated since:** 9

<!--Device-CheckPackageHasInstalledOptions-fail?: (data: any, code: number) => void--><!--Device-CheckPackageHasInstalledOptions-fail?: (data: any, code: number) => void-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | any | Yes |  |
| code | number | Yes |  |

## success

```TypeScript
success?: (data: CheckPackageHasInstalledResponse) => void
```

Called when API call is successful.

**Since:** 3

**Deprecated since:** 9

<!--Device-CheckPackageHasInstalledOptions-success?: (data: CheckPackageHasInstalledResponse) => void--><!--Device-CheckPackageHasInstalledOptions-success?: (data: CheckPackageHasInstalledResponse) => void-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | [CheckPackageHasInstalledResponse](arkts-ability-system-package-checkpackagehasinstalledresponse-i.md) | Yes |  |

## bundleName

```TypeScript
bundleName: string
```

Bundle name.

**Type:** string

**Since:** 3

**Deprecated since:** 9

<!--Device-CheckPackageHasInstalledOptions-bundleName: string--><!--Device-CheckPackageHasInstalledOptions-bundleName: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework
