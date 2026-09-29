# PushParameters

```TypeScript
interface PushParameters
```

Defines the parameters required when using the **PluginManager.Push** API.

**Since:** 8

<!--Device-pluginComponentManager-interface PushParameters--><!--Device-pluginComponentManager-interface PushParameters-End-->

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

<!--Device-PushParameters-data: KVObject--><!--Device-PushParameters-data: KVObject-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## extraData

```TypeScript
extraData: KVObject
```

Extra data.

**Type:** [KVObject](arkts-arkui-plugincomponentmanager-kvobject-t.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PushParameters-extraData: KVObject--><!--Device-PushParameters-extraData: KVObject-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## jsonPath

```TypeScript
jsonPath?: string
```

Path to the [external.json](../../../reference/apis-arkui/js-apis-plugincomponent.md#about-the-externaljson-file) file that stores the template path.

**Type:** string

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PushParameters-jsonPath?: string--><!--Device-PushParameters-jsonPath?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## name

```TypeScript
name: string
```

Component name.

**Type:** string

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PushParameters-name: string--><!--Device-PushParameters-name: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## want

```TypeScript
want: Want
```

Ability information of the component user.

**Type:** [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PushParameters-want: Want--><!--Device-PushParameters-want: Want-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
