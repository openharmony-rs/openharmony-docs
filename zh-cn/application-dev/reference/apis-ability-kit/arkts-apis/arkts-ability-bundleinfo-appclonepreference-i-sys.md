# AppClonePreference（系统接口）

```TypeScript
export interface AppClonePreference
```

应用分身偏好设置，用于配置应用启动时主应用和分身应用的选择策略。

**起始版本：** 26.0.0

<!--Device-unnamed-export interface AppClonePreference--><!--Device-unnamed-export interface AppClonePreference-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## appIndex

```TypeScript
appIndex?: number
```

表示应用分身索引。<br>当mode取值为AppClonePreferenceMode.CLONE_APP时为必填参数，用于指定具体的分身应用，取值范围为1~5的整数（系统最多支持5个分身）。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AppClonePreference-appIndex?: int--><!--Device-AppClonePreference-appIndex?: int-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。

## mode

```TypeScript
mode: bundleManager.AppClonePreferenceMode
```

表示应用分身偏好设置的模式。

**类型：** [bundleManager.AppClonePreferenceMode](arkts-ability-bundlemanager-appclonepreferencemode-e-sys.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AppClonePreference-mode: bundleManager.AppClonePreferenceMode--><!--Device-AppClonePreference-mode: bundleManager.AppClonePreferenceMode-End-->

**系统能力：** SystemCapability.BundleManager.BundleFramework.Core

**系统接口：** 此接口为系统接口。
