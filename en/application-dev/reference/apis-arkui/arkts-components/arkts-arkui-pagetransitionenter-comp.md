# PageTransitionEnter

Defines PageTransitionEnter Component.

## PageTransitionEnter

```TypeScript
PageTransitionEnter(value: PageTransitionOptions)
```

Sets the page entrance animation.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [PageTransitionOptions](arkts-arkui-pagetransitionoptions-i.md) | Yes | pageTransition options |

## PageTransitionEnter

```TypeScript
PageTransitionEnter(event: PageTransitionCallback)
```

Invoked on a per-frame basis until the entrance animation is complete, with the **progress** parameter changing from 0 to 1.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [PageTransitionCallback](arkts-arkui-pagetransitioncallback-t.md) | Yes | Callback invoked on a per-frame basis until the entrance animation is complete, with the **progress** parameter changing from 0 to 1. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [PageTransitionExitInterface](arkts-arkui-pagetransitionexitinterface-i.md) | Provide an interface to set transition style when a page exits. |
| [PageTransitionOptions](arkts-arkui-pagetransitionoptions-i.md) | Parameters of the exit or entrance animation. |

### Types

| Name | Description |
| --- | --- |
| [PageTransitionCallback](arkts-arkui-pagetransitioncallback-t.md) | Represents the callback for page transition events. |

### Enums

| Name | Description |
| --- | --- |
| [RouteType](arkts-arkui-routetype-e.md) | Sets the type of page transition. |
| [SlideEffect](arkts-arkui-slideeffect-e.md) | Slide-in and slide-out effects for page transitions. |

## Examples

```TypeScript
### Example 1: Configuring Entrance and Exit Animations

Custom method 1: Configure different exit and entrance animations through different exit/entrance types.
```

```TypeScript
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

```TypeScript


Method 2: The entrance animation of the current page is configured to slide in from the left, and the exit animation is configured to translate with opacity change.
```

```TypeScript

```

```TypeScript
### Example 2: Setting Translation Effects for Entrance and Exit

Method 1: Configure the various entrance and exit translation effects provided, with the system language layout mode set to right-to-left (RTL).
```

```TypeScript
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

```TypeScript


Customization method 2: Use the system's default entrance and exit effects, with the system language layout mode set to right-to-left (RTL).
```

```TypeScript
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
