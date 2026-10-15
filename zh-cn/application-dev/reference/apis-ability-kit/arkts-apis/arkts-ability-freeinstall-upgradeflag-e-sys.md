# UpgradeFlag（系统接口）

```TypeScript
export enum UpgradeFlag
```

应用模块升级策略的标志。

> **说明：** 
> 
> 不支持组合使用，如：let flag = UpgradeFlag.NOT_UPGRADE | UpgradeFlag.SINGLE_UPGRADE，只支持单个枚举类型传入。

**起始版本：** 9

<!--Device-freeInstall-export enum UpgradeFlag--><!--Device-freeInstall-export enum UpgradeFlag-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.FreeInstall

**系统接口：** 此接口为系统接口。

## NOT_UPGRADE

```TypeScript
NOT_UPGRADE = 0
```

模块无需升级。

**起始版本：** 9

<!--Device-UpgradeFlag-NOT_UPGRADE = 0--><!--Device-UpgradeFlag-NOT_UPGRADE = 0-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.FreeInstall

**系统接口：** 此接口为系统接口。

## RELATION_UPGRADE

```TypeScript
RELATION_UPGRADE = 2
```

关系模块需要升级。

**起始版本：** 9

<!--Device-UpgradeFlag-RELATION_UPGRADE = 2--><!--Device-UpgradeFlag-RELATION_UPGRADE = 2-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.FreeInstall

**系统接口：** 此接口为系统接口。

## SINGLE_UPGRADE

```TypeScript
SINGLE_UPGRADE = 1
```

单个模块需要升级。

**起始版本：** 9

<!--Device-UpgradeFlag-SINGLE_UPGRADE = 1--><!--Device-UpgradeFlag-SINGLE_UPGRADE = 1-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.FreeInstall

**系统接口：** 此接口为系统接口。
