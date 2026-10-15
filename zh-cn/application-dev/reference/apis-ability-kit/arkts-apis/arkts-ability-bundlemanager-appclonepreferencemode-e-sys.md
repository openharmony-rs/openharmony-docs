# AppClonePreferenceMode（系统接口）

```TypeScript
export enum AppClonePreferenceMode
```

应用分身偏好设置的模式。

**起始版本：** 26.0.0

<!--Device-bundleManager-export enum AppClonePreferenceMode--><!--Device-bundleManager-export enum AppClonePreferenceMode-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## ALWAYS_ASK

```TypeScript
ALWAYS_ASK = 0
```

每次启动应用时都询问用户选择主应用或分身应用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AppClonePreferenceMode-ALWAYS_ASK = 0--><!--Device-AppClonePreferenceMode-ALWAYS_ASK = 0-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## CLONE_APP

```TypeScript
CLONE_APP = 2
```

默认使用分身应用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AppClonePreferenceMode-CLONE_APP = 2--><!--Device-AppClonePreferenceMode-CLONE_APP = 2-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## MAIN_APP

```TypeScript
MAIN_APP = 1
```

默认使用主应用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AppClonePreferenceMode-MAIN_APP = 1--><!--Device-AppClonePreferenceMode-MAIN_APP = 1-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。
