# SubIntentInfoForConfiguration (System API)

Describes the unique information of the [intent developed using a configuration file](../../../application-models/insight-intent-config-development.md).

**Since:** 23

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { insightIntentDriver } from '@kit.AbilityKit';
```

## entities

```TypeScript
readonly entities?: Record<string, Object>
```

Entity information contained in the intent.

**Type:** Record&lt;string, Object&gt;

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## form

```TypeScript
readonly form?: FormIntentInfo
```

Information about the widget bound to the intent.

**Type:** [FormIntentInfo](arkts-ability-insightintentdriver-formintentinfo-i-sys.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## inputParams

```TypeScript
readonly inputParams?: Array<Record<string, Object>>
```

Data format of intent parameters, which is used to define the input data format during intent calls.

**Type:** Array&lt;Record&lt;string, Object&gt;&gt;

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## outputParams

```TypeScript
readonly outputParams?: Array<Record<string, Object>>
```

Data format for the results returned by intent calls. It defines how the data should be structured.

**Type:** Array&lt;Record&lt;string, Object&gt;&gt;

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## serviceExtension

```TypeScript
readonly serviceExtension?: ServiceExtensionIntentInfo
```

Information about the ServiceExtensionAbility bound to the intent.

**Type:** [ServiceExtensionIntentInfo](arkts-ability-insightintentdriver-serviceextensionintentinfo-i-sys.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## srcEntry

```TypeScript
readonly srcEntry: string
```

Relative path of the intent execution file. The value is a string of a maximum of 127 bytes.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## uiAbility

```TypeScript
readonly uiAbility?: UIAbilityIntentInfo
```

Information about the UIAbility bound to the intent, including the **ability** and **executeMode** fields.

**Type:** [UIAbilityIntentInfo](arkts-ability-insightintentdriver-uiabilityintentinfo-i-sys.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

## uiExtension

```TypeScript
readonly uiExtension?: UIExtensionIntentInfo
```

Information about the UIExtensionAbility bound to the intent.

**Type:** [UIExtensionIntentInfo](arkts-ability-insightintentdriver-uiextensionintentinfo-i-sys.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.
