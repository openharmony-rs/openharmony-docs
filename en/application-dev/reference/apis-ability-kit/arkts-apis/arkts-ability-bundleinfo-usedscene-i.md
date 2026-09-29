# UsedScene

```TypeScript
export interface UsedScene
```

Describes the use scenario and timing of the permission, helping developers request and use permissions properly.

**Since:** 9

<!--Device-unnamed-export interface UsedScene--><!--Device-unnamed-export interface UsedScene-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## abilities

```TypeScript
abilities: Array<string>
```

Abilities that use the permission.

**Type:** Array&lt;string&gt;

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-UsedScene-abilities: Array<string>--><!--Device-UsedScene-abilities: Array<string>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## when

```TypeScript
when: string
```

Time when the permission is used. The value can be **inuse** or **always**.

**Type:** string

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-UsedScene-when: string--><!--Device-UsedScene-when: string-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core
