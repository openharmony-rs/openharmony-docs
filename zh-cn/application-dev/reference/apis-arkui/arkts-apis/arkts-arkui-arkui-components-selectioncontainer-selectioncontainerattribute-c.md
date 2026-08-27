# SelectionContainerAttribute

支持[通用属性](../arkts-components/arkts-arkui-commonmethod-c.md)。支持[通用事件](../arkts-components/arkts-arkui-commonmethod-c.md)。

> **说明：**
> 
> - 不支持隐私遮罩。
> 
> - 不支持图形变换，跨节点场景中Text子组件不支持图形变换。
> 
> - 不支持拖拽事件。

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
    responseType: Optional<TextResponseType>, options?: Optional<SelectionContainerMenuOptions>): SelectionContainerAttribute
```

绑定到选择菜单。<p>&lt;strong&gt;注意&lt;/strong&gt;： 长按手势需要的时间，bindSelectionMenu为600ms,bindContextMenu为800 ms。 当bindSelectionMenu和bindContextMenu都设置了，并且都设置为长按触发 手势， bindSelectionMenu首先被触发。 如果自定义菜单过长，可以嵌入一个Scroll组件，防止键盘被遮挡。 </p>

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| spanType | [Optional](../arkts-components/arkts-arkui-optional-t.md)&lt;[TextSpanType](../arkts-components/arkts-arkui-textspantype-e.md)&gt; | 是 | 选择菜单的类型。默认值为 TextSpanType.TEXT |
| content | [Optional](../arkts-components/arkts-arkui-optional-t.md)&lt;[CustomBuilder](../arkts-components/arkts-arkui-custombuilder-t.md)&gt; | 是 | 指示选择菜单的内容 |
| responseType | [Optional](../arkts-components/arkts-arkui-optional-t.md)&lt;[TextResponseType](../arkts-components/arkts-arkui-textresponsetype-e.md)&gt; | 是 | 选择菜单响应类型。默认值为 TextResponseType.LONG_press |
| options | [Optional](../arkts-components/arkts-arkui-optional-t.md)&lt;[SelectionContainerMenuOptions](arkts-arkui-arkui-components-selectioncontainer-selectioncontainermenuoptions-i.md)&gt; | 否 | 指示选择菜单的选项 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SelectionContainerAttribute](arkts-arkui-arkui-components-selectioncontainer-selectioncontainerattribute-c.md) | 返回SelectionContainerAttribute的实例。 |

## caretColor

```TypeScript
caretColor(color: Optional<ResourceColor>): SelectionContainerAttribute
```

设置选中文本手柄颜色。未通过该接口设置时，默认手柄颜色为'#007DFF'（蓝色）。

> **说明：**
> 
> - 该属性在跨节点场景中用于各Text子组件选中文本手柄颜色。
> 
> - 在跨节点场景中Text子组件caretColor设置无效，始终使用SelectionContainer的配置。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | [Optional](../arkts-components/arkts-arkui-optional-t.md)&lt;[ResourceColor](arkts-arkui-resourcecolor-t.md)&gt; | 是 | 手柄颜色。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SelectionContainerAttribute](arkts-arkui-arkui-components-selectioncontainer-selectioncontainerattribute-c.md) | returns the instance of the SelectionContainerAttribute. |

## copyOption

```TypeScript
copyOption(value: Optional<CopyOptions>): SelectionContainerAttribute
```

设置组件的复制粘贴配置项。未通过该接口设置时，默认为CopyOptions.InApp。

> **说明：**
> 
> Text子组件已显式设置copyOption时，优先使用Text子组件的配置；未设置时，使用SelectionContainer的配置。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Optional](../arkts-components/arkts-arkui-optional-t.md)&lt;CopyOptions&gt; | 是 | 复制粘贴配置项，用于设置文本的可复制范围。具体说明请参考CopyOptions枚举。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SelectionContainerAttribute](arkts-arkui-arkui-components-selectioncontainer-selectioncontainerattribute-c.md) | returns the instance of the SelectionContainerAttribute. |

## editMenuOptions

```TypeScript
editMenuOptions(editMenu: Optional<SelectionContainerEditMenuOptions>): SelectionContainerAttribute
```

设置选中文本后的编辑菜单选项，包括菜单文本、图标和回调等。

> **说明：**
> 
> 当同时为当前场景设置了[bindSelectionMenu](#bindselectionmenu)和editMenuOptions时，优先使用
> bindSelectionMenu，editMenuOptions不生效。bindSelectionMenu用于完全自定义菜单风格和触发条件，由开发者定义所有菜单项；editMenuOptions用于在系统默认菜单基础上添加扩
> 展项，触发条件不变。建议根据自定义程度需求选择。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| editMenu | [Optional](../arkts-components/arkts-arkui-optional-t.md)&lt;[SelectionContainerEditMenuOptions](arkts-arkui-arkui-components-selectioncontainer-selectioncontainereditmenuoptions-i.md)&gt; | 是 | 自定义编辑菜单配置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SelectionContainerAttribute](arkts-arkui-arkui-components-selectioncontainer-selectioncontainerattribute-c.md) | returns the instance of the SelectionContainerAttribute. |

## enableHapticFeedback

```TypeScript
enableHapticFeedback(isEnabled: Optional<boolean>): SelectionContainerAttribute
```

设置是否开启触控反馈。未通过该接口设置时，默认开启。开启触控反馈时，需要在工程的[module.json5配置文件](../../../quick-start/module-configuration-file.md)中配置requestPermissions字段开启振动权限，配 置如下：

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isEnabled | [Optional](../arkts-components/arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 是否开启触控反馈。 true表示开启触控反馈，false表示不开启触控反馈。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SelectionContainerAttribute](arkts-arkui-arkui-components-selectioncontainer-selectioncontainerattribute-c.md) | returns the instance of the SelectionContainerAttribute. |

## onCopy

```TypeScript
onCopy(callback: Optional<Callback<string>>): SelectionContainerAttribute
```

长按文本内部区域弹出选择菜单后，点击选择菜单的复制按钮，触发该回调。仅支持复制文本。使用callback异步回调。

> **说明：**
> 
> - 回调参数为按Text组件视觉顺序拼接后的选中文本，拼接方式由[textJoinStyle](#textjoinstyle)配置决定。
> 
> - 仅当容器级[onWillCopy](#onwillcopy)返回true时，该回调才会触发。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Optional](../arkts-components/arkts-arkui-optional-t.md)&lt;Callback&lt;string&gt;&gt; | 是 | 复制回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SelectionContainerAttribute](arkts-arkui-arkui-components-selectioncontainer-selectioncontainerattribute-c.md) | returns the instance of the SelectionContainerAttribute. |

## onTextSelectionChange

```TypeScript
onTextSelectionChange(callback: Optional<Callback<Array<string>>>): SelectionContainerAttribute
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

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Optional](../arkts-components/arkts-arkui-optional-t.md)&lt;Callback&lt;Array&lt;string&gt;&gt;&gt; | 是 | 选中文本变化回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SelectionContainerAttribute](arkts-arkui-arkui-components-selectioncontainer-selectioncontainerattribute-c.md) | returns the instance of the SelectionContainerAttribute. |

