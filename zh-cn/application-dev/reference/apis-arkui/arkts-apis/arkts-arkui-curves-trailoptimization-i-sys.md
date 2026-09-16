# TrailOptimization（系统接口）

弹簧动画尾迹优化配置。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { curves } from '@kit.ArkUI';
```

## progressThreshold

```TypeScript
progressThreshold?: number
```

动画进度阈值。

取值范围：[0, 1]

默认值：1

**类型：** number

**默认值：** 1

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## responseDecayFactor

```TypeScript
responseDecayFactor?: number
```

自然振动周期衰减因子。

取值范围：(0, 1]

默认值：1

**类型：** number

**默认值：** 1

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。
