# KeepAliveBundleInfo (System API)

```TypeScript
export interface KeepAliveBundleInfo
```

Describes the keep-alive application information, which can be obtained by calling [getKeepAliveBundles](arkts-ability-appmanager-getkeepalivebundles-f-sys.md) or [getKeepAliveAppServiceExtensions](arkts-ability-appmanager-getkeepaliveappserviceextensions-f-sys.md).

**Since:** 14

<!--Device-appManager-export interface KeepAliveBundleInfo--><!--Device-appManager-export interface KeepAliveBundleInfo-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { appManager } from '@kit.AbilityKit';
```

## allowUserToCancel

```TypeScript
allowUserToCancel?: boolean
```

Whether the user can cancel the keep-alive status. **true** if yes, **false** otherwise.

**Type:** boolean

**Since:** 20

<!--Device-KeepAliveBundleInfo-allowUserToCancel?: boolean--><!--Device-KeepAliveBundleInfo-allowUserToCancel?: boolean-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## bundleName

```TypeScript
bundleName: string
```

Bundle name.

**Type:** string

**Since:** 14

<!--Device-KeepAliveBundleInfo-bundleName: string--><!--Device-KeepAliveBundleInfo-bundleName: string-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## setter

```TypeScript
setter: KeepAliveSetter
```

Type of the party that sets to keep the application alive.

**Type:** [KeepAliveSetter](arkts-ability-appmanager-keepalivesetter-e-sys.md)

**Since:** 14

<!--Device-KeepAliveBundleInfo-setter: KeepAliveSetter--><!--Device-KeepAliveBundleInfo-setter: KeepAliveSetter-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## setterUserId

```TypeScript
setterUserId?: number
```

ID of the user who keeps the application alive.

**Type:** number

**Since:** 20

<!--Device-KeepAliveBundleInfo-setterUserId?: int--><!--Device-KeepAliveBundleInfo-setterUserId?: int-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## type

```TypeScript
type: KeepAliveAppType
```

Type of the application to be kept alive.

**Type:** [KeepAliveAppType](arkts-ability-appmanager-keepaliveapptype-e-sys.md)

**Since:** 14

<!--Device-KeepAliveBundleInfo-type: KeepAliveAppType--><!--Device-KeepAliveBundleInfo-type: KeepAliveAppType-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.
