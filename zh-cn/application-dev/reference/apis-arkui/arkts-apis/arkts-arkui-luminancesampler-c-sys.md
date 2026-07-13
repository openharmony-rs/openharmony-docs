# LuminanceSampler（系统接口）

设置背景亮度取色参数、注册亮度变化监听回调、取消注册监听回调。

> **说明：**
>
> 以下API需先使用UIContext中的[getLuminanceSampler](arkts-arkui-uicontext-c-sys.md#getluminancesampler-1)方法获取到LuminanceSampler对象，再通过该对象调用对应方法。

**起始版本：** 23

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## offBackgroundLuminanceChange

```TypeScript
offBackgroundLuminanceChange(samplingCallback?: Callback<number>): void
```

取消注册取色监听回调。未指定回调时，取消所有监听。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| samplingCallback | Callback&lt;number&gt; | 否 | 监听回调。 |

## onBackgroundLuminanceChange

```TypeScript
onBackgroundLuminanceChange(samplingCallback: Callback<number>): void
```

设置取色监听回调。

回调的触发条件：背景亮度根据[setBackgroundLuminanceSamplingConfigs](arkts-arkui-luminancesampler-c-sys.md#setbackgroundluminancesamplingconfigs-1)
接口设置的亮阈值和暗阈值分为三个区间，[0，暗阈值)，[暗阈值，亮阈值]，(亮阈值，255]。背景亮度所在区间发生变化（或者首次注册监听回调），并且距离上次取色的时间间隔达到设置的取色时间间隔时触发取色回调，并返回当前背景亮度。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| samplingCallback | Callback&lt;number&gt; | 是 | 监听回调。触发同时返回当前背景亮度。<br/>**说明**：监听回调里不能调用[offBackgroundLuminanceChange](LuminanceSampler#off)。 |

## setBackgroundLuminanceSamplingConfigs

```TypeScript
setBackgroundLuminanceSamplingConfigs(configs: BackgroundLuminanceSamplingConfigs): void
```

设置取色参数配置。当亮度阈值不在指定范围内或暗阈值大于亮阈值将抛出异常。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| configs | BackgroundLuminanceSamplingConfigs | 是 | 取色参数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Internal error.<br> 1. Incorrect parameter values.<br> 2. Incorrect parameters types. |

