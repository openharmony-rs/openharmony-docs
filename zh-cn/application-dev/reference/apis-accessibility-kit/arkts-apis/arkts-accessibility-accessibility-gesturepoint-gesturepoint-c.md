# GesturePoint

GesturePoint表示手势触摸点。 本模块用于创建辅助功能注入手势所需的手势路径的触摸点信息。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

<!--Device-unnamed-export declare class GesturePoint--><!--Device-unnamed-export declare class GesturePoint-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## constructor

```TypeScript
constructor(positionX: double, positionY: double)
```

构造函数。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 12

<!--Device-GesturePoint-constructor(positionX: double, positionY: double)--><!--Device-GesturePoint-constructor(positionX: double, positionY: double)-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| positionX | double | 是 | 触摸点X坐标，单位为像素（px）。 |
| positionY | double | 是 | 触摸点Y坐标，单位为像素（px）。 |

## 示例

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

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

<!--Device-GesturePoint-positionX: double--><!--Device-GesturePoint-positionX: double-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

## positionY

```TypeScript
positionY: double
```

触摸点Y坐标，单位为像素（px）。

**类型：** double

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

<!--Device-GesturePoint-positionY: double--><!--Device-GesturePoint-positionY: double-End-->

**系统能力：** SystemCapability.BarrierFree.Accessibility.Core

