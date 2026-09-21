# RemoteWindow (System API)

Defines RemoteWindow Component.

## RemoteWindow

```TypeScript
RemoteWindow(target: WindowAnimationTarget)
```

Called when the remote window interface is used.

**Since:** 9

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| target | [WindowAnimationTarget](arkts-arkui-remotewindow-comp-windowanimationtarget-i-sys.md) | Yes |  |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [RRect](arkts-arkui-remotewindow-comp-rrect-i-sys.md) | Round rect. |
| [WindowAnimationTarget](arkts-arkui-remotewindow-comp-windowanimationtarget-i-sys.md) | Window animation target. |

## Examples

The RemoteWindow component needs to receive the WindowAnimationTarget object from the WindowAnimationController object set by windowAnimationManager. You can create a RemoteWindowExample.ets file as an example to encapsulate the RemoteWindow component and the passed WindowAnimationTarget object.

Since RemoteWindow can be used only in the system application Launcher, you can place the RemoteWindowExample component in the build function of the EntryView.ets page of Launcher, compile Launcher, and then push the Launcher installation package to the device system for running.

```TypeScript
// WindowAnimationControllerImpl.ets file
import { windowAnimationManager } from '@kit.ArkUI';

export default class WindowAnimationControllerImpl implements windowAnimationManager.WindowAnimationController {
  private callback: (target: windowAnimationManager.WindowAnimationTarget) => void = () => {}

  OnTargetUpdate(callback: (target: windowAnimationManager.WindowAnimationTarget) => void)
  {
    this.callback = callback;
  }

  private NotifyTargetUpdate(target: windowAnimationManager.WindowAnimationTarget)
  {
    this.callback(target);
  }

  onStartAppFromLauncher(startingWindowTarget: windowAnimationManager.WindowAnimationTarget,
                         finishedCallback: windowAnimationManager.WindowAnimationFinishedCallback): void
  {
    console.info(`remote window animation onStartAppFromLauncher`);
    this.NotifyTargetUpdate(startingWindowTarget);
    finishedCallback.onAnimationFinish();
  }

  onStartAppFromRecent(startingWindowTarget: windowAnimationManager.WindowAnimationTarget,
                       finishedCallback: windowAnimationManager.WindowAnimationFinishedCallback): void {
    console.info(`remote window animation onStartAppFromRecent`);
    this.NotifyTargetUpdate(startingWindowTarget);
    finishedCallback.onAnimationFinish();
  }

  onStartAppFromOther(startingWindowTarget: windowAnimationManager.WindowAnimationTarget,
                      finishedCallback: windowAnimationManager.WindowAnimationFinishedCallback): void {
    console.info(`remote window animation onStartAppFromOther`);
    this.NotifyTargetUpdate(startingWindowTarget);
    finishedCallback.onAnimationFinish();
  }

  onAppTransition(fromWindowTarget: windowAnimationManager.WindowAnimationTarget,
                  toWindowTarget: windowAnimationManager.WindowAnimationTarget,
                  finishedCallback: windowAnimationManager.WindowAnimationFinishedCallback): void{
    console.info(`remote window animation onAppTransition`);
    this.NotifyTargetUpdate(fromWindowTarget);
    finishedCallback.onAnimationFinish();
  }

  onMinimizeWindow(minimizingWindowTarget: windowAnimationManager.WindowAnimationTarget,
                   finishedCallback: windowAnimationManager.WindowAnimationFinishedCallback): void {
    console.info(`remote window animation onMinimizeWindow`);
    this.NotifyTargetUpdate(minimizingWindowTarget);
    finishedCallback.onAnimationFinish();
  }

  onCloseWindow(closingWindowTarget: windowAnimationManager.WindowAnimationTarget,
                finishedCallback: windowAnimationManager.WindowAnimationFinishedCallback): void {
    console.info(`remote window animation onCloseWindow`);
    this.NotifyTargetUpdate(closingWindowTarget);
    finishedCallback.onAnimationFinish();
  }

  onScreenUnlock(finishedCallback: windowAnimationManager.WindowAnimationFinishedCallback): void {
    console.info(`remote window animation onScreenUnlock`);
    finishedCallback.onAnimationFinish();
  }

  onWindowAnimationTargetsUpdate(fullScreenWindowTarget: windowAnimationManager.WindowAnimationTarget, 
                              floatingWindowTargets: Array<windowAnimationManager.WindowAnimationTarget>): void {
    console.info('onWindowAnimationTargetsUpdate, the fullScreenWindowTarget is: ' + fullScreenWindowTarget);
    console.info('onWindowAnimationTargetsUpdate, the floatingWindowTargets are: ' + floatingWindowTargets);
  }
}
```

```TypeScript
// RemoteWindowExample.ets file
import { windowAnimationManager } from '@kit.ArkUI';
import WindowAnimationControllerImpl from './WindowAnimationControllerImpl';

@Entry
@Component
export default struct RemoteWindowExample {
  @State target:WindowAnimationTarget | undefined = undefined // Obtained through windowAnimationManager.

  aboutToAppear(): void {
    let controller: WindowAnimationControllerImpl = new WindowAnimationControllerImpl();
    windowAnimationManager.setController(controller);
    controller.OnTargetUpdate((target: windowAnimationManager.WindowAnimationTarget) => {
      this.target = target;
    });
  }

  build() {
    Column() {
      if(this.target){
        RemoteWindow(this.target)
          .scale({ x: 0.5, y: 0.5 }) // Used for demonstration purposes only. In general cases, scale({ x: 1, y: 1 }) is required.
          .position({ x: this.getUIContext().px2vp(this.target?.windowBounds.left), y: this.getUIContext().px2vp(this.target?.windowBounds.top) })
          .width(this.getUIContext().px2vp(this.target?.windowBounds.width))
          .height(this.getUIContext().px2vp(this.target?.windowBounds.height))
      }
     }
  }
}
```
