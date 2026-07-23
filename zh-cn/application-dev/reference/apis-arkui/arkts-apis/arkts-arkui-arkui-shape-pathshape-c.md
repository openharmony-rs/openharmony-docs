# PathShape

用于clipShape和maskShape接口的路径。

继承自[CommonShapeMethod](arkts-arkui-arkui-shape-commonshapemethod-c.md)。

**继承/实现关系：** PathShape extends [CommonShapeMethod<PathShape>]

**起始版本：** 12

<!--Device-unnamed-export declare class PathShape extends CommonShapeMethod<PathShape>--><!--Device-unnamed-export declare class PathShape extends CommonShapeMethod<PathShape>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { RectShape, CircleShape, EllipseShape, PathShape } from '@kit.ArkUI';
```

## commands

```TypeScript
commands(commands: string): PathShape
```

设置路径的绘制指令。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-PathShape-commands(commands: string): PathShape--><!--Device-PathShape-commands(commands: string): PathShape-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| commands | string | 是 | 路径的绘制指令。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PathShape](arkts-arkui-arkui-shape-pathshape-c.md) | 返回PathShape对象。 |

## constructor

```TypeScript
constructor(options?: PathShapeOptions)
```

创建PathShape对象。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-PathShape-constructor(options?: PathShapeOptions)--><!--Device-PathShape-constructor(options?: PathShapeOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [PathShapeOptions](arkts-arkui-arkui-shape-pathshapeoptions-i.md) | 否 | 路径参数。 |

