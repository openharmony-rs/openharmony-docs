# PolylineAttribute

折线绘制组件属性。

**继承/实现关系：** PolylineAttribute extends CommonShapeMethod

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface PolylineAttribute--><!--Device-unnamed-export declare interface PolylineAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## attributeModifier

```TypeScript
attributeModifier(modifier: AttributeModifier<PolylineAttribute> | AttributeModifier<CommonMethod> | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-PolylineAttribute-attributeModifier(modifier: AttributeModifier<PolylineAttribute> | AttributeModifier<CommonMethod> | undefined): this--><!--Device-PolylineAttribute-attributeModifier(modifier: AttributeModifier<PolylineAttribute> | AttributeModifier<CommonMethod> | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | [AttributeModifier](../arkts-components/arkts-arkui-attributemodifier-i.md)&lt;[PolylineAttribute](arkts-arkui-polyline-polylineattribute-i.md)&gt; \| [AttributeModifier](../arkts-components/arkts-arkui-attributemodifier-i.md)&lt;[CommonMethod](../arkts-components/arkts-arkui-commonmethod-c.md)&gt; \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## points

```TypeScript
points(value: Array<ShapePoint> | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-PolylineAttribute-points(value: Array<ShapePoint> | undefined): this--><!--Device-PolylineAttribute-points(value: Array<ShapePoint> | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Array&lt;[ShapePoint](arkts-arkui-shapepoint-t.md)&gt; \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## setPolylineOptions

```TypeScript
setPolylineOptions(options?: PolylineOptions): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-PolylineAttribute-setPolylineOptions(options?: PolylineOptions): this--><!--Device-PolylineAttribute-setPolylineOptions(options?: PolylineOptions): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [PolylineOptions](arkts-arkui-polyline-polylineoptions-i.md) | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## default

```TypeScript
default
```

调用attributeModifier。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PolylineAttribute-default--><!--Device-PolylineAttribute-default-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

