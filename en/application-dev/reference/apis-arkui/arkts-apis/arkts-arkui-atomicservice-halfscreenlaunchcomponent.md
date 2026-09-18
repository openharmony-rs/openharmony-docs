# @ohos.atomicservice.HalfScreenLaunchComponent(Defines the halfScreen launch component)

## Child Components

Not supported

## Attributes

The universal attributes are not supported.

## Modules to Import

```TypeScript
import { HalfScreenLaunchComponent } from '@kit.ArkUI';
```

## Summary

### Structs

| Name | Description |
| --- | --- |
| [HalfScreenLaunchComponent](arkts-arkui-atomicservice-halfscreenlaunchcomponent-halfscreenlaunchcomponent-s.md) | **HalfScreenLaunchComponent** is a component designed for launching atomic services in half screen. If the invoked application (the one being launched) grants the invoker the authorization to run the atomic service in an embedded manner, the invoker can operate the atomic service in half-screen embedded mode. If authorization is not provided, the invoker will launch the atomic service in a pop-up manner. |

## Examples

```TypeScript
This example demonstrates how to start a top-up service in embedded mode.

> NOTE
> 
> Embedded atomic services run in separate processes, so their crashes and exceptions are not visible directly in the host's logs. Follow the steps below to view the complete error stack trace during local debugging:
> 
> Open the HiLog panel in DevEco Studio.
> 
> Switch the mode in the top-left corner to User logs of selected app.
> 
> In the process list on the right, select the process of the launched atomic service. The bundle name has embeddable within its suffix segment.
```
