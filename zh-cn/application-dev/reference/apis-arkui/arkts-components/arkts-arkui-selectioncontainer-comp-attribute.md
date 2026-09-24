# SelectionContainer属性/事件

```TypeScript
export declare class SelectionContainerAttribute extends CommonMethod<SelectionContainerAttribute>
```

支持[通用属性](arkts-arkui-common-comp.md#common)。

> **说明：** 
> 
> - 不支持[隐私遮罩](arkts-arkui-common-comp.md#common)。
> 
> - 不支持[图形变换](arkts-arkui-common-comp.md#common)，在SelectionContainer容器中子组件Text不支持图形变换。

**继承/实现关系：** SelectionContainerAttribute extends CommonMethod<SelectionContainerAttribute>

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { OnMenuItemClickWithTextCallback, SelectionContainer, SelectionContainerAttribute, SelectionContainerEditMenuOptions, SelectionContainerInstance, SelectionContainerMenuOptions, SelectionContainerTextJoinStyle, SelectionContainerOptions, SelectionContainerController } from '@kit.ArkUI';
```

## bindSelectionMenu

```TypeScript
bindSelectionMenu(spanType: Optional<TextSpanType>, content: Optional<CustomBuilder>,
    responseType: Optional<TextResponseType>, options?: Optional<SelectionContainerMenuOptions>)
```

设置自定义选择菜单。未通过该接口设置时，默认spanType为TextSpanType.TEXT，responseType为TextResponseType.LONG_PRESS。

> **说明：** 
> 
> - bindSelectionMenu的长按响应时长为600ms，[bindContextMenu](arkts-arkui-common-comp-commonmethod-c.md#bindcontextmenu)的长按响应时长为800ms，当两者同时绑定且触发方式均为长按时，优先响应bindSelectionMenu。
> 
> - 自定义菜单过长时，建议内部嵌套使用[Scroll](arkts-arkui-scroll-comp.md#scroll)组件，避免键盘被遮挡。
> 
> - 选区跨越不可复制Text时，菜单仅基于实际选中的可复制文本进行显示和处理。
> 
> - 在SelectionContainer容器中子组件Text的[bindSelectionMenu](arkts-arkui-text-comp-attribute.md#bindselectionmenu)设置无效，始终使用SelectionContainer的配置。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| spanType | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[TextSpanType](arkts-arkui-text-comp-textspantype-e.md)&gt; | 是 | 选择菜单类型。用于指定选择菜单作用的文本类型范围，不同类型对应不同的菜单行为。各枚举值的含义及适用场景详见[TextSpanType](arkts-arkui-text-comp-textspantype-e.md)。 |
| content | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md)&gt; | 是 | 选择菜单内容。 |
| responseType | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[TextResponseType](arkts-arkui-text-comp-textresponsetype-e.md)&gt; | 是 | 选择菜单响应类型。 |
| options | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[SelectionContainerMenuOptions](arkts-arkui-selectioncontainer-comp-selectioncontainermenuoptions-i.md)&gt; | 否 | 选择菜单选项，用于配置菜单出现、消失、显示、隐藏等事件的回调。当需要监听这些菜单事件时传入此参数，不传入时默认不监听菜单事件。 |

## caretColor

```TypeScript
caretColor(color: Optional<ResourceColor>)
```

设置选中文本手柄颜色。未通过该接口设置时，默认手柄颜色为'#007DFF'（蓝色）。

> **说明：** 
> 
> - 该属性在SelectionContainer容器上用于控制各子组件Text选中文本手柄颜色。
> 
> - 在SelectionContainer容器中子组件Text的[caretColor](arkts-arkui-text-comp-attribute.md#caretcolor)设置无效，始终使用SelectionContainer的配置。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)&gt; | 是 | 手柄颜色。 |

## copyOption

```TypeScript
copyOption(value: Optional<CopyOptions>)
```

设置组件的复制粘贴配置项。未通过该接口设置时，默认为CopyOptions.InApp。

> **说明：** 
> 
> Text子组件已显式设置[copyOption](arkts-arkui-text-comp-attribute.md#copyoption)时，优先使用Text子组件的配置；未设置时，使用SelectionContainer的配置。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[CopyOptions](../arkts-apis/arkts-arkui-copyoptions-e.md)&gt; | 是 | 复制粘贴配置项，用于设置文本的可复制范围。具体说明请参考CopyOptions枚举。 |

## editMenuOptions

```TypeScript
editMenuOptions(editMenu: Optional<SelectionContainerEditMenuOptions>)
```

设置选中文本后的编辑菜单选项，包括菜单文本、图标和回调等。

> **说明：** 
> 
> - 当同时为当前场景设置了[bindSelectionMenu](#bindselectionmenu)和editMenuOptions时，优先使用bindSelectionMenu，editMenuOptions不生效。bindSelectionMenu用于完全自定义菜单风格和触发条件，由开发者定义所有菜单项；editMenuOptions用于在系统默认菜单基础上添加扩展项，触发条件不变。建议根据自定义程度需求选择。
> 
> - 在SelectionContainer容器中子组件Text的[editMenuOptions](arkts-arkui-text-comp-attribute.md#editmenuoptions)设置无效，始终使用SelectionContainer 的配置。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| editMenu | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[SelectionContainerEditMenuOptions](arkts-arkui-selectioncontainer-comp-selectioncontainereditmenuoptions-i.md)&gt; | 是 | 自定义编辑菜单配置。 |

## enableHapticFeedback

```TypeScript
enableHapticFeedback(isEnabled: Optional<boolean>)
```

设置是否开启触控反馈。未通过该接口设置时，默认开启。

开启触控反馈时，需要在工程的[module.json5配置文件](../../../quick-start/module-configuration-file.md)中配置requestPermissions字段开启振动权限，配置如下：

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isEnabled | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | 是 | 是否开启触控反馈。<br>true表示开启触控反馈，false表示不开启触控反馈。 |

## onCopy

```TypeScript
onCopy(callback: Optional<Callback<string>>)
```

长按文本内部区域弹出选择菜单后，点击选择菜单的复制按钮，触发该回调。仅支持复制文本。使用callback异步回调。

> **说明：** 
> 
> - 回调参数为按Text组件视觉顺序拼接后的选中文本，拼接方式由[textJoinStyle](#textjoinstyle)配置决定。
> 
> - 仅当容器级[onWillCopy](#onwillcopy)返回true时，该回调才会触发。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;Callback&lt;string&gt;&gt; | 是 | 复制回调。 |

## onTextSelectionChange

```TypeScript
onTextSelectionChange(callback: Optional<Callback<Array<string>>>)
```

SelectionContainer中选中文本发生变化时触发该回调。使用callback异步回调。

> **说明：** 
> 
> - 回调参数数组中各项顺序与Text组件视觉顺序一致。
> 
> - 数组中的每一项对应一个Text子组件的选中文本。
> 
> - 仅包含有选中文本的Text子组件，不包含未选中Text子组件，也不包含不可复制Text的空字符串占位。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;Callback&lt;Array&lt;string&gt;&gt;&gt; | 是 | 选中文本变化回调。 |

## onWillCopy

```TypeScript
onWillCopy(callback: Optional<Callback<string, boolean>>)
```

在进行复制操作前，触发该回调。使用callback异步回调。

> **说明：** 
> 
> - 回调参数为按Text组件视觉顺序拼接后的选中文本，拼接方式由[textJoinStyle](#textjoinstyle)配置决定。
> 
> - 返回false时，会阻止本次跨节点复制及容器级[onCopy](#oncopy)回调触发，但不会影响各Text子组件已独立处理完成的复制事件逻辑。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;Callback&lt;string, boolean&gt;&gt; | 是 | 复制前检查回调，返回true表示允许复制，返回false表示不允许复制。 |

## selectedBackgroundColor

```TypeScript
selectedBackgroundColor(color: Optional<ResourceColor>)
```

设置文本选中高亮颜色。未通过该接口设置时，默认文本选中高亮颜色为'#007DFF'（蓝色），如果未设置不透明度或设置为完全不透明，默认使用20%不透明度。

> **说明：** 
> 
> - 该属性在SelectionContainer容器上用于控制各子组件Text选中区域的高亮颜色。
> 
> - Text子组件已显式设置[selectedBackgroundColor](arkts-arkui-text-comp-attribute.md#selectedbackgroundcolor)时，优先使用Text子组件的配置；未设置时，使用SelectionContainer的配置。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)&gt; | 是 | 文本选中高亮颜色。 |

## textJoinStyle

```TypeScript
textJoinStyle(style: Optional<SelectionContainerTextJoinStyle>)
```

设置SelectionContainer内聚合文本的拼接方式。未通过该接口设置时，默认为SelectionContainerTextJoinStyle.NEWLINE，表示不同文本节点之间使用换行符\n拼接。

> **说明：** 
> 
> - 该配置会影响[onWillCopy](#onwillcopy)、[onCopy](#oncopy)、[bindSelectionMenu](#bindselectionmenu)相关回调中返回的文本内容。
> 
> - 该配置也会影响系统内置菜单项中依赖文本拼接结果的逻辑。例如，选择两个Text节点中的文本时，若配置为SelectionContainerTextJoinStyle.NEWLINE，执行复制后两段文本之间会插入换行符；若配置为SelectionContainerTextJoinStyle.DIRECT，执行复制后两段文本会直接拼接。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[SelectionContainerTextJoinStyle](arkts-arkui-selectioncontainer-comp-selectioncontainertextjoinstyle-e.md)&gt; | 是 | 聚合文本拼接方式。 |
