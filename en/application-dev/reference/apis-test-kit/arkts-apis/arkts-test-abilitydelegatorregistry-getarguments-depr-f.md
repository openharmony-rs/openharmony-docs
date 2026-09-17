# getArguments

## Modules to Import

```TypeScript
```

## getArguments

```TypeScript
function getArguments(): AbilityDelegatorArgs
```

Obtains the **AbilityDelegatorArgs** object of the application.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getArguments](arkts-test-abilitydelegatorregistry-getarguments-f.md)

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Test API:** This API is used only in automated test scripts.

**Return value:**

| Type | Description |
| --- | --- |
| [AbilityDelegatorArgs](../../apis-ability-kit/arkts-apis/arkts-ability-abilitydelegatorargs-abilitydelegatorargs-i.md) | [AbilityDelegatorArgs](../../apis-ability-kit/arkts-apis/arkts-ability-abilitydelegatorargs-abilitydelegatorargs-i.md) object, which can be used to obtain test parameters. |

**Examples**

```TypeScript
import AbilityDelegatorRegistry from '@ohos.application.abilityDelegatorRegistry';

let args = AbilityDelegatorRegistry.getArguments();
console.info(`getArguments bundleName: ${args.bundleName}`);
console.info(`getArguments testCaseNames: ${args.testCaseNames}`);
console.info(`getArguments testRunnerClassName: ${args.testRunnerClassName}`);
```
