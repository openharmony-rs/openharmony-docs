# AccountManager

```TypeScript
interface AccountManager
```

Provides APIs for managing OS accounts.

**Since:** 7

**System capability:** SystemCapability.Account.OsAccount

## Modules to Import

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

## checkMultiOsAccountEnabled

```TypeScript
checkMultiOsAccountEnabled(callback: AsyncCallback<boolean>): void
```

Checks whether multiple OS accounts are supported. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. The value **true** means multiple OS accounts are supported; the value **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.checkMultiOsAccountEnabled((err: BusinessError, isEnabled: boolean) => {
    if (err) {
      console.error(`checkMultiOsAccountEnabled failed, code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('checkMultiOsAccountEnabled successfully, isEnabled: ' + isEnabled);
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`checkMultiOsAccountEnabled failed, code is ${err.code}, message is ${err.message}`);
}
```

<a id="checkmultiosaccountenabled-1"></a>

## checkMultiOsAccountEnabled

```TypeScript
checkMultiOsAccountEnabled(): Promise<boolean>
```

Checks whether multiple OS accounts are supported. This API uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.OsAccount

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** means multiple OS accounts are supported; the value **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
  accountManager.checkMultiOsAccountEnabled().then((isEnabled: boolean) => {
    console.info('checkMultiOsAccountEnabled successfully, isEnabled: ' + isEnabled);
  }).catch((err: BusinessError) => {
    console.error(`checkMultiOsAccountEnabled failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`checkMultiOsAccountEnabled failed, code is ${err.code}, message is ${err.message}`);
}
```

## checkOsAccountActivated

```TypeScript
checkOsAccountActivated(localId: number, callback: AsyncCallback<boolean>): void
```

Checks whether an OS account is activated. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 9 and deprecated since API version 11. The substitute API is available
> only to system applications.

**Since:** 9

**Deprecated since:** 11

**Required permissions:** ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| localId | number | Yes | ID of the target OS account. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. The value **true** means the account is activated; the value **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid localId. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |

**Examples**

Check whether OS account 100 is activated.

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
// localId indicates the OS account ID, which can be obtained by calling getOsAccountLocalId.
let localId: number = 100;
try {
  accountManager.checkOsAccountActivated(localId, (err: BusinessError, isActivated: boolean) => {
    if (err) {
      console.error(`checkOsAccountActivated failed, code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('checkOsAccountActivated successfully, isActivated:' + isActivated);
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`checkOsAccountActivated exception: code is ${err.code}, message is ${err.message}`);
}
```

<a id="checkosaccountactivated-1"></a>

## checkOsAccountActivated

```TypeScript
checkOsAccountActivated(localId: number): Promise<boolean>
```

Checks whether an OS account is activated. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API is supported since API version 9 and deprecated since API version 11. The substitute API is available
> only to system applications.

**Since:** 9

**Deprecated since:** 11

**Required permissions:** ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| localId | number | Yes | ID of the target OS account. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** means the account is activated; the value **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid localId. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |

**Examples**

Check whether OS account 100 is activated.

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
// localId indicates the OS account ID, which can be obtained by calling getOsAccountLocalId.
let localId: number = 100;
try {
  accountManager.checkOsAccountActivated(localId).then((isActivated: boolean) => {
    console.info('checkOsAccountActivated successfully, isActivated: ' + isActivated);
  }).catch((err: BusinessError) => {
    console.error(`checkOsAccountActivated failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`checkOsAccountActivated exception: code is ${err.code}, message is ${err.message}`);
}
```

## checkOsAccountConstraintEnabled

```TypeScript
checkOsAccountConstraintEnabled(localId: number, constraint: string, callback: AsyncCallback<boolean>): void
```

Checks whether the specified constraint is enabled for an OS account. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 9 and deprecated since API version 11. The substitute API is available
> only to system applications.

**Since:** 9

**Deprecated since:** 11

**Required permissions:** ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| localId | number | Yes | ID of the target OS account. |
| constraint | string | Yes | [Constraint](../../../reference/apis-basic-services-kit/appendix-osAccount-constraints.md) to check. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. The value **true** means the specified constraint is enabled; the value **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid localId or constraint. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |

**Examples**

Check whether OS account 100 is forbidden to use Wi-Fi.

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
// localId indicates the OS account ID, which can be obtained by calling getOsAccountLocalId.
let localId: number = 100;
let constraint: string = 'constraint.wifi';
try {
  accountManager.checkOsAccountConstraintEnabled(localId, constraint, (err: BusinessError, isEnabled: boolean)=>{
    if (err) {
      console.error(`checkOsAccountConstraintEnabled failed, code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('checkOsAccountConstraintEnabled successfully, isEnabled: ' + isEnabled);
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`checkOsAccountConstraintEnabled exception: code is ${err.code}, message is ${err.message}`);
}
```

<a id="checkosaccountconstraintenabled-1"></a>

## checkOsAccountConstraintEnabled

```TypeScript
checkOsAccountConstraintEnabled(localId: number, constraint: string): Promise<boolean>
```

Checks whether the specified constraint is enabled for an OS account. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API is supported since API version 9 and deprecated since API version 11. The substitute API is available
> only to system applications.

**Since:** 9

**Deprecated since:** 11

**Required permissions:** ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| localId | number | Yes | ID of the target OS account. |
| constraint | string | Yes | [Constraint](../../../reference/apis-basic-services-kit/appendix-osAccount-constraints.md) to check. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** means the specified constraint is enabled; the value **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid localId or constraint. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |

**Examples**

Check whether OS account 100 is forbidden to use Wi-Fi.

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
// localId indicates the OS account ID, which can be obtained by calling getOsAccountLocalId.
let localId: number = 100;
let constraint: string = 'constraint.wifi';
try {
  accountManager.checkOsAccountConstraintEnabled(localId, constraint).then((isEnabled: boolean) => {
    console.info('checkOsAccountConstraintEnabled successfully, isEnabled: ' + isEnabled);
  }).catch((err: BusinessError) => {
    console.error(`checkOsAccountConstraintEnabled failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`checkOsAccountConstraintEnabled exception: code is ${err.code}, message is ${err.message}`);
}
```

## checkOsAccountTestable

```TypeScript
checkOsAccountTestable(callback: AsyncCallback<boolean>): void
```

Checks whether the current OS account is a test account. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.OsAccount

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. The value **true** means the account is a test account; the value **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.checkOsAccountTestable((err: BusinessError, isTestable: boolean) => {
    if (err) {
      console.error(`checkOsAccountTestable failed, code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('checkOsAccountTestable successfully, isTestable: ' + isTestable);
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`checkOsAccountTestable code is ${err.code}, message is ${err.message}`);
}
```

<a id="checkosaccounttestable-1"></a>

## checkOsAccountTestable

```TypeScript
checkOsAccountTestable(): Promise<boolean>
```

Checks whether the current OS account is a test account. This API uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.OsAccount

**Test API:** This API is used only in automated test scripts.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** means the account is a test account; the value **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.checkOsAccountTestable().then((isTestable: boolean) => {
    console.info('checkOsAccountTestable successfully, isTestable: ' + isTestable);
  }).catch((err: BusinessError) => {
    console.error(`checkOsAccountTestable failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`checkOsAccountTestable exception: code is ${err.code}, message is ${err.message}`);
}
```

## checkOsAccountVerified

```TypeScript
checkOsAccountVerified(callback: AsyncCallback<boolean>): void
```

Checks whether the current OS account is unlocked. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 9 and deprecated since API version 11. You are advised to use
> [isOsAccountUnlocked](#isosaccountunlocked) instead.

**Since:** 9

**Deprecated since:** 11

**Substitutes:** [isOsAccountUnlocked](#isosaccountunlocked)()

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. The value **true** means the OS account has been verified; the value **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.checkOsAccountVerified((err: BusinessError, isVerified: boolean) => {
    if (err) {
      console.error(`checkOsAccountVerified failed, code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('checkOsAccountVerified successfully, isVerified: ' + isVerified);
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`checkOsAccountVerified exception: code is ${err.code}, message is ${err.message}`);
}
```

<a id="checkosaccountverified-1"></a>

## checkOsAccountVerified

```TypeScript
checkOsAccountVerified(): Promise<boolean>
```

Checks whether the current OS account has been verified. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API is supported since API version 9 and deprecated since API version 11. You are advised to use
> [isOsAccountUnlocked](#isosaccountunlocked) instead.

**Since:** 9

**Deprecated since:** 11

**Substitutes:** [isOsAccountUnlocked](#isosaccountunlocked)()

**System capability:** SystemCapability.Account.OsAccount

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** means the OS account has been verified; the value **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.checkOsAccountVerified().then((isVerified: boolean) => {
    console.info('checkOsAccountVerified successfully, isVerified: ' + isVerified);
  }).catch((err: BusinessError) => {
    console.error(`checkOsAccountVerified failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`checkOsAccountVerified exception: code is ${err.code}, message is ${err.message}`);
}
```

<a id="checkosaccountverified-2"></a>

## checkOsAccountVerified

```TypeScript
checkOsAccountVerified(localId: number, callback: AsyncCallback<boolean>): void
```

Checks whether an OS account has been verified. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 9 and deprecated since API version 11. The substitute API is available
> only to system applications.

**Since:** 9

**Deprecated since:** 11

**Required permissions:** ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| localId | number | Yes | ID of the target OS account. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. The value **true** means the OS account has been verified; the value **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid localId. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
// localId indicates the OS account ID, which can be obtained by calling getOsAccountLocalId.
let localId: number = 100;
try {
  accountManager.checkOsAccountVerified(localId, (err: BusinessError, isVerified: boolean) => {
    if (err) {
      console.error(`checkOsAccountVerified failed, code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('checkOsAccountVerified successfully, isVerified: ' + isVerified);
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`checkOsAccountVerified exception: code is ${err.code}, message is ${err.message}`);
}
```

<a id="checkosaccountverified-3"></a>

## checkOsAccountVerified

```TypeScript
checkOsAccountVerified(localId: number): Promise<boolean>
```

Checks whether an OS account has been verified. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API is supported since API version 9 and deprecated since API version 11. The substitute API is available
> only to system applications.

**Since:** 9

**Deprecated since:** 11

**Required permissions:** ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| localId | number | Yes | ID of the target OS account. If this parameter is not specified, this API checks whether the current OS account has been verified. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** means the OS account has been verified; the value **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid localId. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
// localId indicates the OS account ID, which can be obtained by calling getOsAccountLocalId.
let localId: number = 100;
try {
  accountManager.checkOsAccountVerified(localId).then((isVerified: boolean) => {
    console.info('checkOsAccountVerified successfully, isVerified: ' + isVerified);
  }).catch((err: BusinessError) => {
    console.error(`checkOsAccountVerified failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`checkOsAccountVerified exception: code is ${err.code}, message is ${err.message}`);
}
```

## getActivatedOsAccountLocalIds

```TypeScript
getActivatedOsAccountLocalIds(callback: AsyncCallback<Array<number>>): void
```

Obtains information about all activated OS accounts. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;number&gt;&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is a list of activated OS accounts. Otherwise, **data** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.getActivatedOsAccountLocalIds((err: BusinessError, idArray: number[])=>{
    if (err) {
      console.error(`getActivatedOsAccountLocalIds code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('getActivatedOsAccountLocalIds idArray length:' + idArray.length);
      for(let i=0;i<idArray.length;i++) {
        console.info('activated os account id: ' + idArray[i]);
      }
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getActivatedOsAccountLocalIds exception: code is ${err.code}, message is ${err.message}`);
}
```

<a id="getactivatedosaccountlocalids-1"></a>

## getActivatedOsAccountLocalIds

```TypeScript
getActivatedOsAccountLocalIds(): Promise<Array<number>>
```

Obtains information about all activated OS accounts. This API uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.OsAccount

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;number&gt;&gt; | Promise used to return the information about all activated OS accounts. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.getActivatedOsAccountLocalIds().then((idArray: number[]) => {
    console.info('getActivatedOsAccountLocalIds, idArray: ' + idArray);
  }).catch((err: BusinessError) => {
    console.error(`getActivatedOsAccountLocalIds err: code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getActivatedOsAccountLocalIds exception: code is ${err.code}, message is ${err.message}`);
}
```

## getCreatedOsAccountsCount

```TypeScript
getCreatedOsAccountsCount(callback: AsyncCallback<number>): void
```

Obtains the number of OS accounts created. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use
> [getOsAccountCount](#getosaccountcount) instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getOsAccountCount](#getosaccountcount)(callback: AsyncCallback&lt;number&gt;)

**Required permissions:** ohos.permission.MANAGE_LOCAL_ACCOUNTS

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is the number of created OS accounts. If the operation fails, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
accountManager.getCreatedOsAccountsCount((err: BusinessError, count: number)=>{
  if (err) {
    console.error(`getCreatedOsAccountsCount failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('getCreatedOsAccountsCount successfully, count: ' + count);
  }
});
```

<a id="getcreatedosaccountscount-1"></a>

## getCreatedOsAccountsCount

```TypeScript
getCreatedOsAccountsCount(): Promise<number>
```

Obtains the number of OS accounts created. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use
> [getOsAccountCount](#getosaccountcount) instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getOsAccountCount](#getosaccountcount)()

**Required permissions:** ohos.permission.MANAGE_LOCAL_ACCOUNTS

**System capability:** SystemCapability.Account.OsAccount

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the number of created OS accounts. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
accountManager.getCreatedOsAccountsCount().then((count: number) => {
  console.info('getCreatedOsAccountsCount successfully, count: ' + count);
}).catch((err: BusinessError) => {
  console.error(`getCreatedOsAccountsCount failed, code is ${err.code}, message is ${err.message}`);
});
```

## getCurrentOsAccount

```TypeScript
getCurrentOsAccount(callback: AsyncCallback<OsAccountInfo>): void
```

Obtains information about the OS account to which the current process belongs. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 9 and deprecated since API version 11. The substitute API is available
> only to system applications.

**Since:** 9

**Deprecated since:** 11

**Required permissions:** 
- API version 10 and later: ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.GET_LOCAL_ACCOUNTS
- API version 9: ohos.permission.MANAGE_LOCAL_ACCOUNTS

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;[OsAccountInfo](arkts-basicservices-osaccount-osaccountinfo-i.md)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is the OS account information obtained. Otherwise, **data** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.getCurrentOsAccount((err: BusinessError, curAccountInfo: osAccount.OsAccountInfo)=>{
    if (err) {
      console.error(`getCurrentOsAccount code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('getCurrentOsAccount curAccountInfo:' + JSON.stringify(curAccountInfo));
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getCurrentOsAccount exception: code is ${err.code}, message is ${err.message}`);
}
```

<a id="getcurrentosaccount-1"></a>

## getCurrentOsAccount

```TypeScript
getCurrentOsAccount(): Promise<OsAccountInfo>
```

Obtains information about the OS account to which the current process belongs. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API is supported since API version 9 and deprecated since API version 11. The substitute API is available
> only to system applications.

**Since:** 9

**Deprecated since:** 11

**Required permissions:** 
- API version 10 and later: ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.GET_LOCAL_ACCOUNTS
- API version 9: ohos.permission.MANAGE_LOCAL_ACCOUNTS

**System capability:** SystemCapability.Account.OsAccount

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[OsAccountInfo](arkts-basicservices-osaccount-osaccountinfo-i.md)&gt; | Promise used to return the OS account information obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.getCurrentOsAccount().then((accountInfo: osAccount.OsAccountInfo) => {
    console.info('getCurrentOsAccount, accountInfo: ' + JSON.stringify(accountInfo));
  }).catch((err: BusinessError) => {
    console.error(`getCurrentOsAccount err: code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getCurrentOsAccount exception: code is ${err.code}, message is ${err.message}`);
}
```

## getDistributedVirtualDeviceId

```TypeScript
getDistributedVirtualDeviceId(callback: AsyncCallback<string>): void
```

Obtains the ID of a distributed virtual device. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use
> [queryDistributedVirtualDeviceId](#querydistributedvirtualdeviceid)
> instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [queryDistributedVirtualDeviceId](#querydistributedvirtualdeviceid)(callback: AsyncCallback&lt;string&gt;)

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC or ohos.permission.MANAGE_LOCAL_ACCOUNTS

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is the distributed virtual device ID obtained. Otherwise, **data** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
accountManager.getDistributedVirtualDeviceId((err: BusinessError, virtualID: string) => {
  if (err) {
    console.error(`getDistributedVirtualDeviceId err: code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('getDistributedVirtualDeviceId virtualID: ' + virtualID);
  }
});
```

<a id="getdistributedvirtualdeviceid-1"></a>

## getDistributedVirtualDeviceId

```TypeScript
getDistributedVirtualDeviceId(): Promise<string>
```

Queries the ID of a distributed virtual device. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use
> [queryDistributedVirtualDeviceId](#querydistributedvirtualdeviceid) instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [queryDistributedVirtualDeviceId](#querydistributedvirtualdeviceid)()

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC or ohos.permission.MANAGE_LOCAL_ACCOUNTS

**System capability:** SystemCapability.Account.OsAccount

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the distributed virtual device ID obtained. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
accountManager.getDistributedVirtualDeviceId().then((virtualID: string) => {
  console.info('getDistributedVirtualDeviceId, virtualID: ' + virtualID);
}).catch((err: BusinessError) => {
  console.error(`getDistributedVirtualDeviceId err: code is ${err.code}, message is ${err.message}`);
});
```

## getForegroundOsAccountLocalId

```TypeScript
getForegroundOsAccountLocalId(): Promise<number>
```

Obtains the ID of the foreground OS account. This API uses a promise to return the result.

**Since:** 15

**System capability:** SystemCapability.Account.OsAccount

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the foreground OS account ID. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.getForegroundOsAccountLocalId().then((localId: number) => {
    console.info('getForegroundOsAccountLocalId, localId: ' + localId);
  }).catch((err: BusinessError) => {
    console.error(`getForegroundOsAccountLocalId err: code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getForegroundOsAccountLocalId exception: code is ${err.code}, message is ${err.message}`);
}
```

## getOsAccountAllConstraints

```TypeScript
getOsAccountAllConstraints(localId: number, callback: AsyncCallback<Array<string>>): void
```

Obtains all constraints enabled for an OS account. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. The substitute API is available
> only to system applications.

**Since:** 7

**Deprecated since:** 9

**Required permissions:** ohos.permission.MANAGE_LOCAL_ACCOUNTS

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| localId | number | Yes | ID of the target OS account. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;string&gt;&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is a list of all [constraints](../../../reference/apis-basic-services-kit/appendix-osAccount-constraints.md) enabled for the OS account. Otherwise, **err** is an error object. |

**Examples**

Obtain all constraints of OS account 100.

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
// localId indicates the OS account ID, which can be obtained by calling getOsAccountLocalId.
let localId: number = 100;
accountManager.getOsAccountAllConstraints(localId, (err: BusinessError, constraints: string[])=>{
  if (err) {
    console.error(`getOsAccountAllConstraints code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('getOsAccountAllConstraints:' + JSON.stringify(constraints));
  }
});
```

<a id="getosaccountallconstraints-1"></a>

## getOsAccountAllConstraints

```TypeScript
getOsAccountAllConstraints(localId: number): Promise<Array<string>>
```

Obtains all constraints enabled for an OS account. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. The substitute API is available
> only to system applications.

**Since:** 7

**Deprecated since:** 9

**Required permissions:** ohos.permission.MANAGE_LOCAL_ACCOUNTS

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| localId | number | Yes | ID of the target OS account. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return all the [constraints](../../../reference/apis-basic-services-kit/appendix-osAccount-constraints.md) enabled for the OS account. |

**Examples**

Obtain all constraints of OS account 100.

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
// localId indicates the OS account ID, which can be obtained by calling getOsAccountLocalId.
let localId: number = 100;
accountManager.getOsAccountAllConstraints(localId).then((constraints: string[]) => {
  console.info('getOsAccountAllConstraints, constraints: ' + constraints);
}).catch((err: BusinessError) => {
  console.error(`getOsAccountAllConstraints err: code is ${err.code}, message is ${err.message}`);
});
```

## getOsAccountConstraints

```TypeScript
getOsAccountConstraints(localId: number, callback: AsyncCallback<Array<string>>): void
```

Obtains all constraints enabled for an OS account. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 9 and deprecated since API version 11. The substitute API is available
> only to system applications.

**Since:** 9

**Deprecated since:** 11

**Required permissions:** ohos.permission.MANAGE_LOCAL_ACCOUNTS

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| localId | number | Yes | ID of the target OS account. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;string&gt;&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is all [constraints](../../../reference/apis-basic-services-kit/appendix-osAccount-constraints.md) obtained. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid localId. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |

**Examples**

Obtain all constraints of OS account 100.

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
// localId indicates the OS account ID, which can be obtained by calling getOsAccountLocalId.
let localId: number = 100;
try {
  accountManager.getOsAccountConstraints(localId, (err: BusinessError, constraints: string[]) => {
    if (err) {
      console.error(`getOsAccountConstraints failed, err: code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('getOsAccountConstraints successfully, constraints: ' + JSON.stringify(constraints));
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getOsAccountConstraints exception: code is ${err.code}, message is ${err.message}`);
}
```

<a id="getosaccountconstraints-1"></a>

## getOsAccountConstraints

```TypeScript
getOsAccountConstraints(localId: number): Promise<Array<string>>
```

Obtains all constraints enabled for an OS account. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API is supported since API version 9 and deprecated since API version 11. The substitute API is available
> only to system applications.

**Since:** 9

**Deprecated since:** 11

**Required permissions:** ohos.permission.MANAGE_LOCAL_ACCOUNTS

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| localId | number | Yes | ID of the target OS account. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return all the [constraints](../../../reference/apis-basic-services-kit/appendix-osAccount-constraints.md) enabled for the OS account. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid localId. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |

**Examples**

Obtain all constraints of OS account 100.

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
// localId indicates the OS account ID, which can be obtained by calling getOsAccountLocalId.
let localId: number = 100;
try {
  accountManager.getOsAccountConstraints(localId).then((constraints: string[]) => {
    console.info('getOsAccountConstraints, constraints: ' + constraints);
  }).catch((err: BusinessError) => {
    console.error(`getOsAccountConstraints err: code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getOsAccountConstraints exception: code is ${err.code}, message is ${err.message}`);
}
```

## getOsAccountCount

```TypeScript
getOsAccountCount(callback: AsyncCallback<number>): void
```

Obtains the number of OS accounts created. This API uses an asynchronous callback to return the result. This API can be called only by system applications.

**Since:** 9

**Required permissions:** ohos.permission.MANAGE_LOCAL_ACCOUNTS

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is the number of created OS accounts. If the operation fails, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.getOsAccountCount((err: BusinessError, count: number) => {
    if (err) {
      console.error(`getOsAccountCount failed, code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('getOsAccountCount successfully, count: ' + count);
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getOsAccountCount exception: code is ${err.code}, message is ${err.message}`);
}
```

<a id="getosaccountcount-1"></a>

## getOsAccountCount

```TypeScript
getOsAccountCount(): Promise<number>
```

Obtains the number of OS accounts created. This API uses a promise to return the result. This API can be called only by system applications.

**Since:** 9

**Required permissions:** ohos.permission.MANAGE_LOCAL_ACCOUNTS

**System capability:** SystemCapability.Account.OsAccount

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the number of created OS accounts. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.getOsAccountCount().then((count: number) => {
    console.info('getOsAccountCount successfully, count: ' + count);
  }).catch((err: BusinessError) => {
    console.error(`getOsAccountCount failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getOsAccountCount exception: code is ${err.code}, message is ${err.message}`);
}
```

## getOsAccountDomainInfo

```TypeScript
getOsAccountDomainInfo(localId: number): Promise<DomainAccountInfo>
```

Obtains the domain account information associated with a specified OS account. This API uses a promise to return the result.

**Since:** 15

**Required permissions:** ohos.permission.GET_DOMAIN_ACCOUNTS and ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| localId | number | Yes | ID of the target OS account. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[DomainAccountInfo](arkts-basicservices-osaccount-domainaccountinfo-i.md)&gt; | Promise used to return the domain account information obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | OS account not found. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
// localId indicates the OS account ID, which can be obtained by calling getOsAccountLocalId.
let localId: number = 100;
accountManager.getOsAccountDomainInfo(localId).then((domainAccountInfo: osAccount.DomainAccountInfo) => {
  if (domainAccountInfo === null) {
    console.info('The target OS account is not a domain account.')
  } else {
    console.info('getOsAccountDomainInfo domain: ' + domainAccountInfo.domain);
    console.info('getOsAccountDomainInfo accountName: ' + domainAccountInfo.accountName);
  }
}).catch((err: BusinessError) => {
  console.error(`getOsAccountDomainInfo err: code is ${err.code}, message is ${err.message}`);
})
```

## getOsAccountLocalId

```TypeScript
getOsAccountLocalId(callback: AsyncCallback<number>): void
```

Obtains the ID of the OS account to which the current process belongs. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is the OS account ID obtained. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.getOsAccountLocalId((err: BusinessError, localId: number) => {
    if (err) {
      console.error(`getOsAccountLocalId failed, code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('getOsAccountLocalId successfully, localId: ' + localId);
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getOsAccountLocalId exception: code is ${err.code}, message is ${err.message}`);
}
```

<a id="getosaccountlocalid-1"></a>

## getOsAccountLocalId

```TypeScript
getOsAccountLocalId(): Promise<number>
```

Obtains the ID of the OS account to which the current process belongs. This API uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.OsAccount

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the OS account ID obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.getOsAccountLocalId().then((localId: number) => {
    console.info('getOsAccountLocalId successfully, localId: ' + localId);
  }).catch((err: BusinessError) => {
    console.error(`getOsAccountLocalId failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getOsAccountLocalId exception: code is ${err.code}, message is ${err.message}`);
}
```

## getOsAccountLocalIdBySerialNumber

```TypeScript
getOsAccountLocalIdBySerialNumber(serialNumber: number, callback: AsyncCallback<number>): void
```

Obtains the OS account ID based on the SN. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use
> [getOsAccountLocalIdForSerialNumber](#getosaccountlocalidforserialnumber)
> instead.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getOsAccountLocalIdForSerialNumber](#getosaccountlocalidforserialnumber)(serialNumber: number, callback: AsyncCallback&lt;number&gt;)

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| serialNumber | number | Yes | Account SN. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is the OS account ID obtained. Otherwise, **err** is an error object. |

**Examples**

Obtain the ID of the OS account whose SN is 12345.

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
let serialNumber: number = 12345;
accountManager.getOsAccountLocalIdBySerialNumber(serialNumber, (err: BusinessError, localId: number)=>{
  if (err) {
    console.error(`get localId code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('get localId:' + localId + ' by serialNumber: ' + serialNumber);
  }
});
```

<a id="getosaccountlocalidbyserialnumber-1"></a>

## getOsAccountLocalIdBySerialNumber

```TypeScript
getOsAccountLocalIdBySerialNumber(serialNumber: number): Promise<number>
```

Obtains the OS account ID based on the SN. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use
> [getOsAccountLocalIdForSerialNumber](#getosaccountlocalidforserialnumber)
> instead.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getOsAccountLocalIdForSerialNumber](#getosaccountlocalidforserialnumber)(serialNumber: number)

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| serialNumber | number | Yes | Account SN. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the OS account ID obtained. |

**Examples**

Obtain the ID of the OS account whose SN is 12345.

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
let serialNumber: number = 12345;
accountManager.getOsAccountLocalIdBySerialNumber(serialNumber).then((localId: number) => {
  console.info('getOsAccountLocalIdBySerialNumber localId: ' + localId);
}).catch((err: BusinessError) => {
  console.error(`getOsAccountLocalIdBySerialNumber err: code is ${err.code}, message is ${err.message}`);
});
```

## getOsAccountLocalIdForDomain

```TypeScript
getOsAccountLocalIdForDomain(domainInfo: DomainAccountInfo, callback: AsyncCallback<number>): void
```

Obtains the OS account ID based on the domain account information. This API uses an asynchronous callback to return the result. This API can be called only by system applications.

**Since:** 9

**Required permissions:** ohos.permission.MANAGE_LOCAL_ACCOUNTS

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| domainInfo | [DomainAccountInfo](arkts-basicservices-osaccount-domainaccountinfo-i.md) | Yes | Domain account information. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is the ID of the OS account associated with the domain account. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid domainInfo. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Domain account not found. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let domainInfo: osAccount.DomainAccountInfo = {domain: 'testDomain', accountName: 'testAccountName'};
let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.getOsAccountLocalIdForDomain(domainInfo, (err: BusinessError, localId: number) => {
    if (err) {
      console.error(`getOsAccountLocalIdForDomain failed, code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('getOsAccountLocalIdForDomain successfully, localId: ' + localId);
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getOsAccountLocalIdForDomain exception: code is ${err.code}, message is ${err.message}`);
}
```

<a id="getosaccountlocalidfordomain-1"></a>

## getOsAccountLocalIdForDomain

```TypeScript
getOsAccountLocalIdForDomain(domainInfo: DomainAccountInfo): Promise<number>
```

Obtains the OS account ID based on the domain account information. This API uses a promise to return the result. This API can be called only by system applications.

**Since:** 9

**Required permissions:** ohos.permission.MANAGE_LOCAL_ACCOUNTS

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| domainInfo | [DomainAccountInfo](arkts-basicservices-osaccount-domainaccountinfo-i.md) | Yes | Domain account information. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the ID of the OS account associated with the domain account. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid domainInfo. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Domain account not found. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
let domainInfo: osAccount.DomainAccountInfo = {domain: 'testDomain', accountName: 'testAccountName'};
try {
  accountManager.getOsAccountLocalIdForDomain(domainInfo).then((localId: number) => {
    console.info('getOsAccountLocalIdForDomain successfully, localId: ' + localId);
  }).catch((err: BusinessError) => {
    console.error(`getOsAccountLocalIdForDomain failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getOsAccountLocalIdForDomain exception: code is ${err.code}, message is ${err.message}`);
}
```

## getOsAccountLocalIdForSerialNumber

```TypeScript
getOsAccountLocalIdForSerialNumber(serialNumber: number, callback: AsyncCallback<number>): void
```

Obtains the OS account ID based on the SN. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| serialNumber | number | Yes | Account SN. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is the OS account ID obtained. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid serialNumber. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | The account indicated by serialNumber does not exist. |

**Examples**

Obtain the ID of the OS account whose SN is 12345.

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
// serialNumber indicates the account serial number, which can be obtained by calling getSerialNumberForOsAccountLocalId.
let serialNumber: number = 12345;
try {
  accountManager.getOsAccountLocalIdForSerialNumber(serialNumber, (err: BusinessError, localId: number)=>{
    if (err) {
      console.error(`get localId code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('get localId:' + localId + ' by serialNumber: ' + serialNumber);
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`get localId exception: code is ${err.code}, message is ${err.message}`);
}
```

<a id="getosaccountlocalidforserialnumber-1"></a>

## getOsAccountLocalIdForSerialNumber

```TypeScript
getOsAccountLocalIdForSerialNumber(serialNumber: number): Promise<number>
```

Obtains the OS account ID based on the SN. This API uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| serialNumber | number | Yes | Account SN. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the OS account ID obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid serialNumber. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | The account indicated by serialNumber does not exist. |

**Examples**

Obtain the ID of the OS account whose SN is 12345.

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
// serialNumber indicates the account serial number, which can be obtained by calling getSerialNumberForOsAccountLocalId.
let serialNumber: number = 12345;
try {
  accountManager.getOsAccountLocalIdForSerialNumber(serialNumber).then((localId: number) => {
    console.info('getOsAccountLocalIdForSerialNumber localId: ' + localId);
  }).catch((err: BusinessError) => {
    console.error(`getOsAccountLocalIdForSerialNumber err: code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getOsAccountLocalIdForSerialNumber exception: code is ${err.code}, message is ${err.message}`);
}
```

## getOsAccountLocalIdForUid

```TypeScript
getOsAccountLocalIdForUid(uid: number, callback: AsyncCallback<number>): void
```

Obtains the OS account ID based on the process UID. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uid | number | Yes | Process UID. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is the OS account ID obtained. Otherwise, **data** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid uid. |

**Examples**

Obtain the ID of the OS account whose process UID is 12345678.

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
// uid indicates the application process UID, which can be obtained from the application information.
let uid: number = 12345678;
try {
  accountManager.getOsAccountLocalIdForUid(uid, (err: BusinessError, localId: number) => {
    if (err) {
      console.error(`getOsAccountLocalIdForUid failed, code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('getOsAccountLocalIdForUid successfully, localId: ' + localId);
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getOsAccountLocalIdForUid exception: code is ${err.code}, message is ${err.message}`);
}
```

<a id="getosaccountlocalidforuid-1"></a>

## getOsAccountLocalIdForUid

```TypeScript
getOsAccountLocalIdForUid(uid: number): Promise<number>
```

Obtains the OS account ID based on the process UID. This API uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uid | number | Yes | Process UID. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the OS account ID obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid uid. |

**Examples**

Obtain the ID of the OS account whose process UID is 12345678.

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
// uid indicates the application process UID, which can be obtained from the application information.
let uid: number = 12345678;
try {
  accountManager.getOsAccountLocalIdForUid(uid).then((localId: number) => {
    console.info('getOsAccountLocalIdForUid successfully, localId: ' + localId);
  }).catch((err: BusinessError) => {
    console.error(`getOsAccountLocalIdForUid failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getOsAccountLocalIdForUid exception: code is ${err.code}, message is ${err.message}`);
}
```

## getOsAccountLocalIdForUidSync

```TypeScript
getOsAccountLocalIdForUidSync(uid: number): number
```

Obtains the OS account ID based on the process UID. The API returns the result synchronously.

**Since:** 10

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uid | number | Yes | Process UID. |

**Return value:**

| Type | Description |
| --- | --- |
| number | OS account ID obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid uid. |

**Examples**

Obtain the ID of the OS account whose process UID is 12345678.

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
// uid indicates the application process UID, which can be obtained from the application information.
let uid: number = 12345678;
try {
  let localId : number = accountManager.getOsAccountLocalIdForUidSync(uid);
  console.info('getOsAccountLocalIdForUidSync successfully, localId: ' + localId);
} catch (e) {
  const err = e as BusinessError;
  console.error(`getOsAccountLocalIdForUidSync exception: code is ${err.code}, message is ${err.message}`);
}
```

## getOsAccountLocalIdFromDomain

```TypeScript
getOsAccountLocalIdFromDomain(domainInfo: DomainAccountInfo, callback: AsyncCallback<number>): void
```

Obtains the OS account ID based on the domain account information. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use
> [getOsAccountLocalIdForDomain](#getosaccountlocalidfordomain)
> instead.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getOsAccountLocalIdForDomain](#getosaccountlocalidfordomain)(domainInfo: DomainAccountInfo, callback: AsyncCallback&lt;number&gt;)

**Required permissions:** ohos.permission.MANAGE_LOCAL_ACCOUNTS

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| domainInfo | [DomainAccountInfo](arkts-basicservices-osaccount-domainaccountinfo-i.md) | Yes | Domain account information. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is the OS account ID obtained. Otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let domainInfo: osAccount.DomainAccountInfo = {domain: 'testDomain', accountName: 'testAccountName'};
let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
accountManager.getOsAccountLocalIdFromDomain(domainInfo, (err: BusinessError, localId: number) => {
  if (err) {
    console.error(`getOsAccountLocalIdFromDomain failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('getOsAccountLocalIdFromDomain successfully, localId: ' + localId);
  }
});
```

<a id="getosaccountlocalidfromdomain-1"></a>

## getOsAccountLocalIdFromDomain

```TypeScript
getOsAccountLocalIdFromDomain(domainInfo: DomainAccountInfo): Promise<number>
```

Obtains the OS account ID based on the domain account information. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use
> [getOsAccountLocalIdForDomain](#getosaccountlocalidfordomain-1)
> instead.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getOsAccountLocalIdForDomain](#getosaccountlocalidfordomain-1)(domainInfo: DomainAccountInfo)

**Required permissions:** ohos.permission.MANAGE_LOCAL_ACCOUNTS

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| domainInfo | [DomainAccountInfo](arkts-basicservices-osaccount-domainaccountinfo-i.md) | Yes | Domain account information. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the ID of the OS account associated with the domain account. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
let domainInfo: osAccount.DomainAccountInfo = {domain: 'testDomain', accountName: 'testAccountName'};
accountManager.getOsAccountLocalIdFromDomain(domainInfo).then((localId: number) => {
  console.info('getOsAccountLocalIdFromDomain successfully, localId: ' + localId);
}).catch((err: BusinessError) => {
  console.error(`getOsAccountLocalIdFromDomain failed, code is ${err.code}, message is ${err.message}`);
});
```

## getOsAccountLocalIdFromProcess

```TypeScript
getOsAccountLocalIdFromProcess(callback: AsyncCallback<number>): void
```

Obtains the ID of the OS account to which the current process belongs. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use
> [getOsAccountLocalId](#getosaccountlocalid)
> instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getOsAccountLocalId](#getosaccountlocalid)(callback: AsyncCallback&lt;number&gt;)

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is the OS account ID obtained. Otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
accountManager.getOsAccountLocalIdFromProcess((err: BusinessError, localId: number) => {
  if (err) {
    console.error(`getOsAccountLocalIdFromProcess failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('getOsAccountLocalIdFromProcess id:: ' + localId);
  }
});
```

<a id="getosaccountlocalidfromprocess-1"></a>

## getOsAccountLocalIdFromProcess

```TypeScript
getOsAccountLocalIdFromProcess(): Promise<number>
```

Obtains the ID of the OS account to which the current process belongs. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use
> [getOsAccountLocalId](#getosaccountlocalid) instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getOsAccountLocalId](#getosaccountlocalid)()

**System capability:** SystemCapability.Account.OsAccount

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the OS account ID obtained. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
accountManager.getOsAccountLocalIdFromProcess().then((localId: number) => {
  console.info('getOsAccountLocalIdFromProcess successfully, localId: ' + localId);
}).catch((err: BusinessError) => {
  console.error(`getOsAccountLocalIdFromProcess failed, code is ${err.code}, message is ${err.message}`);
});
```

## getOsAccountLocalIdFromUid

```TypeScript
getOsAccountLocalIdFromUid(uid: number, callback: AsyncCallback<number>): void
```

Obtains the OS account ID based on the process UID. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use
> [getOsAccountLocalIdForUid](#getosaccountlocalidforuid)
> instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getOsAccountLocalIdForUid](#getosaccountlocalidforuid)(uid: number, callback: AsyncCallback&lt;number&gt;)

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uid | number | Yes | Process UID. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is the OS account ID obtained. Otherwise, **data** is an error object. |

**Examples**

Obtain the ID of the OS account whose process UID is 12345678.

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
let uid: number = 12345678;
accountManager.getOsAccountLocalIdFromUid(uid, (err: BusinessError, localId: number) => {
  if (err) {
    console.error(`getOsAccountLocalIdFromUid failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('getOsAccountLocalIdFromUid successfully, localId: ' + localId);
  }
});
```

<a id="getosaccountlocalidfromuid-1"></a>

## getOsAccountLocalIdFromUid

```TypeScript
getOsAccountLocalIdFromUid(uid: number): Promise<number>
```

Obtains the OS account ID based on the process UID. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use
> [getOsAccountLocalIdForUid](#getosaccountlocalidforuid) instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getOsAccountLocalIdForUid](#getosaccountlocalidforuid)(uid: number)

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uid | number | Yes | Process UID. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the OS account ID obtained. |

**Examples**

Obtain the ID of the OS account whose process UID is 12345678.

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
let uid: number = 12345678;
accountManager.getOsAccountLocalIdFromUid(uid).then((localId: number) => {
  console.info('getOsAccountLocalIdFromUid successfully, localId: ' + localId);
}).catch((err: BusinessError) => {
  console.error(`getOsAccountLocalIdFromUid failed, code is ${err.code}, message is ${err.message}`);
});
```

## getOsAccountLocalIds

```TypeScript
getOsAccountLocalIds(): Promise<number[]>
```

Obtains the local IDs of all non-system-level OS accounts. Non-system-level OS accounts are visible to users and are usually used for operations such as login. This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.GET_LOCAL_ACCOUNT_IDENTIFIERS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Account.OsAccount

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number[]&gt; | Promise used to return the local IDs of all non-system-level OS accounts. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.getOsAccountLocalIds().then((localIds: number[]) => {
    console.info('getOsAccountLocalIds localIds: ' + localIds);
  }).catch((err: BusinessError) => {
    console.error(`getOsAccountLocalIds failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getOsAccountLocalIds exception: code is ${err.code}, message is ${err.message}`);
}
```

## getOsAccountName

```TypeScript
getOsAccountName(): Promise<string>
```

Obtains the name of the OS account of the caller. This API uses a promise to return the result.

**Since:** 12

**System capability:** SystemCapability.Account.OsAccount

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the OS account name obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.getOsAccountName().then((name: string) => {
    console.info('getOsAccountName, name: ' + name);
  }).catch((err: BusinessError) => {
    console.error('getOsAccountName err: ' + err);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getOsAccountName exception: code is ${err.code}, message is ${err.message}`);
}
```

## getOsAccountNameByLocalId

```TypeScript
getOsAccountNameByLocalId(localId: number): Promise<string>
```

Obtains the name of an OS account based on its local ID. This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.GET_LOCAL_ACCOUNT_IDENTIFIERS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| localId | number | Yes | Local ID of the target OS account. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the name of the target OS account. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |
| [12300008](../errorcode-account.md#12300008-restricted-account) | Restricted Account. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.getOsAccountNameByLocalId(100).then((name: string) => {
    console.info('getOsAccountNameByLocalId, name: ' + name);
  }).catch((err: BusinessError) => {
    console.error('getOsAccountNameByLocalId err: ' + err);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getOsAccountNameByLocalId exception: code is ${err.code}, message is ${err.message}`);
}
```

## getOsAccountType

```TypeScript
getOsAccountType(callback: AsyncCallback<OsAccountType>): void
```

Obtains the type of the account to which the current process belongs. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;[OsAccountType](arkts-basicservices-osaccount-osaccounttype-e.md)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is the OS account type obtained. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.getOsAccountType((err: BusinessError, accountType: osAccount.OsAccountType) => {
    if (err) {
      console.error(`getOsAccountType err: code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('getOsAccountType accountType: ' + accountType);
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getOsAccountType exception: code is ${err.code}, message is ${err.message}`);
}
```

<a id="getosaccounttype-1"></a>

## getOsAccountType

```TypeScript
getOsAccountType(): Promise<OsAccountType>
```

Obtains the type of the account to which the current process belongs. This API uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.OsAccount

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[OsAccountType](arkts-basicservices-osaccount-osaccounttype-e.md)&gt; | Promise used to return the OS account type obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.getOsAccountType().then((accountType: osAccount.OsAccountType) => {
    console.info('getOsAccountType, accountType: ' + accountType);
  }).catch((err: BusinessError) => {
    console.error(`getOsAccountType err: code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getOsAccountType exception: code is ${err.code}, message is ${err.message}`);
}
```

## getOsAccountTypeFromProcess

```TypeScript
getOsAccountTypeFromProcess(callback: AsyncCallback<OsAccountType>): void
```

Obtains the type of the account to which the current process belongs. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use
> [getOsAccountType](#getosaccounttype)
> instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getOsAccountType](#getosaccounttype)(callback: AsyncCallback&lt;OsAccountType&gt;)

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;[OsAccountType](arkts-basicservices-osaccount-osaccounttype-e.md)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is the OS account type obtained. Otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
accountManager.getOsAccountTypeFromProcess((err: BusinessError, accountType: osAccount.OsAccountType) => {
  if (err) {
    console.error(`getOsAccountTypeFromProcess err: code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('getOsAccountTypeFromProcess accountType: ' + accountType);
  }
});
```

<a id="getosaccounttypefromprocess-1"></a>

## getOsAccountTypeFromProcess

```TypeScript
getOsAccountTypeFromProcess(): Promise<OsAccountType>
```

Obtains the type of the account to which the current process belongs. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use
> [getOsAccountType](#getosaccounttype) instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getOsAccountType](#getosaccounttype)()

**System capability:** SystemCapability.Account.OsAccount

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[OsAccountType](arkts-basicservices-osaccount-osaccounttype-e.md)&gt; | Promise used to return the OS account type obtained. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
accountManager.getOsAccountTypeFromProcess().then((accountType: osAccount.OsAccountType) => {
  console.info('getOsAccountTypeFromProcess, accountType: ' + accountType);
}).catch((err: BusinessError) => {
  console.error(`getOsAccountTypeFromProcess err: code is ${err.code}, message is ${err.message}`);
});
```

## getSerialNumberByOsAccountLocalId

```TypeScript
getSerialNumberByOsAccountLocalId(localId: number, callback: AsyncCallback<number>): void
```

Obtains the SN of an OS account based on the account ID. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use
> [getSerialNumberForOsAccountLocalId](#getserialnumberforosaccountlocalid)
> instead.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getSerialNumberForOsAccountLocalId](#getserialnumberforosaccountlocalid)(localId: number, callback: AsyncCallback&lt;number&gt;)

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| localId | number | Yes | ID of the target OS account. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is the SN obtained. Otherwise, **err** is an error object. |

**Examples**

Obtain the SN of the OS account 100.

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
// localId indicates the OS account ID, which can be obtained by calling getOsAccountLocalId.
let localId: number = 100;
accountManager.getSerialNumberByOsAccountLocalId(localId, (err: BusinessError, serialNumber: number)=>{
  if (err) {
    console.error(`get serialNumber code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('get serialNumber:' + serialNumber + ' by localId: ' + localId);
  }
});
```

<a id="getserialnumberbyosaccountlocalid-1"></a>

## getSerialNumberByOsAccountLocalId

```TypeScript
getSerialNumberByOsAccountLocalId(localId: number): Promise<number>
```

Obtains the SN of an OS account based on the account ID. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use
> [getSerialNumberForOsAccountLocalId](#getserialnumberforosaccountlocalid)
> instead.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getSerialNumberForOsAccountLocalId](#getserialnumberforosaccountlocalid)(localId: number)

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| localId | number | Yes | ID of the target OS account. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the SN obtained. |

**Examples**

Obtain the SN of the OS account 100.

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
// localId indicates the OS account ID, which can be obtained by calling getOsAccountLocalId.
let localId: number = 100;
accountManager.getSerialNumberByOsAccountLocalId(localId).then((serialNumber: number) => {
  console.info('getSerialNumberByOsAccountLocalId serialNumber: ' + serialNumber);
}).catch((err: BusinessError) => {
  console.error(`getSerialNumberByOsAccountLocalId err: code is ${err.code}, message is ${err.message}`);
});
```

## getSerialNumberForOsAccountLocalId

```TypeScript
getSerialNumberForOsAccountLocalId(localId: number, callback: AsyncCallback<number>): void
```

Obtains the SN of an OS account based on the account ID. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| localId | number | Yes | ID of the target OS account. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is the SN obtained. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid localId. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |

**Examples**

Obtain the SN of the OS account 100.

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
// localId indicates the OS account ID, which can be obtained by calling getOsAccountLocalId.
let localId: number = 100;
try {
  accountManager.getSerialNumberForOsAccountLocalId(localId, (err: BusinessError, serialNumber: number)=>{
    if (err) {
      console.error(`get serialNumber code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('get serialNumber:' + serialNumber + ' by localId: ' + localId);
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`get serialNumber exception: code is ${err.code}, message is ${err.message}`);
}
```

<a id="getserialnumberforosaccountlocalid-1"></a>

## getSerialNumberForOsAccountLocalId

```TypeScript
getSerialNumberForOsAccountLocalId(localId: number): Promise<number>
```

Obtains the SN of an OS account based on the account ID. This API uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| localId | number | Yes | ID of the target OS account. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the SN obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| [12300002](../errorcode-account.md#12300002-invalid-parameter) | Invalid localId. |
| [12300003](../errorcode-account.md#12300003-account-not-found) | Account not found. |

**Examples**

Obtain the SN of the OS account 100.

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
// localId indicates the OS account ID, which can be obtained by calling getOsAccountLocalId.
let localId: number = 100;
try {
  accountManager.getSerialNumberForOsAccountLocalId(localId).then((serialNumber: number) => {
    console.info('getSerialNumberForOsAccountLocalId serialNumber: ' + serialNumber);
  }).catch((err: BusinessError) => {
    console.error(`getSerialNumberForOsAccountLocalId err: code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`getSerialNumberForOsAccountLocalId exception: code is ${err.code}, message is ${err.message}`);
}
```

## isMultiOsAccountEnable

```TypeScript
isMultiOsAccountEnable(callback: AsyncCallback<boolean>): void
```

Checks whether multiple OS accounts are supported. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use
> [checkMultiOsAccountEnabled](#checkmultiosaccountenabled)
> instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [checkMultiOsAccountEnabled](#checkmultiosaccountenabled)(callback: AsyncCallback&lt;boolean&gt;)

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. The value **true** means multiple OS accounts are supported; the value **false** means the opposite. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
accountManager.isMultiOsAccountEnable((err: BusinessError, isEnabled: boolean) => {
  if (err) {
    console.error(`isMultiOsAccountEnable failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('isMultiOsAccountEnable successfully, isEnabled: ' + isEnabled);
  }
});
```

<a id="ismultiosaccountenable-1"></a>

## isMultiOsAccountEnable

```TypeScript
isMultiOsAccountEnable(): Promise<boolean>
```

Checks whether multiple OS accounts are supported. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use
> [checkMultiOsAccountEnabled](#checkmultiosaccountenabled) instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [checkMultiOsAccountEnabled](#checkmultiosaccountenabled)()

**System capability:** SystemCapability.Account.OsAccount

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** means multiple OS accounts are supported; the value **false** means the opposite. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
accountManager.isMultiOsAccountEnable().then((isEnabled: boolean) => {
  console.info('isMultiOsAccountEnable successfully, isEnabled: ' + isEnabled);
}).catch((err: BusinessError) => {
  console.error(`isMultiOsAccountEnable failed, code is ${err.code}, message is ${err.message}`);
});
```

## isOsAccountActived

```TypeScript
isOsAccountActived(localId: number, callback: AsyncCallback<boolean>): void
```

Checks whether an OS account is activated. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. The substitute API is available
> only to system applications.

**Since:** 7

**Deprecated since:** 9

**Required permissions:** ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| localId | number | Yes | ID of the target OS account. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. The value **true** means the account is activated; the value **false** means the opposite. |

**Examples**

Check whether OS account 100 is activated.

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
// localId indicates the OS account ID, which can be obtained by calling getOsAccountLocalId.
let localId: number = 100;
accountManager.isOsAccountActived(localId, (err: BusinessError, isActived: boolean) => {
  if (err) {
    console.error(`isOsAccountActived failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('isOsAccountActived successfully, isActived:' + isActived);
  }
});
```

<a id="isosaccountactived-1"></a>

## isOsAccountActived

```TypeScript
isOsAccountActived(localId: number): Promise<boolean>
```

Checks whether an OS account is activated. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. The substitute API is available
> only to system applications.

**Since:** 7

**Deprecated since:** 9

**Required permissions:** ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| localId | number | Yes | ID of the target OS account. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** means the account is activated; the value **false** means the opposite. |

**Examples**

Check whether OS account 100 is activated.

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
// localId indicates the OS account ID, which can be obtained by calling getOsAccountLocalId.
let localId: number = 100;
accountManager.isOsAccountActived(localId).then((isActived: boolean) => {
  console.info('isOsAccountActived successfully, isActived: ' + isActived);
}).catch((err: BusinessError) => {
  console.error(`isOsAccountActived failed, code is ${err.code}, message is ${err.message}`);
});
```

## isOsAccountConstraintEnable

```TypeScript
isOsAccountConstraintEnable(localId: number, constraint: string, callback: AsyncCallback<boolean>): void
```

Checks whether the specified constraint is enabled for an OS account. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. The substitute API is available
> only to system applications.

**Since:** 7

**Deprecated since:** 9

**Required permissions:** ohos.permission.MANAGE_LOCAL_ACCOUNTS

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| localId | number | Yes | ID of the target OS account. |
| constraint | string | Yes | [Constraint](../../../reference/apis-basic-services-kit/appendix-osAccount-constraints.md) to check. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. The value **true** means the specified constraint is enabled; the value **false** means the opposite. |

**Examples**

Check whether OS account 100 is forbidden to use Wi-Fi.

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
// localId indicates the OS account ID, which can be obtained by calling getOsAccountLocalId.
let localId: number = 100;
let constraint: string = 'constraint.wifi';
accountManager.isOsAccountConstraintEnable(localId, constraint, (err: BusinessError, isEnabled: boolean) => {
  if (err) {
    console.error(`isOsAccountConstraintEnable failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('isOsAccountConstraintEnable successfully, isEnabled: ' + isEnabled);
  }
});
```

<a id="isosaccountconstraintenable-1"></a>

## isOsAccountConstraintEnable

```TypeScript
isOsAccountConstraintEnable(localId: number, constraint: string): Promise<boolean>
```

Checks whether the specified constraint is enabled for an OS account. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. The substitute API is available
> only to system applications.

**Since:** 7

**Deprecated since:** 9

**Required permissions:** ohos.permission.MANAGE_LOCAL_ACCOUNTS

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| localId | number | Yes | ID of the target OS account. |
| constraint | string | Yes | [Constraint](../../../reference/apis-basic-services-kit/appendix-osAccount-constraints.md) to check. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** means the specified constraint is enabled; the value **false** means the opposite. |

**Examples**

Check whether OS account 100 is forbidden to use Wi-Fi.

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
// localId indicates the OS account ID, which can be obtained by calling getOsAccountLocalId.
let localId: number = 100;
let constraint: string = 'constraint.wifi';
accountManager.isOsAccountConstraintEnable(localId, constraint).then((isEnabled: boolean) => {
  console.info('isOsAccountConstraintEnable successfully, isEnabled: ' + isEnabled);
}).catch((err: BusinessError) => {
  console.error(`isOsAccountConstraintEnable err: code is ${err.code}, message is ${err.message}`);
});
```

## isOsAccountConstraintEnabled

```TypeScript
isOsAccountConstraintEnabled(constraint: string): Promise<boolean>
```

Checks whether a constraint is enabled for the current OS account. This API uses a promise to return the result.

**Since:** 11

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| constraint | string | Yes | [Constraint](../../../reference/apis-basic-services-kit/appendix-osAccount-constraints.md) to check. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** means the specified constraint is enabled; the value **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |

**Examples**

Check whether the current OS account is forbidden to use Wi-Fi.

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
let constraint: string = 'constraint.wifi';
try {
  accountManager.isOsAccountConstraintEnabled(constraint).then((isEnabled: boolean) => {
    console.info('isOsAccountConstraintEnabled successfully, isEnabled: ' + isEnabled);
  }).catch((err: BusinessError) => {
    console.error(`isOsAccountConstraintEnabled failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`isOsAccountConstraintEnabled exception: code is ${err.code}, message is ${err.message}`);
}
```

## isOsAccountUnlocked

```TypeScript
isOsAccountUnlocked(): Promise<boolean>
```

Checks whether the current OS account has been unlocked. This API uses a promise to return the result.

**Since:** 11

**System capability:** SystemCapability.Account.OsAccount

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** means the OS account has been unlocked; the value **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.isOsAccountUnlocked().then((isVerified: boolean) => {
    console.info('isOsAccountUnlocked successfully, isVerified: ' + isVerified);
  }).catch((err: BusinessError) => {
    console.error(`isOsAccountUnlocked failed, code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`isOsAccountUnlocked exception: code is ${err.code}, message is ${err.message}`);
}
```

## isOsAccountVerified

```TypeScript
isOsAccountVerified(callback: AsyncCallback<boolean>): void
```

Checks whether an OS account has been verified. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use
> [checkOsAccountVerified](#checkosaccountverified)
> instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [checkOsAccountVerified](#checkosaccountverified)(callback: AsyncCallback&lt;boolean&gt;)

**Required permissions:** ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. The value **true** means the OS account has been verified; the value **false** means the opposite. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
accountManager.isOsAccountVerified((err: BusinessError, isVerified: boolean) => {
  if (err) {
    console.error(`isOsAccountVerified failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('isOsAccountVerified successfully, isVerified: ' + isVerified);
  }
});
```

<a id="isosaccountverified-1"></a>

## isOsAccountVerified

```TypeScript
isOsAccountVerified(localId: number, callback: AsyncCallback<boolean>): void
```

Checks whether an OS account has been verified. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. The substitute API is available
> only to system applications.

**Since:** 7

**Deprecated since:** 9

**Required permissions:** ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| localId | number | Yes | ID of the target OS account. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. The value **true** means the OS account has been verified; the value **false** means the opposite. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
// localId indicates the OS account ID, which can be obtained by calling getOsAccountLocalId.
let localId: number = 100;
accountManager.isOsAccountVerified(localId, (err: BusinessError, isVerified: boolean) => {
  if (err) {
    console.error(`isOsAccountVerified failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('isOsAccountVerified successfully, isVerified: ' + isVerified);
  }
});
```

<a id="isosaccountverified-2"></a>

## isOsAccountVerified

```TypeScript
isOsAccountVerified(localId?: number): Promise<boolean>
```

Checks whether an OS account has been verified. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. The substitute API is available
> only to system applications.

**Since:** 7

**Deprecated since:** 9

**Required permissions:** ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| localId | number | No | ID of the target OS account. If this parameter is not specified, this API checks whether the current OS account has been verified. The default value is **-1**. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** means the OS account has been verified; the value **false** means the opposite. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
accountManager.isOsAccountVerified().then((isVerified: boolean) => {
  console.info('isOsAccountVerified successfully, isVerified: ' + isVerified);
}).catch((err: BusinessError) => {
  console.error(`isOsAccountVerified failed, code is ${err.code}, message is ${err.message}`);
});
```

## isTestOsAccount

```TypeScript
isTestOsAccount(callback: AsyncCallback<boolean>): void
```

Checks whether the current OS account is a test account. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use
> [checkOsAccountTestable](#checkosaccounttestable)
> instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [checkOsAccountTestable](#checkosaccounttestable)(callback: AsyncCallback&lt;boolean&gt;)

**System capability:** SystemCapability.Account.OsAccount

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. The value **true** means the account is a test account; the value **false** means the opposite. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
accountManager.isTestOsAccount((err: BusinessError, isTestable: boolean) => {
  if (err) {
    console.error(`isTestOsAccount failed, code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('isTestOsAccount successfully, isTestable: ' + isTestable);
  }
});
```

<a id="istestosaccount-1"></a>

## isTestOsAccount

```TypeScript
isTestOsAccount(): Promise<boolean>
```

Checks whether the current OS account is a test account. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use
> [checkOsAccountTestable](#checkosaccounttestable) instead.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [checkOsAccountTestable](#checkosaccounttestable)()

**System capability:** SystemCapability.Account.OsAccount

**Test API:** This API is used only in automated test scripts.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** means the account is a test account; the value **false** means the opposite. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
  accountManager.isTestOsAccount().then((isTestable: boolean) => {
    console.info('isTestOsAccount successfully, isTestable: ' + isTestable);
  }).catch((err: BusinessError) => {
    console.error(`isTestOsAccount failed, code is ${err.code}, message is ${err.message}`);
});
```

## queryActivatedOsAccountIds

```TypeScript
queryActivatedOsAccountIds(callback: AsyncCallback<Array<number>>): void
```

Obtains information about all activated OS accounts. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use
> [getActivatedOsAccountLocalIds](#getactivatedosaccountlocalids)
> instead.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getActivatedOsAccountLocalIds](#getactivatedosaccountlocalids)(callback: AsyncCallback&lt;Array&lt;number&gt;&gt;)

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;number&gt;&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is a list of activated OS accounts. Otherwise, **data** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
accountManager.queryActivatedOsAccountIds((err: BusinessError, idArray: number[]) => {
  if (err) {
    console.error(`queryActivatedOsAccountIds code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('queryActivatedOsAccountIds idArray length:' + idArray.length);
    for (let i = 0; i < idArray.length; i++) {
      console.info('activated os account id: ' + idArray[i]);
    }
  }
});
```

<a id="queryactivatedosaccountids-1"></a>

## queryActivatedOsAccountIds

```TypeScript
queryActivatedOsAccountIds(): Promise<Array<number>>
```

Obtains information about all activated OS accounts. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use
> [getActivatedOsAccountLocalIds](#getactivatedosaccountlocalids) instead.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getActivatedOsAccountLocalIds](#getactivatedosaccountlocalids)()

**System capability:** SystemCapability.Account.OsAccount

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;number&gt;&gt; | Promise used to return the information about all activated OS accounts. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
accountManager.queryActivatedOsAccountIds().then((idArray: number[]) => {
  console.info('queryActivatedOsAccountIds, idArray: ' + idArray);
}).catch((err: BusinessError) => {
  console.error(`queryActivatedOsAccountIds err: code is ${err.code}, message is ${err.message}`);
});
```

## queryCurrentOsAccount

```TypeScript
queryCurrentOsAccount(callback: AsyncCallback<OsAccountInfo>): void
```

Obtains information about the OS account to which the current process belongs. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. The substitute API is available
> only to system applications.

**Since:** 7

**Deprecated since:** 9

**Required permissions:** ohos.permission.MANAGE_LOCAL_ACCOUNTS

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;[OsAccountInfo](arkts-basicservices-osaccount-osaccountinfo-i.md)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is the OS account information obtained. Otherwise, **data** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
accountManager.queryCurrentOsAccount((err: BusinessError, curAccountInfo: osAccount.OsAccountInfo)=>{
  if (err) {
    console.error(`queryCurrentOsAccount code is ${err.code}, message is ${err.message}`);
  } else {
    console.info('queryCurrentOsAccount curAccountInfo:' + JSON.stringify(curAccountInfo));
  }
});
```

<a id="querycurrentosaccount-1"></a>

## queryCurrentOsAccount

```TypeScript
queryCurrentOsAccount(): Promise<OsAccountInfo>
```

Obtains information about the OS account to which the current process belongs. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. The substitute API is available
> only to system applications.

**Since:** 7

**Deprecated since:** 9

**Required permissions:** ohos.permission.MANAGE_LOCAL_ACCOUNTS

**System capability:** SystemCapability.Account.OsAccount

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[OsAccountInfo](arkts-basicservices-osaccount-osaccountinfo-i.md)&gt; | Promise used to return the OS account information obtained. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
accountManager.queryCurrentOsAccount().then((accountInfo: osAccount.OsAccountInfo) => {
  console.info('queryCurrentOsAccount, accountInfo: ' + JSON.stringify(accountInfo));
}).catch((err: BusinessError) => {
  console.error(`queryCurrentOsAccount err: code is ${err.code}, message is ${err.message}`);
});
```

## queryDistributedVirtualDeviceId

```TypeScript
queryDistributedVirtualDeviceId(callback: AsyncCallback<string>): void
```

Queries the ID of a distributed virtual device. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC or ohos.permission.MANAGE_LOCAL_ACCOUNTS

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is the distributed virtual device ID obtained. Otherwise, **data** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameter types. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.queryDistributedVirtualDeviceId((err: BusinessError, virtualID: string) => {
    if (err) {
      console.error(`queryDistributedVirtualDeviceId err: code is ${err.code}, message is ${err.message}`);
    } else {
      console.info('queryDistributedVirtualDeviceId virtualID: ' + virtualID);
    }
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`queryDistributedVirtualDeviceId exception: code is ${err.code}, message is ${err.message}`);
}
```

<a id="querydistributedvirtualdeviceid-1"></a>

## queryDistributedVirtualDeviceId

```TypeScript
queryDistributedVirtualDeviceId(): Promise<string>
```

Queries the ID of this distributed virtual device. This API uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC or ohos.permission.MANAGE_LOCAL_ACCOUNTS

**System capability:** SystemCapability.Account.OsAccount

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the distributed virtual device ID obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
try {
  accountManager.queryDistributedVirtualDeviceId().then((virtualID: string) => {
    console.info('queryDistributedVirtualDeviceId, virtualID: ' + virtualID);
  }).catch((err: BusinessError) => {
    console.error(`queryDistributedVirtualDeviceId err: code is ${err.code}, message is ${err.message}`);
  });
} catch (e) {
  const err = e as BusinessError;
  console.error(`queryDistributedVirtualDeviceId exception: code is ${err.code}, message is ${err.message}`);
}
```
