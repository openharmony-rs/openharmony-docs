# @ohos.arkui.advanced.FullScreenLaunchComponent(Defines the fullScreen launch component)

## Child Components

Not supported

## Attributes

The universal attributes are not supported.

## Events

The universal events are not supported.

## Modules to Import

```TypeScript
import { FullScreenLaunchComponent } from '@kit.ArkUI';
```

## Summary

### Structs

| Name | Description |
| --- | --- |
| [FullScreenLaunchComponent](arkts-arkui-arkui-advanced-fullscreenlaunchcomponent-fullscreenlaunchcomponent-s.md) | **FullScreenLaunchComponent** is a component designed for launching atomic services in full screen. If the invoked app (the one being launched) grants the invoker the authorization to run the atomic service in an embedded manner, the invoker can operate the atomic service in full-screen embedded mode. If authorization is not provided, the invoker will launch the atomic service in a pop-up manner. |

## Examples

```TypeScript
This example demonstrates how to use the component and how to implement the provider-side atomic service. In actual running, use the appId of your own atomic service.

The FullScreenLaunchComponent component must be invoked by the invoker. After the provider completes local installation, the provider's atomic service can be launched in full-screen embedded mode in the invoker's app or atomic service.

> NOTE
> 
> Because the embedded atomic service runs in an independent process, its crash exceptions are not directly exposed in the host's logs. During local debugging, you can view the actual error stack as follows:
> 
> Open the HiLog panel in DevEco Studio.
> 
> Switch the mode in the upper left corner to User logs of selected app.
> 
> In the process list on the right, select the launched atomic service process (the bundle name of the launched atomic service, with the suffix "embeddable").

User Implementation
```

```TypeScript
Provider Implementation

You need to modify the following files for the atomic service provider:

Entry point file: /src/main/ets/entryability/EntryAbility.ets
```

```TypeScript
Extended ability entry page file: /src/main/ets/pages/Index.ets
```
