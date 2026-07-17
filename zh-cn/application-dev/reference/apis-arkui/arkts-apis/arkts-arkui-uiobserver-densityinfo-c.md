# DensityInfo

屏幕像素密度变化回调包含的信息。

**起始版本：** 12

<!--Device-uiObserver-export class DensityInfo--><!--Device-uiObserver-export class DensityInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { uiObserver } from '@kit.ArkUI';
```

## context

```TypeScript
context: UIContext
```

屏幕像素密度变化时页面对应的上下文信息。

**类型：** UIContext

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DensityInfo-context: UIContext--><!--Device-DensityInfo-context: UIContext-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## density

```TypeScript
density: number
```

变化后的屏幕像素密度。

取值范围：[0, +∞)

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DensityInfo-density: number--><!--Device-DensityInfo-density: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

