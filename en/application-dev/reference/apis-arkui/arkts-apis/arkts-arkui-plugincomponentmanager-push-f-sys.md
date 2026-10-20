# push (System API)

## Modules to Import

```TypeScript
import { pluginComponentManager, PluginComponentTemplate } from '@kit.ArkUI';
```

## push

```TypeScript
function push(param: PushParameterForStage, callback: AsyncCallback<void>): void
```

Proactively pushes the component and data to the component user. This API applies to scenarios where the plug-in component template needs to be proactively pushed, for example, cross-application content sharing and proactive refresh of home screen cards. **push** is proactively initiated by the component provider, while **request** is proactively initiated by the component user. Note that the two have similar parameter structures but opposite meanings of **owner** and **target**, so do not confuse them. The component user must listen for the received data through the **onPush** event. For details about the event listener API, see [@ohos.pluginComponent (PluginComponentManager)](../../../reference/apis-arkui/js-apis-plugincomponent.md#plugincomponentmanageron).

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-pluginComponentManager-function push(param: PushParameterForStage, callback: AsyncCallback<void>): void--><!--Device-pluginComponentManager-function push(param: PushParameterForStage, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| param | [PushParameterForStage](arkts-arkui-plugincomponentmanager-pushparameterforstage-i-sys.md) | Yes | Parameters to be sent by the component provider. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Asynchronous callback used to return the result. |

<!--Del-->
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

<!--DelEnd-->
