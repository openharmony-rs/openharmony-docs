# @ohos.curves(Interpolation Calculation)

This module provides the capability of setting interpolation curves for animations, which is used to construct step curve objects, cubic Bézier curve objects, spring curve objects, spring animation curve objects, responsive spring animation curve objects, interpolating spring curve objects, and custom curve objects.

**Since:** 7

<!--Device-unnamed-declare namespace curves--><!--Device-unnamed-declare namespace curves-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { curves } from '@kit.ArkUI';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [cubicBezier](arkts-arkui-curves-cubicbezier-f.md) | Creates a cubic Bézier curve object. The x-coordinates (x1 and x2) of the two control points of the curve must be from 0 to 1. |
| [cubicBezierCurve](arkts-arkui-curves-cubicbeziercurve-f.md) | Creates a cubic Bézier curve object. The x-coordinates (x1 and x2) of the two control points of the curve must be from 0 to 1. |
| [customCurve](arkts-arkui-curves-customcurve-f.md) | Constructs a custom curve object. You can determine the shape of the curve by customizing the interpolation function. |
| [init](arkts-arkui-curves-init-f.md) | Implements initialization for the interpolation curve, which is used to create an interpolation curve based on the input parameter. |
| [initCurve](arkts-arkui-curves-initcurve-f.md) | Implements initialization for the interpolation curve, which is used to create an interpolation curve based on the input parameter. |
| [interpolatingSpring](arkts-arkui-curves-interpolatingspring-f.md) | Creates an interpolating spring curve animated from 0 to 1. The actual animation value is calculated based on the curve. The animation duration is subject to the curve parameters, rather than the duration parameter in the animation parameters. |
| [responsiveSpringMotion](arkts-arkui-curves-responsivespringmotion-f.md) | Creates a responsive spring animation curve. It is a special case of [springMotion](arkts-arkui-curves-springmotion-f.md), with the only difference in the default values. It can be used together with **springMotion**. |
| [spring](arkts-arkui-curves-spring-f.md) | Creates a spring curve. The curve shape is subject to the spring parameters, and the animation duration is subject to the **duration** parameter in **animation** and **animateTo**. Compared with [interpolatingSpring](arkts-arkui-curves-interpolatingspring-f.md), the two APIs have the same parameter signature but different behavior: **springCurve** is applicable to spring animation scenarios where the animation duration needs to be fixed. **interpolatingSpring** is applicable to physical spring animation scenarios where the animation duration is naturally determined by the spring parameters. |
| [springCurve](arkts-arkui-curves-springcurve-f.md) | Creates a spring curve. The curve shape is subject to the spring parameters, and the animation duration is subject to the duration parameter in the animation parameters. |
| [springMotion](arkts-arkui-curves-springmotion-f.md) | Creates a spring animation curve. Unlike [curves.springCurve](arkts-arkui-curves-springcurve-f.md), which uses spring physics parameters, **springMotion** uses responsive parameters to construct a curve and supports velocity inheritance between animations. It is recommended for continuous spring animations that require velocity inheritance. If multiple spring animations are applied to the same attribute of an object, each animation replaces their predecessor and inherits the velocity. |
| [steps](arkts-arkui-curves-steps-f.md) | Constructs a step curve object, which divides the animation time into a specified number of intervals. The attribute value remains unchanged within each interval and changes at the interval boundaries. |
| [stepsCurve](arkts-arkui-curves-stepscurve-f.md) | Constructs a step curve object, which divides the animation process into several equal intervals, with a step change occurring at the start or end of each interval. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [trailOptimizedInterpolatingSpring](arkts-arkui-curves-trailoptimizedinterpolatingspring-f-sys.md) | Creates an interpolating spring curve animated from 0 to 1. The actual animation value is calculated based on the curve. The animation duration is subject to the curve parameters, rather than the **duration** parameter in **animation** or **animateTo**. |
| [trailOptimizedResponsiveSpringMotion](arkts-arkui-curves-trailoptimizedresponsivespringmotion-f-sys.md) | Creates a responsive spring animation curve. It is a special case of [springMotion](arkts-arkui-curves-springmotion-f.md), with the only difference in the default values. It can be used together with **springMotion**. |
| [trailOptimizedSpringMotion](arkts-arkui-curves-trailoptimizedspringmotion-f-sys.md) | Creates a spring animation curve. If multiple spring animations are applied to the same attribute of an object, each animation replaces their predecessor and inherits the velocity. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [ICurve](arkts-arkui-curves-icurve-i.md) | Represents a curve object. Different types of curve objects can be created using APIs in this module, including [curves.initCurve](arkts-arkui-curves-initcurve-f.md), [curves.stepsCurve](arkts-arkui-curves-stepscurve-f.md), [curves.cubicBezierCurve](arkts-arkui-curves-cubicbeziercurve-f.md), [curves.springCurve](arkts-arkui-curves-springcurve-f.md), [curves.springMotion](arkts-arkui-curves-springmotion-f.md), [curves.responsiveSpringMotion](arkts-arkui-curves-responsivespringmotion-f.md), [curves.interpolatingSpring](arkts-arkui-curves-interpolatingspring-f.md), and [curves.customCurve](arkts-arkui-curves-customcurve-f.md). You can invoke the member method [interpolate](arkts-arkui-curves-icurve-i.md#interpolate) through the curve object. The spring animation curves created by **springMotion**, **responsiveSpringMotion**, and **interpolatingSpring** are physical curves. The time cannot be normalized, and the interpolation cannot be obtained using the **interpolate** function. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [TrailOptimization](arkts-arkui-curves-trailoptimization-i-sys.md) | Trail optimization configuration for spring animations. When the animation progress reaches the threshold, the response value decays each frame to accelerate convergence and optimize the trail duration. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [Curve](arkts-arkui-curves-curve-e.md) | Defines an interpolation curve. For details about the curves and animations, see <!--RP1--> [Bezier Curve](../../../../design/ux-design/animation-attributes.md)<!--RP1End-->. |

## Examples

```TypeScript
// xxx.ets
import { curves } from '@kit.ArkUI';

@Entry
@Component
struct ImageComponent {
  @State widthSize: number = 200;
  @State heightSize: number = 200;

  build() {
    Column() {
      Text()
        .margin({ top: 100 })
        .width(this.widthSize)
        .height(this.heightSize)
        .backgroundColor(Color.Red)
        .onClick(() => {
          let curve = curves.cubicBezierCurve(0.25, 0.1, 0.25, 1.0);
          // Use the Bezier curve interpolation to calculate the width and height of the animation in the intermediate state.
          this.widthSize = curve.interpolate(0.5) * this.widthSize;
          this.heightSize = curve.interpolate(0.5) * this.heightSize;
        })
        .animation({ duration: 2000, curve: curves.stepsCurve(9, true) })
    }.width('100%').height('100%')
  }
}
```
