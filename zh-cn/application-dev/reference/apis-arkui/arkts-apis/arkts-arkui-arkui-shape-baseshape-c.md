# BaseShape

继承自[CommonShapeMethod](arkts-arkui-arkui-shape-commonshapemethod-c.md#CommonShapeMethod)。

**继承/实现关系：** BaseShape extends [CommonShapeMethod](arkts-arkui-arkui-shape-commonshapemethod-c.md#CommonShapeMethod)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare class BaseShape--><!--Device-unnamed-export declare class BaseShape-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## height

```TypeScript
height(height: Length): this
```

设置形状的高度。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BaseShape-height(height: Length): this--><!--Device-BaseShape-height(height: Length): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| height | [Length](../../apis-na/arkts-apis/arkts-na-length-t.md) | 是 | 形状的高度。&lt;br/&gt;单位：vp&lt;br/&gt;取值为异常值时按照0vp处理。 |

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

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

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

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BaseShape-width(width: Length): this--><!--Device-BaseShape-width(width: Length): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| width | [Length](../../apis-na/arkts-apis/arkts-na-length-t.md) | 是 | 形状的宽度。&lt;br/&gt;单位：vp&lt;br/&gt;取值为异常值时按照0vp处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | 返回当前对象。 |

