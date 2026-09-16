# PathShape

用于clipShape和maskShape接口的路径形状，继承自[CommonShapeMethod](arkts-arkui-arkui-shape-commonshapemethod-c.md)。

**继承/实现关系：** PathShape extends CommonShapeMethod<PathShape>

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { RectShape, CircleShape, EllipseShape, PathShape } from '@kit.ArkUI';
```

## commands

```TypeScript
commands(commands: string): PathShape
```

设置路径的绘制指令，用于定义PathShape的绘制路径。指令遵循SVG路径数据格式，具体支持的绘制命令请参考commands。

> **说明：** 
> 
> - 必须设置commands（可通过构造函数PathShapeOptions.commands或本方法设置），PathShape才能在clipShape/maskShape接口中产生可见的裁剪或遮罩效果。
> 
> - 未设置commands的PathShape为空路径，不会产生任何裁剪或遮罩效果。
> 
> - 本方法与构造函数PathShapeOptions.commands设置的是同一属性，后调用的设置会覆盖先前的设置。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| commands | string | 是 | 路径的绘制指令，格式要求请参考commands支持的绘制命令。传入无效指令时不产生可见路径。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PathShape](arkts-arkui-arkui-shape-pathshape-c.md) | 返回设置路径绘制指令后的PathShape对象，可用于链式调用继续配置路径形状。 |

## constructor

```TypeScript
constructor(options?: PathShapeOptions)
```

创建PathShape对象。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [PathShapeOptions](arkts-arkui-arkui-shape-pathshapeoptions-i.md) | 否 | 路径参数。不传入时，路径绘制指令默认为空字符串，不绘制路径。 |
