# UIPickerComponentAttribute

除支持通用属性外，还支持以下属性： 除支持通用事件外，还支持以下事件：

**继承/实现关系：** UIPickerComponentAttribute extends CommonMethod

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface UIPickerComponentAttribute--><!--Device-unnamed-export declare interface UIPickerComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## attributeModifier

```TypeScript
attributeModifier(modifier: AttributeModifier<UIPickerComponentAttribute> | AttributeModifier<CommonMethod> | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-UIPickerComponentAttribute-attributeModifier(modifier: AttributeModifier<UIPickerComponentAttribute> | AttributeModifier<CommonMethod> | undefined): this--><!--Device-UIPickerComponentAttribute-attributeModifier(modifier: AttributeModifier<UIPickerComponentAttribute> | AttributeModifier<CommonMethod> | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | [AttributeModifier](../../apis-arkui/arkts-components/arkts-arkui-attributemodifier-i.md)&lt;[UIPickerComponentAttribute](arkts-na-uipickercomponent-uipickercomponentattribute-i.md)&gt; \| [AttributeModifier](../../apis-arkui/arkts-components/arkts-arkui-attributemodifier-i.md)&lt;[CommonMethod](../../apis-arkui/arkts-components/arkts-arkui-commonmethod-c.md)&gt; \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## canLoop

```TypeScript
canLoop(isLoop: boolean | undefined): UIPickerComponentAttribute
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-UIPickerComponentAttribute-canLoop(isLoop: boolean | undefined): UIPickerComponentAttribute--><!--Device-UIPickerComponentAttribute-canLoop(isLoop: boolean | undefined): UIPickerComponentAttribute-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isLoop | boolean \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [UIPickerComponentAttribute](arkts-na-uipickercomponent-uipickercomponentattribute-i.md) |  |

## displayedItemCount

```TypeScript
displayedItemCount(count: int | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-UIPickerComponentAttribute-displayedItemCount(count: int | undefined): this--><!--Device-UIPickerComponentAttribute-displayedItemCount(count: int | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| count | int \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## enableHapticFeedback

```TypeScript
enableHapticFeedback(enable: boolean | undefined): UIPickerComponentAttribute
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-UIPickerComponentAttribute-enableHapticFeedback(enable: boolean | undefined): UIPickerComponentAttribute--><!--Device-UIPickerComponentAttribute-enableHapticFeedback(enable: boolean | undefined): UIPickerComponentAttribute-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enable | boolean \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [UIPickerComponentAttribute](arkts-na-uipickercomponent-uipickercomponentattribute-i.md) |  |

## itemHeight

```TypeScript
itemHeight(height: LengthMetrics | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-UIPickerComponentAttribute-itemHeight(height: LengthMetrics | undefined): this--><!--Device-UIPickerComponentAttribute-itemHeight(height: LengthMetrics | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| height | [LengthMetrics](arkts-na-graphics-lengthmetrics-c.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onChange

```TypeScript
onChange(callback: OnUIPickerComponentCallback | undefined): UIPickerComponentAttribute
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-UIPickerComponentAttribute-onChange(callback: OnUIPickerComponentCallback | undefined): UIPickerComponentAttribute--><!--Device-UIPickerComponentAttribute-onChange(callback: OnUIPickerComponentCallback | undefined): UIPickerComponentAttribute-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnUIPickerComponentCallback](arkts-na-onuipickercomponentcallback-t.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [UIPickerComponentAttribute](arkts-na-uipickercomponent-uipickercomponentattribute-i.md) |  |

## onScrollStop

```TypeScript
onScrollStop(callback: OnUIPickerComponentCallback | undefined): UIPickerComponentAttribute
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-UIPickerComponentAttribute-onScrollStop(callback: OnUIPickerComponentCallback | undefined): UIPickerComponentAttribute--><!--Device-UIPickerComponentAttribute-onScrollStop(callback: OnUIPickerComponentCallback | undefined): UIPickerComponentAttribute-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnUIPickerComponentCallback](arkts-na-onuipickercomponentcallback-t.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [UIPickerComponentAttribute](arkts-na-uipickercomponent-uipickercomponentattribute-i.md) |  |

## selectionIndicator

```TypeScript
selectionIndicator(style: PickerIndicatorStyle | undefined): UIPickerComponentAttribute
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-UIPickerComponentAttribute-selectionIndicator(style: PickerIndicatorStyle | undefined): UIPickerComponentAttribute--><!--Device-UIPickerComponentAttribute-selectionIndicator(style: PickerIndicatorStyle | undefined): UIPickerComponentAttribute-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [PickerIndicatorStyle](arkts-na-uipickercomponent-pickerindicatorstyle-i.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [UIPickerComponentAttribute](arkts-na-uipickercomponent-uipickercomponentattribute-i.md) |  |

## default

```TypeScript
default
```

设置UIPickerComponent容器可见选项的数量。未通过该接口设置时，可见选项的数量为7行。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIPickerComponentAttribute-default--><!--Device-UIPickerComponentAttribute-default-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

