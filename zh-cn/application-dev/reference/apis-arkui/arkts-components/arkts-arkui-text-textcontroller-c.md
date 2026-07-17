# TextController

Text组件的控制器。

**起始版本：** 11

<!--Device-unnamed-declare class TextController--><!--Device-unnamed-declare class TextController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## closeSelectionMenu

```TypeScript
closeSelectionMenu(): void
```

关闭自定义选择菜单或系统默认选择菜单。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextController-closeSelectionMenu(): void--><!--Device-TextController-closeSelectionMenu(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## getLayoutManager

```TypeScript
getLayoutManager(): LayoutManager
```

获取布局管理器对象。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextController-getLayoutManager(): LayoutManager--><!--Device-TextController-getLayoutManager(): LayoutManager-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LayoutManager](../arkts-apis/arkts-arkui-text-common-layoutmanager-i.md) | 布局管理器对象。 |

## setStyledString

```TypeScript
setStyledString(value: StyledString): void
```

触发绑定或更新属性字符串。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextController-setStyledString(value: StyledString): void--><!--Device-TextController-setStyledString(value: StyledString): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [StyledString](../arkts-apis/arkts-arkui-styled-string-styledstring-c.md) | 是 | 属性字符串。<br/>**说明：** <br/>StyledString的子类[MutableStyledString](../arkts-apis/arkts-arkui-styled-string-mutablestyledstring-c.md)也可以作为入参值。 |

## setTextSelection

```TypeScript
setTextSelection(selectionStart: number | undefined, selectionEnd: number | undefined,
                   options?: SelectionOptions): void
```

设置文本选择区域并高亮显示。

> **说明：**  
>  
> 当[copyOption](TextAttribute#copyOption)设置为CopyOptions.None时，设置setTextSelection不生效。  
>  
> 当[textOverflow](TextAttribute#textOverflow)设置为TextOverflow.MARQUEE时，设置setTextSelection不生效。  
>  
> 当selectionStart大于等于selectionEnd时不选中。可选范围为[0, textSize]，其中textSize为文本内容最大字符数，入参小于0时处理为0，大于textSize时处理为textSize。  
>  
> 当selectionStart或selectionEnd位于截断的不可见区域时，文本不选中。截断为false时，超出父组件的文本选中区域生效。  
>  
> 如果设备为PC/2in1，即使options被赋值为MenuPolicy.SHOW，调用setTextSelection也不弹出菜单。  
>  
> 当emoji表情被选中区域截断时，若表情的起始位置包含在设置的文本选中区域内，该表情就会被选中。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-TextController-setTextSelection(selectionStart: number | undefined, selectionEnd: number | undefined,
                   options?: SelectionOptions): void--><!--Device-TextController-setTextSelection(selectionStart: number | undefined, selectionEnd: number | undefined,
                   options?: SelectionOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| selectionStart | number \| undefined | 是 | 文本选择区域起始位置。<br />取值范围：[0, +∞），值为负数或undefined时按0处理。 |
| selectionEnd | number \| undefined | 是 | 文本选择区域结束位置。<br />取值范围：[0, +∞），值为负数或undefined时按0处理。 |
| options | [SelectionOptions](arkts-arkui-common-selectionoptions-i.md) | 否 | 选中文字时的配置。<br />默认值：SelectionOptions中MenuPolicy.DEFAULT |

