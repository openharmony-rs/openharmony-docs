# Shared Element Transition (sharedTransition)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @hehongyang3-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=39ca26def5c22dc659f3dc0b76ef62a29421e77a translatedAt=2026-09-01T11:55:59.926Z -->

The shared element transition (sharedTransition) is used to implement smooth transition animations of the position, size, and other attributes of a shared element during page redirection, so that the same element maintains visual continuity across different pages, improving user experience and transition smoothness. You can mark an element as a shared element and set the corresponding shared element transition animation by setting the **sharedTransition** attribute of the component. The sharedTransition takes effect only during redirection through [@ohos.router (Page Routing)](../js-apis-router.md).

> **NOTE**
>
> This feature is supported since API version 7. Updates will be marked with a superscript to indicate their earliest API version.

## sharedTransition

sharedTransition(id: string, options?: sharedTransitionOptions): T

Sets the shared element transition animation. This transition takes effect only during page redirection through @ohos.router.

> **NOTE**
>
> - sharedTransition must be used together with [PageTransitionEnter](./ts-page-transition-animation.md#pagetransitionenter) and [PageTransitionExit](./ts-page-transition-animation.md#pagetransitionexit) to jointly control the page transition animation effect.
> - When **type** of PageTransitionEnter/PageTransitionExit is set to **RouteType.None** and **duration** is set to 0, the page has no transition animation as a whole, and only the shared element transition animation is displayed.
> - When PageTransition is not configured, the default page transition animation and the shared element transition animation are played simultaneously, which may result in a visual overlay effect.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                                                        |
| ------ | ------ | ---- | ------------------------------------------------------------ |
| id | string | Yes | Components with the same non-empty id value on two pages are shared elements, and the shared element transition animation is displayed during page transition. An empty string does not trigger the shared element transition animation. |
|     options          |  [sharedTransitionOptions](#sharedtransitionoptions)       | No     |  Parameters of the shared element transition animation. If not set, the default transition animation parameters are used. For the default value of each parameter, see [sharedTransitionOptions](#sharedtransitionoptions). |

**Return value**

| Type| Description|
| --- | --- |
|  T | Current component, used for chained calls. |

## sharedTransitionOptions

Parameters of the shared element transition animation.

> **NOTE**
>
> **motionPath** takes effect only when **type** is set to **SharedTransitionEffectType.Exchange**.
>
> When **type** is set to **SharedTransitionEffectType.Exchange**, the effect produces a transition of the position and size of the matched shared element (which can be observed by configuring the **border** of the component), and does not support the transition effect of the component's drawn content (the transition range of the position and size changes can be observed by configuring the **border** attribute of the shared element component). For example, if a **Text** component uses different **fontSize** attribute values on the two pages, that is, the drawn content differs in size, the **fontSize** effect of the **Text** component will abruptly change to that of the target page in the last frame after the sharedTransition animation ends.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name             | Type     | Read-Only|  Optional    | Description                                                    |
| ----------------- | -------------|------- | ------- | --------------------------------------------------------------|
| duration          |     number   |  No  |    Yes          | Duration of the shared element transition animation.<br>Default value: 1000<br>Unit: ms<br>Value range: [0, +∞) |
| curve             |      [Curve](ts-appendix-enums.md#curve)&nbsp;\|&nbsp;string&nbsp;\|&nbsp;[ICurve](../js-apis-curve.md#icurve9)  | No | Yes | Animation curve.<br>It is recommended to specify the curve in the form of Curve or ICurve.<br>When the type is string, the value is an animation interpolation curve. For details, see the curve parameter in [AnimateParam](./ts-explicit-animation.md#animateparam).<br>Default value: Curve.Linear |
| delay          |     number   |  No  |  Yes         | Delay of the animation playback.<br>Value range: [0, +∞)<br>Default value: 0<br>Unit: ms |
| motionPath          | [MotionPathOptions](./ts-motion-path-animation.md#motionpathoptions)  |  No   |  Yes        | Motion path information, which defines the motion trajectory of the shared element transition. If this parameter is not set, the motion path effect is not enabled. This parameter takes effect only when type is SharedTransitionEffectType.Exchange. |
| zIndex          |     number   |  No   |    Yes           | Z-order of the shared element during the transition animation.<br>Value range: (-∞, +∞)<br>Default value: 0<br>The larger the value, the more frontward (higher in the layer) the shared element is during the transition, and the less likely it is to be obscured by other shared elements. This zIndex takes effect only during the shared element transition animation. It controls the Z-order of the shared element relative to other shared elements that participate in the transition at the same time, and does not participate in the static layout hierarchy control of common components on the page. (The static layout hierarchy of components on the page is controlled by the universal attribute [zIndex](ts-universal-attributes-z-order.md#zindex).) |
| type           |     [SharedTransitionEffectType](ts-appendix-enums.md#sharedtransitioneffecttype)   |  No  |  Yes | Animation type, which determines the transition mode of the shared element transition. The Exchange type produces transition animations of position and size (content transition effects are not supported). For details about other types, see [SharedTransitionEffectType](ts-appendix-enums.md#sharedtransitioneffecttype).<br>Default value: SharedTransitionEffectType.Exchange |


## Example

The sample code implements the custom transition animation of a shared element image when a click on the image area triggers page redirection.

```ts
// xxx.ets
@Entry
@Component
struct SharedTransitionExample {

  build() {
    Column() {
      // Replace $r('app.media.ic_health_heart') with the image resource file you use.
      Image($r('app.media.ic_health_heart')).width(50).height(50).margin({ left: 20, top: 20 })
        .sharedTransition('sharedImage', { duration: 800, curve: Curve.Linear, delay: 100 }) 
    }.width('100%').height('100%').alignItems(HorizontalAlign.Start)
    .onClick(() => {
      this.getUIContext().getRouter().pushUrl({ url: 'pages/PageB' });
    })
  }

  pageTransition() {
    PageTransitionEnter({ type: RouteType.None, duration: 0 })
    PageTransitionExit({ type: RouteType.None, duration: 0 })
  }
}
```

```ts
// PageB.ets
@Entry
@Component
struct PageBExample {
  build() {
    Stack() {
      // Replace $r('app.media.ic_health_heart') with the image resource file you use.
      Image($r('app.media.ic_health_heart')).width(150).height(150)
        .sharedTransition('sharedImage', { duration: 800, curve: Curve.Linear, delay: 100 })
    }.width('100%').height('100%')
  }

  pageTransition() {
    PageTransitionEnter({ type: RouteType.None, duration: 0 })
    PageTransitionExit({ type: RouteType.None, duration: 0 })
  }
}
```

![shared](figures/shared.gif)

