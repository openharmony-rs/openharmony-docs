# ReadingScreenPermissionStatus（系统接口）

读取屏幕信息的授权状态。

**起始版本：** 23

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { onScreen } from '@kit.MultimodalAwarenessKit';
```

## readingCode

```TypeScript
readingCode?: number
```

如果屏幕无法读取，将返回相应的状态码，参考[CollectStrategy](arkts-multimodalawareness-onscreen-collectstrategy-e-sys.md)。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## readingState

```TypeScript
readingState: number
```

表示是否允许读屏。

0：不允许读屏。

1：允许读屏。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。
