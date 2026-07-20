# TextBaseController

文本选择控制器。

**起始版本：** 12

<!--Device-unnamed-declare interface TextBaseController--><!--Device-unnamed-declare interface TextBaseController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="closeselectionmenu"></a>
## closeSelectionMenu

```TypeScript
closeSelectionMenu(): void
```

关闭自定义选择菜单或系统默认选择菜单。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextBaseController-closeSelectionMenu(): void--><!--Device-TextBaseController-closeSelectionMenu(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="getlayoutmanager"></a>
## getLayoutManager

```TypeScript
getLayoutManager(): LayoutManager
```

获取布局管理器对象。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextBaseController-getLayoutManager(): LayoutManager--><!--Device-TextBaseController-getLayoutManager(): LayoutManager-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [LayoutManager](arkts-arkui-layoutmanager-i.md) | 布局管理器对象。 |

<a id="setselection"></a>
## setSelection

```TypeScript
setSelection(selectionStart: number, selectionEnd: number, options?: SelectionOptions): void
```

支持设置组件内的内容选中，选中部分背板高亮。

selectionStart和selectionEnd均为-1时表示全选。

未获焦时调用该接口不产生选中效果。

从API version 12开始，在2in1设备中，无论options取何值，调用setSelection接口都不会弹出菜单，此外，如果组件中已经存在菜单，调用setSelection接口会关闭菜单。

在非2in1设备中，options取值为MenuPolicy.DEFAULT时，遵循以下规则：

1. 组件内有手柄菜单时，接口调用后不关闭菜单，并且调整菜单位置。2. 组件内有不带手柄的菜单时，接口调用后不关闭菜单，并且菜单位置不变。3. 组件内无菜单时，接口调用后也无菜单显示。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextBaseController-setSelection(selectionStart: number, selectionEnd: number, options?: SelectionOptions): void--><!--Device-TextBaseController-setSelection(selectionStart: number, selectionEnd: number, options?: SelectionOptions): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| selectionStart | number | 是 | 选中开始位置。<br/>取值小于0时，按0处理。 |
| selectionEnd | number | 是 | 选中结束位置。<br/>取值大于文本长度时，按当前文本长度处理。 |
| options | [SelectionOptions](../arkts-components/arkts-arkui-selectionoptions-i.md) | 否 | 选择项配置。 默认值继承[SelectionOptions](../arkts-components/arkts-arkui-selectionoptions-i.md)。 |

