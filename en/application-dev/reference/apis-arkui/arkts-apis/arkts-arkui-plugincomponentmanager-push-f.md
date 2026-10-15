# push

## Modules to Import

```TypeScript
import { pluginComponentManager, PluginComponentTemplate } from '@kit.ArkUI';
```

<a id="push1"></a>

## push

```TypeScript
function push(param: PushParameters, callback: AsyncCallback<void>): void
```

Pushes the component and data to the component user. This API is applicable to scenarios where the provider needs to proactively notify the user to refresh the display after data is updated. <br>Cooperation method: The user must first call [on('push', callback)](../../../reference/apis-arkui/js-apis-plugincomponent.md#plugincomponentmanageron) to register a push event listener before receiving the components and data pushed through this API. If the user does not register the listener, the pushed data cannot be received.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-pluginComponentManager-function push(param: PushParameters, callback: AsyncCallback<void>): void--><!--Device-pluginComponentManager-function push(param: PushParameters, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| param | [PushParameters](arkts-arkui-plugincomponentmanager-pushparameters-i.md) | Yes | Detailed parameters for pushing the component. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Asynchronous callback used to return the result. |

**Examples**

```TypeScript
import { pluginComponentManager } from '@kit.ArkUI';

pluginComponentManager.push(
  {
    want: {
      bundleName: "com.example.provider",
      abilityName: "com.example.provider.MainAbility",
    },
    name: "plugintemplate",
    data: {
      "key_1": "plugin component test",
      "key_2": 34234,
    },
    extraData: {
      "extra_str": "this is push event",
    },
    jsonPath: "",
  },
  (err) => {
    if (err) {
      console.error(`push_callback: err.code = ${err.code}, err.message = ${err.message}`);
      return;
    }
    console.info("push_callback: push ok!");
  }
)
```
