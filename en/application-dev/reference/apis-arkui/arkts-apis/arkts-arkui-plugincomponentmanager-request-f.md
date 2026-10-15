# request

## Modules to Import

```TypeScript
import { pluginComponentManager, PluginComponentTemplate } from '@kit.ArkUI';
```

<a id="request1"></a>

## request

```TypeScript
function request(param: RequestParameters, callback: AsyncCallback<RequestCallbackParameters>): void
```

Requests the component from the component provider. This API is applicable to scenarios where the user needs to obtain the provider's components and data on demand. <br>Cooperation method: The provider must first call [on('request', callback)](../../../reference/apis-arkui/js-apis-plugincomponent.md#plugincomponentmanageron) to register a request event listener before receiving the request initiated by the user through this API and returning data. If the provider does not register the listener, the request cannot be responded to.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-pluginComponentManager-function request(param: RequestParameters, callback: AsyncCallback<RequestCallbackParameters>): void--><!--Device-pluginComponentManager-function request(param: RequestParameters, callback: AsyncCallback<RequestCallbackParameters>): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| param | [RequestParameters](arkts-arkui-plugincomponentmanager-requestparameters-i.md) | Yes | Details about the component template request. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[RequestCallbackParameters](arkts-arkui-plugincomponentmanager-requestcallbackparameters-i.md)&gt; | Yes | Asynchronous callback for this request, used to return the data obtained from the request through the parameter of the callback. |

**Examples**

```TypeScript
import { pluginComponentManager } from '@kit.ArkUI';

pluginComponentManager.request(
  {
    want: {
      bundleName: "com.example.provider",
      abilityName: "com.example.provider.MainAbility",
    },
    name: "plugintemplate",
    data: {
      "key_1": "plugin component test",
      "key_2": 1111111,
    },
    jsonPath: "",
  },
  (err, data) => {
    if (err) {
      console.error(`request_callback: err.code = ${err.code}, err.message = ${err.message}`);
      return;
    }
    console.info("request_callback: componentTemplate.ability=" + data.componentTemplate.ability);
    console.info("request_callback: componentTemplate.source=" + data.componentTemplate.source);
    console.info("request_callback: data=" + JSON.stringify(data.data));
    console.info("request_callback: extraData=" + JSON.stringify(data.extraData));
  }
)
```
