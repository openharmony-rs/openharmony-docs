# PathShapeOptions

PathShape的构造函数参数。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { RectShape, CircleShape, EllipseShape, PathShape } from '@kit.ArkUI';
```

## commands

```TypeScript
commands?: string
```

绘制路径的指令。默认值为空字符串，不设置时不绘制路径。更多说明请参考commands支持的绘制命令。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
