# SelectionContainerAttribute

支持[通用属性](../../../reference/apis-arkui/arkui-ts/ts-component-general-attributes.md)。 > **说明：** > > - 不支持[隐私遮罩](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-obscured.md)。 > > - 不支持[图形变换](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-transformation.md)，跨节点场景中Text子组件不支持图形变 > 换。

**继承/实现关系：** SelectionContainerAttribute extends CommonMethod

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-export declare interface SelectionContainerAttribute--><!--Device-unnamed-export declare interface SelectionContainerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## attributeModifier

```TypeScript
attributeModifier(modifier: AttributeModifier<SelectionContainerAttribute> | AttributeModifier<CommonMethod>
    | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-SelectionContainerAttribute-attributeModifier(modifier: AttributeModifier<SelectionContainerAttribute> | AttributeModifier<CommonMethod>    | undefined): this--><!--Device-SelectionContainerAttribute-attributeModifier(modifier: AttributeModifier<SelectionContainerAttribute> | AttributeModifier<CommonMethod>    | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | AttributeModifier&lt;[SelectionContainerAttribute](../../apis-arkui/arkts-apis/arkts-arkui-arkui-components-selectioncontainer-selectioncontainerattribute-c.md)&gt; \| AttributeModifier&lt;CommonMethod&gt; \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## bindSelectionMenu

```TypeScript
bindSelectionMenu(spanType: TextSpanType | undefined, content: CustomBuilder | undefined,
    responseType: TextResponseType | undefined, options?: SelectionContainerMenuOptions | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-SelectionContainerAttribute-bindSelectionMenu(spanType: TextSpanType | undefined, content: CustomBuilder | undefined,    responseType: TextResponseType | undefined, options?: SelectionContainerMenuOptions | undefined): this--><!--Device-SelectionContainerAttribute-bindSelectionMenu(spanType: TextSpanType | undefined, content: CustomBuilder | undefined,    responseType: TextResponseType | undefined, options?: SelectionContainerMenuOptions | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| spanType | TextSpanType \| undefined | 是 |  |
| content | CustomBuilder \| undefined | 是 |  |
| responseType | TextResponseType \| undefined | 是 |  |
| options | [SelectionContainerMenuOptions](../../apis-arkui/arkts-apis/arkts-arkui-arkui-components-selectioncontainer-selectioncontainermenuoptions-i.md) \| undefined | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## caretColor

```TypeScript
caretColor(color: ResourceColor | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-SelectionContainerAttribute-caretColor(color: ResourceColor | undefined): this--><!--Device-SelectionContainerAttribute-caretColor(color: ResourceColor | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | ResourceColor \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## copyOption

```TypeScript
copyOption(value: CopyOptions | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-SelectionContainerAttribute-copyOption(value: CopyOptions | undefined): this--><!--Device-SelectionContainerAttribute-copyOption(value: CopyOptions | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | CopyOptions \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## editMenuOptions

```TypeScript
editMenuOptions(editMenu: SelectionContainerEditMenuOptions | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-SelectionContainerAttribute-editMenuOptions(editMenu: SelectionContainerEditMenuOptions | undefined): this--><!--Device-SelectionContainerAttribute-editMenuOptions(editMenu: SelectionContainerEditMenuOptions | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| editMenu | [SelectionContainerEditMenuOptions](../../apis-arkui/arkts-apis/arkts-arkui-arkui-components-selectioncontainer-selectioncontainereditmenuoptions-i.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## enableHapticFeedback

```TypeScript
enableHapticFeedback(isEnabled: boolean | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-SelectionContainerAttribute-enableHapticFeedback(isEnabled: boolean | undefined): this--><!--Device-SelectionContainerAttribute-enableHapticFeedback(isEnabled: boolean | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isEnabled | boolean \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onCopy

```TypeScript
onCopy(callback: Callback<string> | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-SelectionContainerAttribute-onCopy(callback: Callback<string> | undefined): this--><!--Device-SelectionContainerAttribute-onCopy(callback: Callback<string> | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;string&gt; \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onTextSelectionChange

```TypeScript
onTextSelectionChange(callback: Callback<Array<string>> | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-SelectionContainerAttribute-onTextSelectionChange(callback: Callback<Array<string>> | undefined): this--><!--Device-SelectionContainerAttribute-onTextSelectionChange(callback: Callback<Array<string>> | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;Array&lt;string&gt;&gt; \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onWillCopy

```TypeScript
onWillCopy(callback: Callback<string, boolean> | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-SelectionContainerAttribute-onWillCopy(callback: Callback<string, boolean> | undefined): this--><!--Device-SelectionContainerAttribute-onWillCopy(callback: Callback<string, boolean> | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Callback&lt;string, boolean&gt; \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## selectedBackgroundColor

```TypeScript
selectedBackgroundColor(color: ResourceColor | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-SelectionContainerAttribute-selectedBackgroundColor(color: ResourceColor | undefined): this--><!--Device-SelectionContainerAttribute-selectedBackgroundColor(color: ResourceColor | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | ResourceColor \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## setSelectionContainerOptions

```TypeScript
setSelectionContainerOptions(): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-SelectionContainerAttribute-setSelectionContainerOptions(): this--><!--Device-SelectionContainerAttribute-setSelectionContainerOptions(): this-End-->

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## textJoinStyle

```TypeScript
textJoinStyle(style: SelectionContainerTextJoinStyle | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为-1。

**废弃版本：** -1

<!--Device-SelectionContainerAttribute-textJoinStyle(style: SelectionContainerTextJoinStyle | undefined): this--><!--Device-SelectionContainerAttribute-textJoinStyle(style: SelectionContainerTextJoinStyle | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [SelectionContainerTextJoinStyle](../../apis-arkui/arkts-apis/arkts-arkui-arkui-components-selectioncontainer-selectioncontainertextjoinstyle-e.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## default

```TypeScript
default
```

设置SelectionContainer选项。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SelectionContainerAttribute-default--><!--Device-SelectionContainerAttribute-default-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

