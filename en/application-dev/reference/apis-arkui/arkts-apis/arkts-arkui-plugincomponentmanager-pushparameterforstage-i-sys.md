# PushParameterForStage (System API)

```TypeScript
interface PushParameterForStage
```

Sets the parameters to be passed in the **pluginComponentManager.push** API in the stage model.

**Since:** 9

<!--Device-pluginComponentManager-interface PushParameterForStage--><!--Device-pluginComponentManager-interface PushParameterForStage-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { pluginComponentManager, PluginComponentTemplate } from '@kit.ArkUI';
```

## data

```TypeScript
data: KVObject
```

Component data, stored in key-value pairs. It is used to transfer service data to the component user, such as the page path (if **key** is **'js'**, **value** is the template path string) and custom data fields.

**Type:** [KVObject](arkts-arkui-plugincomponentmanager-kvobject-t.md)

**Since:** 9

<!--Device-PushParameterForStage-data: KVObject--><!--Device-PushParameterForStage-data: KVObject-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## extraData

```TypeScript
extraData: KVObject
```

Extra data used to transfer additional custom data when sending a component. It is distinguished from component data (**data**) and can be set based on service requirements.

**Type:** [KVObject](arkts-arkui-plugincomponentmanager-kvobject-t.md)

**Since:** 9

<!--Device-PushParameterForStage-extraData: KVObject--><!--Device-PushParameterForStage-extraData: KVObject-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## jsonPath

```TypeScript
jsonPath?: string
```

Path of the [external.json](../../../reference/apis-arkui/js-apis-plugincomponent.md#about-the-externaljson-file) file that stores the template path. When **jsonPath** is not empty, Push communication is not triggered, and the component template path is read from the **external.json** file. When **jsonPath** is empty (default), the component template is sent to the component user through Push communication.

**Type:** string

**Since:** 9

<!--Device-PushParameterForStage-jsonPath?: string--><!--Device-PushParameterForStage-jsonPath?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## name

```TypeScript
name: string
```

Component name. When **jsonPath** is not empty, the component name must be consistent with the key name in the [external.json](../../../reference/apis-arkui/js-apis-plugincomponent.md#about-the-externaljson-file) file.

**Type:** string

**Since:** 9

<!--Device-PushParameterForStage-name: string--><!--Device-PushParameterForStage-name: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## owner

```TypeScript
owner: Want
```

Ability information of the component provider.

**Type:** [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md)

**Since:** 9

<!--Device-PushParameterForStage-owner: Want--><!--Device-PushParameterForStage-owner: Want-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## target

```TypeScript
target: Want
```

Ability information of the component user.

**Type:** [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md)

**Since:** 9

<!--Device-PushParameterForStage-target: Want--><!--Device-PushParameterForStage-target: Want-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
