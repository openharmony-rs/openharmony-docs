# ToolBar

工具栏组件，用于展示针对当前界面内容的操作选项，在界面底部显示。适用于需要为用户提供快捷操作入口的场景，如编辑页面的复制、粘贴、分享等操作。底部最多显示5个入口，超过则收纳入“更多”子项中，在最右侧显示。

> **说明：**
> 
> - 该组件仅可在Stage模型下使用。
> 
> - 如果ToolBar设置通用属性和通用事件，编译工具链会额外
> 生成节点__Common__，并将通用属性或通用事件挂载在__Common__上，而不是直接应用到ToolBar本身。这可能导致开发者设置的通用属性或通用事件不生效或不符合预期，因此，不建议ToolBar设置通用属性和通用事件。

**起始版本：** 10

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { ItemState, ToolBar, ToolBarOption, ToolBarOptions, ToolBarModifier } from '@kit.ArkUI';
```

## activateIndex

```TypeScript
activateIndex?: number
```

激活态的子项索引。默认值：-1，表示没有激活态的子项。设置小于-1的值时按没有激活项处理。

**类型：** number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## controller

```TypeScript
controller: TabsController
```

工具栏控制器，用于关联Tabs组件页面切换，不支持控制工具栏子项。  
**说明：**根据自定义组件成员属性访问限定符[使用限制](../../../ui/state-management/arkts-custom-components-access-restrictions.md#使用限制)，该接口属于常规成员 变量，可以传参进行初始化；也可以不传。不传时，使用组件内预设值进行初始化，组件内预设值为：new TabsController()。

**类型：** [TabsController](../arkts-components/arkts-arkui-tabscontroller-c.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## dividerModifier

```TypeScript
dividerModifier?: DividerModifier
```

工具栏头部分割线属性，可设置分割线高度、颜色等。默认值：系统默认值。

**类型：** DividerModifier

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## toolBarList

```TypeScript
toolBarList: ToolBarOptions
```

工具栏列表。

**类型：** [ToolBarOptions](arkts-arkui-arkui-advanced-toolbar-toolbaroptions-c.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## toolBarModifier

```TypeScript
toolBarModifier?: ToolBarModifier
```

工具栏属性，可设置工具栏高度、背景色、内边距（仅在工具栏子项数量小于5时生效）、是否显示按压态。默认值：工具栏高度：56vp背景色：ohos_id_toolbar_bg内边距：24vp显示按压态。

**类型：** [ToolBarModifier](arkts-arkui-arkui-advanced-toolbar-toolbarmodifier-c.md)

**起始版本：** 13

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本13开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
