# Version (System API)

Version: the bundle version class.

**Since:** 9

**System capability:** SystemCapability.BundleManager.BundleFramework.FreeInstall

**System API:** This is a system API.

## code

```TypeScript
readonly code: number
```

Version number of the bundle used only for bundle management. The value is a 32-bit non-negative integer. It is used only to determine whether a version is later than another version. A larger value indicates a later version.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.BundleManager.BundleFramework.FreeInstall

**System API:** This is a system API.

## minCompatibleVersionCode

```TypeScript
readonly minCompatibleVersionCode: number
```

Minimum compatible version of the bundle. It is used to check whether the bundle is compatible with a version on other devices in the cross-device scenario. The value is a 32-bit non-negative integer.

**Type:** number

**Since:** 9

**System capability:** SystemCapability.BundleManager.BundleFramework.FreeInstall

**System API:** This is a system API.

## name

```TypeScript
readonly name: string
```

Version number of the bundle visible to users.

**Type:** string

**Since:** 9

**System capability:** SystemCapability.BundleManager.BundleFramework.FreeInstall

**System API:** This is a system API.
