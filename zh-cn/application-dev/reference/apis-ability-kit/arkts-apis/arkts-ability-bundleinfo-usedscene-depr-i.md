# UsedScene

> **说明：**  
>  
> 从API version 7开始支持，从API version 9开始废弃，建议使用[UsedScene](arkts-ability-bundleinfo-usedscene-depr-i.md)替代。

描述权限使用的场景和时机。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [bundleInfo:UsedScene](arkts-ability-bundleinfo-usedscene-depr-i.md)

<!--Device-unnamed-export interface UsedScene--><!--Device-unnamed-export interface UsedScene-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## abilities

```TypeScript
abilities: Array<string>
```

使用到该权限的Ability集合。

**类型：** Array&lt;string&gt;

**默认值：** Indicates the abilities that need the permission

**起始版本：** 7

**废弃版本：** 9

**替代接口：** abilities

<!--Device-UsedScene-abilities: Array<string>--><!--Device-UsedScene-abilities: Array<string>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## when

```TypeScript
when: string
```

使用该权限的时机。

**类型：** string

**默认值：** Indicates the time when the permission is used

**起始版本：** 7

**废弃版本：** 9

**替代接口：** when

<!--Device-UsedScene-when: string--><!--Device-UsedScene-when: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

