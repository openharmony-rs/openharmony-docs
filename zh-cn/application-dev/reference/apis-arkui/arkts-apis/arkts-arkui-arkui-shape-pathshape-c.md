# PathShape

用于clipShape和maskShape接口的路径。 继承自[CommonShapeMethod](arkts-arkui-arkui-shape-commonshapemethod-c.md)。

**继承/实现关系：** PathShape extends [CommonShapeMethod](arkts-arkui-arkui-shape-commonshapemethod-c.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class PathShape--><!--Device-unnamed-export declare class PathShape-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { RectShape, CircleShape, EllipseShape, PathShape } from '@kit.ArkUI';
```

## commands

```TypeScript
commands(commands: string): this
```

设置路径的绘制指令。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PathShape-commands(commands: string): this--><!--Device-PathShape-commands(commands: string): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| commands | string | 是 | 路径的绘制指令。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | 返回PathShape对象。 |

## constructor

```TypeScript
constructor(options?: PathShapeOptions)
```

创建PathShape对象。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PathShape-constructor(options?: PathShapeOptions)--><!--Device-PathShape-constructor(options?: PathShapeOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [PathShapeOptions](arkts-arkui-arkui-shape-pathshapeoptions-i.md) | 否 | 路径参数。 |

