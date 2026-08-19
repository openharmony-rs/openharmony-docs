# BaseShape

继承自[CommonShapeMethod](arkts-arkui-arkui-shape-commonshapemethod-c.md)。

**继承/实现关系：** BaseShape extends [CommonShapeMethod](arkts-arkui-arkui-shape-commonshapemethod-c.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class BaseShape--><!--Device-unnamed-export declare class BaseShape-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { RectShape, CircleShape, EllipseShape, PathShape } from '@kit.ArkUI';
```

## height

```TypeScript
height(height: Length): this
```

设置形状的高度。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BaseShape-height(height: Length): this--><!--Device-BaseShape-height(height: Length): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| height | [Length](../../apis-na/arkts-apis/arkts-na-length-t.md) | 是 | 形状的高度。<br/>单位：vp<br/>取值为异常值时按照0vp处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | 返回当前对象。 |

## size

```TypeScript
size(size: SizeOptions): this
```

设置形状的大小。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BaseShape-size(size: SizeOptions): this--><!--Device-BaseShape-size(size: SizeOptions): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | [SizeOptions](../../apis-na/arkts-apis/arkts-na-units-sizeoptions-i.md) | 是 | 形状的大小。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | 返回当前对象。 |

## width

```TypeScript
width(width: Length): this
```

设置形状的宽度。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BaseShape-width(width: Length): this--><!--Device-BaseShape-width(width: Length): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| width | [Length](../../apis-na/arkts-apis/arkts-na-length-t.md) | 是 | 形状的宽度。<br/>单位：vp<br/>取值为异常值时按照0vp处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | 返回当前对象。 |

