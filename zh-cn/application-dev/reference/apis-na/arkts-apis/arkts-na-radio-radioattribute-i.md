# RadioAttribute

除支持通用属性外，还支持以下属性：

**继承/实现关系：** RadioAttribute extends CommonMethod

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface RadioAttribute--><!--Device-unnamed-export declare interface RadioAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## attributeModifier

```TypeScript
attributeModifier(modifier: AttributeModifier<RadioAttribute> | AttributeModifier<CommonMethod> | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-RadioAttribute-attributeModifier(modifier: AttributeModifier<RadioAttribute> | AttributeModifier<CommonMethod> | undefined): this--><!--Device-RadioAttribute-attributeModifier(modifier: AttributeModifier<RadioAttribute> | AttributeModifier<CommonMethod> | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | [AttributeModifier](../../apis-arkui/arkts-components/arkts-arkui-attributemodifier-i.md)&lt;[RadioAttribute](arkts-na-radio-radioattribute-i.md)&gt; \| [AttributeModifier](../../apis-arkui/arkts-components/arkts-arkui-attributemodifier-i.md)&lt;[CommonMethod](../../apis-arkui/arkts-components/arkts-arkui-commonmethod-c.md)&gt; \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## checked

```TypeScript
checked(isChecked: boolean | undefined | Bindable<boolean>): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-RadioAttribute-checked(isChecked: boolean | undefined | Bindable<boolean>): this--><!--Device-RadioAttribute-checked(isChecked: boolean | undefined | Bindable<boolean>): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isChecked | boolean \| undefined \| [Bindable](arkts-na-common-bindable-i.md)&lt;boolean&gt; | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## contentModifier

```TypeScript
contentModifier(modifier: ContentModifier<RadioConfiguration> | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-RadioAttribute-contentModifier(modifier: ContentModifier<RadioConfiguration> | undefined): this--><!--Device-RadioAttribute-contentModifier(modifier: ContentModifier<RadioConfiguration> | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | [ContentModifier](../../apis-arkui/arkts-components/arkts-arkui-contentmodifier-i.md)&lt;[RadioConfiguration](arkts-na-radio-radioconfiguration-i.md)&gt; \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onChange

```TypeScript
onChange(callback: OnRadioChangeCallback | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-RadioAttribute-onChange(callback: OnRadioChangeCallback | undefined): this--><!--Device-RadioAttribute-onChange(callback: OnRadioChangeCallback | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnRadioChangeCallback](arkts-na-onradiochangecallback-t.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## radioStyle

```TypeScript
radioStyle(value?: RadioStyle | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-RadioAttribute-radioStyle(value?: RadioStyle | undefined): this--><!--Device-RadioAttribute-radioStyle(value?: RadioStyle | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [RadioStyle](arkts-na-radio-radiostyle-i.md) \| undefined | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## default

```TypeScript
default
```

定制Radio属性区的方法。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RadioAttribute-default--><!--Device-RadioAttribute-default-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

