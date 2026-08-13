# SelectionContainerAttribute

支持[通用属性](../../../reference/apis-arkui/arkui-ts/ts-component-general-attributes.md)。 支持[通用事件](../../../reference/apis-arkui/arkui-ts/ts-component-general-events.md)。 > **说明：** > > - 不支持[隐私遮罩](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-obscured.md)。 > > - 不支持[图形变换](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-transformation.md)，跨节点场景中Text子组件不支持图形变换。 > > - 不支持[拖拽事件](../../../reference/apis-arkui/arkui-ts/ts-universal-events-drag-drop.md)。

**继承/实现关系：** SelectionContainerAttribute extends CommonMethod<SelectionContainerAttribute>

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-export declare class SelectionContainerAttribute--><!--Device-unnamed-export declare class SelectionContainerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## bindSelectionMenu

```TypeScript
bindSelectionMenu(spanType: Optional<TextSpanType>, content: Optional<CustomBuilder>,
    responseType: Optional<TextResponseType>, options?: Optional<SelectionContainerMenuOptions>): SelectionContainerAttribute
```

绑定到选择菜单。 &lt;p&gt;&lt;strong&gt;注意&lt;/strong&gt;： &lt;br&gt;长按手势需要的时间，bindSelectionMenu为600ms,bindContextMenu为800 ms。 &lt;br&gt;当bindSelectionMenu和bindContextMenu都设置了，并且都设置为长按触发 手势， bindSelectionMenu首先被触发。 &lt;br&gt;如果自定义菜单过长，可以嵌入一个Scroll组件，防止键盘被遮挡。 &lt;/p&gt;

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SelectionContainerAttribute-bindSelectionMenu(spanType: Optional<TextSpanType>, content: Optional<CustomBuilder>,    responseType: Optional<TextResponseType>, options?: Optional<SelectionContainerMenuOptions>): SelectionContainerAttribute--><!--Device-SelectionContainerAttribute-bindSelectionMenu(spanType: Optional<TextSpanType>, content: Optional<CustomBuilder>,    responseType: Optional<TextResponseType>, options?: Optional<SelectionContainerMenuOptions>): SelectionContainerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| spanType | Optional&lt;TextSpanType&gt; | 是 | 选择菜单的类型。默认值为 TextSpanType.TEXT |
| content | Optional&lt;CustomBuilder&gt; | 是 | 指示选择菜单的内容 |
| responseType | Optional&lt;TextResponseType&gt; | 是 | 选择菜单响应类型。默认值为 TextResponseType.LONG_press |
| options | Optional&lt;[SelectionContainerMenuOptions](arkts-arkui-arkui-components-selectioncontainer-selectioncontainermenuoptions-i.md)&gt; | 否 | 指示选择菜单的选项 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SelectionContainerAttribute](arkts-arkui-arkui-components-selectioncontainer-selectioncontainerattribute-c.md) | 返回SelectionContainerAttribute的实例。 |

## caretColor

```TypeScript
caretColor(color: Optional<ResourceColor>): SelectionContainerAttribute
```

设置选中文本手柄颜色。未通过该接口设置时，默认手柄颜色为'#007DFF'（蓝色）。 > **说明：** > > - 该属性在跨节点场景中用于各Text子组件选中文本手柄颜色。 > > - 在跨节点场景中Text子组件caretColor设置无效，始终使用SelectionContainer的配置。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SelectionContainerAttribute-caretColor(color: Optional<ResourceColor>): SelectionContainerAttribute--><!--Device-SelectionContainerAttribute-caretColor(color: Optional<ResourceColor>): SelectionContainerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | Optional&lt;ResourceColor&gt; | 是 | 手柄颜色。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SelectionContainerAttribute](arkts-arkui-arkui-components-selectioncontainer-selectioncontainerattribute-c.md) | returns the instance of the SelectionContainerAttribute. |

## copyOption

```TypeScript
copyOption(value: Optional<CopyOptions>): SelectionContainerAttribute
```

设置组件的复制粘贴配置项。未通过该接口设置时，默认为CopyOptions.InApp。 > **说明：** > > Text子组件已显式设置copyOption时，优先使用Text子组件的配置；未设置时，使用SelectionContainer的配置。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SelectionContainerAttribute-copyOption(value: Optional<CopyOptions>): SelectionContainerAttribute--><!--Device-SelectionContainerAttribute-copyOption(value: Optional<CopyOptions>): SelectionContainerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Optional&lt;CopyOptions&gt; | 是 | 复制粘贴配置项，用于设置文本的可复制范围。具体说明请参考CopyOptions枚举。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SelectionContainerAttribute](arkts-arkui-arkui-components-selectioncontainer-selectioncontainerattribute-c.md) | returns the instance of the SelectionContainerAttribute. |

