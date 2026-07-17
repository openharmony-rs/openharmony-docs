# OnCreateMenuCallback

```TypeScript
type OnCreateMenuCallback = (menuItems: Array<TextMenuItem>) => Array<TextMenuItem>
```

菜单创建时触发。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-type OnCreateMenuCallback = (menuItems: Array<TextMenuItem>) => Array<TextMenuItem>--><!--Device-unnamed-type OnCreateMenuCallback = (menuItems: Array<TextMenuItem>) => Array<TextMenuItem>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| menuItems | Array&lt;TextMenuItem&gt; | 是 | 当前显示的菜单项。<br/>**说明：**<br/>对默认菜单项的名称、图标、快捷键提示修改不生效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;TextMenuItem&gt; | 处理后的菜单项。 |

