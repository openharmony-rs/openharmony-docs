# @ohos.arkui.advanced.InnerFullScreenLaunchComponent(System API)

## Child Components

Not supported

## Attributes

The [universal attributes](../arkts-components/arkts-arkui-common-comp.md#common) are not supported.

## Events

The [universal events](../arkts-components/arkts-arkui-common-comp.md#common) are not supported.

## Modules to Import

```TypeScript
import { InnerFullScreenLaunchComponent, LaunchController } from '@kit.ArkUI';
```

## Summary

<!--Del-->
### Classes(System API)

| Name | Description |
| --- | --- |
| [LaunchController](arkts-arkui-arkui-advanced-innerfullscreenlaunchcomponent-launchcontroller-c-sys.md) | Controller for launching the atomic service. |
<!--DelEnd-->

<!--Del-->
### Structs(System API)

| Name | Description |
| --- | --- |
| [InnerFullScreenLaunchComponent](arkts-arkui-arkui-advanced-innerfullscreenlaunchcomponent-innerfullscreenlaunchcomponent-s-sys.md) | **InnerFullScreenLaunchComponent** is a component that allows the invoker to choose the timing for launching an atomic service. If the invoked app (the one being launched) grants the invoker the authorization to run the atomic service in an embedded manner, the invoker can operate the atomic service in full-screen embedded mode. If authorization is not provided, the invoker will launch the atomic service in a pop-up manner. |
<!--DelEnd-->

<!--Del-->
### Types(System API)

| Name | Description |
| --- | --- |
| [LaunchAtomicServiceCallback](arkts-arkui-launchatomicservicecallback-t-sys.md) | Triggered when an atomic service is launched. |
<!--DelEnd-->

## Examples

> NOTE
> 
> Because the embedded atomic service runs in an independent process, its crash exceptions are not directly exposed in the host's logs. During local debugging, you can view the actual error stack as follows:
> 
> Open the HiLog panel in DevEco Studio.
> 
> Switch the mode in the upper left corner to User logs of selected app.
> 
> In the process list on the right, select the launched atomic service process (the bundle name of the launched atomic service, with the suffix "embeddable").

```TypeScript
import { InnerFullScreenLaunchComponent, LaunchController } from '@kit.ArkUI';

@Entry
@Component
struct Index {

  @Builder
  ColumnChild() {
    Column() {
      Text('InnerFullScreenLaunchComponent').fontSize(16).margin({top: 100})
      Button('Start Sunrise/Sunset')
        .onClick(() => {
          let appId1: string = '576****************';
          this.controller.launchAtomicService(appId1, {});
        }).height(30).width('50%').margin({top: 50})
      Button('Start Top-up')
        .onClick(() => {
          let appId2: string = '576****************';
          this.controller.launchAtomicService(appId2, {});
        }).height(30).width('50%').margin({top: 50})
    }.backgroundColor(Color.Pink).height('100%').width('100%')
  }
  controller: LaunchController = new LaunchController();

  build() {
    Column() {
      InnerFullScreenLaunchComponent({
          content: this.ColumnChild,
          controller: this.controller,
          onReceive: (data) => {
            console.info('onReceive, data: ' + JSON.stringify(data['ohos.atomicService.window']));
          },
          onError: (err: BusinessError) => {
            console.error(`onError, code: ${err.code}, message: ${err.message}`);
          },
          onTerminated: (info: TerminationInfo) => {
            console.info('onTerminated, info: ' + JSON.stringify(info));
          }
        })
    }
    .width('100%').height('100%')
  }
}
```
