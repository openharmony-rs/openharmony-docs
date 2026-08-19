# ToggleAttribute

除支持通用属性外，还支持以下属性：

**继承/实现关系：** ToggleAttribute extends CommonMethod

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface ToggleAttribute--><!--Device-unnamed-export declare interface ToggleAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## attributeModifier

```TypeScript
attributeModifier(modifier: AttributeModifier<ToggleAttribute> | AttributeModifier<CommonMethod> | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-ToggleAttribute-attributeModifier(modifier: AttributeModifier<ToggleAttribute> | AttributeModifier<CommonMethod> | undefined): this--><!--Device-ToggleAttribute-attributeModifier(modifier: AttributeModifier<ToggleAttribute> | AttributeModifier<CommonMethod> | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | [AttributeModifier](../../apis-arkui/arkts-components/arkts-arkui-attributemodifier-i.md)&lt;[ToggleAttribute](arkts-na-toggle-toggleattribute-i.md)&gt; \| [AttributeModifier](../../apis-arkui/arkts-components/arkts-arkui-attributemodifier-i.md)&lt;[CommonMethod](../../apis-arkui/arkts-components/arkts-arkui-commonmethod-c.md)&gt; \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## contentModifier

```TypeScript
contentModifier(modifier: ContentModifier<ToggleConfiguration> | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-ToggleAttribute-contentModifier(modifier: ContentModifier<ToggleConfiguration> | undefined): this--><!--Device-ToggleAttribute-contentModifier(modifier: ContentModifier<ToggleConfiguration> | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | [ContentModifier](../../apis-arkui/arkts-components/arkts-arkui-contentmodifier-i.md)&lt;[ToggleConfiguration](arkts-na-toggle-toggleconfiguration-i.md)&gt; \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onChange

```TypeScript
onChange(callback: ((isOn: boolean) => void) | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-ToggleAttribute-onChange(callback: ((isOn: boolean) => void) | undefined): this--><!--Device-ToggleAttribute-onChange(callback: ((isOn: boolean) => void) | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | ((isOn: boolean) =&gt; void) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## selectedColor

```TypeScript
selectedColor(value: ResourceColor | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-ToggleAttribute-selectedColor(value: ResourceColor | undefined): this--><!--Device-ToggleAttribute-selectedColor(value: ResourceColor | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../../apis-arkui/arkts-apis/arkts-arkui-resourcecolor-t.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## switchPointColor

```TypeScript
switchPointColor(color: ResourceColor | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-ToggleAttribute-switchPointColor(color: ResourceColor | undefined): this--><!--Device-ToggleAttribute-switchPointColor(color: ResourceColor | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | [ResourceColor](../../apis-arkui/arkts-apis/arkts-arkui-resourcecolor-t.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## switchStyle

```TypeScript
switchStyle(value: SwitchStyle | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-ToggleAttribute-switchStyle(value: SwitchStyle | undefined): this--><!--Device-ToggleAttribute-switchStyle(value: SwitchStyle | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [SwitchStyle](arkts-na-toggle-switchstyle-i.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## default

```TypeScript
default
```

Set the attribute modifier of toggle.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ToggleAttribute-default--><!--Device-ToggleAttribute-default-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

