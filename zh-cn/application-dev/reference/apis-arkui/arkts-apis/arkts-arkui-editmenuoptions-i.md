# EditMenuOptions

编辑菜单选项

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## onCreateMenu

```TypeScript
onCreateMenu(menuItems: Array<TextMenuItem>): Array<TextMenuItem>
```

在菜单创建时触发该回调，可在该回调中进行菜单数据设置。入参和返回值只包含一级菜单项，不包含二级菜单项。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| menuItems | Array&lt;[TextMenuItem](arkts-arkui-textmenuitem-i.md)&gt; | 是 | 将要显示的菜单项。    **说明：** 对默认菜单项的名称、图标、快捷键提示修改不生效。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;[TextMenuItem](arkts-arkui-textmenuitem-i.md)&gt; | 处理后的菜单项。 |

## onMenuItemClick

```TypeScript
onMenuItemClick(menuItem: TextMenuItem, range: TextRange): boolean
```

在菜单项被点击时触发该回调，用于处理菜单项的点击行为。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| menuItem | [TextMenuItem](arkts-arkui-textmenuitem-i.md) | 是 | 菜单项。    **说明：** 从API version 23开始，对于具备可展开二级菜单能力的一级菜单项，例如自动填充，仅执行系统默认逻辑，不会执行用户自定义逻辑。 |
| range | [TextRange](arkts-arkui-textrange-i.md) | 是 | 选中的文本信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 菜单项的执行逻辑。 |

## onPrepareMenu

```TypeScript
onPrepareMenu?: OnPrepareMenuCallback
```

当文本选择区域变化后显示菜单之前触发该回调，可在该回调中进行菜单数据设置。与[onCreateMenu](#oncreatemenu)功能相似但触发时机不同：onCreateMenu在菜单创建时触发，适用于初始化菜单项；本接口在每次选择区域变化后、菜单显示前触 发，适用于根据选择内容动态调整菜单。两者可同时使用。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
