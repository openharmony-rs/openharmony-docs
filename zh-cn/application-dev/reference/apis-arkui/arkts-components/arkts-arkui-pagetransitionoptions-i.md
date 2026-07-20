# PageTransitionOptions

退场/进场动效的参数。

**起始版本：** 7

<!--Device-unnamed-declare interface PageTransitionOptions--><!--Device-unnamed-declare interface PageTransitionOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## curve

```TypeScript
curve?: Curve | string | ICurve
```

动画曲线。

推荐以Curve或ICurve形式指定。

当类型为string时，为动画插值曲线，取值参考[AnimateParam](docroot://reference/apis-arkui/arkui-ts/ts-explicit-animation.md#animateparam对象说明)的curve参数。

默认值：Curve.Linear

**类型：** Curve \| string \| ICurve

**默认值：** Curve.Linear

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PageTransitionOptions-curve?: Curve | string | ICurve--><!--Device-PageTransitionOptions-curve?: Curve | string | ICurve-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## delay

```TypeScript
delay?: number
```

动画延迟时长。

单位：毫秒

默认值：0

**说明：**

没有匹配时使用系统默认的页面转场效果(根据设备可能会有差异)，如需禁用系统默认页面转场效果，可以指定duration为0。

**类型：** number

**默认值：** 0

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PageTransitionOptions-delay?: number--><!--Device-PageTransitionOptions-delay?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## duration

```TypeScript
duration?: number
```

动画的时长。

单位：毫秒

默认值：1000

取值范围：[0, +∞)

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PageTransitionOptions-duration?: number--><!--Device-PageTransitionOptions-duration?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type?: RouteType
```

页面转场效果生效的路由类型。

默认值：RouteType.None。

**类型：** RouteType

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PageTransitionOptions-type?: RouteType--><!--Device-PageTransitionOptions-type?: RouteType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

