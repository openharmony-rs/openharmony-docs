# RequestCallbackParameters

```TypeScript
interface RequestCallbackParameters
```

Provides the result returned after the **pluginComponentManager.request** API is called.

**Since:** 8

<!--Device-pluginComponentManager-interface RequestCallbackParameters--><!--Device-pluginComponentManager-interface RequestCallbackParameters-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { pluginComponentManager, PluginComponentTemplate } from '@kit.ArkUI';
```

## componentTemplate

```TypeScript
componentTemplate: PluginComponentTemplate
```

Component template.

**Type:** [PluginComponentTemplate](arkts-arkui-plugincomponent-plugincomponenttemplate-i.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-RequestCallbackParameters-componentTemplate: PluginComponentTemplate--><!--Device-RequestCallbackParameters-componentTemplate: PluginComponentTemplate-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## data

```TypeScript
data: KVObject
```

Component data stored in key-value pairs. The key and value types are defined by the service.

**Type:** [KVObject](arkts-arkui-plugincomponentmanager-kvobject-t.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-RequestCallbackParameters-data: KVObject--><!--Device-RequestCallbackParameters-data: KVObject-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## extraData

```TypeScript
extraData: KVObject
```

Extra data. This is an optional parameter. If not provided, it is not included in the returned result by default.

**Type:** [KVObject](arkts-arkui-plugincomponentmanager-kvobject-t.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-RequestCallbackParameters-extraData: KVObject--><!--Device-RequestCallbackParameters-extraData: KVObject-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
