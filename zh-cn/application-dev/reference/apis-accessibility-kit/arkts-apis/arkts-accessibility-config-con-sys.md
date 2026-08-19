# 常量（系统接口）

## audioBalance

```TypeScript
const audioBalance: Config<double>
```

表示左右声道音量平衡的配置。-1.0表示仅左声道输出；0.0表示左右声道平衡输出；1.0表示仅右声道输出；中间值为左右声道音量的线性比例。取值范围为-1.0~1.0。默认值为0.0。

**起始版本：** 23

<!--Device-config-const audioBalance: Config<double>--><!--Device-config-const audioBalance: Config<double>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## audioMono

```TypeScript
const audioMono: Config<boolean>
```

表示单声道音频功能启用状态。true表示已启用单声道音频功能，false表示未启用单声道音频功能，默认值为false。

**起始版本：** 23

<!--Device-config-const audioMono: Config<boolean>--><!--Device-config-const audioMono: Config<boolean>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## clickResponseTime

```TypeScript
const clickResponseTime: Config<ClickResponseTime>
```

表示点击持续时间功能配置。

**起始版本：** 23

<!--Device-config-const clickResponseTime: Config<ClickResponseTime>--><!--Device-config-const clickResponseTime: Config<ClickResponseTime>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## daltonizationState

```TypeScript
const daltonizationState: Config<boolean>
```

表示色彩校正功能启用状态。配合daltonizationColorFilter使用。true表示已启用色彩校正功能，false表示未启用色彩校正功能，默认值为false。

**起始版本：** 23

<!--Device-config-const daltonizationState: Config<boolean>--><!--Device-config-const daltonizationState: Config<boolean>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## ignoreRepeatClick

```TypeScript
const ignoreRepeatClick: Config<boolean>
```

表示忽略重复点击功能启用状态。配合repeatClickInterval使用。true表示已启用忽略重复点击功能，false表示未启用忽略重复点击功能，默认值为false。

**起始版本：** 23

<!--Device-config-const ignoreRepeatClick: Config<boolean>--><!--Device-config-const ignoreRepeatClick: Config<boolean>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## repeatClickInterval

```TypeScript
const repeatClickInterval: Config<RepeatClickInterval>
```

表示忽略重复点击的时间间隔配置。配合ignoreRepeatClick使用，仅当ignoreRepeatClick设置为true时，此配置生效。默认值为Shortest，表示最短间隔。

**起始版本：** 23

<!--Device-config-const repeatClickInterval: Config<RepeatClickInterval>--><!--Device-config-const repeatClickInterval: Config<RepeatClickInterval>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## screenMagnification

```TypeScript
const screenMagnification: Config<boolean>
```

Indicates the configuration of screen magnification.

**起始版本：** 23

<!--Device-config-const screenMagnification: Config<boolean>--><!--Device-config-const screenMagnification: Config<boolean>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

## shortkeyMultiTargets

```TypeScript
const shortkeyMultiTargets: Config<Array<string>>
```

表示辅助扩展快捷键的多目标列表配置。取值为辅助扩展应用的名称，格式为：['bundleName/abilityName']。格式不正确或名称无效时，设置不生效。

**起始版本：** 23

<!--Device-config-const shortkeyMultiTargets: Config<Array<string>>--><!--Device-config-const shortkeyMultiTargets: Config<Array<string>>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**系统接口：** 此接口为系统接口。

