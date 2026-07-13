# GesturePath

GesturePath表示手势路径信息。

本模块用于创建辅助功能注入手势所需的手势路径信息。

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## constructor

```TypeScript
constructor(durationTime: number)
```

构造函数。

**起始版本：** 9

**废弃版本：** 12

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| durationTime | number | 是 | 手势总耗时，单位为毫秒。 |

**示例：**

```TypeScript
import { GesturePath } from '@kit.AccessibilityKit';

let gesturePath = new GesturePath(20);

```

## durationTime

```TypeScript
durationTime: number
```

手势总耗时，单位为毫秒。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## points

```TypeScript
points: Array<GesturePoint>
```

手势触摸点。

**类型：** Array<GesturePoint>

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

