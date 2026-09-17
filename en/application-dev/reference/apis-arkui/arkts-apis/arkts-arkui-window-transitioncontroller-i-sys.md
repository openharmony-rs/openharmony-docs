# TransitionController (System API)

Implements the transition animation controller. Before calling any API, you must create a system window. For details, see the sample code.

**Since:** 9

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## animationForHidden

```TypeScript
animationForHidden(context: TransitionContext): void
```

Customizes the animation for the scenario when the window is hidden.

**Since:** 9

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [TransitionContext](arkts-arkui-window-transitioncontext-i-sys.md) | Yes | Context of the transition animation. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Examples**

```TypeScript
// xxx.ts
export class AnimationConfig {
  private animationForHiddenCallFunc_: ((context : window.TransitionContext) => void) | undefined = undefined;
  HideWindowWithCustomAnimation(windowClass: window.Window, callback: (context : window.TransitionContext) => void) {
    if (!windowClass) {
      console.error('windowClass is undefined');
      return false;
    }
    this.animationForHiddenCallFunc_ = callback;
    let controller: window.TransitionController = windowClass.getTransitionController();
    controller.animationForHidden = (context : window.TransitionContext)=> {
      this.animationForHiddenCallFunc_(context);
    };
    windowClass.hideWithAnimation(()=>{
      console.info('hide with animation success');
    });
  }
}
```

```TypeScript
// xxx.ets
let animationConfig = new AnimationConfig();
let systemTypeWindow = window.findWindow("systemTypeWindow"); // Obtain a system window.
try {
  animationConfig?.HideWindowWithCustomAnimation(systemTypeWindow, (context : window.TransitionContext)=>{
    console.info('complete transition end');
    let toWindow = context.toWindow;
    this.getUIContext()?.animateTo({
      duration: 1000, // Animation duration.
      tempo: 0.5, // Playback speed.
      curve: Curve.EaseInOut, // Animation curve.
      delay: 0, // Animation delay.
      iterations: 1, // Number of playback times.
      playMode: PlayMode.Normal // Animation playback mode.
      onFinish: () => {
        console.info('onFinish in animation');
        context.completeTransition(true)
      }
    }, () => {
      let translateOptions : window.TranslateOptions = {
        x : 100.0,
        y : 0.0,
        z : 0.0
      };
      toWindow?.translate(translateOptions); // Set the transition animation.
      console.info('toWindow translate end in animation');
    });
    console.info('complete transition end');
  });
} catch (error) {
  console.error(`HideWindowWithCustomAnimation error code: ${error.code}, message: ${error.message}` );
}
```

## animationForShown

```TypeScript
animationForShown(context: TransitionContext): void
```

Customizes the animation for the scenario when the window is shown.

**Since:** 9

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [TransitionContext](arkts-arkui-window-transitioncontext-i-sys.md) | Yes | Context of the transition animation. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API.<br>**Applicable version:** 12 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Examples**

```TypeScript
// xxx.ts
export class AnimationConfig {
  private animationForShownCallFunc_: ((context : window.TransitionContext) => void) | undefined = undefined;
  ShowWindowWithCustomAnimation(windowClass: window.Window, callback: (context : window.TransitionContext) => void) {
    if (!windowClass) {
      console.error('windowClass is undefined');
      return false;
    }
    this.animationForShownCallFunc_ = callback;
    let controller: window.TransitionController = windowClass.getTransitionController();
    controller.animationForShown = (context : window.TransitionContext)=> {
      this.animationForShownCallFunc_(context);
    };
    windowClass.showWithAnimation(()=>{
      console.info('Show with animation success');
    });
  }
}
```

```TypeScript
// xxx.ets
let animationConfig = new AnimationConfig();
let systemTypeWindow = window.findWindow("systemTypeWindow"); // Obtain a system window.
try {
  animationConfig?.ShowWindowWithCustomAnimation(systemTypeWindow, (context : window.TransitionContext)=>{
    console.info('complete transition end');
    let toWindow = context.toWindow;
    this.getUIContext()?.animateTo({
      duration: 1000, // Animation duration.
      tempo: 0.5, // Playback speed.
      curve: Curve.EaseInOut, // Animation curve.
      delay: 0, // Animation delay.
      iterations: 1, // Number of playback times.
      playMode: PlayMode.Normal // Animation playback mode.
      onFinish: () => {
        console.info('onFinish in animation');
        context.completeTransition(true)
      }
    }, () => {
      let translateOptions : window.TranslateOptions = {
        x : 100.0,
        y : 0.0,
        z : 0.0
      };
      toWindow?.translate(translateOptions); // Set the transition animation.
      console.info('toWindow translate end in animation');
    });
    console.info('complete transition end');
  });
} catch (error) {
  console.error(`ShowWindowWithCustomAnimation error code: ${error.code}, message: ${error.message}`);
}
```
