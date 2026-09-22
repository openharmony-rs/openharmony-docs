# UsedScene

```TypeScript
export interface UsedScene
```


> **NOTE:** 
> 
> This API has been supported since API version 7 and deprecated since API version 9. You are advised to use
> [UsedScene](#usedscene) instead.

Describes the application scenario and timing for using the permission.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [UsedScene](#usedscene)

**System capability:** SystemCapability.BundleManager.BundleFramework

## abilities

```TypeScript
abilities: Array<string>
```

Abilities that use the permission.

**Type:** Array&lt;string&gt;

**Default:** Indicates the abilities that need the permission

**Since:** 7

**Deprecated since:** 9

**Substitutes:** abilities

**System capability:** SystemCapability.BundleManager.BundleFramework

## when

```TypeScript
when: string
```

Time when the permission is used.

**Type:** string

**Default:** Indicates the time when the permission is used

**Since:** 7

**Deprecated since:** 9

**Substitutes:** when

**System capability:** SystemCapability.BundleManager.BundleFramework
