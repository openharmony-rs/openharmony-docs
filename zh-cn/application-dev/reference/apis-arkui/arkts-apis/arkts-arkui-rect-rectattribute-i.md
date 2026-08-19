# RectAttribute

矩形绘制组件。

**继承/实现关系：** RectAttribute extends CommonShapeMethod

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface RectAttribute--><!--Device-unnamed-export declare interface RectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## attributeModifier

```TypeScript
attributeModifier(modifier: AttributeModifier<RectAttribute> | AttributeModifier<CommonMethod> | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-RectAttribute-attributeModifier(modifier: AttributeModifier<RectAttribute> | AttributeModifier<CommonMethod> | undefined): this--><!--Device-RectAttribute-attributeModifier(modifier: AttributeModifier<RectAttribute> | AttributeModifier<CommonMethod> | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | [AttributeModifier](../arkts-components/arkts-arkui-attributemodifier-i.md)&lt;[RectAttribute](arkts-arkui-rect-rectattribute-i.md)&gt; \| [AttributeModifier](../arkts-components/arkts-arkui-attributemodifier-i.md)&lt;[CommonMethod](../arkts-components/arkts-arkui-commonmethod-c.md)&gt; \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## radius

```TypeScript
radius(value: Length | Array<RadiusItem> | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-RectAttribute-radius(value: Length | Array<RadiusItem> | undefined): this--><!--Device-RectAttribute-radius(value: Length | Array<RadiusItem> | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](arkts-arkui-length-t.md) \| Array&lt;[RadiusItem](arkts-arkui-radiusitem-t.md)&gt; \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## radiusHeight

```TypeScript
radiusHeight(value: Length | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-RectAttribute-radiusHeight(value: Length | undefined): this--><!--Device-RectAttribute-radiusHeight(value: Length | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](arkts-arkui-length-t.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## radiusWidth

```TypeScript
radiusWidth(value: Length | undefined): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-RectAttribute-radiusWidth(value: Length | undefined): this--><!--Device-RectAttribute-radiusWidth(value: Length | undefined): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](arkts-arkui-length-t.md) \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## setRectOptions

```TypeScript
setRectOptions(options?: RectOptions | RoundedRectOptions): this
```

**起始版本：** -1

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为-1。

<!--Device-RectAttribute-setRectOptions(options?: RectOptions | RoundedRectOptions): this--><!--Device-RectAttribute-setRectOptions(options?: RectOptions | RoundedRectOptions): this-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [RectOptions](arkts-arkui-rect-rectoptions-i.md) \| [RoundedRectOptions](arkts-arkui-rect-roundedrectoptions-i.md) | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## default

```TypeScript
default
```

Call attributeModifier.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RectAttribute-default--><!--Device-RectAttribute-default-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

