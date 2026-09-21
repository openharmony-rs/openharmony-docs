# PageTransitionOptions

```TypeScript
declare interface PageTransitionOptions
```

退场/入场动效的参数。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## curve

```TypeScript
curve?: Curve | string | ICurve
```

动画曲线。

推荐以Curve或ICurve形式指定。

当类型为string时，为动画插值曲线，取值参考[AnimateParam](arkts-arkui-common-comp-animateparam-i.md)的curve参数。

默认值：Curve.Linear

**类型：** Curve &#124; string &#124; ICurve

**默认值：** Curve.Linear

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## delay

```TypeScript
delay?: number
```

动画延迟时长。

单位：毫秒

默认值：0

**类型：** number

**默认值：** 0

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

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

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type?: RouteType
```

页面转场效果生效的路由类型。

默认值：RouteType.None。

**说明：** 

当pageTransition函数中配置了多个[PageTransitionEnter](arkts-arkui-pagetransitionenter-comp.md#pagetransitionenter)或[PageTransitionExit](arkts-arkui-pagetransitionenter-comp-con.md#pagetransitionexit)时，按照RouteType匹配规则生效：系统会根据当前路由操作类型（Push或Pop）从所有配置的PageTransitionEnter/PageTransitionExit中选择最后一个匹配的组件生效；若没有匹配的组件，则使用系统默认的页面转场效果（根据设备可能会有差异）。如果存在多个匹配相同RouteType的PageTransitionEnter，则最后配置的生效；如果存在多个匹配相同RouteType的PageTransitionExit，则最后配置的生效。RouteType.None与所有路由类型均匹配。

取值原则：None表示对所有路由类型生效；Push仅对push路由生效；Pop仅对pop路由生效。

**类型：** [RouteType](arkts-arkui-pagetransitionenter-comp-routetype-e.md)

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
