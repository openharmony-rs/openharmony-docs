# SmartRotateEvent（系统接口）

智能旋转传感器事件的基本数据结构。该事件包含传感器检测到的物理方向和由智能算法计算得出的逻辑方向。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.MultimodalAwareness.Motion

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { motion } from '@kit.MultimodalAwarenessKit';
```

## logicalOrientation

```TypeScript
logicalOrientation?: LogicalOrientation
```

智能算法调整后的逻辑方向。当智能算法无法确定方向时，该字段可能为空或不返回。

**类型：** [LogicalOrientation](arkts-multimodalawareness-motion-logicalorientation-e-sys.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.MultimodalAwareness.Motion

**系统接口：** 此接口为系统接口。

## physicalOrientation

```TypeScript
physicalOrientation: PhysicalOrientation
```

重力传感器报告的物理方向。

**类型：** [PhysicalOrientation](arkts-multimodalawareness-motion-physicalorientation-e-sys.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.MultimodalAwareness.Motion

**系统接口：** 此接口为系统接口。
