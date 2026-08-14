# CheckboxAttribute

除支持通用属性外，还支持以下属性：

**继承/实现关系：** CheckboxAttribute extends CommonMethod

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface CheckboxAttribute--><!--Device-unnamed-export declare interface CheckboxAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## attributeModifier

```TypeScript
attributeModifier(
        modifier: AttributeModifier<CheckboxAttribute> | AttributeModifier<CommonMethod> | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-CheckboxAttribute-attributeModifier(        modifier: AttributeModifier<CheckboxAttribute> | AttributeModifier<CommonMethod> | undefined): this--><!--Device-CheckboxAttribute-attributeModifier(        modifier: AttributeModifier<CheckboxAttribute> | AttributeModifier<CommonMethod> | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | [AttributeModifier](../../apis-arkui/arkts-components/arkts-arkui-attributemodifier-i.md)&lt;[CheckboxAttribute](arkts-na-checkbox-checkboxattribute-i.md)&gt; \| [AttributeModifier](../../apis-arkui/arkts-components/arkts-arkui-attributemodifier-i.md)&lt;[CommonMethod](../../apis-arkui/arkts-components/arkts-arkui-commonmethod-c.md)&gt; \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## contentModifier

```TypeScript
contentModifier(modifier: ContentModifier<CheckBoxConfiguration> | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-CheckboxAttribute-contentModifier(modifier: ContentModifier<CheckBoxConfiguration> | undefined): this--><!--Device-CheckboxAttribute-contentModifier(modifier: ContentModifier<CheckBoxConfiguration> | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | [ContentModifier](../../apis-arkui/arkts-components/arkts-arkui-contentmodifier-i.md)&lt;[CheckBoxConfiguration](arkts-na-checkbox-checkboxconfiguration-i.md)&gt; \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## mark

```TypeScript
mark(value: MarkStyle | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-CheckboxAttribute-mark(value: MarkStyle | undefined): this--><!--Device-CheckboxAttribute-mark(value: MarkStyle | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [MarkStyle](../../apis-arkui/arkts-apis/arkts-arkui-markstyle-i.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onChange

```TypeScript
onChange(callback: OnCheckboxChangeCallback | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-CheckboxAttribute-onChange(callback: OnCheckboxChangeCallback | undefined): this--><!--Device-CheckboxAttribute-onChange(callback: OnCheckboxChangeCallback | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnCheckboxChangeCallback](arkts-na-oncheckboxchangecallback-t.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## select

```TypeScript
select(isSelected: boolean | undefined | Bindable<boolean>): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-CheckboxAttribute-select(isSelected: boolean | undefined | Bindable<boolean>): this--><!--Device-CheckboxAttribute-select(isSelected: boolean | undefined | Bindable<boolean>): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isSelected | boolean \| undefined \| [Bindable](arkts-na-common-bindable-i.md)&lt;boolean&gt; | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## selectedColor

```TypeScript
selectedColor(value: ResourceColor | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-CheckboxAttribute-selectedColor(value: ResourceColor | undefined): this--><!--Device-CheckboxAttribute-selectedColor(value: ResourceColor | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../../apis-arkui/arkts-apis/arkts-arkui-resourcecolor-t.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## shape

```TypeScript
shape(value: CheckBoxShape | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-CheckboxAttribute-shape(value: CheckBoxShape | undefined): this--><!--Device-CheckboxAttribute-shape(value: CheckBoxShape | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [CheckBoxShape](../../apis-arkui/arkts-apis/arkts-arkui-checkboxshape-e.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## unselectedColor

```TypeScript
unselectedColor(value: ResourceColor | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-CheckboxAttribute-unselectedColor(value: ResourceColor | undefined): this--><!--Device-CheckboxAttribute-unselectedColor(value: ResourceColor | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../../apis-arkui/arkts-apis/arkts-arkui-resourcecolor-t.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## default

```TypeScript
default
```

设置多选框的属性修改器。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-CheckboxAttribute-default--><!--Device-CheckboxAttribute-default-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

