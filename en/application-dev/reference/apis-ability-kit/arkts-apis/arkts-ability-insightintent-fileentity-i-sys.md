# FileEntity (System API)

```TypeScript
interface FileEntity extends IntentEntity
```

Defines the struct of a file entity. It represents key file objects involved during intent execution, including intent parameters and execution results.

You can define file entities by implementing this interface. The child class must be decorated with [@InsightIntentEntity](../../../reference/apis-ability-kit/js-apis-app-ability-InsightIntentDecorator.md#insightintententity)

**Inheritance/Implementation:** FileEntity extends [IntentEntity](arkts-ability-insightintent-intententity-i.md)

**Since:** 26.2.0

<!--Device-insightIntent-interface FileEntity extends IntentEntity--><!--Device-insightIntent-interface FileEntity extends IntentEntity-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { insightIntent } from '@kit.AbilityKit';
```

## flags

```TypeScript
flags?: number
```

Permission to be granted to the URI list.

**Note:** 

This parameter supports only FLAG_AUTH_READ_URI_PERMISSION, FLAG_AUTH_WRITE_URI_PERMISSION, and FLAG_AUTH_READ_URI_PERMISSION|FLAG_AUTH_WRITE_URI_PERMISSION. For details about the permissions, see [Flags](arkts-ability-wantconstant-flags-e.md). The value should be an integer.

**Type:** number

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-FileEntity-flags?: int--><!--Device-FileEntity-flags?: int-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.
