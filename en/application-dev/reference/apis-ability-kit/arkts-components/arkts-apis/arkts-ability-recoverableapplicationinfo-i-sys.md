# RecoverableApplicationInfo (System API)

The module defines the information about a preinstalled application that can be restored after being uninstalled. The information can be obtained through [bundleManager.getRecoverableApplicationInfo](arkts-ability-bundlemanager-getrecoverableapplicationinfo-f-sys.md).

> **NOTE:** 
> 
> The APIs provided by this module are system APIs.

**Since:** 11

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## bundleName

```TypeScript
readonly bundleName: string
```

Bundle name.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## bundleType

```TypeScript
readonly bundleType: bundleManager.BundleType
```

Bundle type.

**Type:** [bundleManager.BundleType](arkts-ability-bundlemanager-bundletype-e.md)

**Since:** 12

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## codePaths

```TypeScript
readonly codePaths: Array<string>
```

Installation directory of the application.

**Type:** Array&lt;string&gt;

**Since:** 12

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## iconId

```TypeScript
readonly iconId: number
```

ID of the module icon.

**Type:** number

**Since:** 11

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## labelId

```TypeScript
readonly labelId: number
```

ID of the module label.

**Type:** number

**Since:** 11

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## moduleName

```TypeScript
readonly moduleName: string
```

Module name.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

## systemApp

```TypeScript
readonly systemApp: boolean
```

Whether the application is a system application. **true** if it is a system application, **false** otherwise.

**Type:** boolean

**Since:** 12

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.
