# PushParameters

```TypeScript
interface PushParameters
```

Defines the parameters required when using the **pluginComponentManager.push** API.

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

Component data stored in key-value pairs, used to transfer service data to the component user. The key and value types are defined by the service.

**Type:** [KVObject](arkts-arkui-plugincomponentmanager-kvobject-t.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PushParameters-data: KVObject--><!--Device-PushParameters-data: KVObject-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## extraData

```TypeScript
extraData: KVObject
```

Extra data stored in key-value pairs, used to transfer additional service information. The key and value types are defined by the service.

**Type:** [KVObject](arkts-arkui-plugincomponentmanager-kvobject-t.md)

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PushParameters-extraData: KVObject--><!--Device-PushParameters-extraData: KVObject-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## jsonPath

```TypeScript
jsonPath?: string
```

Path of the [external.json](../../../reference/apis-arkui/js-apis-plugincomponent.md#about-the-externaljson-file) file that stores the template path. This parameter is passed when the template needs to be loaded directly through an external configuration file instead of being sent through Push communication. When **jsonPath** is not empty, Push communication is not triggered, and the template path is read directly from **external.json** for loading. When this parameter is not passed or is empty, Push communication is triggered to push the component and data to the component user.

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
