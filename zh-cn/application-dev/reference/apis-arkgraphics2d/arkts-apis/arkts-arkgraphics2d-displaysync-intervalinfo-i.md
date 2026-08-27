# IntervalInfo

开发者可以从回调函数中获取帧绘制的时间戳信息，包含当前帧到达的时间timestamp和下一帧预期到达的时间targetTimestamp。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { displaySync } from '@kit.ArkGraphics2D';
```

## targetTimestamp

```TypeScript
targetTimestamp: number
```

下一帧预期到达的时间（单位：纳秒）。系统启动以来的单调递增时间，值应大于timestamp。

**类型：** number

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## timestamp

```TypeScript
timestamp: number
```

当前帧到达的时间（单位：纳秒）。系统启动以来的单调递增时间。

**类型：** number

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
