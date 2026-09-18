# RequestResult

Defines the result of the request for the modal dialog box. It contains **ResultCode** and **ResultWant**.

**Since:** 9

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { dialogRequest } from '@kit.AbilityKit';
```

## result

```TypeScript
result: ResultCode
```

Result code of the request.

**Type:** [ResultCode](arkts-ability-dialogrequest-resultcode-e.md)

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## want

```TypeScript
want?: Want
```

Want information, such as the ability name and bundle name.

**Type:** [Want](arkts-ability-app-ability-want-want-c.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
