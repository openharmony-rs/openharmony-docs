# BundleStatsInfo

应用包统计信息。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-applicationManager-interface BundleStatsInfo--><!--Device-applicationManager-interface BundleStatsInfo-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## abilityInFgTotalTime

```TypeScript
abilityInFgTotalTime: number
```

Ability在前台运行的总时长，单位：毫秒。

**类型：** number

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BundleStatsInfo-abilityInFgTotalTime: number--><!--Device-BundleStatsInfo-abilityInFgTotalTime: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## appIndex

```TypeScript
appIndex: number
```

应用分身索引，取值范围：大于等于0的整数。 appIndex可以通过@ohos.bundle.bundleManager中的 [getAppCloneIdentity](../../apis-ability-kit/arkts-apis/arkts-ability-bundlemanager-getappcloneidentity-f.md#getAppCloneIdentity)等接口来获取。

**类型：** number

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BundleStatsInfo-appIndex: number--><!--Device-BundleStatsInfo-appIndex: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## bundleName

```TypeScript
bundleName: string
```

应用的包名。

**类型：** string

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BundleStatsInfo-bundleName: string--><!--Device-BundleStatsInfo-bundleName: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

