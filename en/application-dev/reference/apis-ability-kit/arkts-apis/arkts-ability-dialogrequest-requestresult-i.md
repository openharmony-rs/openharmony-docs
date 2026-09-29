# RequestResult

```TypeScript
export interface RequestResult
```

Defines the result of the request for the modal dialog box. It contains **ResultCode** and **ResultWant**.

**Since:** 9

<!--Device-dialogRequest-export interface RequestResult--><!--Device-dialogRequest-export interface RequestResult-End-->

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

<!--Device-RequestResult-result: ResultCode--><!--Device-RequestResult-result: ResultCode-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## want

```TypeScript
want?: Want
```

Want information, such as the ability name and bundle name.

**Type:** [Want](arkts-ability-app-ability-want-want-c.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-RequestResult-want?: Want--><!--Device-RequestResult-want?: Want-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
