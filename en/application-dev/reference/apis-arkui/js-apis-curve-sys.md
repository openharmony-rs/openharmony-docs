# @ohos.curves (Interpolation Calculation) (System API)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @hehongyang3-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=4d61c222c0143c39fcbcfbde2425145a676f0e3d translatedAt=2026-10-21T09:33:09.107Z pushedAt=2026-10-22T03:04:28.205Z -->

This module provides the system APIs for setting animation interpolation curves, used to construct objects for curves such as spring animation curves, responsive spring animation curves, and interpolating spring curves.

> **NOTE**
>
> This topic contains only the system APIs of this module. For other public APIs, see [@ohos.curves (Interpolation Calculation)](js-apis-curve.md).

**Since**: 26.0.0

## Modules to Import

```ts
import { curves } from '@kit.ArkUI';
```


## TrailOptimization

Implements trailing optimization for a spring animation.

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full


| Parameter | Type | Read-Only | Optional | Description |
| --- | --- | --- | --- | --- |
| progressThreshold | number | No | Yes | Animation progress threshold, which is used to set the start point at which the animation playback is accelerated. When the animation progress exceeds this threshold, accelerated playback starts. When the value of **responseDecayFactor** is less than 1, a smaller **progressThreshold** value causes the animation to start accelerated playback earlier.<br/>Value range: [0, 1]. Values less than 0 are treated as 0, and values greater than 1 are treated as 1.<br/>Default value: **1** |
| responseDecayFactor | number | No | Yes | Natural vibration period decay factor. After the animation playback progress exceeds the animation progress threshold, the response of each frame is multiplied by this decay factor to accelerate the animation. When the value of **progressThreshold** is less than 1, a smaller **responseDecayFactor** value causes the animation to end earlier.<br/>Value range: (0, 1]. Values less than or equal to 0 are treated as 1e-8, and values greater than 1 are treated as 1.<br/>Default value: **1** |


## curves.trailOptimizedSpringMotion

trailOptimizedSpringMotion(response?: number, dampingFraction?: number, overlapDuration?: number, trail?: TrailOptimization): ICurve

