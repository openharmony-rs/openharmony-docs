# EditorMenuOptions

编辑菜单选项。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { EditorEventInfo, EditorMenuOptions, ExpandedMenuOptions, SelectionMenu, SelectionMenuOptions } from '@kit.ArkUI';
```

## action

```TypeScript
action?: () => void
```

点击菜单项的事件回调。同时配置builder和action时，点击图标会同时响应。不设置时点击无响应。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## builder

```TypeScript
builder?: () => void
```

点击时显示用户自定义组件，自定义组件在构造时结合@Builder使用。不设置时不显示自定义组件。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon: ResourceStr
```

编辑菜单项的图标资源。若同时设置symbolStyle，则本属性不生效。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## symbolStyle

```TypeScript
symbolStyle?: SymbolGlyphModifier
```

Symbol图标资源。当需要使用系统Symbol图标（支持动态颜色、多色等高级特性）时传入此参数，不传入时使用icon属性指定的图标资源。优先级大于icon，同时设置时优先使用symbolStyle。

**类型：** SymbolGlyphModifier

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
