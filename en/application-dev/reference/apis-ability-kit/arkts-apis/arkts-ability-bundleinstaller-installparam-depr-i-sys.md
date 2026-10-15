# InstallParam (System API)

```TypeScript
export interface InstallParam
```


> **NOTE:** 
> 
> This API has been supported since API version 7 and deprecated since API version 9. You are advised to use
> [InstallParam](arkts-ability-installer-installparam-i-sys.md) instead.
> Describes the parameters required for bundle installation, recovery, or uninstall.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [InstallParam](arkts-ability-installer-installparam-i-sys.md)

<!--Device-unnamed-export interface InstallParam--><!--Device-unnamed-export interface InstallParam-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

**System API:** This is a system API.

## installFlag

```TypeScript
installFlag: number
```

Install flag. Default value: 1. </br>Value range:</br>1: overwrite installation.</br>16: free installation.

**Type:** number

**Default:** Indicates the install flag

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [installFlag](arkts-ability-installer-installparam-i-sys.md#installflag)

<!--Device-InstallParam-installFlag: number--><!--Device-InstallParam-installFlag: number-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

**System API:** This is a system API.

## isKeepData

```TypeScript
isKeepData: boolean
```

Whether to retain the bundle data when the application is uninstalled. The default value is **false**. **true** to retain, **false** otherwise.

**Type:** boolean

**Default:** Indicates whether the param has data

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [isKeepData](arkts-ability-installer-installparam-i-sys.md#iskeepdata)

<!--Device-InstallParam-isKeepData: boolean--><!--Device-InstallParam-isKeepData: boolean-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

**System API:** This is a system API.

## userId

```TypeScript
userId: number
```

User ID. Default value: the userId of the caller.

**Type:** number

**Default:** Indicates the user id

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [userId](arkts-ability-installer-installparam-i-sys.md#userid)

<!--Device-InstallParam-userId: number--><!--Device-InstallParam-userId: number-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework

**System API:** This is a system API.
