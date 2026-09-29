# Dependency

```TypeScript
export interface Dependency
```

Describes the information about the dynamic shared library on which the module depends.

**Since:** 9

<!--Device-unnamed-export interface Dependency--><!--Device-unnamed-export interface Dependency-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## bundleName

```TypeScript
readonly bundleName: string
```

Name of the shared bundle on which the current module depends.

**Type:** string

**Since:** 10

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-Dependency-readonly bundleName: string--><!--Device-Dependency-readonly bundleName: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## moduleName

```TypeScript
readonly moduleName: string
```

Module name of the shared bundle on which the current module depends.

**Type:** string

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-Dependency-readonly moduleName: string--><!--Device-Dependency-readonly moduleName: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## versionCode

```TypeScript
readonly versionCode: number
```

Version number of the shared bundle.

**Type:** number

**Since:** 10

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-Dependency-readonly versionCode: long--><!--Device-Dependency-readonly versionCode: long-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core
