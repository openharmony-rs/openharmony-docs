# DistributedAccountAbility

```TypeScript
interface DistributedAccountAbility
```

Provides APIs for querying and updating the login state of a distributed account. You must obtain a **DistributedAccountAbility** instance first.

**Since:** 7

**System capability:** SystemCapability.Account.OsAccount

## Modules to Import

```TypeScript
import { distributedAccount } from '@kit.BasicServicesKit';
```

## getOsAccountDistributedInfo

```TypeScript
getOsAccountDistributedInfo(callback: AsyncCallback<DistributedInfo>): void
```

Obtains the distributed account information. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.MANAGE_DISTRIBUTED_ACCOUNTS or ohos.permission.GET_DISTRIBUTED_ACCOUNTS or ohos.permission.DISTRIBUTED_DATASYNC

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;[DistributedInfo](arkts-basicservices-distributedaccount-distributedinfo-i.md)&gt; | Yes | Callback used to return the result. If the distributed account information is obtained successfully, **err** is **undefined** and **data** is the distributed account information obtained. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain a DistributedAccountAbility instance.
const accountAbility: distributedAccount.DistributedAccountAbility = distributedAccount.getDistributedAccountAbility();
try {
  accountAbility.getOsAccountDistributedInfo(
    (err: BusinessError, data: distributedAccount.DistributedInfo) => {
      if (err) {
        console.error(`getOsAccountDistributedInfo exception: code is ${err.code}, message is ${err.message}`);
      } else {
        console.info('distributed information: ' + JSON.stringify(data));
      }
    });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getOsAccountDistributedInfo exception: code is ${err.code}, message is ${err.message}`);
}
```

<a id="getosaccountdistributedinfo-1"></a>

## getOsAccountDistributedInfo

```TypeScript
getOsAccountDistributedInfo(): Promise<DistributedInfo>
```

Obtains the distributed account information. This API uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.MANAGE_DISTRIBUTED_ACCOUNTS or ohos.permission.GET_DISTRIBUTED_ACCOUNTS or ohos.permission.DISTRIBUTED_DATASYNC

**System capability:** SystemCapability.Account.OsAccount

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[DistributedInfo](arkts-basicservices-distributedaccount-distributedinfo-i.md)&gt; | Promise used to return the distributed account information obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain a DistributedAccountAbility instance.
const accountAbility: distributedAccount.DistributedAccountAbility = distributedAccount.getDistributedAccountAbility();
try {
  accountAbility.getOsAccountDistributedInfo().then((data: distributedAccount.DistributedInfo) => {
    console.info('distributed information: ' + JSON.stringify(data));
  }).catch((err: BusinessError) => {
    console.error(`getOsAccountDistributedInfo exception: code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getOsAccountDistributedInfo exception: code is ${err.code}, message is ${err.message}`);
}
```

## queryOsAccountDistributedInfo

```TypeScript
queryOsAccountDistributedInfo(callback: AsyncCallback<DistributedInfo>): void
```

Queries the distributed account information. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use
> [getOsAccountDistributedInfo](#getosaccountdistributedinfo)
> instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getOsAccountDistributedInfo](#getosaccountdistributedinfo)(callback: AsyncCallback&lt;DistributedInfo&gt;)

**Required permissions:** ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.DISTRIBUTED_DATASYNC

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;[DistributedInfo](arkts-basicservices-distributedaccount-distributedinfo-i.md)&gt; | Yes | Callback used to return the result. If the distributed account information is obtained successfully, **err** is **undefined** and **data** is the distributed account information obtained. Otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain a DistributedAccountAbility instance.
const accountAbility: distributedAccount.DistributedAccountAbility = distributedAccount.getDistributedAccountAbility();
accountAbility.queryOsAccountDistributedInfo(
  (err: BusinessError, data: distributedAccount.DistributedInfo) => {
    if (err) {
      console.error(`queryOsAccountDistributedInfo exception: code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('distributed information: ' + JSON.stringify(data));
    }
  });
```

<a id="queryosaccountdistributedinfo-1"></a>

## queryOsAccountDistributedInfo

```TypeScript
queryOsAccountDistributedInfo(): Promise<DistributedInfo>
```

Queries the distributed account information. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use
> [getOsAccountDistributedInfo](#getosaccountdistributedinfo)
> instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getOsAccountDistributedInfo](#getosaccountdistributedinfo)()

**Required permissions:** ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.DISTRIBUTED_DATASYNC

**System capability:** SystemCapability.Account.OsAccount

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[DistributedInfo](arkts-basicservices-distributedaccount-distributedinfo-i.md)&gt; | Promise used to return the distributed account information obtained. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain a DistributedAccountAbility instance.
const accountAbility: distributedAccount.DistributedAccountAbility = distributedAccount.getDistributedAccountAbility();
accountAbility.queryOsAccountDistributedInfo().then((data: distributedAccount.DistributedInfo) => {
  console.info('distributed information: ' + JSON.stringify(data));
}).catch((err: BusinessError) => {
  console.error(`queryOsAccountDistributedInfo exception: code is ${err.code}, message is ${err.message}`);
});
```

## setOsAccountDistributedInfo

```TypeScript
setOsAccountDistributedInfo(accountInfo: DistributedInfo, callback: AsyncCallback<void>): void
```

Sets the distributed account information. This API uses an asynchronous callback to return the result. This API can be called only by system applications.

**Since:** 9

