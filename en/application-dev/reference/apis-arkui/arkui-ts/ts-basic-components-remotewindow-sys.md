# RemoteWindow (System API)

<!--Kit: ArkUI-->
<!--Subsystem: Graphic-->
<!--Owner: @xubo85-->
<!--Designer: @comicchang; @chensiyi_CE-->
<!--Tester: @zhaoxiaoguang2-->
<!--Adviser: @ge-yafang-->

**RemoteWindow** is a component used to control the application window, providing the component animator and application window animation linkage during application startup and exit.

>  **NOTE**
>  
>  This component is supported since API version 9. Updates will be marked with a superscript to indicate their earliest API version.
>
>  The APIs provided by this module are system APIs.

## Child Components

Not supported

## APIs

RemoteWindow(target: WindowAnimationTarget)

Creates a **RemoteWindow** through a window animation object.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory | Description|
| -------- | -------- | --------------- | -------- |
| target | [WindowAnimationTarget](#windowanimationtarget) | Yes  | Description of the animation window to control.|

## WindowAnimationTarget

Implements a target window, which is used to remotely control the animation.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only | Optional| Description|
| ------- | ------ | ------ | ------ | ----------------------- |
| bundleName   | string          | Yes| No| Process corresponding to the animation window.|
| abilityName  | string          | Yes| No| Ability corresponding to the animation window.|
| windowBounds | [RRect](#rrect) | Yes| No| Actual size of the animation window.|
| missionId    | number          | Yes| No| Mission ID.|

## RRect

Implements a rounded rectangle.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only | Optional| Description|
| ------- | ------ | ------ | ------ | ----------------------- |
| left   | number | No| No| Horizontal coordinate of the upper left corner of the animation window relative to the screen.|
| top    | number | No| No| Vertical coordinate of the upper left corner of the animation window relative to the screen.|
| width  | number | No| No| Width of the animation window.|
| height | number | No| No| Height of the animation window.|
| radius | number | No| No| Radius of the rounded corner of the animation window.|

## Attributes

The [universal attributes](ts-component-general-attributes.md) are supported.

## Events

The [universal events](ts-component-general-events.md) are supported.

## Example
The **RemoteWindow** component needs to receive the **WindowAnimationTarget** object from the **WindowAnimationController** object set by [windowAnimationManager](../js-apis-windowAnimationManager-sys.md). You can create a **RemoteWindowExample.ets** file as an example to encapsulate the **RemoteWindow** component and the passed **WindowAnimationTarget** object.
The **RemoteWindow** component can be used only in the system home screen application. Therefore, you can place the **RemoteWindowExample** component in the **build** function of the **EntryView.ets** page of the home screen application, compile the application, and push the application installation package to the device.

```ts
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

```ts
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
          .scale({ x: 0.5, y: 0.5}) // Used for demonstration purposes only. .In general cases, scale({ x: 1, y: 1 }) is required.
          .position({ x: this.getUIContext().px2vp(this.target?.windowBounds.left), y: this.getUIContext().px2vp(this.target?.windowBounds.top) })
          .width(this.getUIContext().px2vp(this.target?.windowBounds.width))
          .height(this.getUIContext().px2vp(this.target?.windowBounds.height))
      }
     }
  }
}
```
