# SelectionContainerAttribute

支持\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。 > **说明：** > > - 不支持\_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_。 > > - 不支持\_\_\_MD\_LINK\_DESC\_USD\_2\_\_\_，跨节点场景中Text子组件不支持图形变 > 换。

**继承/实现关系：** SelectionContainerAttribute extends [CommonMethod](../../apis-na/arkts-apis/arkts-na-component/common-commonmethod-i.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export declare interface SelectionContainerAttribute extends CommonMethod--><!--Device-unnamed-export declare interface SelectionContainerAttribute extends CommonMethod-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## attributeModifier

```TypeScript
default attributeModifier(modifier: AttributeModifier<SelectionContainerAttribute> | AttributeModifier<CommonMethod>
    | undefined): this
```

设置组件的动态属性。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SelectionContainerAttribute-default attributeModifier(modifier: AttributeModifier<SelectionContainerAttribute> | AttributeModifier<CommonMethod>    | undefined): this--><!--Device-SelectionContainerAttribute-default attributeModifier(modifier: AttributeModifier<SelectionContainerAttribute> | AttributeModifier<CommonMethod>    | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;SelectionContainerAttribute&gt; \| AttributeModifier&lt;CommonMethod&gt; \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | returns the instance of the SelectionContainerAttribute. |

## bindSelectionMenu

```TypeScript
default bindSelectionMenu(spanType: TextSpanType | undefined, content: CustomBuilder | undefined,
    responseType: TextResponseType | undefined, options?: SelectionContainerMenuOptions | undefined): this
```

设置自定义选择菜单。未通过该接口设置时，默认spanType为TextSpanType.TEXT，responseType为TextResponseType.LONG\_PRESS。 > **说明：** > > - bindSelectionMenu的长按响应时长为600ms， > \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_的长按响应时 > 长为800ms，当两者同时绑定且触发方式均为长按时，优先响应bindSelectionMenu。 > > - 自定义菜单过长时，建议内部嵌套使用\_\_\_MD\_LINK\_DESC\_USD\_1\_\_\_组件，避免键盘被遮挡。 > > - 选区跨越不可复制Text时，菜单仅基于实际选中的可复制文本进行显示和处理。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SelectionContainerAttribute-default bindSelectionMenu(spanType: TextSpanType | undefined, content: CustomBuilder | undefined,    responseType: TextResponseType | undefined, options?: SelectionContainerMenuOptions | undefined): this--><!--Device-SelectionContainerAttribute-default bindSelectionMenu(spanType: TextSpanType | undefined, content: CustomBuilder | undefined,    responseType: TextResponseType | undefined, options?: SelectionContainerMenuOptions | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| spanType | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 选择菜单类型。用于指定选择菜单作用的文本类型范围，不同类型对应不同的菜单行为。各枚举值的含义及适用场景详见\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |
| content | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 选择菜单内容。 |
| responseType | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 选择菜单响应类型。 |
| options | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 否 | 选择菜单选项，用于配置菜单出现、消失、显示、隐藏等事件的回调。当需要监听这些菜单事件时传入此参数，不传入时默认不监听菜单事件。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | returns the instance of the SelectionContainerAttribute. |

## caretColor

```TypeScript
default caretColor(color: ResourceColor | undefined): this
```

设置选中文本手柄颜色。未通过该接口设置时，默认手柄颜色为'#007DFF'（蓝色）。 > **说明：** > > - 该属性在跨节点场景中用于各Text子组件选中文本手柄颜色。 > > - 在跨节点场景中Text子组件\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_设置无 > 效，始终使用SelectionContainer的配置。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SelectionContainerAttribute-default caretColor(color: ResourceColor | undefined): this--><!--Device-SelectionContainerAttribute-default caretColor(color: ResourceColor | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 手柄颜色。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | returns the instance of the SelectionContainerAttribute. |

## copyOption

```TypeScript
default copyOption(value: CopyOptions | undefined): this
```

设置组件的复制粘贴配置项。未通过该接口设置时，默认为CopyOptions.InApp。 > **说明：** > > Text子组件已显式设置\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_时，优先使用 > Text子组件的配置；未设置时，使用SelectionContainer的配置。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SelectionContainerAttribute-default copyOption(value: CopyOptions | undefined): this--><!--Device-SelectionContainerAttribute-default copyOption(value: CopyOptions | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 复制粘贴配置项，用于设置文本的可复制范围。具体说明请参考CopyOptions枚举。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | returns the instance of the SelectionContainerAttribute. |

## editMenuOptions

```TypeScript
default editMenuOptions(editMenu: SelectionContainerEditMenuOptions | undefined): this
```

设置选中文本后的编辑菜单选项，包括菜单文本、图标和回调等。 > **说明：** > > 当同时为当前场景设置了[bindSelectionMenu]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_和editMenuOptions时，优先使用bindSelectionMenu，editMenuOptions不生 > 效。bindSelectionMenu用于完全自定义菜单风格和触发条件，由开发者定义所有菜单项；editMenuOptions用于在系统默认菜单基础上添加扩展项，触发条件不变。建议根据自定义程度需求选择。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SelectionContainerAttribute-default editMenuOptions(editMenu: SelectionContainerEditMenuOptions | undefined): this--><!--Device-SelectionContainerAttribute-default editMenuOptions(editMenu: SelectionContainerEditMenuOptions | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| editMenu | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 自定义编辑菜单配置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | returns the instance of the SelectionContainerAttribute. |

## enableHapticFeedback

```TypeScript
default enableHapticFeedback(isEnabled: boolean | undefined): this
```

设置是否开启触控反馈。未通过该接口设置时，默认开启。 开启触控反馈时，需要在工程的\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_中配置requestPermissions字段开启振动权限，配 置如下：

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SelectionContainerAttribute-default enableHapticFeedback(isEnabled: boolean | undefined): this--><!--Device-SelectionContainerAttribute-default enableHapticFeedback(isEnabled: boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isEnabled | boolean \| undefined | 是 | 是否开启触控反馈。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_true表示开启触控反馈，false表示不开启触控反馈。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | returns the instance of the SelectionContainerAttribute. |

## onCopy

```TypeScript
default onCopy(callback: Callback<string> | undefined): this
```

长按文本内部区域弹出选择菜单后，点击选择菜单的复制按钮，触发该回调。仅支持复制文本。使用callback异步回调。 > **说明：** > > - 回调参数为按Text组件视觉顺序拼接后的选中文本，拼接方式由[textJoinStyle]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_配置决定。 > > - 仅当容器级[onWillCopy]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_返回true时，该回调才会触发。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SelectionContainerAttribute-default onCopy(callback: Callback<string> | undefined): this--><!--Device-SelectionContainerAttribute-default onCopy(callback: Callback<string> | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;string&gt; \| undefined | 是 | 复制回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | returns the instance of the SelectionContainerAttribute. |

## onTextSelectionChange

```TypeScript
default onTextSelectionChange(callback: Callback<Array<string>> | undefined): this
```

SelectionContainer中选中文本发生变化时触发该回调。使用callback异步回调。 > **说明：** > > - 回调参数数组中各项顺序与Text组件视觉顺序一致。 > > - 数组中的每一项对应一个Text子组件的选中文本。 > > - 仅包含有选中文本的Text子组件，不包含未选中Text子组件，也不包含不可复制Text的空字符串占位。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SelectionContainerAttribute-default onTextSelectionChange(callback: Callback<Array<string>> | undefined): this--><!--Device-SelectionContainerAttribute-default onTextSelectionChange(callback: Callback<Array<string>> | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;Array&lt;string&gt;&gt; \| undefined | 是 | 选中文本变化回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | returns the instance of the SelectionContainerAttribute. |

## onWillCopy

```TypeScript
default onWillCopy(callback: Callback<string, boolean> | undefined): this
```

在进行复制操作前，触发该回调。使用callback异步回调。 > **说明：** > > - 回调参数为按Text组件视觉顺序拼接后的选中文本，拼接方式由[textJoinStyle]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_配置决定。 > > - 返回false时，会阻止本次跨节点复制及容器级[onCopy]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_回调触发，但不会影响各Text子组件已独立处理完成的复制事件逻辑。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SelectionContainerAttribute-default onWillCopy(callback: Callback<string, boolean> | undefined): this--><!--Device-SelectionContainerAttribute-default onWillCopy(callback: Callback<string, boolean> | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;string, boolean&gt; \| undefined | 是 | 复制前检查回调，返回true表示允许复制，返回false表示不允许复制。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | returns the instance of the SelectionContainerAttribute. |

## selectedBackgroundColor

```TypeScript
default selectedBackgroundColor(color: ResourceColor | undefined): this
```

设置选中文本底板颜色。未通过该接口设置时，默认选中文本底板颜色为'#007DFF'（蓝色），如果未设置不透明度，默认为20%不透明度。 > **说明：** > > - 该属性在跨节点场景中用于各Text子组件选中区域的高亮颜色。 > > - Text子组件已显式设置 > \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_ > 时，优先使用Text子组件的配置；未设置时，使用SelectionContainer的配置。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SelectionContainerAttribute-default selectedBackgroundColor(color: ResourceColor | undefined): this--><!--Device-SelectionContainerAttribute-default selectedBackgroundColor(color: ResourceColor | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 选中文本底板颜色。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | returns the instance of the SelectionContainerAttribute. |

## setSelectionContainerOptions

```TypeScript
default setSelectionContainerOptions(): this
```

设置SelectionContainer选项。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SelectionContainerAttribute-default setSelectionContainerOptions(): this--><!--Device-SelectionContainerAttribute-default setSelectionContainerOptions(): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | returns the instance of the SelectionContainerAttribute. |

## textJoinStyle

```TypeScript
default textJoinStyle(style: SelectionContainerTextJoinStyle | undefined): this
```

设置SelectionContainer内聚合文本的拼接方式。未通过该接口设置时，默认为SelectionContainerTextJoinStyle.NEWLINE，表示不同文本节点之间使用换行符\n拼接。 > **说明：** > > - 该配置会影响[onWillCopy]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_、[onCopy]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_、[bindSelectionMenu]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_相关回调中返回 > 的文本内容。 > > - 该配置也会影响系统内置菜单项中依赖文本拼接结果的逻辑。例如，选择两个Text节点中的文本时，若配置为SelectionContainerTextJoinStyle.NEWLINE，执行复制后两段文本之间会插入换行符；若配置 > 为SelectionContainerTextJoinStyle.DIRECT，执行复制后两段文本会直接拼接。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SelectionContainerAttribute-default textJoinStyle(style: SelectionContainerTextJoinStyle | undefined): this--><!--Device-SelectionContainerAttribute-default textJoinStyle(style: SelectionContainerTextJoinStyle | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | 聚合文本拼接方式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | returns the instance of the SelectionContainerAttribute. |

