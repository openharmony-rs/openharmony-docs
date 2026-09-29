# RequestParameters

```TypeScript
interface RequestParameters
```

Defines the parameters required when using the **PluginManager.Request** API.

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

Component data.

**Type:** [KVObject](arkts-arkui-plugincomponentmanager-kvobject-t.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-RequestParameters-data: KVObject--><!--Device-RequestParameters-data: KVObject-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## jsonPath

```TypeScript
jsonPath?: string
```

Path to the [external.json](../../../reference/apis-arkui/js-apis-plugincomponent.md#about-the-externaljson-file) file that stores the template path.

**Type:** string

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-RequestParameters-jsonPath?: string--><!--Device-RequestParameters-jsonPath?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## name

```TypeScript
name: string
```

Component name.

**Type:** string

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-RequestParameters-name: string--><!--Device-RequestParameters-name: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## want

```TypeScript
want: Want
```

Ability information of the component user.

**Type:** [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-RequestParameters-want: Want--><!--Device-RequestParameters-want: Want-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