## editMenuOptions

```TypeScript
editMenuOptions(editMenu: Optional<SelectionContainerEditMenuOptions>): SelectionContainerAttribute
```

设置选中文本后的编辑菜单选项，包括菜单文本、图标和回调等。 > **说明：** > > 当同时为当前场景设置了[bindSelectionMenu](#bindSelectionMenu)和editMenuOptions时，优先使用 > bindSelectionMenu，editMenuOptions不生效。bindSelectionMenu用于完全自定义菜单风格和触发条件，由开发者定义所有菜单项；editMenuOptions用于在系统默认菜单基础上添加扩 > 展项，触发条件不变。建议根据自定义程度需求选择。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SelectionContainerAttribute-editMenuOptions(editMenu: Optional<SelectionContainerEditMenuOptions>): SelectionContainerAttribute--><!--Device-SelectionContainerAttribute-editMenuOptions(editMenu: Optional<SelectionContainerEditMenuOptions>): SelectionContainerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| editMenu | Optional&lt;[SelectionContainerEditMenuOptions](arkts-arkui-arkui-components-selectioncontainer-selectioncontainereditmenuoptions-i.md)&gt; | 是 | 自定义编辑菜单配置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SelectionContainerAttribute](arkts-arkui-arkui-components-selectioncontainer-selectioncontainerattribute-c.md) | returns the instance of the SelectionContainerAttribute. |

## enableHapticFeedback

```TypeScript
enableHapticFeedback(isEnabled: Optional<boolean>): SelectionContainerAttribute
```

设置是否开启触控反馈。未通过该接口设置时，默认开启。 开启触控反馈时，需要在工程的[module.json5配置文件](../../../quick-start/module-configuration-file.md)中配置requestPermissions字段开启振动权限，配 置如下：

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SelectionContainerAttribute-enableHapticFeedback(isEnabled: Optional<boolean>): SelectionContainerAttribute--><!--Device-SelectionContainerAttribute-enableHapticFeedback(isEnabled: Optional<boolean>): SelectionContainerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isEnabled | Optional&lt;boolean&gt; | 是 | 是否开启触控反馈。 &lt;br&gt;true表示开启触控反馈，false表示不开启触控反馈。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SelectionContainerAttribute](arkts-arkui-arkui-components-selectioncontainer-selectioncontainerattribute-c.md) | returns the instance of the SelectionContainerAttribute. |

## onCopy

```TypeScript
onCopy(callback: Optional<Callback<string>>): SelectionContainerAttribute
```

长按文本内部区域弹出选择菜单后，点击选择菜单的复制按钮，触发该回调。仅支持复制文本。使用callback异步回调。 > **说明：** > > - 回调参数为按Text组件视觉顺序拼接后的选中文本，拼接方式由[textJoinStyle](#textJoinStyle)配置决定。 > > - 仅当容器级[onWillCopy](#onWillCopy)返回true时，该回调才会触发。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SelectionContainerAttribute-onCopy(callback: Optional<Callback<string>>): SelectionContainerAttribute--><!--Device-SelectionContainerAttribute-onCopy(callback: Optional<Callback<string>>): SelectionContainerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Optional&lt;Callback&lt;string&gt;&gt; | 是 | 复制回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SelectionContainerAttribute](arkts-arkui-arkui-components-selectioncontainer-selectioncontainerattribute-c.md) | returns the instance of the SelectionContainerAttribute. |

## onTextSelectionChange

```TypeScript
onTextSelectionChange(callback: Optional<Callback<Array<string>>>): SelectionContainerAttribute
```

SelectionContainer中选中文本发生变化时触发该回调。使用callback异步回调。 > **说明：** > > - 回调参数数组中各项顺序与Text组件视觉顺序一致。 > > - 数组中的每一项对应一个Text子组件的选中文本。 > > - 仅包含有选中文本的Text子组件，不包含未选中Text子组件，也不包含不可复制Text的空字符串占位。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SelectionContainerAttribute-onTextSelectionChange(callback: Optional<Callback<Array<string>>>): SelectionContainerAttribute--><!--Device-SelectionContainerAttribute-onTextSelectionChange(callback: Optional<Callback<Array<string>>>): SelectionContainerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Optional&lt;Callback&lt;Array&lt;string&gt;&gt;&gt; | 是 | 选中文本变化回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SelectionContainerAttribute](arkts-arkui-arkui-components-selectioncontainer-selectioncontainerattribute-c.md) | returns the instance of the SelectionContainerAttribute. |

