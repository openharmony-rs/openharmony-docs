# request (System API)

## Modules to Import

```TypeScript
import { pluginComponentManager, PluginComponentTemplate } from '@kit.ArkUI';
```

## request

```TypeScript
function request(param: RequestParameterForStage, callback: AsyncCallback<RequestCallbackParameters>): void
```

Requests the component from the component provider. This API applies to scenarios where the component user needs to dynamically obtain the plug-in component template on demand, for example, dynamically loading plug-in content provided by other applications and displaying cross-application components on demand. The component provider must listen for the request response through the **onRequest** event, and return the component template information through a callback. For details about the event listener API, see [@ohos.pluginComponent (PluginComponentManager)](../../../reference/apis-arkui/js-apis-plugincomponent.md#plugincomponentmanageron).

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-pluginComponentManager-function request(param: RequestParameterForStage, callback: AsyncCallback<RequestCallbackParameters>): void--><!--Device-pluginComponentManager-function request(param: RequestParameterForStage, callback: AsyncCallback<RequestCallbackParameters>): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| param | [RequestParameterForStage](arkts-arkui-plugincomponentmanager-requestparameterforstage-i-sys.md) | Yes | Details about the component template request. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[RequestCallbackParameters](arkts-arkui-plugincomponentmanager-requestcallbackparameters-i.md)&gt; | Yes | Asynchronous callback for this request, which returns the request response data through the parameter of the callback. |

<!--Del-->
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

<!--DelEnd-->
