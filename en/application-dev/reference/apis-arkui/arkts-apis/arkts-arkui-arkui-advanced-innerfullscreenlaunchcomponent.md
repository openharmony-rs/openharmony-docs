# @ohos.arkui.advanced.InnerFullScreenLaunchComponent(System API)

## Child Components

Not supported

## Attributes

The universal attributes are not supported.

## Events

The universal events are not supported.

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

```TypeScript
> NOTE
> 
> Because the embedded atomic service runs in an independent process, its crash exceptions are not directly exposed in the host's logs. During local debugging, you can view the actual error stack as follows:
> 
> Open the HiLog panel in DevEco Studio.
> 
> Switch the mode in the upper left corner to User logs of selected app.
> 
> In the process list on the right, select the launched atomic service process (the bundle name of the launched atomic service, with the suffix "embeddable").
```
