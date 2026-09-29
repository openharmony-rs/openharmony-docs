# PackageConfig (System API)

```TypeScript
export interface PackageConfig
```

PackageConfig: the package info class.

**Since:** 9

<!--Device-unnamed-export interface PackageConfig--><!--Device-unnamed-export interface PackageConfig-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.FreeInstall

**System API:** This is a system API.

## deliveryWithInstall

```TypeScript
readonly deliveryWithInstall: boolean
```

Whether it should be installed together with the application. **true** if it should be installed together with the application, **false** otherwise.

**Type:** boolean

**Since:** 9

<!--Device-PackageConfig-readonly deliveryWithInstall: boolean--><!--Device-PackageConfig-readonly deliveryWithInstall: boolean-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.FreeInstall

**System API:** This is a system API.

## deviceTypes

```TypeScript
readonly deviceTypes: Array<string>
```

Device types supported by the bundle.

**Type:** Array&lt;string&gt;

**Since:** 9

<!--Device-PackageConfig-readonly deviceTypes: Array<string>--><!--Device-PackageConfig-readonly deviceTypes: Array<string>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.FreeInstall

**System API:** This is a system API.

## moduleType

```TypeScript
readonly moduleType: string
```

Module type of the bundle.

**Type:** string

**Since:** 9

<!--Device-PackageConfig-readonly moduleType: string--><!--Device-PackageConfig-readonly moduleType: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.FreeInstall

**System API:** This is a system API.

## name

```TypeScript
readonly name: string
```

Bundle name.

**Type:** string

**Since:** 9

<!--Device-PackageConfig-readonly name: string--><!--Device-PackageConfig-readonly name: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.FreeInstall

**System API:** This is a system API.