## onWillCopy

```TypeScript
onWillCopy(callback: Optional<Callback<string, boolean>>): SelectionContainerAttribute
```

在进行复制操作前，触发该回调。使用callback异步回调。 > **说明：** > > - 回调参数为按Text组件视觉顺序拼接后的选中文本，拼接方式由[textJoinStyle](#textJoinStyle)配置决定。 > > - 返回false时，会阻止本次跨节点复制及容器级[onCopy](#onCopy)回调触发，但不会影响各Text子组件已独立处理完成的复制事件逻辑。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SelectionContainerAttribute-onWillCopy(callback: Optional<Callback<string, boolean>>): SelectionContainerAttribute--><!--Device-SelectionContainerAttribute-onWillCopy(callback: Optional<Callback<string, boolean>>): SelectionContainerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | Optional&lt;Callback&lt;string, boolean&gt;&gt; | 是 | 复制前检查回调，返回true表示允许复制，返回false表示不允许复制。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SelectionContainerAttribute](arkts-arkui-arkui-components-selectioncontainer-selectioncontainerattribute-c.md) | returns the instance of the SelectionContainerAttribute. |

## selectedBackgroundColor

```TypeScript
selectedBackgroundColor(color: Optional<ResourceColor>): SelectionContainerAttribute
```

设置选中文本底板颜色。未通过该接口设置时，默认选中文本底板颜色为'#007DFF'（蓝色），如果未设置不透明度，默认为20%不透明度。 > **说明：** > > - 该属性在跨节点场景中用于各Text子组件选中区域的高亮颜色。 > > - Text子组件已显式设置selectedBackgroundColor时，优先使用Text子组件的配置；未设置时，使用 > SelectionContainer的配置。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SelectionContainerAttribute-selectedBackgroundColor(color: Optional<ResourceColor>): SelectionContainerAttribute--><!--Device-SelectionContainerAttribute-selectedBackgroundColor(color: Optional<ResourceColor>): SelectionContainerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | Optional&lt;ResourceColor&gt; | 是 | 选中文本底板颜色。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SelectionContainerAttribute](arkts-arkui-arkui-components-selectioncontainer-selectioncontainerattribute-c.md) | returns the instance of the SelectionContainerAttribute. |

## textJoinStyle

```TypeScript
textJoinStyle(style: Optional<SelectionContainerTextJoinStyle>): SelectionContainerAttribute
```

设置SelectionContainer内聚合文本的拼接方式。未通过该接口设置时，默认为SelectionContainerTextJoinStyle.NEWLINE，表示不同文本节点之间使用换行符\n拼接。 > **说明：** > > - 该配置会影响[onWillCopy](#onWillCopy)、 > [onCopy](#onCopy)、 > [bindSelectionMenu](#bindSelectionMenu)相关回调中返回的文本内容。 > > - 该配置也会影响系统内置菜单项中依赖文本拼接结果的逻辑。例如，选择两个Text节点中的文本时，若配置为SelectionContainerTextJoinStyle.NEWLINE，执行复制后两段文本之间会插入换行符；若配置 > 为SelectionContainerTextJoinStyle.DIRECT，执行复制后两段文本会直接拼接。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SelectionContainerAttribute-textJoinStyle(style: Optional<SelectionContainerTextJoinStyle>): SelectionContainerAttribute--><!--Device-SelectionContainerAttribute-textJoinStyle(style: Optional<SelectionContainerTextJoinStyle>): SelectionContainerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | Optional&lt;[SelectionContainerTextJoinStyle](arkts-arkui-arkui-components-selectioncontainer-selectioncontainertextjoinstyle-e.md)&gt; | 是 | 聚合文本拼接方式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SelectionContainerAttribute](arkts-arkui-arkui-components-selectioncontainer-selectioncontainerattribute-c.md) | returns the instance of the SelectionContainerAttribute. |