## onWillCopy

```TypeScript
onWillCopy(callback: Optional<Callback<string, boolean>>): SelectionContainerAttribute
```

在进行复制操作前，触发该回调。使用callback异步回调。

> **说明：**
> 
> - 回调参数为按Text组件视觉顺序拼接后的选中文本，拼接方式由[textJoinStyle](#textjoinstyle)配置决定。
> 
> - 返回false时，会阻止本次跨节点复制及容器级[onCopy](#oncopy)回调触发，但不会影响各Text子组件已独立处理完成的复制事件逻辑。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Optional](../arkts-components/arkts-arkui-optional-t.md)&lt;Callback&lt;string, boolean&gt;&gt; | 是 | 复制前检查回调，返回true表示允许复制，返回false表示不允许复制。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SelectionContainerAttribute](arkts-arkui-arkui-components-selectioncontainer-selectioncontainerattribute-c.md) | returns the instance of the SelectionContainerAttribute. |

## selectedBackgroundColor

```TypeScript
selectedBackgroundColor(color: Optional<ResourceColor>): SelectionContainerAttribute
```

设置选中文本底板颜色。未通过该接口设置时，默认选中文本底板颜色为'#007DFF'（蓝色），如果未设置不透明度，默认为20%不透明度。

> **说明：**
> 
> - 该属性在跨节点场景中用于各Text子组件选中区域的高亮颜色。
> 
> - Text子组件已显式设置selectedBackgroundColor时，优先使用Text子组件的配置；未设置时，使用
> SelectionContainer的配置。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | [Optional](../arkts-components/arkts-arkui-optional-t.md)&lt;[ResourceColor](arkts-arkui-resourcecolor-t.md)&gt; | 是 | 选中文本底板颜色。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SelectionContainerAttribute](arkts-arkui-arkui-components-selectioncontainer-selectioncontainerattribute-c.md) | returns the instance of the SelectionContainerAttribute. |

## textJoinStyle

```TypeScript
textJoinStyle(style: Optional<SelectionContainerTextJoinStyle>): SelectionContainerAttribute
```

设置SelectionContainer内聚合文本的拼接方式。未通过该接口设置时，默认为SelectionContainerTextJoinStyle.NEWLINE，表示不同文本节点之间使用换行符\n拼接。

> **说明：**
> 
> - 该配置会影响[onWillCopy](#onwillcopy)、
> [onCopy](#oncopy)、
> [bindSelectionMenu](#bindselectionmenu)相关回调中返回的文本内容。
> 
> - 该配置也会影响系统内置菜单项中依赖文本拼接结果的逻辑。例如，选择两个Text节点中的文本时，若配置为SelectionContainerTextJoinStyle.NEWLINE，执行复制后两段文本之间会插入换行符；若配置
> 为SelectionContainerTextJoinStyle.DIRECT，执行复制后两段文本会直接拼接。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [Optional](../arkts-components/arkts-arkui-optional-t.md)&lt;[SelectionContainerTextJoinStyle](arkts-arkui-arkui-components-selectioncontainer-selectioncontainertextjoinstyle-e.md)&gt; | 是 | 聚合文本拼接方式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SelectionContainerAttribute](arkts-arkui-arkui-components-selectioncontainer-selectioncontainerattribute-c.md) | returns the instance of the SelectionContainerAttribute. |
