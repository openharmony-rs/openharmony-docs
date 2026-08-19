# DepthComponentOptions（系统接口）

景深组件配置项。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export declare interface DepthComponentOptions--><!--Device-unnamed-export declare interface DepthComponentOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## depthSpace

```TypeScript
depthSpace?: DepthSpaceType
```

景深空间类型。

**类型：** [DepthSpaceType](arkts-na-depthcomponent-depthspacetype-e-sys.md)

**默认值：** DepthSpaceType.INSTANCE

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DepthComponentOptions-depthSpace?: DepthSpaceType--><!--Device-DepthComponentOptions-depthSpace?: DepthSpaceType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## render3DScale

```TypeScript
render3DScale?: double
```

3D渲染窗口的缩放比例，同时作用于宽度和高度。取值范围：(0.0, 1.0]，超出该范围的值无效（继承之前的取值，如果之前未设置取默认值）。默认值：1.0。

**类型：** double

**默认值：** 1.0

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DepthComponentOptions-render3DScale?: double--><!--Device-DepthComponentOptions-render3DScale?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

