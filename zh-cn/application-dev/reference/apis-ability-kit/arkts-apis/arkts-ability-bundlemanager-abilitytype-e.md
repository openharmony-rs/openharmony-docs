# AbilityType

标识Ability组件的类型。

**起始版本：** 9

<!--Device-bundleManager-export enum AbilityType--><!--Device-bundleManager-export enum AbilityType-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## PAGE

```TypeScript
PAGE = 1
```

UI界面类型的Ability。表示基于Page模板开发的FA，用于提供与用户交互的能力。

**起始版本：** 9

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-AbilityType-PAGE = 1--><!--Device-AbilityType-PAGE = 1-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## SERVICE

```TypeScript
SERVICE = 2
```

后台服务类型的Ability，无UI界面。表示基于Service模板开发的[ParticleAbility](arkts-ability-particleability.md)，用于提供后台运行任务的能力，例如后台下载或者播放音乐。

**起始版本：** 9

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-AbilityType-SERVICE = 2--><!--Device-AbilityType-SERVICE = 2-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

## DATA

```TypeScript
DATA = 3
```

表示基于Data模板开发的[ParticleAbility](arkts-ability-particleability.md)，用于对外部提供统一的数据访问对象。

**起始版本：** 9

**模型约束：** 此接口仅可在FA模型下使用。

<!--Device-AbilityType-DATA = 3--><!--Device-AbilityType-DATA = 3-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

