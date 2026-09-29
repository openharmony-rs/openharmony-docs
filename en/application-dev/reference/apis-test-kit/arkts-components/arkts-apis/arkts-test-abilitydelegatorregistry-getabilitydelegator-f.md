# getAbilityDelegator

## Modules to Import

```TypeScript
import { abilityDelegatorRegistry } from '@kit.TestKit';
```

## getAbilityDelegator

```TypeScript
function getAbilityDelegator(): AbilityDelegator
```

Obtains an [AbilityDelegator](../../apis-ability-kit/arkts-apis/arkts-ability-abilitydelegator-i.md) object.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-abilityDelegatorRegistry-function getAbilityDelegator(): AbilityDelegator--><!--Device-abilityDelegatorRegistry-function getAbilityDelegator(): AbilityDelegator-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Test API:** This API is used only in automated test scripts.

**Return value:**

| Type | Description |
| --- | --- |
| [AbilityDelegator](arkts-test-abilitydelegatorregistry-abilitydelegator-t.md) | [AbilityDelegator](../../apis-ability-kit/arkts-apis/arkts-ability-abilitydelegator-i.md) object, which can be used to schedule the functionalities of the test framework. |

**Examples**

```TypeScript
import { abilityDelegatorRegistry } from '@kit.TestKit';
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain the AbilityDelegator object of the application.
let abilityDelegator = abilityDelegatorRegistry.getAbilityDelegator();
// Construct a Want parameter to specify the target ability.
let want: Want = {
  bundleName: 'com.example.myapplication',
  abilityName: 'EntryAbility'
};

// Start the specified ability.
abilityDelegator.startAbility(want, (err: BusinessError) => {
  if (err) {
    console.error(`Failed start ability. code: ${err.code}, message: ${err.message}`);
  } else {
    console.info('Success start ability.');
  }
});
```
