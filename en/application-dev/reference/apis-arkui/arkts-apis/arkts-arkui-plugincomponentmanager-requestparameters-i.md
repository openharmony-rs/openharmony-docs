# RequestParameters

```TypeScript
interface RequestParameters
```

Defines the parameters required when using the **pluginComponentManager.request** API.

**Since:** 8

<!--Device-pluginComponentManager-interface RequestParameters--><!--Device-pluginComponentManager-interface RequestParameters-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { pluginComponentManager, PluginComponentTemplate } from '@kit.ArkUI';
```

## data

```TypeScript
data: KVObject
```

Component data stored in key-value pairs, used to transfer service data to the component provider. The key and value types are defined by the service.

**Type:** [KVObject](arkts-arkui-plugincomponentmanager-kvobject-t.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-RequestParameters-data: KVObject--><!--Device-RequestParameters-data: KVObject-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## jsonPath

```TypeScript
jsonPath?: string
```

Path to the [external.json](../../../reference/apis-arkui/js-apis-plugincomponent.md#about-the-externaljson-file) file that stores the template path. This parameter is passed when the template needs to be loaded directly through an external configuration file instead of being obtained through Request communication. When **jsonPath** is not empty, Request communication is not triggered and the template path is read directly from **external.json**. When this parameter is not passed or is empty, Request communication is triggered to request the template from the component provider.

**Type:** string

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-RequestParameters-jsonPath?: string--><!--Device-RequestParameters-jsonPath?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## name

```TypeScript
name: string
```

Name of the requested component.

**Type:** string

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-RequestParameters-name: string--><!--Device-RequestParameters-name: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## want

```TypeScript
want: Want
```

Ability information of the component provider.

**Type:** [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-RequestParameters-want: Want--><!--Device-RequestParameters-want: Want-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
