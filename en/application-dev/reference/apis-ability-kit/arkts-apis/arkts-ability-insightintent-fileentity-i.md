# FileEntity

```TypeScript
interface FileEntity extends IntentEntity
```

Defines the struct of a file entity. It represents key file objects involved during intent execution, including intent parameters and execution results.

You can define file entities by implementing this interface. The child class must be decorated with [@InsightIntentEntity](../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintententity)

**Inheritance/Implementation:** FileEntity extends [IntentEntity](arkts-ability-insightintent-intententity-i.md)

**Since:** 26.1.0

<!--Device-insightIntent-interface FileEntity extends IntentEntity--><!--Device-insightIntent-interface FileEntity extends IntentEntity-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { insightIntent } from '@kit.AbilityKit';
```

## entityId

```TypeScript
entityId: 'OHOS_FILE_ENTITY'
```

ID of the file entity. The value is fixed to 'OHOS_FILE_ENTITY'.

**Type:** 'OHOS_FILE_ENTITY'

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-FileEntity-entityId: 'OHOS_FILE_ENTITY'--><!--Device-FileEntity-entityId: 'OHOS_FILE_ENTITY'-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## uris

```TypeScript
uris: Array<string>
```

List of file URIs.

**Note:** 

The FLAG_AUTH_READ_URI_PERMISSION permission on the URI is granted by default. For details about the permission, see [Flags](arkts-ability-wantconstant-flags-e.md).

**Type:** Array&lt;string&gt;

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-FileEntity-uris: Array<string>--><!--Device-FileEntity-uris: Array<string>-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
