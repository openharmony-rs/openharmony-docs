# UsedScene

描述权限使用的场景和时机。

**起始版本：** 9

<!--Device-unnamed-export interface UsedScene--><!--Device-unnamed-export interface UsedScene-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## abilities

```TypeScript
abilities: Array<string>
```

使用到该权限的Ability集合。

**类型：** Array<string>

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UsedScene-abilities: Array<string>--><!--Device-UsedScene-abilities: Array<string>-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## when

```TypeScript
when: string
```

使用该权限的时机。支持的取值有inuse（使用时）、always（始终）。

**类型：** string

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-UsedScene-when: string--><!--Device-UsedScene-when: string-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

