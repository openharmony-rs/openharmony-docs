# killProcessWithAccount (System API)

## Modules to Import

```TypeScript
```

## killProcessWithAccount

```TypeScript
function killProcessWithAccount(bundleName: string, accountId: number): Promise<void>
```

Kill process with account.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [killProcessWithAccount](arkts-ability-appmanager-killprocesswithaccount-f-sys.md)

**Required permissions:** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS and ohos.permission.CLEAN_BACKGROUND_PROCESSES

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | The process bundle name. |
| accountId | number | Yes | The account id. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | The promise returned by the function. |

**Examples**

```TypeScript
import appManager from '@ohos.application.appManager';
import { BusinessError } from '@ohos.base';

let bundleName = 'bundleName';
let accountId = 0;
appManager.killProcessWithAccount(bundleName, accountId)
  .then((data) => {
    console.info(`KillProcessWithAccount success, data: ${JSON.stringify(data)}.`);
  })
  .catch((err: BusinessError) => {
    console.error(`KillProcessWithAccount failed, error code: ${err.code}, error msg: ${err.message}.`);
  });
```

```TypeScript
import appManager from '@ohos.application.appManager';
import { BusinessError } from '@ohos.base';

let bundleName = 'bundleName';
let accountId = 0;

function killProcessWithAccountCallback(err: BusinessError, data: void) {
  if (err) {
    console.error(`KillProcessWithAccountCallback failed, error code: ${err.code}, error msg: ${err.message}.`);
  } else {
    console.info(`KillProcessWithAccountCallback success, data: ${JSON.stringify(data)}`);
  }
}

appManager.killProcessWithAccount(bundleName, accountId, killProcessWithAccountCallback);
```


## killProcessWithAccount

```TypeScript
function killProcessWithAccount(bundleName: string, accountId: number, callback: AsyncCallback<void>): void
```

Kill process with account.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [killProcessWithAccount](arkts-ability-appmanager-killprocesswithaccount-f-sys.md)

**Required permissions:** ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS and ohos.permission.CLEAN_BACKGROUND_PROCESSES

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | The process bundle name. |
| accountId | number | Yes | The account id. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Cut off the callback function of the account process. |

**Examples**

See [killProcessWithAccount](#killprocesswithaccount)
