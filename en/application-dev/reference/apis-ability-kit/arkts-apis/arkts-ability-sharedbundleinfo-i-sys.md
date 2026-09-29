# SharedBundleInfo (System API)

```TypeScript
export interface SharedBundleInfo
```

Defines the shared bundle information.

**Since:** 10

<!--Device-unnamed-export interface SharedBundleInfo--><!--Device-unnamed-export interface SharedBundleInfo-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## compatiblePolicy

```TypeScript
readonly compatiblePolicy: bundleManager.CompatiblePolicy
```

Compatibility type of the shared bundle.

**Type:** [bundleManager.CompatiblePolicy](arkts-ability-bundlemanager-compatiblepolicy-e.md)

**Since:** 10

<!--Device-SharedBundleInfo-readonly compatiblePolicy: bundleManager.CompatiblePolicy--><!--Device-SharedBundleInfo-readonly compatiblePolicy: bundleManager.CompatiblePolicy-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## name

```TypeScript
readonly name: string
```

Name of the shared bundle.

**Type:** string

**Since:** 10

<!--Device-SharedBundleInfo-readonly name: string--><!--Device-SharedBundleInfo-readonly name: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## sharedModuleInfo

```TypeScript
readonly sharedModuleInfo: Array<SharedModuleInfo>
```

Information about the shared module.

**Type:** Array&lt;[SharedModuleInfo](arkts-ability-sharedbundleinfo-sharedmoduleinfo-i-sys.md)&gt;

**Since:** 10

<!--Device-SharedBundleInfo-readonly sharedModuleInfo: Array<SharedModuleInfo>--><!--Device-SharedBundleInfo-readonly sharedModuleInfo: Array<SharedModuleInfo>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.
