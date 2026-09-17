# GesturePath

表示手势路径信息，用于无障碍服务中模拟用户触摸手势（如点击、滑动等）。

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## 导入模块

```TypeScript
import { GesturePath } from '@kit.AccessibilityKit';
```

## constructor

```TypeScript
constructor(durationTime: number)
```

通过传入手势总耗时创建手势路径对象。创建GesturePath实例后，还需设置必填属性points。

**起始版本：** 9

**废弃版本：** 12

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| durationTime | number | 是 | 手势总耗时，单位：ms。取值需大于0。 |

**示例**

```TypeScript
import { GesturePath, GesturePoint } from '@kit.AccessibilityKit';

let gesturePath = new GesturePath(20);
let startPoint = new GesturePoint(100, 100);
let endPoint = new GesturePoint(200, 200);
gesturePath.points = [startPoint, endPoint];
```

## durationTime

```TypeScript
durationTime: number
```

手势总耗时，单位：ms。取值需大于0。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## points

```TypeScript
points: Array<GesturePoint>
```

手势路径上的触摸点序列，用于构成手势的移动轨迹。每个触摸点表示路径中的一个坐标位置。数组长度需大于0。

**类型：** Array&lt;[GesturePoint](arkts-accessibility-accessibility-gesturepoint-gesturepoint-c.md)&gt;

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core
