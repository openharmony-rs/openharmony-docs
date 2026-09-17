# GesturePoint

表示手势触摸点，是构成GesturePath路径节点的基本单元，用于定义辅助功能注入手势轨迹中的触摸位置。详细使用方式请参见[GesturePath](arkts-accessibility-accessibility-gesturepath-gesturepath-c.md)。

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## 导入模块

```TypeScript
import { GesturePoint } from '@kit.AccessibilityKit';
```

## constructor

```TypeScript
constructor(positionX: number, positionY: number)
```

根据传入的X坐标和Y坐标创建GesturePoint实例。

**起始版本：** 9

**废弃版本：** 12

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| positionX | number | 是 | 触摸点X坐标，单位为像素（px）。 |
| positionY | number | 是 | 触摸点Y坐标，单位为像素（px）。 |

**示例**

```TypeScript
import { GesturePoint } from '@kit.AccessibilityKit';

let gesturePoint = new GesturePoint(1, 2);
```

## positionX

```TypeScript
positionX: number
```

触摸点X坐标，单位为像素（px）。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## positionY

```TypeScript
positionY: number
```

触摸点Y坐标，单位为像素（px）。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core
