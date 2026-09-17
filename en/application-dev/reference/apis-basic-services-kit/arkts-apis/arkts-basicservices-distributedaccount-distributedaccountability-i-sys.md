# DistributedAccountAbility

Provides APIs for querying and updating the login state of a distributed account. You must obtain a **DistributedAccountAbility** instance first.

**Since:** 7

**System capability:** SystemCapability.Account.OsAccount

## Modules to Import

```TypeScript
import { distributedAccount } from '@kit.BasicServicesKit';
```

## getOsAccountDistributedInfoByLocalId

```TypeScript
getOsAccountDistributedInfoByLocalId(localId: number, callback: AsyncCallback<DistributedInfo>): void
```

Obtains the distributed account information about an OS account. This API uses an asynchronous callback to return the result.

**Since:** 10

**Required permissions:** 
- API version 20 and later: ohos.permission.MANAGE_DISTRIBUTED_ACCOUNTS or (ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS and ohos.permission.GET_DISTRIBUTED_ACCOUNTS)
- API versions 10 to 19: ohos.permission.MANAGE_DISTRIBUTED_ACCOUNTS or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| localId | number | Yes | ID of the target OS account. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;[DistributedInfo](arkts-basicservices-distributedaccount-distributedinfo-i.md)&gt; | Yes | Callback used to return the result. If the distributed account information is obtained successfully, **err** is **undefined** and **data** is the distributed account information obtained. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const accountAbility: distributedAccount.DistributedAccountAbility = distributedAccount.getDistributedAccountAbility();
try {
  let localId: number = 100; // This is an example. Replace it with an actual OS account ID.
  accountAbility.getOsAccountDistributedInfoByLocalId(localId,
    (err: BusinessError, data: distributedAccount.DistributedInfo) => {
      if (err) {
        console.error(`getOsAccountDistributedInfoByLocalId exception: code is ${err.code}, message is ${err.message}`);
      } else {
        console.info('distributed information: ' + JSON.stringify(data));
      }
    });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getOsAccountDistributedInfoByLocalId exception: code is ${err.code}, message is ${err.message}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const accountAbility: distributedAccount.DistributedAccountAbility = distributedAccount.getDistributedAccountAbility();
try {
  let localId: number = 100; // This is an example. Replace it with an actual OS account ID.
  accountAbility.getOsAccountDistributedInfoByLocalId(localId).then((
    data: distributedAccount.DistributedInfo) => {
    console.info('distributed information: ' + JSON.stringify(data));
  }).catch((err: BusinessError) => {
    console.error(`getOsAccountDistributedInfoByLocalId exception: code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getOsAccountDistributedInfoByLocalId exception: code is ${err.code}, message is ${err.message}`);
}
```

## getOsAccountDistributedInfoByLocalId

```TypeScript
getOsAccountDistributedInfoByLocalId(localId: number): Promise<DistributedInfo>
```

Obtains the distributed account information about an OS account. This API uses a promise to return the result.

**Since:** 10

**Required permissions:** 
- API version 20 and later: ohos.permission.MANAGE_DISTRIBUTED_ACCOUNTS or (ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS and ohos.permission.GET_DISTRIBUTED_ACCOUNTS)
- API versions 10 to 19: ohos.permission.MANAGE_DISTRIBUTED_ACCOUNTS or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| localId | number | Yes | ID of the target OS account. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[DistributedInfo](arkts-basicservices-distributedaccount-distributedinfo-i.md)&gt; | Promise used to return the distributed account information obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |

**Examples**

See [getOsAccountDistributedInfoByLocalId](#getosaccountdistributedinfobylocalid)

## setOsAccountDistributedInfoByLocalId

```TypeScript
setOsAccountDistributedInfoByLocalId(localId: number, distributedInfo: DistributedInfo, callback: AsyncCallback<void>): void
```

Sets the distributed account information about an OS account. This API uses an asynchronous callback to return the result.

**Since:** 10

**Required permissions:** ohos.permission.MANAGE_DISTRIBUTED_ACCOUNTS

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| localId | number | Yes | ID of the target OS account. |
| distributedInfo | [DistributedInfo](arkts-basicservices-distributedaccount-distributedinfo-i.md) | Yes | Distributed account information to set. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the distributed account information is set successfully, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid distributedInfo. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account identified by localId or by distributedInfo not found. |
| [12300008](../errorcode-account.md#12300008-restricted-account) | Restricted OS account. |
| 12300406 | The distributed account information has already been bound to a sub-profile of the target OS account.<br>**Applicable version:** 26.0.0 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const accountAbility: distributedAccount.DistributedAccountAbility = distributedAccount.getDistributedAccountAbility();
let accountInfo: distributedAccount.DistributedInfo =
  { id: '12345', name: 'ZhangSan', event: 'Ohos.account.event.LOGIN' };
try {
  let localId: number = 100; // This is an example. Replace it with an actual OS account ID.
  accountAbility.setOsAccountDistributedInfoByLocalId(localId, accountInfo, (err: BusinessError) => {
    if (err) {
      console.error(`setOsAccountDistributedInfoByLocalId exception: code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('setOsAccountDistributedInfoByLocalId successfully');
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`setOsAccountDistributedInfoByLocalId exception: code is ${err.code}, message is ${err.message}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const accountAbility: distributedAccount.DistributedAccountAbility = distributedAccount.getDistributedAccountAbility();
let accountInfo: distributedAccount.DistributedInfo =
  { id: '12345', name: 'ZhangSan', event: 'Ohos.account.event.LOGIN' };
try {
  let localId: number = 100; // This is an example. Replace it with an actual OS account ID.
  accountAbility.setOsAccountDistributedInfoByLocalId(localId, accountInfo).then(() => {
    console.info('setOsAccountDistributedInfoByLocalId successfully');
  }).catch((err: BusinessError) => {
    console.error(`setOsAccountDistributedInfoByLocalId exception: code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`setOsAccountDistributedInfoByLocalId exception: code is ${err.code}, message is ${err.message}`);
}
```

## setOsAccountDistributedInfoByLocalId

```TypeScript
setOsAccountDistributedInfoByLocalId(localId: number, distributedInfo: DistributedInfo): Promise<void>
```

Sets the distributed account information about an OS account. This API uses a promise to return the result.

**Since:** 10

**Required permissions:** ohos.permission.MANAGE_DISTRIBUTED_ACCOUNTS

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| localId | number | Yes | ID of the target OS account. |
| distributedInfo | [DistributedInfo](arkts-basicservices-distributedaccount-distributedinfo-i.md) | Yes | Distributed account information to set. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid distributedInfo. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account identified by localId or by distributedInfo not found. |
| [12300008](../errorcode-account.md#12300008-restricted-account) | Restricted OS account. |
| 12300406 | The distributed account information has already been bound to a sub-profile of the target OS account.<br>**Applicable version:** 26.0.0 and later |

**Examples**

See [setOsAccountDistributedInfoByLocalId](#setosaccountdistributedinfobylocalid)
