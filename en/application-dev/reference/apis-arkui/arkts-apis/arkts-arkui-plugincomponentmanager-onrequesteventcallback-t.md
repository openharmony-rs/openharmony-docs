# OnRequestEventCallback

```TypeScript
type OnRequestEventCallback = (source: Want, name: string, data: KVObject) => RequestEventResult
```

Registers the listener for the request event.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-pluginComponentManager-type OnRequestEventCallback = (source: Want, name: string, data: KVObject) => RequestEventResult--><!--Device-pluginComponentManager-type OnRequestEventCallback = (source: Want, name: string, data: KVObject) => RequestEventResult-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| source | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | Information about the request sender. |
| name | string | Yes | Name of the requested component. |
| data | [KVObject](arkts-arkui-plugincomponentmanager-kvobject-t.md) | Yes | Data content transmitted in the request event, stored in key-value pairs. The key and value types are defined by the service. |

**Return value:**

| Type | Description |
| --- | --- |
| [RequestEventResult](arkts-arkui-plugincomponentmanager-requesteventresult-i.md) | Data type for responding to a request event after the request listener is registered. |

**Examples**

```TypeScript
import { pluginComponentManager } from '@kit.ArkUI';
import { Want } from '@kit.AbilityKit';

const onRequestListener = (source: Want, name: string, data: pluginComponentManager.KVObject) => {
  console.info("onRequestListener");
  console.info("onRequestListener source=" + JSON.stringify(source));
  console.info("onRequestListener name=" + name);
  console.info("onRequestListener data=" + JSON.stringify(data));
  // Build the return data for the Request event callback, specifying the component template path and carrying the request data back to the requester.
  let returnData: Record<string, string | pluginComponentManager.KVObject> = {
    "template": "ets/pages/plugin.js",
    "data": data,
  }
  return returnData;
}
```
