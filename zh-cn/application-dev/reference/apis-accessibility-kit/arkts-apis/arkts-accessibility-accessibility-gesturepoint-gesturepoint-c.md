# GesturePoint(手势触摸点)

GesturePoint表示手势触摸点，是构成手势路径GesturePath的基本单元。 本模块用于创建手势路径的触摸点信息，供辅助功能注入手势使用。

**起始版本：** 9

<!--Device-unnamed-export declare class GesturePoint--><!--Device-unnamed-export declare class GesturePoint-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## 导入模块

```TypeScript
import { GesturePoint } from '@kit.AccessibilityKit';
```

## constructor

```TypeScript
constructor(positionX: double, positionY: double)
```

根据传入的X坐标和Y坐标创建GesturePoint实例。

**起始版本：** 9

**废弃版本：** 12

<!--Device-GesturePoint-constructor(positionX: double, positionY: double)--><!--Device-GesturePoint-constructor(positionX: double, positionY: double)-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| positionX | double | 是 | 触摸点X坐标，单位为像素（px）。 |
| positionY | double | 是 | 触摸点Y坐标，单位为像素（px）。 |

**示例**

```TypeScript
import { GesturePoint } from '@kit.AccessibilityKit';

let gesturePoint = new GesturePoint(1, 2);
```

## positionX

```TypeScript
positionX: double
```

触摸点X坐标，单位为像素（px）。

**类型：** double

**起始版本：** 9

<!--Device-GesturePoint-positionX: double--><!--Device-GesturePoint-positionX: double-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## positionY

```TypeScript
positionY: double
```

触摸点Y坐标，单位为像素（px）。

**类型：** double

**起始版本：** 9

<!--Device-GesturePoint-positionY: double--><!--Device-GesturePoint-positionY: double-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

