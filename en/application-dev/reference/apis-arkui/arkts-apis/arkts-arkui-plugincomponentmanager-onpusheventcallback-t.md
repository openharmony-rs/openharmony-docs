# OnPushEventCallback

```TypeScript
type OnPushEventCallback = (source: Want, template: PluginComponentTemplate, data: KVObject,
     extraData: KVObject) => void
```

Registers the listener for the push event.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-pluginComponentManager-type OnPushEventCallback = (source: Want, template: PluginComponentTemplate, data: KVObject,     extraData: KVObject) => void--><!--Device-pluginComponentManager-type OnPushEventCallback = (source: Want, template: PluginComponentTemplate, data: KVObject,     extraData: KVObject) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| source | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | Information about the push request sender. |
| template | [PluginComponentTemplate](arkts-arkui-plugincomponent-plugincomponenttemplate-i.md) | Yes | Component template. |
| data | [KVObject](arkts-arkui-plugincomponentmanager-kvobject-t.md) | Yes | Data content transmitted in the push event, stored in key-value pairs. The key and value types are defined by the service. |
| extraData | [KVObject](arkts-arkui-plugincomponentmanager-kvobject-t.md) | Yes | Extra data transmitted in the push event, stored in key-value pairs. The key and value types are defined by the service. |

**Examples**

```TypeScript
import { pluginComponentManager, PluginComponentTemplate } from '@kit.ArkUI';
import { Want } from '@kit.AbilityKit';

const onPushListener = (source: Want, template: PluginComponentTemplate, data: pluginComponentManager.KVObject, extraData: pluginComponentManager.KVObject) => {
  console.info("onPushListener template.source=" + template.source);
  console.info("onPushListener source=" + JSON.stringify(source));
  console.info("onPushListener template=" + JSON.stringify(template));
  console.info("onPushListener data=" + JSON.stringify(data));
  console.info("onPushListener extraData=" + JSON.stringify(extraData));
};
```
