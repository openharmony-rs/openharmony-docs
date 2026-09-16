# BaseShape

继承自[CommonShapeMethod](arkts-arkui-arkui-shape-commonshapemethod-c.md)。

**继承/实现关系：** BaseShape extends CommonShapeMethod<T>

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { RectShape, CircleShape, EllipseShape, PathShape } from '@kit.ArkUI';
```

## height

```TypeScript
height(height: Length): T
```

设置形状的高度。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| height | [Length](arkts-arkui-length-t.md) | 是 | 形状的高度。<br>单位：vp <br>取值为异常值时按照0vp处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前对象，用于链式调用。 |

## size

```TypeScript
size(size: SizeOptions): T
```

设置形状的大小，同时设置宽度和高度。

> **说明：** 
> 
> - size()等同于同时调用width()和height()设置宽高。
> 
> - 后调用的方法会覆盖先前方法设置的对应属性。例如先调用size({width:100, height:200})再调用width(50)，最终宽度为50，高度保持200。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | [SizeOptions](arkts-arkui-sizeoptions-i.md) | 是 | 形状的大小。<br>width和height类型为number时取值范围是[0, +∞)，string类型时参考[Length](arkts-arkui-length-t.md)。<br>单位：vp <br>取值为异常值时按照0vp处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前对象，用于链式调用。 |

## width

```TypeScript
width(width: Length): T
```

设置形状的宽度。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| width | [Length](arkts-arkui-length-t.md) | 是 | 形状的宽度。<br>单位：vp <br>取值为异常值时按照0vp处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前对象，用于链式调用。 |
