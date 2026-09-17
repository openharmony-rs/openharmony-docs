# AnimationController

Implements an animation controller object. It provides APIs for playing, stopping, resuming, and pausing animations, as well as querying the status.

**Since:** 21

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { DrawableDescriptor, LayeredDrawableDescriptor, PixelMapDrawableDescriptor, AnimationOptions, AnimatedDrawableDescriptor, AnimationController, DrawableDescriptorLoadedResult, AnimationStopMode, PictureDrawableDescriptor, HdrCompositionConfig } from '@kit.ArkUI';
```

## getStatus

```TypeScript
getStatus(): AnimationStatus
```

Obtains the current animation playback status.

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [AnimationStatus](arkts-arkui-animationstatus-e.md) | Current animation state: initial, running, paused, or stopped. |

**Examples**

```TypeScript
import { AnimationOptions, AnimatedDrawableDescriptor } from '@kit.ArkUI';

@Entry
@Component
struct Example {
  options: AnimationOptions = { duration: 1000, iterations: -1 };
  // Replace $r('app.media.gif') with the image resource file you use.
  @State animated: AnimatedDrawableDescriptor = new AnimatedDrawableDescriptor($r('app.media.gif'), this.options);

  statusToString(status: AnimationStatus): string {
    switch (status) {
      case AnimationStatus.Initial:
        return "Initial"
      case AnimationStatus.Running:
        return "Running"
      case AnimationStatus.Paused:
        return "Paused"
      case AnimationStatus.Stopped:
        return "Stopped"
      default:
        return "Error"
    }
  }

  build() {
    Column() {
      Image(this.animated)
        .width(100)
        .height(100)
        .onClick(() => {
          let controller = this.animated.getAnimationController()
          // Obtain the current animation playback status.
          let status = controller?.getStatus()
          console.info(`animation status = ${this.statusToString(status)}`)
        })
    }
  }
}
```

## pause

```TypeScript
pause(): void
```

Pauses playback on the current frame.

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Examples**

```TypeScript
import { AnimationOptions, AnimatedDrawableDescriptor } from '@kit.ArkUI';

@Entry
@Component
struct Example {
  options: AnimationOptions = { duration: 1000, iterations: -1 };
  // Replace $r('app.media.gif') with the image resource file you use.
  @State animated: AnimatedDrawableDescriptor = new AnimatedDrawableDescriptor($r('app.media.gif'), this.options);

  build() {
    Column() {
      Image(this.animated)
        .width(100)
        .height(100)
        .onClick(() => {
          let controller = this.animated.getAnimationController()
          // Pause playback on the current frame.
          controller?.pause()
        })
    }
  }
}
```

## resume

```TypeScript
resume(): void
```

Resumes playback from the current frame.

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Examples**

```TypeScript
import { AnimationOptions, AnimatedDrawableDescriptor } from '@kit.ArkUI';

@Entry
@Component
struct Example {
  options: AnimationOptions = { duration: 1000, iterations: -1 };
  // Replace $r('app.media.gif') with the image resource file you use.
  @State animated: AnimatedDrawableDescriptor = new AnimatedDrawableDescriptor($r('app.media.gif'), this.options);

  build() {
    Column() {
      Image(this.animated)
        .width(100)
        .height(100)
        .onClick(() => {
          let controller = this.animated.getAnimationController()
          // Start playback from the current frame when the animated image is paused or stopped.
          controller?.resume()
        })
    }
  }
}
```

## start

```TypeScript
start(): void
```

Starts playback from the first frame.

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Examples**

```TypeScript
import { AnimationOptions, AnimatedDrawableDescriptor } from '@kit.ArkUI';

@Entry
@Component
struct Example {
  options: AnimationOptions = { duration: 1000, iterations: -1, autoPlay: false };
  // Replace $r('app.media.gif') with the image resource file you use.
  @State animated: AnimatedDrawableDescriptor = new AnimatedDrawableDescriptor($r('app.media.gif'), this.options);

  build() {
    Column() {
      Image(this.animated)
        .width(100)
        .height(100)
        .onClick(() => {
          let controller = this.animated.getAnimationController()
          // Start playback.
          controller?.start()
        })
    }
  }
}
```

## stop

```TypeScript
stop(): void
```

Stops playback and resets to the first frame.

**Since:** 21

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Examples**

```TypeScript
import { AnimationOptions, AnimatedDrawableDescriptor } from '@kit.ArkUI';

@Entry
@Component
struct Example {
  options: AnimationOptions = { duration: 1000, iterations: -1 };
  // Replace $r('app.media.gif') with the image resource file you use.
  @State animated: AnimatedDrawableDescriptor = new AnimatedDrawableDescriptor($r('app.media.gif'), this.options);

  build() {
    Column() {
      Image(this.animated)
        .width(100)
        .height(100)
        .onClick(() => {
          let controller = this.animated.getAnimationController()
          // Stop playback and reset to the first frame.
          controller?.stop()
        })
    }
  }
}
```
