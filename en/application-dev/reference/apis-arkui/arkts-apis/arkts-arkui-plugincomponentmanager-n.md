# pluginComponentManager(PluginComponentManager)

Implements a plugin component manager.

**Since:** 8

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { pluginComponentManager, PluginComponentTemplate } from '@kit.ArkUI';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [push](arkts-arkui-plugincomponentmanager-push-f.md) | Pushes the component and data to the component user. |
| [request](arkts-arkui-plugincomponentmanager-request-f.md) | Requests the component from the component provider. |
| [on](arkts-arkui-plugincomponentmanager-on-f.md) | Listens for events of the request type and returns the requested data, or listens for events of the push type and receives the data pushed by the provider. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [push](arkts-arkui-plugincomponentmanager-push-f-sys.md) | Plugin component push method used to send the information of the template it provides. |
| [request](arkts-arkui-plugincomponentmanager-request-f-sys.md) | Plugin component request method used to send a request for the information of the template it wants. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [PushParameters](arkts-arkui-plugincomponentmanager-pushparameters-i.md) | Defines the parameters required when using the **PluginManager.Push** API. |
| [RequestParameters](arkts-arkui-plugincomponentmanager-requestparameters-i.md) | Defines the parameters required when using the **PluginManager.Request** API. |
| [RequestCallbackParameters](arkts-arkui-plugincomponentmanager-requestcallbackparameters-i.md) | Provides the result returned after the **PluginManager.Request** API is called. |
| [RequestEventResult](arkts-arkui-plugincomponentmanager-requesteventresult-i.md) | Provides the result returned after the request listener is registered and the requested event is received. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [PushParameterForStage](arkts-arkui-plugincomponentmanager-pushparameterforstage-i-sys.md) | Plugin component push parameters which is used in push function. |
| [RequestParameterForStage](arkts-arkui-plugincomponentmanager-requestparameterforstage-i-sys.md) | Plugin component request parameters which is used in request function. |
<!--DelEnd-->

### Types

| Name | Description |
| --- | --- |
| [KVObject](arkts-arkui-plugincomponentmanager-kvobject-t.md) | Defines a key-value pair data structure that conforms to JSON format. |
| [OnPushEventCallback](arkts-arkui-plugincomponentmanager-onpusheventcallback-t.md) | Registers the listener for the push event. |
| [OnRequestEventCallback](arkts-arkui-plugincomponentmanager-onrequesteventcallback-t.md) | Registers the listener for the request event. |
