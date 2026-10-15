# RequestParameterForStage (System API)

```TypeScript
interface RequestParameterForStage
```

Sets the parameters to be passed in the **pluginComponentManager.request** API in the stage model.

**Since:** 9

<!--Device-pluginComponentManager-interface RequestParameterForStage--><!--Device-pluginComponentManager-interface RequestParameterForStage-End-->

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

Extra data stored in key-value pairs, used to transfer custom service parameters to the component provider during a request, so that the provider can return an appropriate component template based on the data.

**Type:** [KVObject](arkts-arkui-plugincomponentmanager-kvobject-t.md)

**Since:** 9

<!--Device-RequestParameterForStage-data: KVObject--><!--Device-RequestParameterForStage-data: KVObject-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## jsonPath

```TypeScript
jsonPath?: string
```

Path of the [external.json](../../../reference/apis-arkui/js-apis-plugincomponent.md#about-the-externaljson-file) file that stores the template path. This parameter is passed when the template path needs to be loaded from the **external.json** file instead of being obtained through Request communication. When **jsonPath** is not empty, Request communication is not triggered. When **jsonPath** is empty (default), the component template is requested from the component provider through Request communication.

**Type:** string

**Since:** 9

<!--Device-RequestParameterForStage-jsonPath?: string--><!--Device-RequestParameterForStage-jsonPath?: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## name

```TypeScript
name: string
```

Name of the requested component. When **jsonPath** is not empty, it must be consistent with the key name in the [external.json](../../../reference/apis-arkui/js-apis-plugincomponent.md#about-the-externaljson-file) file.

**Type:** string

**Since:** 9

<!--Device-RequestParameterForStage-name: string--><!--Device-RequestParameterForStage-name: string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## owner

```TypeScript
owner: Want
```

Ability information of the component user.

**Type:** [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md)

**Since:** 9

<!--Device-RequestParameterForStage-owner: Want--><!--Device-RequestParameterForStage-owner: Want-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## target

```TypeScript
target: Want
```

Ability information of the component provider.

**Type:** [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md)

**Since:** 9

<!--Device-RequestParameterForStage-target: Want--><!--Device-RequestParameterForStage-target: Want-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