**Required permissions:** ohos.permission.MANAGE_DISTRIBUTED_ACCOUNTS

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| accountInfo | [DistributedInfo](arkts-basicservices-distributedaccount-distributedinfo-i.md) | Yes | Distributed account information. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the distributed account information is updated successfully, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid accountInfo. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |
| 12300406 | The distributed account information has already been bound to a sub-profile of the same OS account.<br>**Applicable version:** 26.0.0 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain a DistributedAccountAbility instance.
const accountAbility: distributedAccount.DistributedAccountAbility = distributedAccount.getDistributedAccountAbility();
// This is an example. Replace it with the actual distributed account information obtained using getOsAccountDistributedInfo.
let accountInfo: distributedAccount.DistributedInfo =
  { id: '12345', name: 'ZhangSan', event: 'Ohos.account.event.LOGIN' };
try {
  accountAbility.setOsAccountDistributedInfo(accountInfo, (err: BusinessError) => {
    if (err) {
      console.error(`setOsAccountDistributedInfo exception: code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('setOsAccountDistributedInfo successfully');
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`setOsAccountDistributedInfo exception: code is ${err.code}, message is ${err.message}`);
}
```

<a id="setosaccountdistributedinfo-1"></a>

## setOsAccountDistributedInfo

```TypeScript
setOsAccountDistributedInfo(accountInfo: DistributedInfo): Promise<void>
```

Sets the distributed account information. This API uses a promise to return the result. This API can be called only by system applications.

**Since:** 9

**Required permissions:** ohos.permission.MANAGE_DISTRIBUTED_ACCOUNTS

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| accountInfo | [DistributedInfo](arkts-basicservices-distributedaccount-distributedinfo-i.md) | Yes | Distributed account information. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | System service exception. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid accountInfo. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |
| 12300406 | The distributed account information has already been bound to a sub-profile of the same OS account.<br>**Applicable version:** 26.0.0 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain a DistributedAccountAbility instance.
const accountAbility: distributedAccount.DistributedAccountAbility = distributedAccount.getDistributedAccountAbility();
// This is an example. Replace it with the actual distributed account information obtained using getOsAccountDistributedInfo.
let accountInfo: distributedAccount.DistributedInfo =
  { id: '12345', name: 'ZhangSan', event: 'Ohos.account.event.LOGIN' };
try {
  accountAbility.setOsAccountDistributedInfo(accountInfo).then(() => {
    console.info('setOsAccountDistributedInfo successfully');
  }).catch((err: BusinessError) => {
    console.error(`setOsAccountDistributedInfo exception: code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`setOsAccountDistributedInfo exception: code is ${err.code}, message is ${err.message}`);
}
```

## updateOsAccountDistributedInfo

```TypeScript
updateOsAccountDistributedInfo(accountInfo: DistributedInfo, callback: AsyncCallback<void>): void
```

Updates the distributed account information. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use
> [setOsAccountDistributedInfo](#setosaccountdistributedinfo)
> instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [setOsAccountDistributedInfo](#setosaccountdistributedinfo)(accountInfo: DistributedInfo, callback: AsyncCallback&lt;void&gt;)

**Required permissions:** ohos.permission.MANAGE_LOCAL_ACCOUNTS

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| accountInfo | [DistributedInfo](arkts-basicservices-distributedaccount-distributedinfo-i.md) | Yes | Distributed account information. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the distributed account information is updated successfully, **err** is **undefined**. Otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain a DistributedAccountAbility instance.
const accountAbility: distributedAccount.DistributedAccountAbility = distributedAccount.getDistributedAccountAbility();
// This is an example. Replace it with the actual distributed account information obtained using getOsAccountDistributedInfo.
let accountInfo: distributedAccount.DistributedInfo =
  { id: '12345', name: 'ZhangSan', event: 'Ohos.account.event.LOGIN' };
accountAbility.updateOsAccountDistributedInfo(accountInfo, (err: BusinessError) => {
  if (err) {
    console.error(`updateOsAccountDistributedInfo exception: code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('updateOsAccountDistributedInfo successfully');
  }
});
```

<a id="updateosaccountdistributedinfo-1"></a>

## updateOsAccountDistributedInfo

```TypeScript
updateOsAccountDistributedInfo(accountInfo: DistributedInfo): Promise<void>
```

Updates the distributed account information. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use
> [setOsAccountDistributedInfo](#setosaccountdistributedinfo-1)
> instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [setOsAccountDistributedInfo](#setosaccountdistributedinfo-1)(accountInfo: DistributedInfo)

**Required permissions:** ohos.permission.MANAGE_LOCAL_ACCOUNTS

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| accountInfo | [DistributedInfo](arkts-basicservices-distributedaccount-distributedinfo-i.md) | Yes | Distributed account information. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain a DistributedAccountAbility instance.
const accountAbility: distributedAccount.DistributedAccountAbility = distributedAccount.getDistributedAccountAbility();
// This is an example. Replace it with the actual distributed account information obtained using getOsAccountDistributedInfo.
let accountInfo: distributedAccount.DistributedInfo =
  { id: '12345', name: 'ZhangSan', event: 'Ohos.account.event.LOGIN' };
accountAbility.updateOsAccountDistributedInfo(accountInfo).then(() => {
  console.info('updateOsAccountDistributedInfo successfully');
}).catch((err: BusinessError) => {
  console.error(`updateOsAccountDistributedInfo exception: code is ${err.code}, message is ${err.message}`);
});
```
