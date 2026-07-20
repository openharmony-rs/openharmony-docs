# OnPrepareMenuCallback

```TypeScript
type OnPrepareMenuCallback = (menuItems: Array<TextMenuItem>) => Array<TextMenuItem>
```

当文本选择区域变化后显示菜单之前触发该回调，可在该回调中进行菜单数据设置。入参和返回值只包含一级菜单项，不包含二级菜单项。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-type OnPrepareMenuCallback = (menuItems: Array<TextMenuItem>) => Array<TextMenuItem>--><!--Device-unnamed-type OnPrepareMenuCallback = (menuItems: Array<TextMenuItem>) => Array<TextMenuItem>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| menuItems | Array&lt;TextMenuItem&gt; | 是 | 将要显示的菜单项。<br/>**说明：** <br/>对默认菜单项的名称、图标、快捷键提示修改不生效。  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;TextMenuItem&gt; | 处理后的菜单项。  |

