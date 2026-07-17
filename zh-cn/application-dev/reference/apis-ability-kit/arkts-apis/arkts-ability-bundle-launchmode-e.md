# LaunchMode

> **说明：**  
>  
> 从API version 7开始支持，从API version 9开始废弃，建议使用  
> [bundleManager.LaunchType](arkts-ability-bundlemanager-launchtype-e.md)替代。

Ability组件的启动模式。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [LaunchType](arkts-ability-bundlemanager-launchtype-e.md)

<!--Device-bundle-export enum LaunchMode--><!--Device-bundle-export enum LaunchMode-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## SINGLETON

```TypeScript
SINGLETON = 0
```

Ability只有一个实例。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** SINGLETON

<!--Device-LaunchMode-SINGLETON = 0--><!--Device-LaunchMode-SINGLETON = 0-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

## STANDARD

```TypeScript
STANDARD = 1
```

Ability有多个实例。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** MULTITON

<!--Device-LaunchMode-STANDARD = 1--><!--Device-LaunchMode-STANDARD = 1-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework

