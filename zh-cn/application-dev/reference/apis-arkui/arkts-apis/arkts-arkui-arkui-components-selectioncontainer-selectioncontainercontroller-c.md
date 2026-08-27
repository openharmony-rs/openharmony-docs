# SelectionContainerController

SelectionContainer组件的控制器。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { OnMenuItemClickWithTextCallback, SelectionContainer, SelectionContainerAttribute, SelectionContainerEditMenuOptions, SelectionContainerInstance, SelectionContainerMenuOptions, SelectionContainerTextJoinStyle, SelectionContainerOptions, SelectionContainerController } from '@kit.ArkUI';
```

## clearTextSelection

```TypeScript
clearTextSelection(): void
```

清除SelectionContainer当前的文本选中状态；若选择菜单正在显示，会同时关闭选择菜单。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## closeSelectionMenu

```TypeScript
closeSelectionMenu(): void
```

关闭SelectionContainer的自定义或默认选择菜单。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
