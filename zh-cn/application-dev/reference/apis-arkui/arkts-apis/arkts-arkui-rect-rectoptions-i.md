# RectOptions

用于描述Rect组件绘制属性。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface RectOptions--><!--Device-unnamed-export declare interface RectOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## height

```TypeScript
height?: Length
```

高度，取值范围≥0。 默认值：0 默认单位：vp 异常值undefined、null、NaN和Infinity按照默认值处理。 Anonymous Object Rectification

**类型：** [Length](arkts-arkui-length-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RectOptions-height?: Length--><!--Device-RectOptions-height?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## radius

```TypeScript
radius?: Length | Array<RadiusItem>
```

圆角半径，支持分别设置四个角的圆角度数，取值范围≥0。 该属性和radiusWidth/radiusHeight属性效果类似，在组合使用时优先于radiusWidth/radiusHeight生效。 默认值：0 默认单位：vp 异常值undefined、null、NaN和Infinity按照默认值处理。 Anonymous Object Rectification

**类型：** [Length](arkts-arkui-length-t.md) \| Array&lt;[RadiusItem](arkts-arkui-radiusitem-t.md)&gt;

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RectOptions-radius?: Length | Array<RadiusItem>--><!--Device-RectOptions-radius?: Length | Array<RadiusItem>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width?: Length
```

宽度，取值范围≥0。 默认值：0 默认单位：vp 异常值undefined、null、NaN和Infinity按照默认值处理。 Anonymous Object Rectification

**类型：** [Length](arkts-arkui-length-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RectOptions-width?: Length--><!--Device-RectOptions-width?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

