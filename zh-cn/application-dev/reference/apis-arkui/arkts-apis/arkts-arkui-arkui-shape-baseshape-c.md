# BaseShape

继承自[CommonShapeMethod](arkts-arkui-arkui-shape-commonshapemethod-c.md)。

**继承/实现关系：** BaseShape extends [CommonShapeMethod<T>](CommonShapeMethod<T>)

**起始版本：** 12

<!--Device-unnamed-declare class BaseShape<T> extends CommonShapeMethod<T>--><!--Device-unnamed-declare class BaseShape<T> extends CommonShapeMethod<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { RectShape, CircleShape, EllipseShape, PathShape } from '@kit.ArkUI';
```

<a id="height"></a>
## height

```TypeScript
height(height: Length): T
```

设置形状的高度。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-BaseShape-height(height: Length): T--><!--Device-BaseShape-height(height: Length): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| height | [Length](arkts-arkui-length-t.md) | 是 | 形状的高度。<br/>单位：vp<br/>取值为异常值时按照0vp处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前对象。 |

<a id="size"></a>
## size

```TypeScript
size(size: SizeOptions): T
```

设置形状的大小。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-BaseShape-size(size: SizeOptions): T--><!--Device-BaseShape-size(size: SizeOptions): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | [SizeOptions](arkts-arkui-sizeoptions-i.md) | 是 | 形状的大小。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前对象。 |

<a id="width"></a>
## width

```TypeScript
width(width: Length): T
```

设置形状的宽度。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-BaseShape-width(width: Length): T--><!--Device-BaseShape-width(width: Length): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| width | [Length](arkts-arkui-length-t.md) | 是 | 形状的宽度。<br/>单位：vp<br/>取值为异常值时按照0vp处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前对象。 |

