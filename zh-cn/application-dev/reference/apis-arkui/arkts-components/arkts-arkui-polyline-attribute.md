# Polyline属性/事件

除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下属性：

**继承/实现关系：** PolylineAttribute extends [CommonShapeMethod<PolylineAttribute>](CommonShapeMethod<PolylineAttribute>)

**起始版本：** 7

<!--Device-unnamed-declare class PolylineAttribute extends CommonShapeMethod<PolylineAttribute>--><!--Device-unnamed-declare class PolylineAttribute extends CommonShapeMethod<PolylineAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## points

```TypeScript
points(value: Array<any>)
```

设置折线经过坐标点列表，支持[attributeModifier](arkts-arkui-common-commonmethod-c.md#attributemodifier-1)动态设置属性方法。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-PolylineAttribute-points(value: Array<any>): PolylineAttribute--><!--Device-PolylineAttribute-points(value: Array<any>): PolylineAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<any> | 是 | 折线经过坐标点列表。使用时传入一个二维数组，每个子数组表示一个顶点的[x, y]坐标。<br/>默认值：[]（空数组）<br/>默认单位：vp <br/>异常值undefined和null按照默认值处理。 |

