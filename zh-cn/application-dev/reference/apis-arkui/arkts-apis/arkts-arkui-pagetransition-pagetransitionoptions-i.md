# PageTransitionOptions

退场/进场动效的参数。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface PageTransitionOptions--><!--Device-unnamed-export declare interface PageTransitionOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## curve

```TypeScript
curve?: Curve | string | ICurve
```

动画曲线。 推荐以Curve或ICurve形式指定。 当类型为string时，为动画插值曲线，取值参考 [AnimateParam](../../../reference/apis-arkui/arkui-ts/ts-explicit-animation.md#animateparam对象说明)的curve参数。 默认值：Curve.Linear

**类型：** [Curve](arkts-arkui-curve-e.md) \| string \| [ICurve](../arkts-components/arkts-arkui-icurve-i.md)

**默认值：** Curve.Linear

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PageTransitionOptions-curve?: Curve | string | ICurve--><!--Device-PageTransitionOptions-curve?: Curve | string | ICurve-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## delay

```TypeScript
delay?: int
```

动画延迟时长。 单位：毫秒 默认值：0 **说明：** 没有匹配时使用系统默认的页面转场效果(根据设备可能会有差异)，如需禁用系统默认页面转场效果，可以指定duration为0。

**类型：** int

**默认值：** 0

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PageTransitionOptions-delay?: int--><!--Device-PageTransitionOptions-delay?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## duration

```TypeScript
duration?: int
```

动画的时长。 单位：毫秒 默认值：1000 取值范围：[0, +∞)

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PageTransitionOptions-duration?: int--><!--Device-PageTransitionOptions-duration?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type?: RouteType
```

页面转场效果生效的路由类型。 默认值：RouteType.None。

**类型：** [RouteType](arkts-arkui-pagetransition-routetype-e.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PageTransitionOptions-type?: RouteType--><!--Device-PageTransitionOptions-type?: RouteType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

