# RequestEventResult

```TypeScript
interface RequestEventResult
```

Provides the data type used to respond to a request event after the request listener is registered.

**Since:** 8

<!--Device-pluginComponentManager-interface RequestEventResult--><!--Device-pluginComponentManager-interface RequestEventResult-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { pluginComponentManager, PluginComponentTemplate } from '@kit.ArkUI';
```

## data

```TypeScript
data?: KVObject
```

Component data stored in key-value pairs, used to transfer service data when responding to a request. The key and value types are defined by the service. This is an optional parameter. If not provided, it is not included in the return result by default.

**Type:** [KVObject](arkts-arkui-plugincomponentmanager-kvobject-t.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-RequestEventResult-data?: KVObject--><!--Device-RequestEventResult-data?: KVObject-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## extraData

```TypeScript
extraData?: KVObject
```

Extra data passed in the request event. This is an optional parameter. If not provided, it is not included in the return result by default.

**Type:** [KVObject](arkts-arkui-plugincomponentmanager-kvobject-t.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-RequestEventResult-extraData?: KVObject--><!--Device-RequestEventResult-extraData?: KVObject-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## template

```TypeScript
template?: string
```

Component template. This is an optional parameter. If not provided, it is not included in the return result by default. Set this parameter when the component template information needs to be returned; it can be omitted when the template is not required.

**Type:** string

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-RequestEventResult-template?: string--><!--Device-RequestEventResult-template?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
