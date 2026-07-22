# GesturePath

GesturePath表示手势路径信息。

本模块用于创建辅助功能注入手势所需的手势路径信息。

**起始版本：** 9

<!--Device-unnamed-export declare class GesturePath--><!--Device-unnamed-export declare class GesturePath-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## 导入模块

```TypeScript
import { GesturePath } from '@kit.AccessibilityKit';
```

## constructor

```TypeScript
constructor(durationTime: number)
```

构造函数。

**起始版本：** 9

**废弃版本：** 12

<!--Device-GesturePath-constructor(durationTime: long)--><!--Device-GesturePath-constructor(durationTime: long)-End-->

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

<!--Device-GesturePath-durationTime: long--><!--Device-GesturePath-durationTime: long-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## points

```TypeScript
points: Array<GesturePoint>
```

手势触摸点。

**类型：** Array&lt;GesturePoint&gt;

**起始版本：** 9

<!--Device-GesturePath-points: Array<GesturePoint>--><!--Device-GesturePath-points: Array<GesturePoint>-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

