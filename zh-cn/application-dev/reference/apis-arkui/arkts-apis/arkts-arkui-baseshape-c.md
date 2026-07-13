# BaseShape

继承自[CommonShapeMethod](arkts-arkui-commonshapemethod-c.md)。

**继承/实现关系：** BaseShape extends [CommonShapeMethod<T>](CommonShapeMethod<T>)

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## height

```TypeScript
height(height: Length): T
```

设置形状的高度。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| height | Length | 是 | 形状的高度。<br/>单位：vp<br/>取值为异常值时按照0vp处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前对象。 |

## size

```TypeScript
size(size: SizeOptions): T
```

设置形状的大小。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | SizeOptions | 是 | 形状的大小。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前对象。 |

## width

```TypeScript
width(width: Length): T
```

设置形状的宽度。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| width | Length | 是 | 形状的宽度。<br/>单位：vp<br/>取值为异常值时按照0vp处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前对象。 |

