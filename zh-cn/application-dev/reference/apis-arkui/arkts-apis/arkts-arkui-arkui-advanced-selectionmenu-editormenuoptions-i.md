# EditorMenuOptions

编辑菜单选项。

**起始版本：** 11

<!--Device-unnamed-export interface EditorMenuOptions--><!--Device-unnamed-export interface EditorMenuOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { EditorMenuOptions, SelectionMenuOptions, EditorEventInfo, SelectionMenu, ExpandedMenuOptions } from '@kit.ArkUI';
```

## action

```TypeScript
action?: () => void
```

点击菜单项的事件回调。

**类型：** () => void

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-EditorMenuOptions-action?: () => void--><!--Device-EditorMenuOptions-action?: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## builder

```TypeScript
builder?: () => void
```

点击时显示用户自定义组件，自定义组件在构造时结合@Builder使用。

**类型：** () => void

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-EditorMenuOptions-builder?: () => void--><!--Device-EditorMenuOptions-builder?: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon: ResourceStr
```

图标资源。

**类型：** ResourceStr

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-EditorMenuOptions-icon: ResourceStr--><!--Device-EditorMenuOptions-icon: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## symbolStyle

```TypeScript
symbolStyle?: SymbolGlyphModifier
```

Symbol图标资源，优先级大于icon。

**类型：** SymbolGlyphModifier

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-EditorMenuOptions-symbolStyle?: SymbolGlyphModifier--><!--Device-EditorMenuOptions-symbolStyle?: SymbolGlyphModifier-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

