# Page Transition (pageTransition)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @hehongyang3-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=e10e7def4863f4f964c4d0cb425b7650081cb83e translatedAt=2026-09-01T11:38:23.681Z pushedAt=2026-09-02T11:24:42.701Z -->

When a route ([router](../js-apis-router.md)) is switched, you can customize the page entrance and exit transition effects in the [pageTransition](ts-custom-component-lifecycle.md#pagetransition9) function. For details, see [Page Transition Animation](../../../ui/arkts-page-transition-animation.md).

> **NOTE**
>
> This feature is supported since API version 7. Updates will be marked with a superscript to indicate their earliest API version.
>
> To achieve a better transition effect, you are advised to use the [Navigation](../../../ui/arkts-navigation-architecture.md) component and [modal transition](../../../ui/arkts-modal-transition.md).

## PageTransitionEnter

Defines the **PageTransitionEnter** component.

### PageTransitionEnter

PageTransitionEnter(value: PageTransitionOptions)

Sets the custom entrance animation of the current page. It must be configured in the **pageTransition()** function and inherits from [CommonTransition](#commontransition).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                  | Mandatory| Description                |
| ------ | ------------------------------------------------------ | ---- | -------------------- |
| value  | [PageTransitionOptions](#pagetransitionoptions) | Yes   | Parameters for configuring the entrance animation, including the route type (**type**), duration (**duration**), animation curve (**curve**), and animation delay (**delay**) of the page transition effect. |

### onEnter

onEnter(event: PageTransitionCallback): PageTransitionEnterInterface

Defines a frame-by-frame callback, which is invoked until the entrance animation ends, with **progress** changing from 0 to 1. When used together with preset animation methods such as **slide**, **translate**, **scale**, and **opacity**, **onEnter** provides frame-by-frame custom logic on top of the preset animation. It can also be used alone to implement a fully custom entrance animation effect.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                              | Mandatory| Description                                               |
| ------ | ----------------------------------------------------------------- | ---- | ------------------------------------------------    |
| event  | [PageTransitionCallback](#pagetransitioncallback18) | Yes   | Frame-by-frame callback of the entrance animation, invoked until the animation ends, with **progress** changing from 0 to 1. This callback is triggered only when the configured **type** matches the actual route type. |

**Example**

```js
  pageTransition() {
    PageTransitionEnter({ duration: 1200, curve: Curve.Linear })
      // During the transition animation, the entrance animation has a type that represents the route type, and a progress that increases from 0 to 1.
      .onEnter((type: RouteType, progress: number) => {
        // Service logic
      })
  }
```

## PageTransitionExit

Defines the **PageTransitionExit** component.

### PageTransitionExit

PageTransitionExit(value: PageTransitionOptions)

Sets the custom exit animation of the current page. It must be configured in the **pageTransition()** function and inherits from [CommonTransition](#commontransition).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                   | Mandatory| Description                |
| ------ | ------------------------------------------------------- | ---- | -------------------- |
| value  | [PageTransitionOptions](#pagetransitionoptions) | Yes   | Parameter for configuring the exit animation effect, including the route type (**type**), animation duration (**duration**), animation curve (**curve**), and animation delay (**delay**) of the page transition effect. |

### onExit

onExit(event: PageTransitionCallback): PageTransitionExitInterface

Defines a frame-by-frame callback, which is invoked until the exit animation ends, with **progress** changing from 0 to 1. When used together with preset animation methods such as **slide**, **translate**, **scale**, and **opacity**, **onExit** provides frame-by-frame custom logic on top of the preset animation. It can also be used alone to implement a fully custom exit animation effect.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                              | Mandatory| Description                                               |
| ------ | ----------------------------------------------------------------- | ---- | ------------------------------------------------    |
| event  | [PageTransitionCallback](#pagetransitioncallback18) | Yes   | Frame-by-frame callback of the exit animation, until the animation ends, with **progress** changing from 0 to 1. This callback is triggered only when the configured **type** matches the actual route type. |

**Example**

```js
  pageTransition() {
    PageTransitionExit({ duration: 1200, curve: Curve.Linear })
      // During the transition animation, the exit animation type is the route type, and progress gradually increases from 0 to 1.
      .onExit((type: RouteType, progress: number) => {
        // Service logic
      })
  }
```

## PageTransitionOptions

Defines the parameters of the exit/entrance animation.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Type                                                        | Read-Only| Optional| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ---- | ------------------------------------------------------------ |
| type     | [RouteType](#routetype)                              | No   | Yes   | Route type for which the page transition effect takes effect.<br>Default value: **RouteType.None**.<br>**Note:**<br>When multiple [PageTransitionEnter](#pagetransitionenter) or [PageTransitionExit](#pagetransitionexit) components are configured in the **pageTransition** function, they take effect according to the **RouteType** matching rule: the system selects the last matching component from all configured **PageTransitionEnter**/**PageTransitionExit** components based on the current route operation type (**Push** or **Pop**); if no component matches, the system default page transition effect is used (which may vary by device). If multiple **PageTransitionEnter** components match the same **RouteType**, the last configured one takes effect; if multiple **PageTransitionExit** components match the same **RouteType**, the last configured one takes effect. **RouteType.None** matches all route types.<br>Value selection principle: **None** indicates that it takes effect for all route types; **Push** takes effect only for push routes; **Pop** takes effect only for pop routes.    |
| duration | number                                                       | No   | Yes   | Duration of the animation.<br>Unit: ms<br>Default value: **1000**<br>Value range: [0, +∞)                 |
| curve    | [Curve](ts-appendix-enums.md#curve)&nbsp;\|&nbsp;string&nbsp;\|&nbsp;[ICurve](../js-apis-curve.md#icurve9)<sup>10+</sup> | No   | Yes   | Animation curve.<br>It is recommended to specify it in the form of **Curve** or **ICurve**.<br>When the type is string, it is the animation interpolation curve. For details about the value, see the **curve** parameter of [AnimateParam](./ts-explicit-animation.md#animateparam).<br>Default value: **Curve.Linear** |
| delay    | number                                                       | No   | Yes   | Animation delay.<br>Unit: ms<br>Default value: **0** |

## CommonTransition

Defines the common transition animation for page transitions, which is inherited and used by [PageTransitionEnter](#pagetransitionenter) and [PageTransitionExit](#pagetransitionexit). It must be configured in the **pageTransition()** function. Both **slide** and **translate** involve position movement: **slide** is suitable for scenarios that require sliding in and out along a preset direction (left/right/up/down/**START**/**END)** and is simple to use; **translate** is suitable for scenarios that require a custom translation distance and offers higher flexibility. When **slide** and **translate** are set simultaneously, **slide** takes effect by default. **scale** and **opacity** set the scale and opacity effects respectively, and can be combined with the effects above.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### constructor

constructor()

A constructor used to create a common transition animation.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### slide

slide(value: SlideEffect): T

Sets the slide-in and slide-out effect during page transition. When set simultaneously with **translate**, **slide** takes effect by default.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                                                        | Mandatory| Description                                                        |
| ------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| value   | [SlideEffect](#slideeffect) | Yes  | Slide-in and slide-out effects for page transitions.|

**Return value**

| Type  | Description                    |
| ------ | ------------------------ |
| T | Current component, used for chained calls. |

### translate

translate(value: TranslateOptions): T

Sets the translation effect for page transitions.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| value  | [TranslateOptions](ts-universal-attributes-transformation.md#translateoptions) | Yes   | Translation effect during page transition, which is the value at the start point when entering and at the end point when exiting. When set simultaneously with **slide**, **slide** takes effect by default.<br>-&nbsp;**x**: horizontal translation distance.<br>-&nbsp;**y**: vertical translation distance.<br>-&nbsp;**z**: z-axis translation distance. |

**Return value**

| Type  | Description                    |
| ------ | ------------------------ |
| T | Current component, used for chained calls. |

### scale

scale(value: ScaleOptions): T

Sets the scaling effect for page transitions.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| value  | [ScaleOptions](ts-universal-attributes-transformation.md#scaleoptions) | Yes   | Scale effect during page transition, which is the value at the start point when entering and at the end point when exiting.<br>-&nbsp;**x**: horizontal scale multiple (or scale ratio).<br>-&nbsp;**y**: vertical scale multiple (or scale ratio).<br>-&nbsp;**z**: depth scale multiple (or scale ratio).<br>-&nbsp;**centerX** and **centerY**: scale center point. The default values of **centerX** and **centerY** are **"50%"**, that is, the center point of the page is used as the scale center point by default.<br>-&nbsp;A center point of (0, 0) represents the upper left corner of the page. |

**Return value**

| Type  | Description                    |
| ------ | ------------------------ |
| T | Current component, used for chained calls. |

### opacity

opacity(value: number): T

Sets the starting opacity value for entrance or the ending opacity value for exit.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                                                        | Mandatory| Description                                                        |
| ------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| value   | number | Yes   | Start opacity value of the entrance animation or the end opacity value of the exit animation.<br>Value range: [0, 1] |

**Return value**

| Type  | Description                    |
| ------ | ------------------------ |
| T | Current component, used for chained calls. |

## PageTransitionCallback<sup>18+</sup>

type PageTransitionCallback = (type: RouteType, progress: number) => void

Represents the callback for page transition events.

**Atomic service API**: This API can be used in atomic services since API version 18.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type   | Mandatory| Description             |
| ------ | ------ | ---- | ---------------- |
| type | [RouteType](#routetype) | Yes | Route type for which the page transition effect takes effect. |
| progress | number | Yes| Transition progress, ranging from 0 to 1.|

## RouteType

Sets the type of page transition.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Atomic service API**: This API can be used in atomic services since API version 11.

| Name| Value| Description                                                        |
| ---- | ---- | -------------------------------------------------------- |
| None | 0 | The page is not redirected. For example, when **RouteType** is **None** as described in **Push** and **Pop**, the transition effect of **PageTransitionEnter** takes effect when the page enters, and the transition effect of **PageTransitionExit** takes effect when the page exits. |
| Push | 1 | Jumps to the next page, for example, from PageA to PageB. For PageA, the component style of **PageTransitionExit** with **RouteType** set to **None** or **Push** takes effect; for PageB, the component style of **PageTransitionEnter** with **RouteType** set to **None** or **Push** takes effect. |
| Pop  | 2 | Returns to the previous page, for example, from PageB to PageA. For PageB, the component style of **PageTransitionExit** with **RouteType** set to **None** or **Pop** takes effect; for PageA, the component style of **PageTransitionEnter** with **RouteType** set to **None** or **Pop** takes effect. |

## SlideEffect

Defines the slide-in and slide-out effects for page transitions.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name | Value | Description |
| ------------------- | ---- | -------------------------------------------------------- |
| Left | 1 | When set for entrance, it indicates sliding in from the left; when set for exit, it indicates sliding out to the left.<br>**Atomic service API:** Since API version 11, this interface is supported in atomic services. |
| Right | 2 | When set for entrance, it indicates sliding in from the right; when set for exit, it indicates sliding out to the right.<br>**Atomic service API:** Since API version 11, this interface is supported in atomic services. |
| Top | 3 | When set for entrance, it indicates sliding in from the top; when set for exit, it indicates sliding out to the top.<br>**Atomic service API:** Since API version 11, this interface is supported in atomic services. |
| Bottom | 4 | When set for entrance, it indicates sliding in from the bottom; when set for exit, it indicates sliding out to the bottom.<br>**Atomic service API:** Since API version 11, this interface is supported in atomic services. |
| START<sup>12+</sup> | 5 | When set for LTR entrance, it indicates sliding in from the left; for exit, it indicates sliding out to the left. When set for RTL entrance, it indicates sliding in from the right; for exit, it indicates sliding out to the right.<br>**Atomic service API:** Since API version 12, this interface is supported in atomic services.<br>**Model constraint:** This interface can be used only under the Stage model. |
| END<sup>12+</sup> | 6 | When set for LTR entrance, it indicates sliding in from the right; for exit, it indicates sliding out to the right. When set for RTL entrance, it indicates sliding in from the left; for exit, it indicates sliding out to the left.<br>**Atomic service API:** Since API version 12, this interface is supported in atomic services.<br>**Model constraint:** This interface can be used only under the Stage model. |

## Example

### Example 1: Configuring Entrance and Exit Animations

Custom method 1: Configure different exit and entrance animations through different exit/entrance types.

```ts
// Index.ets
@Entry
@Component
struct Index {
  @State pageScale: number = 1;
  @State pageOpacity: number = 1;

  build() {
    Column() {
      // Replace $r("app.media.transition_image1") with the image resource file you use.
      Image($r('app.media.transition_image1')).width('100%').height('100%')
    }
    .width('100%')
    .height('100%')
    .scale({ x: this.pageScale })
    .opacity(this.pageOpacity)
    .onClick(() => {
      this.getUIContext().getRouter().pushUrl({ url: 'pages/Page1' });
    })
  }

  pageTransition() {
    PageTransitionEnter({ duration: 1200, curve: Curve.Linear })
      .onEnter((type: RouteType, progress: number) => {
        if (type == RouteType.Push || type == RouteType.Pop) {
          this.pageScale = progress;
          this.pageOpacity = progress;
        }
      })
    PageTransitionExit({ duration: 1200, curve: Curve.Ease })
      .onExit((type: RouteType, progress: number) => {
        if (type == RouteType.Push) {
          this.pageScale = 1 - progress;
          this.pageOpacity = 1 - progress;
        }
      })
  }
}
```

```ts
// Page1.ets
@Entry
@Component
struct Page1 {
  @State pageScale: number = 1;
  @State pageOpacity: number = 1;

  build() {
    Column() {
      // Replace $r("app.media.transition_image2") with the image resource file you use.
      Image($r("app.media.transition_image2")).width('100%').height('100%') // Store the image in the media folder.
    }
    .width('100%')
    .height('100%')
    .scale({ x: this.pageScale })
    .opacity(this.pageOpacity)
    .onClick(() => {
      this.getUIContext().getRouter().pushUrl({ url: 'pages/Index' });
    })
  }

  pageTransition() {
    PageTransitionEnter({ duration: 1200, curve: Curve.Linear })
      .onEnter((type: RouteType, progress: number) => {
        if (type == RouteType.Push || type == RouteType.Pop) {
          this.pageScale = progress;
        }
        this.pageOpacity = progress;
      })
    PageTransitionExit({ duration: 1200, curve: Curve.Ease })
      .onExit((type: RouteType, progress: number) => {
        if (type == RouteType.Pop) {
          this.pageScale = 1 - progress;
          this.pageOpacity = 1 - progress;
        }
      })
  }
}
```

![pageTransition1](figures/pageTransition1.gif)

Method 2: The entrance animation of the current page is configured to slide in from the left, and the exit animation is configured to translate with opacity change.

```ts
// Index.ets 
@Entry
@Component
struct Index {
  build() {
    Column() {
      // Replace $r('app.media.bg1') with the image resource file you use.
      Image($r('app.media.bg1')).width('100%').height('100%') // The image is stored in the media folder.
    }
    .onClick(() => {
      this.getUIContext().getRouter().pushUrl({ url: 'pages/Page1' });
    })
  }

  // Use the default effects provided by the system (translation, scaling, opacity, etc.).
  pageTransition() {
    // Set the duration of the entrance animation to 1200 ms, to match the duration of the exit animation of the other page.
    PageTransitionEnter({ duration: 1200 })
      .slide(SlideEffect.Left)
    // Set the duration of the exit animation to 1000 ms, to match the duration of the entrance animation of the other page.
    PageTransitionExit({ duration: 1000 })
      .translate({ x: 100.0, y: 100.0 })
      .opacity(0)
  }
}
```

```ts
// Page1.ets
@Entry
@Component
struct Page1 {
  build() {
    Column() {
      // Replace $r('app.media.bg2') with the image resource file you use.
      Image($r('app.media.bg2')).width('100%').height('100%') // The image is stored in the media folder.
    }
    .onClick(() => {
      this.getUIContext().getRouter().pushUrl({ url: 'pages/Index' });
    })
  }

  // Custom method 2: use the various default effects provided by the system (translation, scaling, opacity, etc.).
  pageTransition() {
    // Set the duration of the entrance animation to 1000 ms, to match the duration of the exit animation of the other page.
    PageTransitionEnter({ duration: 1000 })
      .slide(SlideEffect.Left)
    // Set the duration of the exit animation to 1200 ms, to match the duration of the entrance animation of the other page.
    PageTransitionExit({ duration: 1200 })
      .translate({ x: 100.0, y: 100.0 })
      .opacity(0)
  }
}
```

![pageTransition2](figures/pageTransition2.gif)

### Example 2: Setting Translation Effects for Entrance and Exit

Method 1: Configure the various entrance and exit translation effects provided, with the system language layout mode set to right-to-left (RTL).

```ts
// Index.ets
@Entry
@Component
struct Index {
  @State pageScale: number = 1;
  @State pageOpacity: number = 1;

  build() {
    Column() {
      Button("Page 1").onClick(() => {
        this.getUIContext().getRouter().pushUrl({
          url: "pages/Page1"
        })
      })
        .width(200)
        .height(60)
        .fontSize(36)
      Text("START")
        .fontSize(36)
        .textAlign(TextAlign.Center)
    }
    .scale({ x: this.pageScale })
    .opacity(this.pageOpacity)
    .height("100%")
    .width("100%")
    .justifyContent(FlexAlign.Center)
  }

  // Custom method 2: use the various default effects provided by the system (translation, scaling, opacity, etc.).
  pageTransition() {
    // Set the entrance animation.
    PageTransitionEnter({ duration: 200 })
      .slide(SlideEffect.START)
    // Set the exit animation.
    PageTransitionExit({ delay: 100 })
      .slide(SlideEffect.START) // Left
  }
}
```

```ts
// Page1.ets
@Entry
@Component
struct Page1 {
  @State pageScale: number = 1;
  @State pageOpacity: number = 1;

  build() {
    Column() {
      Button("Page 2").onClick(() => {
        this.getUIContext().getRouter().pushUrl({
          url: "pages/Index"
        });
      })
        .width(200)
        .height(60)
        .fontSize(36)
      Text("END")
        .fontSize(36)
        .textAlign(TextAlign.Center)
    }
    .scale({ x: this.pageScale })
    .opacity(this.pageOpacity)
    .height("100%")
    .width("100%")
    .justifyContent(FlexAlign.Center)
  }

  // Custom method 2: use the multiple default effects provided by the system (translation, scaling, opacity, etc.).
  pageTransition() {
    PageTransitionEnter({ duration: 200 })
      .slide(SlideEffect.END) // Right
    PageTransitionExit({ delay: 100 })
      .slide(SlideEffect.END)
  }
}

```

![pageTransition1](figures/pageRTL.gif)

Customization method 2: Use the system's default entrance and exit effects, with the system language layout mode set to right-to-left (RTL).

```ts
// Index.ets
@Entry
@Component
struct Index {
  @State pageScale: number = 1;
  @State pageOpacity: number = 1;

  build() {
    Column() {
      Button("Page 1").onClick(() => {
        this.getUIContext().getRouter().pushUrl({
          url: "pages/Page1"
        });
      })
        .width(200)
        .height(60)
        .fontSize(36)
    }
    .scale({ x: this.pageScale })
    .opacity(this.pageOpacity)
    .height("100%")
    .width("100%")
    .justifyContent(FlexAlign.Center)
  }
}
```

```ts
// Page1.ets
@Entry
@Component
struct Page1 {
  @State pageScale: number = 1;
  @State pageOpacity: number = 1;

  build() {
    Column() {
      Button("Page 2").onClick(() => {
        this.getUIContext().getRouter().pushUrl({
          url: "pages/Index"
        });
      })
        .width(200)
        .height(60)
        .fontSize(36)
    }
    .scale({ x: this.pageScale })
    .opacity(this.pageOpacity)
    .height("100%")
    .width("100%")
    .justifyContent(FlexAlign.Center)
  }
}
```

![pageTransition1](figures/pageRTL2.gif)
