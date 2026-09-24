# ActionMenuSuccessResponse

```TypeScript
interface ActionMenuSuccessResponse
```

操作菜单的响应结果。

**起始版本：** 9

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { promptAction, LevelMode, ImmersiveMode, LevelOrder } from '@kit.ArkUI';
```

## index

```TypeScript
index: number
```

选中按钮在buttons数组中的索引，从0开始，可用于判断用户点击了哪个按钮。

**类型：** number

**起始版本：** 9

**模型约束：** 此接口可在Stage模型和FA模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
