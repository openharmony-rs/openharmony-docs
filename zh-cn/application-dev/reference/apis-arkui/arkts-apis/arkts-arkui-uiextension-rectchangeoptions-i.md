# RectChangeOptions

组件（EmbeddedComponent或UIExtensionComponent）矩形（位置及尺寸）变化返回的值及变化原因。

**起始版本：** 14

<!--Device-uiExtension-interface RectChangeOptions--><!--Device-uiExtension-interface RectChangeOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { uiExtension } from '@kit.ArkUI';
```

## reason

```TypeScript
reason: RectChangeReason
```

组件矩形变化的原因。

**类型：** RectChangeReason

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-RectChangeOptions-reason: RectChangeReason--><!--Device-RectChangeOptions-reason: RectChangeReason-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## rect

```TypeScript
rect: window.Rect
```

组件矩形变化后的值。

**类型：** window.Rect

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-RectChangeOptions-rect: window.Rect--><!--Device-RectChangeOptions-rect: window.Rect-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

