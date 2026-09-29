# ModuleDistroInfo (System API)

```TypeScript
export interface ModuleDistroInfo
```

ModuleDistroInfo: the bundle info summary class.

**Since:** 9

<!--Device-unnamed-export interface ModuleDistroInfo--><!--Device-unnamed-export interface ModuleDistroInfo-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.FreeInstall

**System API:** This is a system API.

## deliveryWithInstall

```TypeScript
readonly deliveryWithInstall: boolean
```

Whether it should be installed together with the application. **true** if it should be installed together with the application, **false** otherwise.

**Type:** boolean

**Since:** 9

<!--Device-ModuleDistroInfo-readonly deliveryWithInstall: boolean--><!--Device-ModuleDistroInfo-readonly deliveryWithInstall: boolean-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.FreeInstall

**System API:** This is a system API.

## installationFree

```TypeScript
readonly installationFree: boolean
```

Whether the HAP file supports the installation-free feature. **true** if the HAP file supports the installation- free feature and meets installation-free constraints, **false** otherwise.

**Type:** boolean

**Since:** 9

<!--Device-ModuleDistroInfo-readonly installationFree: boolean--><!--Device-ModuleDistroInfo-readonly installationFree: boolean-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.FreeInstall

**System API:** This is a system API.

## moduleName

```TypeScript
readonly moduleName: string
```

Module name.

**Type:** string

**Since:** 9

<!--Device-ModuleDistroInfo-readonly moduleName: string--><!--Device-ModuleDistroInfo-readonly moduleName: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.FreeInstall

**System API:** This is a system API.

## moduleType

```TypeScript
readonly moduleType: string
```

Module type.

**Type:** string

**Since:** 9

<!--Device-ModuleDistroInfo-readonly moduleType: string--><!--Device-ModuleDistroInfo-readonly moduleType: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.FreeInstall

**System API:** This is a system API.
