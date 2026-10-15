# pluginComponentManager(PluginComponentManager)

```TypeScript
declare namespace pluginComponentManager
```

Implements a plugin component manager, which provides management capabilities such as requesting, pushing, and event listening for plug-in components.

**Since:** 8

<!--Device-unnamed-declare namespace pluginComponentManager--><!--Device-unnamed-declare namespace pluginComponentManager-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { pluginComponentManager, PluginComponentTemplate } from '@kit.ArkUI';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [on](arkts-arkui-plugincomponentmanager-on-f.md) | Listens for events of the request type and returns the requested data, or listens for events of the push type and receives the data pushed by the provider. |
| [push](arkts-arkui-plugincomponentmanager-push-f.md#push1) | Pushes the component and data to the component user. This API is applicable to scenarios where the provider needs to proactively notify the user to refresh the display after data is updated. <br>Cooperation method: The user must first call [on('push', callback)](../../../reference/apis-arkui/js-apis-plugincomponent.md#plugincomponentmanageron) to register a push event listener before receiving the components and data pushed through this API. If the user does not register the listener, the pushed data cannot be received. |
| [request](arkts-arkui-plugincomponentmanager-request-f.md#request1) | Requests the component from the component provider. This API is applicable to scenarios where the user needs to obtain the provider's components and data on demand. <br>Cooperation method: The provider must first call [on('request', callback)](../../../reference/apis-arkui/js-apis-plugincomponent.md#plugincomponentmanageron) to register a request event listener before receiving the request initiated by the user through this API and returning data. If the provider does not register the listener, the request cannot be responded to. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [push](arkts-arkui-plugincomponentmanager-push-f-sys.md#push2) | Proactively pushes the component and data to the component user. This API applies to scenarios where the plug-in component template needs to be proactively pushed, for example, cross-application content sharing and proactive refresh of home screen cards. **push** is proactively initiated by the component provider, while **request** is proactively initiated by the component user. Note that the two have similar parameter structures but opposite meanings of **owner** and **target**, so do not confuse them. The component user must listen for the received data through the **onPush** event. For details about the event listener API, see [@ohos.pluginComponent (PluginComponentManager)](../../../reference/apis-arkui/js-apis-plugincomponent.md#plugincomponentmanageron). |
| [request](arkts-arkui-plugincomponentmanager-request-f-sys.md#request2) | Requests the component from the component provider. This API applies to scenarios where the component user needs to dynamically obtain the plug-in component template on demand, for example, dynamically loading plug-in content provided by other applications and displaying cross-application components on demand. The component provider must listen for the request response through the **onRequest** event, and return the component template information through a callback. For details about the event listener API, see [@ohos.pluginComponent (PluginComponentManager)](../../../reference/apis-arkui/js-apis-plugincomponent.md#plugincomponentmanageron). |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [PushParameters](arkts-arkui-plugincomponentmanager-pushparameters-i.md) | Defines the parameters required when using the **pluginComponentManager.push** API. |
| [RequestCallbackParameters](arkts-arkui-plugincomponentmanager-requestcallbackparameters-i.md) | Provides the result returned after the **pluginComponentManager.request** API is called. |
| [RequestEventResult](arkts-arkui-plugincomponentmanager-requesteventresult-i.md) | Provides the data type used to respond to a request event after the request listener is registered. |
| [RequestParameters](arkts-arkui-plugincomponentmanager-requestparameters-i.md) | Defines the parameters required when using the **pluginComponentManager.request** API. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [PushParameterForStage](arkts-arkui-plugincomponentmanager-pushparameterforstage-i-sys.md) | Sets the parameters to be passed in the **pluginComponentManager.push** API in the stage model. |
| [RequestParameterForStage](arkts-arkui-plugincomponentmanager-requestparameterforstage-i-sys.md) | Sets the parameters to be passed in the **pluginComponentManager.request** API in the stage model. |
<!--DelEnd-->

### Types

| Name | Description |
| --- | --- |
| [KVObject](arkts-arkui-plugincomponentmanager-kvobject-t.md) | Stores information in the form of key-value pairs, conforming to the JSON format. |
| [OnPushEventCallback](arkts-arkui-plugincomponentmanager-onpusheventcallback-t.md) | Registers the listener for the push event. |
| [OnRequestEventCallback](arkts-arkui-plugincomponentmanager-onrequesteventcallback-t.md) | Registers the listener for the request event. |