Constructs a spring animation curve object with trailing optimization by adding trailing optimization parameters based on [springMotion](js-apis-curve.md#curvesspringmotion9). If multiple spring animations are applied to the same attribute of the same object, each animation replaces the previous one and inherits its velocity.

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full


**Parameters**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| response | number | No | Duration of one complete oscillation.<br/>Default value: **0.55**<br/>Unit: s<br/>Value range: (0, +∞)<br/>**NOTE**<br/>If this parameter is set to a value less than or equal to 0, the default value **0.55** is used. |
| dampingFraction | number | No | Damping coefficient.<br/>**0**: undamped. In this case, the spring oscillates forever.<br/>> 0 and < 1: underdamped. In this case, the spring overshoots the equilibrium position.<br/>**1**: critically damped.<br/>> 1: overdamped. In this case, the spring approaches equilibrium gradually.<br/>Default value: **0.825**<br/>Value range: [0, +∞)<br/>**NOTE**<br/>A value less than 0 evaluates to the default value **0.825**. |
| overlapDuration | number | No | Duration for spring animation transition. When animation inheritance occurs, if the **response** values of the two consecutive spring animations differ, the **response** parameter transitions smoothly within the **overlapDuration** period.<br/>Default value: **0**<br/>Unit: s<br/>Value range: [0, +∞)<br/>**NOTE**<br/>If the value is less than 0, the default value **0** is used.<br/>The spring animation curve is a physical curve. The **duration** parameter in [animation](arkui-ts/ts-animatorproperty.md), [animateTo](arkui-ts/ts-explicit-animation.md), and [pageTransition](arkui-ts/ts-page-transition-animation.md) does not take effect. The animation duration depends on the **trailOptimizedSpringMotion** animation curve parameters and the previous velocity. The time cannot be normalized, so interpolation cannot be obtained through the **interpolate** API of this curve. |
| trail | [TrailOptimization](#trailoptimization) | No | Trailing optimization configuration. If this parameter is not set, **progressThreshold** and **responseDecayFactor** take the default values of [TrailOptimization](#trailoptimization).<br/>**NOTE**<br/>After the animation progress reaches **progressThreshold**, if the animation is still within the **overlapDuration** period, the remaining duration of **overlapDuration** is no longer interpolated based on the **response** parameters of the two consecutive spring animations. Instead, it decays directly at the rate determined by **responseDecayFactor**. |

**Return value**

| Type | Description |
| --- | --- |
| [ICurve](js-apis-curve.md#icurve9) | Curve object.<br/>**NOTE**<br/>The spring animation curve is a physical curve. The **duration** parameter in [animation](arkui-ts/ts-animatorproperty.md), [animateTo](arkui-ts/ts-explicit-animation.md), and [pageTransition](arkui-ts/ts-page-transition-animation.md) does not take effect. The animation duration depends on the **trailOptimizedSpringMotion** animation curve parameters and the previous velocity. The time cannot be normalized, so interpolation cannot be obtained through the [interpolate](js-apis-curve.md#interpolate9) API of this curve. |


## curves.trailOptimizedResponsiveSpringMotion

trailOptimizedResponsiveSpringMotion(response?: number, dampingFraction?: number, overlapDuration?: number, trail?: TrailOptimization): ICurve

Constructs a responsive spring animation curve object with trailing optimization by adding trailing optimization parameters based on [responsiveSpringMotion](js-apis-curve.md#curvesresponsivespringmotion9).

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full


**Parameters**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| response | number | No | See **response** in **springMotion**.<br/>Default value: **0.15**<br/>Unit: s<br/>Value range: (0, +∞)<br/>**NOTE**<br/>If this parameter is set to a value less than or equal to 0, the default value **0.15** is used. |
| dampingFraction | number | No | See **dampingFraction** in **springMotion**.<br/>Default value: **0.86**<br/>Value range: [0, +∞)<br/>**NOTE**<br/>A value less than 0 evaluates to the default value **0.86**. |
| overlapDuration | number | No | See **overlapDuration** in **springMotion**.<br/>Default value: **0.25**<br/>Unit: s<br/>Value range: [0, +∞)<br/>**NOTE**<br/>A value less than 0 evaluates to the default value **0.25**.<br/>The responsive spring animation curve is a special case of **springMotion**, differing only in default values. If a spring curve with custom parameters is used, it is recommended to use **springMotion** to construct the curve. If a follow animation is used, it is recommended to use the responsive spring animation curve with default parameters.<br/>The **duration** parameter in [animation](arkui-ts/ts-animatorproperty.md), [animateTo](arkui-ts/ts-explicit-animation.md), and [pageTransition](arkui-ts/ts-page-transition-animation.md) does not take effect. The animation duration depends on the **trailOptimizedResponsiveSpringMotion** animation curve parameters and the previous velocity, and the interpolation cannot be obtained through the **interpolate** API of this curve. |
| trail | [TrailOptimization](#trailoptimization) | No | Trailing optimization configuration. If this parameter is not set, **progressThreshold** and **responseDecayFactor** take the default values of [TrailOptimization](#trailoptimization).<br/>**NOTE**<br/>After the animation progress reaches **progressThreshold**, if the animation is still within the **overlapDuration** period, the remaining duration of **overlapDuration** is no longer interpolated based on the **response** parameters of the two consecutive spring animations. Instead, it decays directly at the rate determined by **responseDecayFactor**. |

**Return value**

| Type | Description |
| --- | --- |
| [ICurve](js-apis-curve.md#icurve9) | Curve object.<br/>**NOTE**<br/>1. The responsive spring animation curve is a special case of **springMotion**, differing only in default values. If a spring curve with custom parameters is used, it is recommended to use **springMotion** to construct the curve. If a responsive animation is used, it is recommended to use the responsive spring animation curve with default parameters.<br/>2. The **duration** parameter in [animation](arkui-ts/ts-animatorproperty.md), [animateTo](arkui-ts/ts-explicit-animation.md), and [pageTransition](arkui-ts/ts-page-transition-animation.md) does not take effect. The animation duration depends on the **trailOptimizedResponsiveSpringMotion** animation curve parameters and the previous velocity, and the interpolation cannot be obtained through the [interpolate](js-apis-curve.md#interpolate9) API of this curve. |


## curves.trailOptimizedInterpolatingSpring

trailOptimizedInterpolatingSpring(velocity: number, mass: number, stiffness: number, damping: number, trail?: TrailOptimization): ICurve

Construct an interpolating spring curve object with trailing optimization by adding trailing optimization parameters based on [interpolatingSpring](js-apis-curve.md#curvesinterpolatingspring10), generating an animation curve from 0 to 1. Actual animation values are calculated through interpolation based on the curve. The animation duration is determined by the curve parameters and is not controlled by the duration parameter in the animation settings.

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full


**Parameters**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| velocity | number | Yes | Initial velocity. It is applied by external factors to the spring animation, designed to help ensure the smooth transition from the previous motion state. The velocity is the normalized velocity, and its value is equal to the actual velocity at the beginning of the animation divided by the animation attribute change value.<br/>Value range: (-∞, +∞) |
| mass | number | Yes | Mass, which influences the inertia in the spring system. The greater the mass, the greater the amplitude of the oscillation, and the slower the speed of restoring to the equilibrium position.<br/>Value range: (0, +∞)<br/>**NOTE** <br/>If this parameter is set to a value less than or equal to 0, the value **1** is used. |
| stiffness | number | Yes | Stiffness. It is the degree to which an object deforms by resisting the force applied. The greater the stiffness, the stronger the ability to resist deformation, and the faster the speed of restoring to the equilibrium position.<br/>Value range: (0, +∞)<br/>**NOTE** <br/>If this parameter is set to a value less than or equal to 0, the value **1** is used. |
| damping | number | Yes | Damping. It is used to describe the oscillation and attenuation of the system after being disturbed. The larger the damping, the smaller the number of oscillations of elastic motion, and the smaller the oscillation amplitude.<br/>Value range: (0, +∞)<br/>**NOTE** <br/>If this parameter is set to a value less than or equal to 0, the value **1** is used. |
| trail | [TrailOptimization](#trailoptimization) | No | Trailing optimization configuration. If this parameter is not set, **progressThreshold** and **responseDecayFactor** use the default values of [TrailOptimization](#trailoptimization). |

**Return value**

| Type | Description |
| --- | --- |
| [ICurve](js-apis-curve.md#icurve9) | Curve object.<br/>**Note:** The spring animation curve is physics-based. Its duration depends on the **trailOptimizedInterpolatingSpring** parameters, rather than the **duration** parameter in [animation](arkui-ts/ts-animatorproperty.md), [animateTo](arkui-ts/ts-explicit-animation.md), or [pageTransition](arkui-ts/ts-page-transition-animation.md). The time cannot be normalized. Therefore, the interpolation cannot be obtained using the [interpolate](js-apis-curve.md#interpolate9) API of the curve. |

## Example

### Example 1: Trailing Optimization Effect of trailOptimizedSpringMotion

This example demonstrates the acceleration effect of trailing optimization on the spring animation by comparing the animation execution durations of [springMotion](js-apis-curve.md#curvesspringmotion9) and [trailOptimizedSpringMotion](#curvestrailoptimizedspringmotion).

```ts
import { curves } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State widthSize: number = 150;
  @State heightSize: number = 50;
  @State myAnimateTimeOrigin: number = 0;
  @State myAnimateTimeOptimized: number = 0;
  @State myAngleOrigin: number = 0;
  @State myAngleOptimized: number = 0;

  build() {
    Column() {
      Row() {
        Column() {
          Column()
            .height(100)
            .width(100)
            .borderRadius(10)
            .backgroundColor(Color.Blue)
            .rotate({
              x: 0,
              y: 0,
              z: 1,
              angle: this.myAngleOrigin
            })
          // The actual animation execution duration may fluctuate each time.
          Text('Original execution duration: ' + this.myAnimateTimeOrigin)
            .margin({ top: 25, bottom: 25 })
        }
        .width('50%')

        Column() {
          Column()
            .height(100)
            .width(100)
            .borderRadius(10)
            .backgroundColor(Color.Red)
            .rotate({
              x: 0,
              y: 0,
              z: 1,
              angle: this.myAngleOptimized
            })
          // The actual animation execution duration may fluctuate each time.
          Text('Execution duration after trailing optimization: ' + this.myAnimateTimeOptimized)
            .margin({ top: 25, bottom: 25 })
        }
        .width('50%')
      }
      .justifyContent(FlexAlign.Center)

      Button('Play')
        .width(this.widthSize)
        .height(this.heightSize)
        .margin(5)
        .onClick(() => {
          const startTime = Date.now();

          this.getUIContext()?.animateTo({
            duration: 2000,
            curve: curves.springMotion(0.55, 0.825, 0),
            iterations: 1,
            playMode: PlayMode.Normal,
            onFinish: () => {
              const endTime = Date.now();
              this.myAnimateTimeOrigin = endTime - startTime;
            }
          }, () => {
            this.myAngleOrigin = 360;
          })

          this.getUIContext()?.animateTo({
            duration: 2000,
            curve: curves.trailOptimizedSpringMotion(0.55, 0.825, 0,
              { progressThreshold: 0.98, responseDecayFactor: 0.9 }),
            iterations: 1,
            playMode: PlayMode.Normal,
            onFinish: () => {
              const endTime = Date.now();
              this.myAnimateTimeOptimized = endTime - startTime;
            }
          }, () => {
            this.myAngleOptimized = 360;
          })
        })
    }
    .justifyContent(FlexAlign.Center)
    .width('100%')
    .height('100%')
  }
}
```

<!--Del-->![trailOptimizedSpringMotion] (figures/trailOptimizedSpringMotion.gif)
<!--DelEnd-->

### Example 2: Trailing Optimization Effect of trailOptimizedResponsiveSpringMotion

This example demonstrates the acceleration effect of trailing optimization on the responsive spring animation by comparing the animation durations of [responsiveSpringMotion](js-apis-curve.md#curvesresponsivespringmotion9) and [trailOptimizedResponsiveSpringMotion](#curvestrailoptimizedresponsivespringmotion).

```ts
import { curves } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State widthSize: number = 150;
  @State heightSize: number = 50;
  @State myAnimateTimeOrigin: number = 0;
  @State myAnimateTimeOptimized: number = 0;
  @State myAngleOrigin: number = 0;
  @State myAngleOptimized: number = 0;

  build() {
    Column() {
      Row() {
        Column() {
          Column()
            .height(100)
            .width(100)
            .borderRadius(10)
            .backgroundColor(Color.Blue)
            .rotate({
              x: 0,
              y: 0,
              z: 1,
              angle: this.myAngleOrigin
            })
          // The actual animation execution duration may fluctuate each time.
          Text('Original execution duration: ' + this.myAnimateTimeOrigin)
            .margin({ top: 25, bottom: 25 })
        }
        .width('50%')

        Column() {
          Column()
            .height(100)
            .width(100)
            .borderRadius(10)
            .backgroundColor(Color.Red)
            .rotate({
              x: 0,
              y: 0,
              z: 1,
              angle: this.myAngleOptimized
            })
          // The actual animation execution duration may fluctuate each time.
          Text('Execution duration after trailing optimization: ' + this.myAnimateTimeOptimized)
            .margin({ top: 25, bottom: 25 })
        }
        .width('50%')
      }
      .justifyContent(FlexAlign.Center)

      Button('Play')
        .width(this.widthSize)
        .height(this.heightSize)
        .margin(5)
        .onClick(() => {
          const startTime = Date.now();

          this.getUIContext()?.animateTo({
            duration: 2000,
            curve: curves.responsiveSpringMotion(0.15, 5, 0.25),
            iterations: 1,
            playMode: PlayMode.Normal,
            onFinish: () => {
              const endTime = Date.now();
              this.myAnimateTimeOrigin = endTime - startTime;
            }
          }, () => {
            this.myAngleOrigin = 360;
          })

          this.getUIContext()?.animateTo({
            duration: 2000,
            curve: curves.trailOptimizedResponsiveSpringMotion(0.15, 5, 0.25,
              { progressThreshold: 0.98, responseDecayFactor: 0.9 }),
            iterations: 1,
            playMode: PlayMode.Normal,
            onFinish: () => {
              const endTime = Date.now();
              this.myAnimateTimeOptimized = endTime - startTime;
            }
          }, () => {
            this.myAngleOptimized = 360;
          })
        })
    }
    .justifyContent(FlexAlign.Center)
    .width('100%')
    .height('100%')
  }
}
```

<!--Del-->![trailOptimizedResponsiveSpringMotion] (figures/trailOptimizedResponsiveSpringMotion.gif)
<!--DelEnd-->

### Example 3: Trailing Optimization Effect of trailOptimizedInterpolatingSpring

This example demonstrates the acceleration effect of trailing optimization on the interpolating spring animation by comparing the animation execution durations of [interpolatingSpring](js-apis-curve.md#curvesinterpolatingspring10) and [trailOptimizedInterpolatingSpring](#curvestrailoptimizedinterpolatingspring).

```ts
import { curves } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State widthSize: number = 150;
  @State heightSize: number = 50;
  @State myAnimateTimeOrigin: number = 0;
  @State myAnimateTimeOptimized: number = 0;
  @State myAngleOrigin: number = 0;
  @State myAngleOptimized: number = 0;

  build() {
    Column() {
      Row() {
        Column() {
          Column()
            .height(100)
            .width(100)
            .borderRadius(10)
            .backgroundColor(Color.Blue)
            .rotate({
              x: 0,
              y: 0,
              z: 1,
              angle: this.myAngleOrigin
            })
          // The actual animation execution duration may fluctuate each time.
          Text('Original execution duration: ' + this.myAnimateTimeOrigin)
            .margin({ top: 25, bottom: 25 })
        }
        .width('50%')

        Column() {
          Column()
            .height(100)
            .width(100)
            .borderRadius(10)
            .backgroundColor(Color.Red)
            .rotate({
              x: 0,
              y: 0,
              z: 1,
              angle: this.myAngleOptimized
            })
          // The actual animation execution duration may fluctuate each time.
          Text('Execution duration after trailing optimization: ' + this.myAnimateTimeOptimized)
            .margin({ top: 25, bottom: 25 })
        }
        .width('50%')
      }
      .justifyContent(FlexAlign.Center)

      Button('Play')
        .width(this.widthSize)
        .height(this.heightSize)
        .margin(5)
        .onClick(() => {
          const startTime = Date.now();

          this.getUIContext()?.animateTo({
            duration: 2000,
            curve: curves.interpolatingSpring(0.85, 0.1, 7, 1.0),
            iterations: 1,
            playMode: PlayMode.Normal,
            onFinish: () => {
              const endTime = Date.now();
              this.myAnimateTimeOrigin = endTime - startTime;
            }
          }, () => {
            this.myAngleOrigin = 360;
          })

          this.getUIContext()?.animateTo({
            duration: 2000,
            curve: curves.trailOptimizedInterpolatingSpring(0.85, 0.1, 7, 1.0,
              { progressThreshold: 0.98, responseDecayFactor: 0.9 }),
            iterations: 1,
            playMode: PlayMode.Normal,
            onFinish: () => {
              const endTime = Date.now();
              this.myAnimateTimeOptimized = endTime - startTime;
            }
          }, () => {
            this.myAngleOptimized = 360;
          })
        })
    }
    .justifyContent(FlexAlign.Center)
    .width('100%')
    .height('100%')
  }
}
```

<!--Del-->![trailOptimizedInterpolatingSpring] (figures/trailOptimizedInterpolatingSpring.gif)
<!--DelEnd-->

