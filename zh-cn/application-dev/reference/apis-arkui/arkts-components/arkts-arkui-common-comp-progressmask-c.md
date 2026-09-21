# ProgressMask

```TypeScript
declare class ProgressMask
```

ProgressMask用于设置遮罩的进度、最大值和颜色。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(value: number, total: number, color: ResourceColor)
```

构造ProgressMask对象。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 进度遮罩的当前值，与total配合使用确定进度比例，当value等于total时表示进度满。<br>取值范围：[0.0, +∞)。传入负数时自动修正为0。 |
| total | number | 是 | 进度遮罩的最大值。<br> 取值范围：[0.0, +∞)。传入负数时自动修正为100。 |
| color | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 进度遮罩的颜色。 |

## enableBreathingAnimation

```TypeScript
enableBreathingAnimation(value: boolean): void
```

进度满时的呼吸光晕动画开关，开启后进度满时遮罩边缘会出现周期性明暗变化的发光效果。未设置时，默认关闭呼吸光晕动画。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否开启进度满时的呼吸光晕动画。<br>true：开启呼吸光晕动画。<br>false：关闭呼吸光晕动画。 |

## updateColor

```TypeScript
updateColor(value: ResourceColor): void
```

更新进度遮罩的颜色。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 进度遮罩的颜色。 |

## updateProgress

```TypeScript
updateProgress(value: number): void
```

更新进度遮罩的进度值。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 进度遮罩的当前值。<br>取值范围：[0.0, +∞)。传入负数时自动修正为0。 |
