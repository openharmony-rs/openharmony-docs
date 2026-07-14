# GesturePoint

GesturePoint表示手势触摸点。

本模块用于创建辅助功能注入手势所需的手势路径的触摸点信息。

**起始版本：** 9

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## constructor

```TypeScript
constructor(positionX: number, positionY: number)
```

构造函数。

**起始版本：** 9

**废弃版本：** 12

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| positionX | number | 是 | 触摸点X坐标，单位为像素（px）。 |
| positionY | number | 是 | 触摸点Y坐标，单位为像素（px）。 |

**示例：**

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

