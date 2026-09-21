# getForegroundUIAbilities (System API)

## Modules to Import

```TypeScript
import { abilityManager } from '@kit.AbilityKit';
```

## getForegroundUIAbilities

```TypeScript
function getForegroundUIAbilities(callback: AsyncCallback<Array<AbilityStateData>>): void
```

Obtains the information about the UIAbility components of an application that is running in the foreground. This API uses an asynchronous callback to return the result.

**Since:** 11

**Required permissions:** ohos.permission.GET_RUNNING_INFO

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[AbilityStateData](arkts-ability-abilitymanager-abilitystatedata-t.md)&gt;&gt; | Yes | Callback used to return the API call result and the UIAbility information. You can perform error handling or custom processing in it. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System App. Interface caller is not a system app. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |

**Examples**

```TypeScript
import { abilityManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

abilityManager.getForegroundUIAbilities((err: BusinessError, data: Array<abilityManager.AbilityStateData>) => {
  if (err) {
    console.error(`Get foreground ui abilities failed, error: ${JSON.stringify(err)}`);
  } else {
    console.info(`Get foreground ui abilities data is: ${JSON.stringify(data)}`);
  }
});
```


<a id="getforegrounduiabilities-1"></a>

## getForegroundUIAbilities

```TypeScript
function getForegroundUIAbilities(): Promise<Array<AbilityStateData>>
```

Obtains the information about the UIAbility components of an application that is running in the foreground. This API uses a promise to return the result.

**Since:** 11

**Required permissions:** ohos.permission.GET_RUNNING_INFO

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[AbilityStateData](arkts-ability-abilitymanager-abilitystatedata-t.md)&gt;&gt; | Promise used to return the API call result and the UIAbility information. You can perform error handling or custom processing in it. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not System App. Interface caller is not a system app. |
| [16000050](../errorcode-ability.md#16000050-internal-error) | Internal error. |

**Examples**

```TypeScript
import { abilityManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

abilityManager.getForegroundUIAbilities().then((data: Array<abilityManager.AbilityStateData>) => {
  console.info(`Get foreground ui abilities data is: ${JSON.stringify(data)}`);
}).catch((error: BusinessError) => {
  console.error(`Get foreground ui abilities failed, error: ${JSON.stringify(error)}`);
});
```
