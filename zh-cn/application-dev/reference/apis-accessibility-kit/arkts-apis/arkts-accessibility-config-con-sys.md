# 常量（系统接口）

## audioBalance

```TypeScript
const audioBalance: Config<number>
```

表示左右声道音量平衡的配置。取值范围为-1.0~1.0。默认值为0.0。

**起始版本：** 10

<!--Device-config-const audioBalance: Config<double>--><!--Device-config-const audioBalance: Config<double>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## audioMono

```TypeScript
const audioMono: Config<boolean>
```

表示单声道音频的配置。true表示已启用单声道音频，false表示未启用单声道音频，默认值为false。

**起始版本：** 10

<!--Device-config-const audioMono: Config<boolean>--><!--Device-config-const audioMono: Config<boolean>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## clickResponseTime

```TypeScript
const clickResponseTime: Config<ClickResponseTime>
```

表示点击持续时间功能配置。

**起始版本：** 11

<!--Device-config-const clickResponseTime: Config<ClickResponseTime>--><!--Device-config-const clickResponseTime: Config<ClickResponseTime>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## daltonizationState

```TypeScript
const daltonizationState: Config<boolean>
```

表示颜色滤镜功能启动状态。配合daltonizationColorFilter使用。true表示已启用颜色滤镜功能，false表示未启用颜色滤镜功能，默认值为false。

**起始版本：** 11

<!--Device-config-const daltonizationState: Config<boolean>--><!--Device-config-const daltonizationState: Config<boolean>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## ignoreRepeatClick

```TypeScript
const ignoreRepeatClick: Config<boolean>
```

表示忽略重复点击功能启用状态。配合repeatClickInterval使用。true表示已启用忽略重复点击功能，false表示未启用忽略重复点击功能，默认值为false。

**起始版本：** 11

<!--Device-config-const ignoreRepeatClick: Config<boolean>--><!--Device-config-const ignoreRepeatClick: Config<boolean>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## repeatClickInterval

```TypeScript
const repeatClickInterval: Config<RepeatClickInterval>
```

表示忽略重复点击功能配置。

**起始版本：** 11

<!--Device-config-const repeatClickInterval: Config<RepeatClickInterval>--><!--Device-config-const repeatClickInterval: Config<RepeatClickInterval>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## screenMagnification

```TypeScript
const screenMagnification: Config<boolean>
```

Indicates the configuration of screen magnification.

**起始版本：** 12

<!--Device-config-const screenMagnification: Config<boolean>--><!--Device-config-const screenMagnification: Config<boolean>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## shortkeyMultiTargets

```TypeScript
const shortkeyMultiTargets: Config<Array<string>>
```

表示辅助扩展快捷键的列表配置。取值为辅助应用的名称，格式为：['bundleName/abilityName']。

**起始版本：** 11

<!--Device-config-const shortkeyMultiTargets: Config<Array<string>>--><!--Device-config-const shortkeyMultiTargets: Config<Array<string>>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

