# UIPickerComponent属性/事件

除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下属性：

除支持[通用事件](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下事件：

**继承/实现关系：** UIPickerComponentAttribute extends [CommonMethod<UIPickerComponentAttribute>](CommonMethod<UIPickerComponentAttribute>)

**起始版本：** 22

<!--Device-unnamed-declare class UIPickerComponentAttribute extends CommonMethod<UIPickerComponentAttribute>--><!--Device-unnamed-declare class UIPickerComponentAttribute extends CommonMethod<UIPickerComponentAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## canLoop

```TypeScript
canLoop(isLoop: Optional<boolean>)
```

设置选项列是否可循环滚动。

- true：可循环滚动。  
- false：不可循环滚动。

默认值：true。当isLoop的值为undefined时，使用默认值。如果子组件的个数小于8个，无论isLoop设置为true还是false，都不会循环滚动。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-UIPickerComponentAttribute-canLoop(isLoop: Optional<boolean>): UIPickerComponentAttribute--><!--Device-UIPickerComponentAttribute-canLoop(isLoop: Optional<boolean>): UIPickerComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isLoop | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 是否可循环滚动。 |

## displayedItemCount

```TypeScript
displayedItemCount(count: Optional<number>)
```

设置UIPickerComponent容器可见选项的数量。未通过该接口设置时，可见选项的数量为7行。

取值范围：[2, 9]内的整数。

默认值：7

设置小数时，使用向下取整后的整数。设置偶数时，自动转为不小于该值的奇数（例如2变为3、8变为9）。设置不在取值范围内时，使用默认值7行。当count的值为undefined时，使用默认值7行。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-UIPickerComponentAttribute-displayedItemCount(count: Optional<int>): UIPickerComponentAttribute--><!--Device-UIPickerComponentAttribute-displayedItemCount(count: Optional<int>): UIPickerComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| count | [Optional](arkts-arkui-optional-t.md)&lt;number&gt; | 是 | 可见选项数量。 |

## enableHapticFeedback

```TypeScript
enableHapticFeedback(enable: Optional<boolean>)
```

设置是否开启触控反馈。

开启触感反馈时，需要在工程的src/main/module.json5文件的"module"内配置requestPermissions字段开启振动权限。

- true：开启触控反馈。  
- false：不开启触控反馈。

默认值：true当enable的值为undefined时，使用默认值。开启后，是否存在触控反馈取决于系统硬件支持情况。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-UIPickerComponentAttribute-enableHapticFeedback(enable: Optional<boolean>): UIPickerComponentAttribute--><!--Device-UIPickerComponentAttribute-enableHapticFeedback(enable: Optional<boolean>): UIPickerComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 设置是否开启触控反馈。 |

## itemHeight

```TypeScript
itemHeight(height: Optional<LengthMetrics>)
```

设置UIPickerComponent容器每个选项的高度。未通过该接口设置时，每个选项的高度为40vp。

单位：与[LengthMetrics](../arkts-apis/arkts-arkui-graphics-lengthmetrics-c.md)一致。

取值范围：[40vp, 64vp]

默认值：40vp设置小于40vp或大于64vp时，使用默认值40vp。当height的值为undefined时，使用默认值40vp。不支持“百分比”类型。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-UIPickerComponentAttribute-itemHeight(height: Optional<LengthMetrics>): UIPickerComponentAttribute--><!--Device-UIPickerComponentAttribute-itemHeight(height: Optional<LengthMetrics>): UIPickerComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| height | [Optional](arkts-arkui-optional-t.md)&lt;LengthMetrics&gt; | 是 | 选项高度。 |

## onChange

```TypeScript
onChange(callback: Optional<OnUIPickerComponentCallback>)
```

滑动选择器选项时，若选中项发生变化，触发该事件。

说明：

- 如果某个选项有一半以上的区域进入选中项区域内，则该选项成为选中项。

- 选中项区域可通过设置[selectionIndicator](UIPickerComponentAttribute#selectionIndicator)进行标识。如果设置选中项指示器为背景，则背景区域即为选中项区域。如果设置选中项指示器为分割线，则上下分割线的中心线内的区域为选中项区域。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-UIPickerComponentAttribute-onChange(callback: Optional<OnUIPickerComponentCallback>): UIPickerComponentAttribute--><!--Device-UIPickerComponentAttribute-onChange(callback: Optional<OnUIPickerComponentCallback>): UIPickerComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Optional](arkts-arkui-optional-t.md)&lt;OnUIPickerComponentCallback&gt; | 是 | 当选中项发生变化时触发的回调函数。当callback的值为undefined时，不使用回调函数。 |

## onScrollStop

```TypeScript
onScrollStop(callback: Optional<OnUIPickerComponentCallback>)
```

选择器滑动停止时，触发该事件。选择器滑动停止指某次行为触发的滑动动画完全结束。如果某次滑动动画还未结束时又触发了新的滑动动画，则不属于滑动停止。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-UIPickerComponentAttribute-onScrollStop(callback: Optional<OnUIPickerComponentCallback>): UIPickerComponentAttribute--><!--Device-UIPickerComponentAttribute-onScrollStop(callback: Optional<OnUIPickerComponentCallback>): UIPickerComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Optional](arkts-arkui-optional-t.md)&lt;OnUIPickerComponentCallback&gt; | 是 | 当选择器滑动停止时触发的回调函数。当callback的值为undefined时，不使用回调函数。 |

## selectionIndicator

```TypeScript
selectionIndicator(style: Optional<PickerIndicatorStyle>)
```

设置选中项指示器的样式。

默认值： { type: PickerIndicatorType.BACKGROUND, borderRadius: { value: 12, unit: LengthUnit.vp },backgroundColor: 'sys.color.comp_background_tertiary' }当style的值为undefined时，使用默认值。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-UIPickerComponentAttribute-selectionIndicator(style: Optional<PickerIndicatorStyle>): UIPickerComponentAttribute--><!--Device-UIPickerComponentAttribute-selectionIndicator(style: Optional<PickerIndicatorStyle>): UIPickerComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-optional-t.md)&lt;PickerIndicatorStyle&gt; | 是 | 选中项指示器的样式。 |

