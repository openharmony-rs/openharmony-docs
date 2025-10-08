# @ohos.account.osAccount (System Account) (System API)

<!--Kit: Basic Services Kit-->
<!--Subsystem: Account-->
<!--Owner: @steven-q-->
<!--Designer: @JiDong-CS1-->
<!--Tester: @zhaimengchao-->
<!--Adviser: @zengyawen-->

The **osAccount** module provides basic capabilities for managing system (OS) accounts, including adding, deleting, querying, setting, subscribing to, and enabling a system account.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - This topic describes only the system APIs provided by the module. For details about its public APIs, see [ohos.account.osAccount (System Account Management)](js-apis-osAccount.md).

## Modules to Import

```ts
import { osAccount } from '@kit.BasicServicesKit';
```

## AccountManager

Provides APIs for managing system accounts.

### activateOsAccount

activateOsAccount(localId: number, callback: AsyncCallback&lt;void&gt;): void

Activates a system account. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS_EXTENSION

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name  | Type                      | Mandatory| Description                                               |
| -------- | ------------------------- | ---- | -------------------------------------------------- |
| localId  | number                    | Yes  | ID of the target system account.                 |
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object.|

**Error codes**

| ID| Error Message            |
| -------- | ------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | The system service works abnormally. |
| 12300002 | Invalid localId.    |
| 12300003 | Account not found. |
| 12300008 | Restricted Account. |
| 12300010 | Service busy. Possible causes: The target account is being operated. |
| 12300016 | The number of logged in accounts reaches the upper limit. |

**Example**: Activate system account 100.
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
  let localId: number = 100;
  try {
    accountManager.activateOsAccount(localId, (err: BusinessError)=>{
      if (err) {
        console.error(`activateOsAccount failed, code is ${err.code}, message is ${err.message}`);
      } else {
        console.info('activateOsAccount successfully');
      }
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`activateOsAccount failed, code is ${err.code}, message is ${err.message}`);
  }
  ```

### activateOsAccount

activateOsAccount(localId: number): Promise&lt;void&gt;

Activates a system account. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS_EXTENSION

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name | Type  | Mandatory| Description                |
| ------- | ------ | ---- | -------------------- |
| localId | number | Yes  | ID of the target system account.|

**Return value**

| Type               | Description                                 |
| ------------------- | ------------------------------------ |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

| ID| Error Message            |
| -------- | ------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | The system service works abnormally. |
| 12300002 | Invalid localId.    |
| 12300003 | Account not found. |
| 12300008 | Restricted Account. |
| 12300010 | Service busy. Possible causes: The target account is being operated. |
| 12300016 | The number of logged in accounts reaches the upper limit. |

**Example**: Activate system account 100.
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
  let localId: number = 100;
  try {
    accountManager.activateOsAccount(localId).then(() => {
      console.info('activateOsAccount successfully');
    }).catch((err: BusinessError) => {
      console.error(`activateOsAccount failed, code is ${err.code}, message is ${err.message}`);
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`activateOsAccount exception: code is ${err.code}, message is ${err.message}`);
  }
  ```

### activateOsAccount<sup>21+</sup>

activateOsAccount(localId: number, displayId: number): Promise&lt;void&gt;

Activates (Starts on the foreground or switches to) the target system account on the specified logical display. This API uses a promise to return the result.
Currently, cross-logical-display activation is not supported. That is, you cannot activate a system account that is already running on the foreground of another logical display on the specified logical display.

**System API**: This is a system API.

**Required permissions**: ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS_EXTENSION

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name   | Type  | Mandatory| Description          |
| --------- | ------ | ---- | -------------- |
| localId   | number | Yes  | ID of the target system account.  |
| displayId | number | Yes  | Logical display ID.  |

**Return value**

| Type               | Description                                 |
| ------------------- | -------------------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Account Management Error Codes](./errorcode-account.md).

| ID| Error Message|
| -------- | -------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 801 | Capability not supported.|
| 12300001 | The system service works abnormally. |
| 12300003 | Account not found. |
| 12300008 | Restricted Account. |
| 12300010 | Service busy. Possible causes: The target account is being operated. |
| 12300016 | The number of logged in accounts reaches the upper limit. |
| 12300018 | Display not found. |
| 12300019 | Cross-display activation not supported. |

**Example**
Activate the system account 100 on the logical screen 0.
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
  let localId: number = 100;
  let displayId: number = 0;
  try {
    accountManager.activateOsAccount(localId, displayId).then(() => {
      console.info('activateOsAccount with displayId successfully');
    }).catch((err: BusinessError) => {
      console.error(`activateOsAccount with displayId failed, err: ${err.code} ${err.message}`);
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`activateOsAccount with displayId exception: ${err.code} ${err.message}`);
  }
  ```

### deactivateOsAccount<sup>12+</sup>

deactivateOsAccount(localId: number): Promise&lt;void&gt;

Deactivates (logs out of) a system account. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS_EXTENSION

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name | Type  | Mandatory| Description                |
| ------- | ------ | ---- | -------------------- |
| localId | number | Yes  | ID of the target system account.|

**Return value**

| Type               | Description                                 |
| ------------------- | ------------------------------------ |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

| ID| Error Message            |
| -------- | ------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | The system service works abnormally. |
| 12300003 | Account not found. |
| 12300008 | Restricted Account. |
| 12300010 | Service busy. Possible causes: The target account is being operated. |

**Example**: Deactivate system account 100.
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
  let localId: number = 100;
  try {
    accountManager.deactivateOsAccount(localId).then(() => {
      console.info('deactivateOsAccount successfully');
    }).catch((err: BusinessError) => {
      console.error(`deactivateOsAccount failed, code is ${err.code}, message is ${err.message}`);
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`deactivateOsAccount exception: code is ${err.code}, message is ${err.message}`);
  }
  ```

### isOsAccountActivated<sup>11+</sup>

isOsAccountActivated(localId: number): Promise&lt;boolean&gt;

Checks whether a system account is activated. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name | Type  | Mandatory| Description                              |
| ------- | ------ | ---- | --------------------------------- |
| localId | number | Yes  | ID of the target system account.|

**Return value**

| Type                  | Description                                                      |
| ---------------------- | ---------------------------------------------------------- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** means the account is activated; the value **false** means the opposite.|

**Error codes**

| ID| Error Message            |
| -------- | ------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | The system service works abnormally. |
| 12300003 | Account not found. |

**Example**: Check whether system account 100 is activated.

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
  let localId: number = 100;
  try {
    accountManager.isOsAccountActivated(localId).then((isActivated: boolean) => {
      console.info('isOsAccountActivated successfully, isActivated: ' + isActivated);
    }).catch((err: BusinessError) => {
      console.error(`isOsAccountActivated failed, code is ${err.code}, message is ${err.message}`);
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`isOsAccountActivated exception: code is ${err.code}, message is ${err.message}`);
  }
  ```

### isOsAccountConstraintEnabled<sup>11+</sup>

isOsAccountConstraintEnabled(localId: number, constraint: string): Promise&lt;boolean&gt;

Checks whether a constraint is enabled for a system account. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name    | Type  | Mandatory| Description                               |
| ---------- | ------ | ---- | ---------------------------------- |
| localId    | number | Yes  | ID of the target system account. |
| constraint | string | Yes  | [Constraint](js-apis-osAccount.md#constraints) to check.|

**Return value**

| Type                  | Description                                                                 |
| --------------------- | --------------------------------------------------------------------- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** means the specified constraint is enabled; the value **false** means the opposite.|

**Error codes**

| ID| Error Message            |
| -------- | ------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | The system service works abnormally. |
| 12300003 | Account not found. |

**Example**: Check whether system account 100 is forbidden to use Wi-Fi.

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
  let localId: number = 100;
  let constraint: string = 'constraint.wifi';
  try {
    accountManager.isOsAccountConstraintEnabled(localId, constraint).then((isEnabled: boolean) => {
      console.info('isOsAccountConstraintEnabled successfully, isEnabled: ' + isEnabled);
    }).catch((err: BusinessError) => {
      console.error(`isOsAccountConstraintEnabled failed, code is ${err.code}, message is ${err.message}`);
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`isOsAccountConstraintEnabled exception: code is ${err.code}, message is ${err.message}`);
  }
  ```

### isOsAccountUnlocked<sup>11+</sup>

isOsAccountUnlocked(localId: number): Promise&lt;boolean&gt;

Checks whether a system account has been verified. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name | Type  | Mandatory| Description                                                             |
| ------- | ------ | ---- | --------------------------------------------------------------- |
| localId | number | Yes  | ID of the target system account. If this parameter is not specified, this API checks whether the current system account has been verified.|

**Return value**

| Type                  | Description                                                              |
| ---------------------- | ----------------------------------------------------------------- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** means the system account has been verified; the value **false** means the opposite.|

**Error codes**

| ID| Error Message            |
| -------- | ------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | The system service works abnormally. |
| 12300003 | Account not found. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
  let localId: number = 100;
  try {
    accountManager.isOsAccountUnlocked(localId).then((isVerified: boolean) => {
      console.info('isOsAccountUnlocked successfully, isVerified: ' + isVerified);
    }).catch((err: BusinessError) => {
      console.error(`isOsAccountUnlocked failed, code is ${err.code}, message is ${err.message}`);
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`isOsAccountUnlocked exception: code is ${err.code}, message is ${err.message}`);
  }
  ```

### removeOsAccount

removeOsAccount(localId: number, callback: AsyncCallback&lt;void&gt;): void

Removes a system account. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MANAGE_LOCAL_ACCOUNTS

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name  | Type                     | Mandatory| Description                                                |
| -------- | ------------------------- | ---- | -------------------------------------------------- |
| localId  | number                    | Yes  | ID of the target system account.                 |
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object.|

**Error codes**

| ID| Error Message            |
| -------- | ------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.|
| 12300001 | The system service works abnormally. |
| 12300002 | Invalid localId.    |
| 12300003 | Account not found. |
| 12300008 | Restricted Account. |
| 12300010 | Service busy. Possible causes: The target account is being operated. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
  let accountName: string = 'testAccountName';
  try {
    accountManager.createOsAccount(accountName, osAccount.OsAccountType.NORMAL,
      (err: BusinessError, osAccountInfo: osAccount.OsAccountInfo) => {
        accountManager.removeOsAccount(osAccountInfo.localId, (err: BusinessError)=>{
          if (err) {
            console.error(`removeOsAccount failed, code is ${err.code}, message is ${err.message}`);
          } else {
            console.info('removeOsAccount successfully');
          }
      });
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`removeOsAccount exception: code is ${err.code}, message is ${err.message}`);
  }
  ```

### removeOsAccount

removeOsAccount(localId: number): Promise&lt;void&gt;

Removes a system account. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MANAGE_LOCAL_ACCOUNTS

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name | Type  | Mandatory| Description                              |
| ------- | ------ | ---- | --------------------------------- |
| localId | number | Yes  | ID of the target system account.|

**Return value**

| Type               | Description                                 |
| ------------------- | ------------------------------------ |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

| ID| Error Message            |
| -------- | ------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.|
| 12300001 | The system service works abnormally. |
| 12300002 | Invalid localId.    |
| 12300003 | Account not found. |
| 12300008 | Restricted Account. |
| 12300010 | Service busy. Possible causes: The target account is being operated. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
  let accountName: string = 'testAccountName';
  try {
    accountManager.createOsAccount(accountName, osAccount.OsAccountType.NORMAL,
      (err: BusinessError, osAccountInfo: osAccount.OsAccountInfo)=>{
        accountManager.removeOsAccount(osAccountInfo.localId).then(() => {
          console.info('removeOsAccount successfully');
        }).catch((err: BusinessError) => {
            console.error(`removeOsAccount failed, code is ${err.code}, message is ${err.message}`);
        });
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`removeOsAccount exception: code is ${err.code}, message is ${err.message}`);
  }
  ```

### setOsAccountConstraints

setOsAccountConstraints(localId: number, constraints: Array&lt;string&gt;, enable: boolean,callback: AsyncCallback&lt;void&gt;): void

Sets or removes constraints for a system account. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MANAGE_LOCAL_ACCOUNTS

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name     | Type                     | Mandatory| Description                                            |
| ----------- | ------------------------- | ---- | ----------------------------------------------- |
| localId     | number                    | Yes  | ID of the target system account.              |
| constraints | Array&lt;string&gt;       | Yes  | [Constraints](js-apis-osAccount.md#constraints) to set or remove.       |
| enable      | boolean                   | Yes  | Whether to set or remove constraints. The value **true** means to set constraints, and **false** means to remove constraints.                         |
| callback    | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object.|

**Error codes**

| ID| Error Message            |
| -------- | ------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.|
| 12300001 | The system service works abnormally. |
| 12300002 | Invalid localId or constraints.    |
| 12300003 | Account not found. |
| 12300008 | Restricted Account. |

**Example**: Disable Wi-Fi for system account 100.

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
  let localId: number = 100;
  let constraint: string = 'constraint.wifi';
  try {
    accountManager.setOsAccountConstraints(localId, [constraint], true, (err: BusinessError) => {
      if (err) {
        console.error(`setOsAccountConstraints failed, code is ${err.code}, message is ${err.message}`);
      } else {
        console.info('setOsAccountConstraints successfully');
      }
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`setOsAccountConstraints exception: code is ${err.code}, message is ${err.message}`);
  }
  ```

### setOsAccountConstraints

setOsAccountConstraints(localId: number, constraints: Array&lt;string&gt;, enable: boolean): Promise&lt;void&gt;

Sets or removes constraints for a system account. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MANAGE_LOCAL_ACCOUNTS

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name     | Type               | Mandatory| Description                                        |
| ----------- | ------------------- | ---- | -------------------------------------------- |
| localId     | number              | Yes  | ID of the target system account.          |
| constraints | Array&lt;string&gt; | Yes  | [Constraints](js-apis-osAccount.md#constraints) to set or remove.   |
| enable      | boolean             | Yes  | Set or remove constraints. The value **true** means to set constraints, and **false** means to remove constraints.                    |

**Return value**

| Type               | Description                                |
| :------------------ | :----------------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

| ID| Error Message            |
| -------- | ------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.|
| 12300001 | The system service works abnormally. |
| 12300002 | Invalid localId or constraints.    |
| 12300003 | Account not found. |
| 12300008 | Restricted Account. |

**Example**: Remove the constraint on the use of Wi-Fi for system account 100.

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
  let localId: number = 100;
  try {
    accountManager.setOsAccountConstraints(localId, ['constraint.location.set'], false).then(() => {
      console.info('setOsAccountConstraints successfully');
    }).catch((err: BusinessError) => {
      console.error(`setOsAccountConstraints failed, code is ${err.code}, message is ${err.message}`);
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`setOsAccountConstraints exception: code is ${err.code}, message is ${err.message}`);
  }
  ```

### setOsAccountName

setOsAccountName(localId: number, localName: string, callback: AsyncCallback&lt;void&gt;): void

Sets the name of a system account. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MANAGE_LOCAL_ACCOUNTS

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name   | Type                     | Mandatory| Description                                            |
| :-------- | ------------------------- | ---- | ----------------------------------------------- |
| localId   | number                    | Yes  | ID of the target system account.              |
| localName | string                    | Yes  | Account name to set. The value cannot exceed 1024 characters.                         |
| callback  | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object.|

**Error codes**

| ID| Error Message            |
| -------- | ------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.|
| 12300001 | The system service works abnormally. |
| 12300002 | Invalid localId or localName. |
| 12300003 | Account not found. |
| 12300008 | Restricted Account. |

**Example**: Set the name of system account 100 to **demoName**.

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
  let localId: number = 100;
  let name: string = 'demoName';
  try {
    accountManager.setOsAccountName(localId, name, (err: BusinessError) => {
      if (err) {
        console.error(`setOsAccountName failed, code is ${err.code}, message is ${err.message}`);
      } else {
        console.info('setOsAccountName successfully');
      }
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`setOsAccountName exception: code is ${err.code}, message is ${err.message}`);
  }
  ```

### setOsAccountName

setOsAccountName(localId: number, localName: string): Promise&lt;void&gt;

Sets the name of a system account. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MANAGE_LOCAL_ACCOUNTS

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name   | Type  | Mandatory| Description                               |
| --------- | ------ | ---- | --------------------------------- |
| localId   | number | Yes  | ID of the target system account.|
| localName | string | Yes  | Account name to set. The value cannot exceed 1024 characters.           |

**Return value**

| Type               | Description                                 |
| ------------------- | ------------------------------------ |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

| ID| Error Message            |
| -------- | ------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.|
| 12300001 | The system service works abnormally. |
| 12300002 | Invalid localId or localName.    |
| 12300003 | Account not found. |
| 12300008 | Restricted Account. |

**Example**: Set the name of system account 100 to **demoName**.

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
  let localId: number = 100;
  let name: string = 'testName';
  try {
    accountManager.setOsAccountName(localId, name).then(() => {
      console.info('setOsAccountName successfully');
    }).catch((err: BusinessError) => {
      console.error(`setOsAccountName failed, code is ${err.code}, message is ${err.message}`);
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`setOsAccountName exception: code is ${err.code}, message is ${err.message}`);
  }
  ```

### queryMaxOsAccountNumber

queryMaxOsAccountNumber(callback: AsyncCallback&lt;number&gt;): void

Queries the maximum number of system accounts that can be created. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name  | Type                       | Mandatory| Description                                                                             |
| -------- | --------------------------- | ---- | -------------------------------------------------------------------------------- |
| callback | AsyncCallback&lt;number&gt; | Yes  | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is the maximum number of system accounts that can be created. Otherwise, **err** is an error object.|

**Error codes**

| ID| Error Message      |
| -------- | ------------- |
| 202 | Not system application.|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.|
| 12300001 | The system service works abnormally. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
  try {
    accountManager.queryMaxOsAccountNumber((err: BusinessError, maxCnt: number) => {
      if (err) {
        console.error(`queryMaxOsAccountNumber failed, code is ${err.code}, message is ${err.message}`);
      } else {
        console.info('queryMaxOsAccountNumber successfully, maxCnt:' + maxCnt);
      }
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`queryMaxOsAccountNumber exception: code is ${err.code}, message is ${err.message}`);
  }
  ```

### queryMaxOsAccountNumber

queryMaxOsAccountNumber(): Promise&lt;number&gt;

Queries the maximum number of system accounts that can be created. This API uses a promise to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Return value**

| Type                 | Description                                        |
| --------------------- | ------------------------------------------- |
| Promise&lt;number&gt; | Promise used to return the result.|

**Error codes**

| ID| Error Message      |
| -------- | ------------- |
| 202 | Not system application.|
| 12300001 | The system service works abnormally. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
  try {
    accountManager.queryMaxOsAccountNumber().then((maxCnt: number) => {
      console.info('queryMaxOsAccountNumber successfully, maxCnt: ' + maxCnt);
    }).catch((err: BusinessError) => {
      console.error(`queryMaxOsAccountNumber failed, code is ${err.code}, message is ${err.message}`);
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`queryMaxOsAccountNumber exception: code is ${err.code}, message is ${err.message}`);
  }
  ```

### queryMaxLoggedInOsAccountNumber<sup>12+</sup>

queryMaxLoggedInOsAccountNumber(): Promise&lt;number&gt;

Queries the maximum number of system accounts allowed to log in to the system. This API uses a promise to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Return value**

| Type                 | Description                                        |
| --------------------- | ------------------------------------------- |
| Promise&lt;number&gt; | Promise used to return the result.|

**Error codes**

| ID| Error Message      |
| -------- | ------------- |
| 202 | Not system application.|
| 12300001 | The system service works abnormally. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
  try {
    accountManager.queryMaxLoggedInOsAccountNumber().then((maxNum: number) => {
      console.info('queryMaxLoggedInOsAccountNumber successfully, maxNum: ' + maxNum);
    }).catch((err: BusinessError) => {
      console.error(`queryMaxLoggedInOsAccountNumber failed, code is ${err.code}, message is ${err.message}`);
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`queryMaxLoggedInOsAccountNumber exception: code is ${err.code}, message is ${err.message}`);
  }
  ```

### getEnabledOsAccountConstraints<sup>11+</sup>

getEnabledOsAccountConstraints(localId: number): Promise&lt;Array&lt;string&gt;&gt;

Obtains all the enabled constraints of a system account. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name | Type  | Mandatory| Description        |
| ------- | ------ | ---- | ------------ |
| localId | number | Yes  | ID of the target system account.|

**Return value**

| Type                              | Description                                                      |
| ---------------------------------- | ---------------------------------------------------------- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return all the enabled [constraints](js-apis-osAccount.md#constraints) of the system account.|

**Error codes**

| ID| Error Message            |
| -------- | ------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.|
| 12300001 | The system service works abnormally. |
| 12300003 | Account not found. |

**Example**: Obtain all constraints of system account 100.

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
  let localId: number = 100;
  try {
    accountManager.getEnabledOsAccountConstraints(localId).then((constraints: string[]) => {
      console.info('getEnabledOsAccountConstraints, constraints: ' + constraints);
    }).catch((err: BusinessError) => {
      console.error(`getEnabledOsAccountConstraints err: code is ${err.code}, message is ${err.message}`);
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`getEnabledOsAccountConstraints exception: code is ${err.code}, message is ${err.message}`);
  }
  ```

### queryAllCreatedOsAccounts

queryAllCreatedOsAccounts(callback: AsyncCallback&lt;Array&lt;OsAccountInfo&gt;&gt;): void

Queries information about all the system accounts created. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Required permissions**: ohos.permission.MANAGE_LOCAL_ACCOUNTS

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                              |
| -------- | ------------------------------------------------------------ | ---- | -------------------------------------------------- |
| callback | AsyncCallback&lt;Array&lt;[OsAccountInfo](js-apis-osAccount.md#osaccountinfo)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is a list of all created system accounts. Otherwise, **data** is an error object.|

**Error codes**

| ID| Error Message      |
| -------- | ------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types.|
| 12300001 | The system service works abnormally. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
  try {
    accountManager.queryAllCreatedOsAccounts((err: BusinessError, accountArr: osAccount.OsAccountInfo[])=>{
      if (err) {
        console.error(`queryAllCreatedOsAccounts exception:code is ${err.code}, message is ${err.message}`);
      } else {
        console.info('queryAllCreatedOsAccounts accountArr:' + JSON.stringify(accountArr));
      }
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`queryAllCreatedOsAccounts exception: code is ${err.code}, message is ${err.message}`);
  }
  ```

### queryAllCreatedOsAccounts

queryAllCreatedOsAccounts(): Promise&lt;Array&lt;OsAccountInfo&gt;&gt;

Queries information about all the system accounts created. This API uses a promise to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Required permissions**: ohos.permission.MANAGE_LOCAL_ACCOUNTS

**Return value**

| Type                                                       | Description                                          |
| ----------------------------------------------------------- | --------------------------------------------- |
| Promise&lt;Array&lt;[OsAccountInfo](js-apis-osAccount.md#osaccountinfo)&gt;&gt; | Promise used to return the information about all the system accounts created.|

**Error codes**

| ID| Error Message      |
| -------- | ------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 12300001 | The system service works abnormally. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
  try {
    accountManager.queryAllCreatedOsAccounts().then((accountArr: osAccount.OsAccountInfo[]) => {
      console.info('queryAllCreatedOsAccounts, accountArr: ' + JSON.stringify(accountArr));
    }).catch((err: BusinessError) => {
      console.error(`queryAllCreatedOsAccounts err: code is ${err.code}, message is ${err.message}`);
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`queryAllCreatedOsAccounts exception: code is ${err.code}, message is ${err.message}`);
  }
  ```

### createOsAccount

createOsAccount(localName: string, type: OsAccountType, callback: AsyncCallback&lt;OsAccountInfo&gt;): void

Creates a system account. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MANAGE_LOCAL_ACCOUNTS

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name   | Type                                                | Mandatory| Description                                                                        |
| :-------- | ---------------------------------------------------- | ---- | --------------------------------------------------------------------------- |
| localName | string                                               | Yes  | Name of the system account to create.                                                       |
| type      | [OsAccountType](js-apis-osAccount.md#osaccounttype)                      | Yes  | Type of the system account to create.                                                       |
| callback  | AsyncCallback&lt;[OsAccountInfo](js-apis-osAccount.md#osaccountinfo)&gt; | Yes  | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is the created system account. Otherwise, **err** is an error object.|

**Error codes**

| ID | Error Message                  |
| -------- | ------------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | The system service works abnormally. |
| 12300002 | Invalid localName or type. |
| 12300004 | Local name already exists. |
| 12300005 | Multi-user not supported. |
| 12300006 | Unsupported account type. |
| 12300007 | The number of accounts has reached the upper limit. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
  try {
    accountManager.createOsAccount('testName', osAccount.OsAccountType.NORMAL,
      (err: BusinessError, osAccountInfo: osAccount.OsAccountInfo)=>{
      if (err) {
        console.error(`createOsAccount exception:code is ${err.code}, message is ${err.message}`);
      } else {
        console.info('createOsAccount osAccountInfo:' + JSON.stringify(osAccountInfo));
      }
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`createOsAccount exception: code is ${err.code}, message is ${err.message}`);
  }
  ```

### createOsAccount

createOsAccount(localName: string, type: OsAccountType, options?: CreateOsAccountOptions): Promise&lt;OsAccountInfo&gt;

Creates a system account. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MANAGE_LOCAL_ACCOUNTS

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name   | Type                           | Mandatory| Description                  |
| --------- | ------------------------------- | ---- | ---------------------- |
| localName | string                          | Yes  | Name of the system account to create.|
| type      | [OsAccountType](js-apis-osAccount.md#osaccounttype) | Yes  | Type of the system account to create.|
| options      | [CreateOsAccountOptions](#createosaccountoptions12) | No  | Options for creating a system account. By default, this parameter is left blank.<br>This parameter is supported since API version 12.|

**Return value**

| Type                                          | Description                                 |
| ---------------------------------------------- | ------------------------------------- |
| Promise&lt;[OsAccountInfo](js-apis-osAccount.md#osaccountinfo)&gt; | Promise used to return the information about the created system account.|

**Error codes**

| ID | Error Message                  |
| -------- | ------------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | The system service works abnormally. |
| 12300002 | Invalid localName, type or options. |
| 12300004 | Local name already exists. |
| 12300005 | Multi-user not supported. |
| 12300006 | Unsupported account type. |
| 12300007 | The number of accounts has reached the upper limit. |
| 12300015 | The short name already exists. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
  let options: osAccount.CreateOsAccountOptions = {
    shortName: 'myShortName',
    disallowedPreinstalledBundles: [],
    allowedPreinstalledBundles: [],
  }
  try {
    accountManager.createOsAccount('testAccountName', osAccount.OsAccountType.NORMAL, options).then(
      (accountInfo: osAccount.OsAccountInfo) => {
      console.info('createOsAccount, accountInfo: ' + JSON.stringify(accountInfo));
    }).catch((err: BusinessError) => {
      console.error(`createOsAccount err: code is ${err.code}, message is ${err.message}`);
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`createOsAccount exception: code is ${err.code}, message is ${err.message}`);
  }
  ```

### createOsAccountForDomain<sup>8+</sup>

createOsAccountForDomain(type: OsAccountType, domainInfo: DomainAccountInfo, callback: AsyncCallback&lt;OsAccountInfo&gt;): void

Creates a system account and associates it with the specified domain account. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MANAGE_LOCAL_ACCOUNTS

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name    | Type                                                | Mandatory| Description                                                                        |
| ---------- | ---------------------------------------------------- | ---- | -------------------------------------------------------------------------- |
| type       | [OsAccountType](js-apis-osAccount.md#osaccounttype)                      | Yes  | Type of the system account to create.                                                      |
| domainInfo | [DomainAccountInfo](#domainaccountinfo8)              | Yes  | Domain account information.                                                              |
| callback   | AsyncCallback&lt;[OsAccountInfo](js-apis-osAccount.md#osaccountinfo)&gt; | Yes  | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is the created system account. Otherwise, **err** is an error object.|

**Error codes**

| ID| Error Message                    |
| -------- | ------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 801 | Capability not supported.|
| 12300001 | The system service works abnormally. |
| 12300002 | Invalid type or domainInfo. |
| 12300004 | Account already exists. |
| 12300005 | Multi-user not supported. |
| 12300006 | Unsupported account type. |
| 12300007 | The number of accounts has reached the upper limit. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
  let domainInfo: osAccount.DomainAccountInfo =
    {domain: 'testDomain', accountName: 'testAccountName'};
  try {
    accountManager.createOsAccountForDomain(osAccount.OsAccountType.NORMAL, domainInfo,
      (err: BusinessError, osAccountInfo: osAccount.OsAccountInfo)=>{
      if (err) {
        console.error(`createOsAccountForDomain exception:code is ${err.code}, message is ${err.message}`);
      } else {
        console.info('createOsAccountForDomain osAccountInfo:' + JSON.stringify(osAccountInfo));
      }
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`createOsAccountForDomain exception: code is ${err.code}, message is ${err.message}`);
  }
  ```

### createOsAccountForDomain<sup>8+</sup>

createOsAccountForDomain(type: OsAccountType, domainInfo: DomainAccountInfo, options?: CreateOsAccountForDomainOptions): Promise&lt;OsAccountInfo&gt;

Creates a system account and associates it with the specified domain account. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MANAGE_LOCAL_ACCOUNTS

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name    | Type                                     | Mandatory| Description                |
| ---------- | ---------------------------------------- | ---- | -------------------- |
| type       | [OsAccountType](js-apis-osAccount.md#osaccounttype)          | Yes  | Type of the system account to create.|
| domainInfo | [DomainAccountInfo](#domainaccountinfo8) | Yes  | Domain account information.         |
| options      | [CreateOsAccountForDomainOptions](#createosaccountfordomainoptions12) | No  | Optional parameters for creating the account. By default, this parameter is left blank.<br>This parameter is supported since API version 12.|

**Return value**

| Type                                          | Description                                   |
| ---------------------------------------------- | -------------------------------------- |
| Promise&lt;[OsAccountInfo](js-apis-osAccount.md#osaccountinfo)&gt; | Promise used to return the information about the created system account.|

**Error codes**

| ID| Error Message                    |
| -------- | ------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 801 | Capability not supported.|
| 12300001 | The system service works abnormally. |
| 12300002 | Invalid type, domainInfo or options. |
| 12300004 | Account already exists. |
| 12300005 | Multi-user not supported. |
| 12300006 | Unsupported account type. |
| 12300007 | The number of accounts has reached the upper limit. |
| 12300015 | The short name already exists. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
  let domainInfo: osAccount.DomainAccountInfo =
    {domain: 'testDomain', accountName: 'testAccountName'};
  let options: osAccount.CreateOsAccountForDomainOptions = {
    shortName: 'myShortName'
  }
  try {
    accountManager.createOsAccountForDomain(osAccount.OsAccountType.NORMAL, domainInfo, options).then(
      (accountInfo: osAccount.OsAccountInfo) => {
      console.info('createOsAccountForDomain, account info: ' + JSON.stringify(accountInfo));
    }).catch((err: BusinessError) => {
      console.error(`createOsAccountForDomain err: code is ${err.code}, message is ${err.message}`);
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`createOsAccountForDomain exception: code is ${err.code}, message is ${err.message}`);
  }
  ```

### queryOsAccount<sup>11+</sup>

queryOsAccount(): Promise&lt;OsAccountInfo&gt;

Obtains information about the system account to which the current process belongs. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.GET_LOCAL_ACCOUNTS

**System capability**: SystemCapability.Account.OsAccount

**Return value**

| Type                                          | Description                                      |
| ---------------------------------------------- | ----------------------------------------- |
| Promise&lt;[OsAccountInfo](js-apis-osAccount.md#osaccountinfo)&gt; | Promise used to return the system account information obtained.|

**Error codes**

| ID| Error Message            |
| -------- | ------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 12300001 | The system service works abnormally. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
  try {
    accountManager.queryOsAccount().then((accountInfo: osAccount.OsAccountInfo) => {
      console.info('queryOsAccount, accountInfo: ' + JSON.stringify(accountInfo));
    }).catch((err: BusinessError) => {
      console.error(`queryOsAccount err: code is ${err.code}, message is ${err.message}`);
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`queryOsAccount exception: code is ${err.code}, message is ${err.message}`);
  }
  ```

### queryOsAccountById

queryOsAccountById(localId: number, callback: AsyncCallback&lt;OsAccountInfo&gt;): void

Queries information about the system account of the given ID. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS_EXTENSION

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name  | Type                                                | Mandatory| Description                                                                      |
| -------- | ---------------------------------------------------- | ---- | ------------------------------------------------------------------------ |
| localId  | number                                               | Yes  | ID of the target system account.                                                     |
| callback | AsyncCallback&lt;[OsAccountInfo](js-apis-osAccount.md#osaccountinfo)&gt; | Yes  | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is the system account information obtained. Otherwise, **data** is an error object.|

**Error codes**

| ID| Error Message            |
| -------- | ------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | The system service works abnormally. |
| 12300002 | Invalid localId.    |
| 12300003 | Account not found. |

**Example**: Query information about system account 100.

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
  let localId: number = 100;
  try {
    accountManager.queryOsAccountById(localId, (err: BusinessError, accountInfo: osAccount.OsAccountInfo)=>{
      if (err) {
        console.error(`queryOsAccountById exception:code is ${err.code}, message is ${err.message}`);
      } else {
        console.info('queryOsAccountById accountInfo:' + JSON.stringify(accountInfo));
      }
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`queryOsAccountById exception: code is ${err.code}, message is ${err.message}`);
  }
  ```

### queryOsAccountById

queryOsAccountById(localId: number): Promise&lt;OsAccountInfo&gt;

Queries information about the system account of the given ID. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS_EXTENSION

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name | Type  | Mandatory| Description                |
| ------- | ------ | ---- | -------------------- |
| localId | number | Yes  | ID of the target system account.|

**Return value**

| Type                                          | Description                                |
| ---------------------------------------------- | ------------------------------------ |
| Promise&lt;[OsAccountInfo](js-apis-osAccount.md#osaccountinfo)&gt; | Promise used to return the system account information obtained.|

**Error codes**

| ID| Error Message            |
| -------- | ------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | The system service works abnormally. |
| 12300002 | Invalid localId. |
| 12300003 | Account not found. |

**Example**: Query information about system account 100.

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
  let localId: number = 100;
  try {
    accountManager.queryOsAccountById(localId).then((accountInfo: osAccount.OsAccountInfo) => {
      console.info('queryOsAccountById, accountInfo: ' + JSON.stringify(accountInfo));
    }).catch((err: BusinessError) => {
      console.error(`queryOsAccountById err: code is ${err.code}, message is ${err.message}`);
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`queryOsAccountById exception: code is ${err.code}, message is ${err.message}`);
  }
  ```

### getOsAccountProfilePhoto

getOsAccountProfilePhoto(localId: number, callback: AsyncCallback&lt;string&gt;): void

Obtains the profile photo of a system account. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MANAGE_LOCAL_ACCOUNTS

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name  | Type                       | Mandatory| Description                                                                        |
| -------- | --------------------------- | ---- | -------------------------------------------------------------------------- |
| localId  | number                      | Yes  | ID of the target system account.                                                               |
| callback | AsyncCallback&lt;string&gt; | Yes  | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is the profile photo information obtained. Otherwise, **err** is an error object.|

**Error codes**

| ID| Error Message            |
| -------- | ------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | The system service works abnormally. |
| 12300002 | Invalid localId.    |
| 12300003 | Account not found. |

**Example**: Obtain the profile photo of system account 100.

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
  let localId: number = 100;
  try {
    accountManager.getOsAccountProfilePhoto(localId, (err: BusinessError, photo: string)=>{
      if (err) {
        console.error(`getOsAccountProfilePhoto exception:code is ${err.code}, message is ${err.message}`);
      } else {
        console.info('get photo:' + photo + ' by localId: ' + localId);
      }
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`getOsAccountProfilePhoto exception: code is ${err.code}, message is ${err.message}`);
  }
  ```

### getOsAccountProfilePhoto

getOsAccountProfilePhoto(localId: number): Promise&lt;string&gt;

Obtains the profile photo of a system account. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MANAGE_LOCAL_ACCOUNTS

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name | Type  | Mandatory| Description        |
| ------- | ------ | ---- | ------------ |
| localId | number | Yes  | ID of the target system account.|

**Return value**

| Type                 | Description                                   |
| --------------------- | -------------------------------------- |
| Promise&lt;string&gt; | Promise used to return the profile photo information obtained.|

**Error codes**

| ID| Error Message            |
| -------- | ------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | The system service works abnormally. |
| 12300002 | Invalid localId.    |
| 12300003 | Account not found. |

**Example**: Obtain the profile photo of system account 100.

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
  let localId: number = 100;
  try {
    accountManager.getOsAccountProfilePhoto(localId).then((photo: string) => {
      console.info('getOsAccountProfilePhoto: ' + photo);
    }).catch((err: BusinessError) => {
      console.error(`getOsAccountProfilePhoto err: code is ${err.code}, message is ${err.message}`);
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`getOsAccountProfilePhoto exception: code is ${err.code}, message is ${err.message}`);
  }
  ```

### setOsAccountProfilePhoto

setOsAccountProfilePhoto(localId: number, photo: string, callback: AsyncCallback&lt;void&gt;): void

Sets a profile photo for a system account. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MANAGE_LOCAL_ACCOUNTS

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name  | Type                     | Mandatory| Description        |
| -------- | ------------------------- | ---- | ------------ |
| localId  | number                    | Yes  | ID of the target system account.|
| photo    | string                    | Yes  | Profile photo information.  |
| callback | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object. |

**Error codes**

| ID| Error Message            |
| -------- | ------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | The system service works abnormally. |
| 12300002 | Invalid localId or photo.    |
| 12300003 | Account not found. |
| 12300008 | Restricted Account. |

**Example**: Set a profile photo for system account 100.

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
  let localId: number = 100;
  let photo: string = 'data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAA0AAAAPCAYAAAA/I0V3AAAAAXNSR0IArs4c6QAAAARnQU1BAA'+
  'Cxjwv8YQUAAAAJcEhZcwAADsMAAA7DAcdvqGQAAACwSURBVDhPvZLBDYMwDEV/ugsXRjAT0EHCOuFIBwkbdIRewi6unbiAyoGgSn1SFH85+Y'+
  'q/4ljARW62X+LHS8uIzjm4dXUYF+utzBikB52Jo5e5iEPKqpACk7R9NM2RvWm5tIkD2czLCUFNKLD6IjdMHFHDzws285MgGrT0xCtp3WOKHo'+
  '+7q0mP0DZW9pNmoEFUzrQjp5cCnaen2kSJXLFD8ghbXyZCMQf/8e8Ns1XVAG/XAgqKzVnJFAAAAABJRU5ErkJggg=='
  try {
    accountManager.setOsAccountProfilePhoto(localId, photo, (err: BusinessError)=>{
      if (err) {
        console.error(`setOsAccountProfilePhoto exception:code is ${err.code}, message is ${err.message}`);
      } else {
        console.info('setOsAccountProfilePhoto successful.');
      }
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`setOsAccountProfilePhoto exception: code is ${err.code}, message is ${err.message}`);
  }
  ```

### setOsAccountProfilePhoto

setOsAccountProfilePhoto(localId: number, photo: string): Promise&lt;void&gt;

Sets a profile photo for a system account. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MANAGE_LOCAL_ACCOUNTS

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name | Type  | Mandatory| Description        |
| ------- | ------ | ---- | ------------ |
| localId | number | Yes  | ID of the target system account.|
| photo   | string | Yes  | Profile photo information.  |

**Return value**

| Type               | Description                                |
| ------------------- | ------------------------------------ |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

| ID| Error Message            |
| -------- | ------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | The system service works abnormally. |
| 12300002 | Invalid localId or photo.    |
| 12300003 | Account not found. |
| 12300008 | Restricted Account. |

**Example**: Set a profile photo for system account 100.

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
  let localId: number = 100;
  let photo: string = 'data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAA0AAAAPCAYAAAA/I0V3AAAAAXNSR0IArs4c6QAAAARnQU1BAA'+
  'Cxjwv8YQUAAAAJcEhZcwAADsMAAA7DAcdvqGQAAACwSURBVDhPvZLBDYMwDEV/ugsXRjAT0EHCOuFIBwkbdIRewi6unbiAyoGgSn1SFH85+Y'+
  'q/4ljARW62X+LHS8uIzjm4dXUYF+utzBikB52Jo5e5iEPKqpACk7R9NM2RvWm5tIkD2czLCUFNKLD6IjdMHFHDzws285MgGrT0xCtp3WOKHo'+
  '+7q0mP0DZW9pNmoEFUzrQjp5cCnaen2kSJXLFD8ghbXyZCMQf/8e8Ns1XVAG/XAgqKzVnJFAAAAABJRU5ErkJggg=='
  try {
    accountManager.setOsAccountProfilePhoto(localId, photo).then(() => {
      console.info('setOsAccountProfilePhoto success');
    }).catch((err: BusinessError) => {
      console.error(`setOsAccountProfilePhoto err: code is ${err.code}, message is ${err.message}`);
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`setOsAccountProfilePhoto exception: code is ${err.code}, message is ${err.message}`);
  }
  ```

### on

on(type: 'activate' | 'activating', name: string, callback: Callback&lt;number&gt;): void

Subscribes to the system account activation states, including the states of the account being activated and the account with activation completed. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS_EXTENSION

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name  | Type                      | Mandatory| Description                                                        |
| -------- | -------------------------- | ---- | ------------------------------------------------------------ |
| type     | 'activate' \| 'activating' | Yes  | Type of the event to subscribe to. The value **activate** indicates that a system account is activated, and **activating** indicates that a system account is being activated.|
| name     | string                     | Yes  | Subscription name, which can be customized. The value cannot be empty or exceed 1024 bytes.          |
| callback | Callback&lt;number&gt;     | Yes  | Callback used to return the ID of the system account being activated or activated.   |

**Error codes**

| ID| Error Message      |
| -------- | ------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | The system service works abnormally. |
| 12300002 | Invalid type or name. |

**Example**

  ```ts
  let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
  function onCallback(receiveLocalId: number){
    console.info('receive localId:' + receiveLocalId);
  }
  try {
    accountManager.on('activating', 'osAccountOnOffNameA', onCallback);
  } catch (e) {
    const err = e as BusinessError;
    console.error(`receive localId exception: code is ${err.code}, message is ${err.message}`);
  }
  ```

### off

off(type: 'activate' | 'activating', name: string, callback?: Callback&lt;number&gt;): void

Unsubscribes from the system account activation states, including the states of the account being activated and the account with activation completed. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS_EXTENSION

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name  | Type                      | Mandatory| Description                                                        |
| -------- | -------------------------- | ---- | ------------------------------------------------------------ |
| type     | 'activate' \| 'activating' | Yes  | Type of the event to unsubscribe from. The value **activate** indicates that a system account is activated, and **activating** indicates that a system account is being activated.|
| name     | string                     | Yes  | Subscription name, which can be customized. The value cannot be empty or exceed 1024 bytes, and must be the same as the value passed by **on()**.|
| callback | Callback&lt;number&gt;     | No  | Callback to unregister. By default, this parameter is left empty, which unregisters all callbacks for the system account activation states.                     |

**Error codes**

| ID| Error Message      |
| -------- | ------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | The system service works abnormally. |
| 12300002 | Invalid type or name. |

**Example**

  ```ts
  let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
  function offCallback(){
    console.info('off enter')
  }
  try {
    accountManager.off('activating', 'osAccountOnOffNameA', offCallback);
  } catch (e) {
    const err = e as BusinessError;
    console.error(`off exception: code is ${err.code}, message is ${err.message}`);
  }
  ```

### on<sup>12+</sup>

on(type: 'switching', callback: Callback&lt;OsAccountSwitchEventData&gt;): void

Subscribes to the switchover between a foreground system account and a background system account in progress. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Note**: The ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS permission is supported since API version 21.

**Required permissions**: ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name  | Type                      | Mandatory| Description                                                        |
| -------- | -------------------------- | ---- | ------------------------------------------------------------ |
| type     | 'switching'                 | Yes  | Event type. The value **switching** indicates that the switchover between a foreground system account and a background account is being performed.|
| callback | Callback&lt;[OsAccountSwitchEventData](#osaccountswitcheventdata12)&gt;     | Yes  | Callback to be invoked when a system account is switching between the foreground and background. The source and target system account IDs are subscribed to.<br>Note: Since API version 21, the optional field **displayId** is available, indicating the ID of the logical display where the switch event occurs.   |

**Error codes**

| ID| Error Message      |
| -------- | ------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | The system service works abnormally. |
| 12300002 | Invalid type. |

**Example**

  ```ts
  let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
  function onSwitchingCallback(eventData: osAccount.OsAccountSwitchEventData){
    console.info('receive eventData:' + JSON.stringify(eventData));
  }
  try {
    accountManager.on('switching', onSwitchingCallback);
  } catch (e) {
    const err = e as BusinessError;
    console.error(`receive eventData exception: code is ${err.code}, message is ${err.message}`);
  }
  ```

### off<sup>12+</sup>

off(type: 'switching', callback?: Callback&lt;OsAccountSwitchEventData&gt;): void

Unsubscribes from the switchover between a foreground system account and a background system account in progress. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Note**: The ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS permission is supported since API version 21.

**Required permissions**: ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name  | Type                      | Mandatory| Description                                                        |
| -------- | -------------------------- | ---- | ------------------------------------------------------------ |
| type     | 'switching'                 | Yes  | Event type. The value **switching** indicates that the switchover between a foreground system account and a background account is being performed.|
| callback | Callback&lt;[OsAccountSwitchEventData](#osaccountswitcheventdata12)&gt;     | No  | Callback to unregister. By default, this parameter is left empty, which unregisters all callbacks for the **switching** event.                     |

**Error codes**

| ID| Error Message      |
| -------- | ------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | The system service works abnormally. |
| 12300002 | Invalid type. |

**Example**

  ```ts
  let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
  try {
    accountManager.off('switching');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`off exception: code is ${err.code}, message is ${err.message}`);
  }
  ```

### on<sup>12+</sup>

on(type: 'switched', callback: Callback&lt;OsAccountSwitchEventData&gt;): void

Subscribes to the end of a switchover between a foreground system account and a background system account. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Note**: The ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS permission is supported since API version 21.

**Required permissions**: ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name  | Type                      | Mandatory| Description                                                        |
| -------- | -------------------------- | ---- | ------------------------------------------------------------ |
| type     | 'switched'                 | Yes  | Event type. The value **switched** indicates that the switchover between a foreground system account and a background system account is complete.|
| callback | Callback&lt;[OsAccountSwitchEventData](#osaccountswitcheventdata12)&gt;     | Yes  | Callback to be invoked when a system account is switched between the foreground and background. The source and target system account IDs are subscribed to.<br>Note: Since API version 21, the optional field **displayId** is available, indicating the ID of the logical display where the switch event occurs.   |

**Error codes**

| ID| Error Message      |
| -------- | ------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | The system service works abnormally. |
| 12300002 | Invalid type. |

**Example**

  ```ts
  let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
  function onSwitchedCallback(eventData: osAccount.OsAccountSwitchEventData){
    console.info('receive eventData:' + JSON.stringify(eventData));
  }
  try {
    accountManager.on('switched', onSwitchedCallback);
  } catch (e) {
    const err = e as BusinessError;
    console.error(`receive eventData exception: code is ${err.code}, message is ${err.message}`);
  }
  ```

### off<sup>12+</sup>

off(type: 'switched', callback?: Callback&lt;OsAccountSwitchEventData&gt;): void

Unsubscribes from the end of a switchover between a foreground system account and a background system account. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Note**: The ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS permission is supported since API version 21.

**Required permissions**: ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name  | Type                      | Mandatory| Description                                                        |
| -------- | -------------------------- | ---- | ------------------------------------------------------------ |
| type     | 'switched'                 | Yes  | Event type. The value **switched** indicates that the switchover between a foreground system account and a background system account is complete.|
| callback | Callback&lt;[OsAccountSwitchEventData](#osaccountswitcheventdata12)&gt;     | No  | Callback to unregister. By default, this parameter is left empty, which unregisters all callbacks for the **switched** event.                     |

**Error codes**

| ID| Error Message      |
| -------- | ------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | The system service works abnormally. |
| 12300002 | Invalid type. |

**Example**

  ```ts
  let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
  try {
    accountManager.off('switched');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`off exception: code is ${err.code}, message is ${err.message}`);
  }
  ```

### getBundleIdForUid<sup>9+</sup>

getBundleIdForUid(uid: number, callback: AsyncCallback&lt;number&gt;): void

Obtains the bundle ID based on the UID. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name  | Type                      | Mandatory| Description                                                                       |
| -------- | --------------------------- | ---- | ------------------------------------------------------------------------ |
| uid      | number                      | Yes  | Process UID.                                                                |
| callback | AsyncCallback&lt;number&gt; | Yes  | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is the bundle ID obtained. Otherwise, **data** is an error object.|

**Error codes**

| ID| Error Message      |
| -------- | ------------- |
| 202 | Not system application.|
| 401 |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | The system service works abnormally. |
| 12300002 | Invalid uid. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
  let testUid: number = 1000000;
  try {
    accountManager.getBundleIdForUid(testUid, (err: BusinessError, bundleId: number) => {
      if (err) {
        console.error(`getBundleIdForUid errInfo:code is ${err.code}, message is ${err.message}`);
      } else {
        console.info('getBundleIdForUid bundleId:' + JSON.stringify(bundleId));
      }
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`getBundleIdForUid exception: code is ${err.code}, message is ${err.message}`);
  }
  ```

### getBundleIdForUid<sup>9+</sup>

getBundleIdForUid(uid: number): Promise&lt;number&gt;

Obtains the bundle ID based on the UID. This API uses a promise to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name | Type  | Mandatory| Description        |
| ------- | ------ | ---- | ------------ |
| uid     | number | Yes  |  Process UID.|

**Return value**

| Type                 | Description                                 |
| --------------------- | ------------------------------------ |
| Promise&lt;number&gt; | Promise used to return the bundle ID obtained.|

**Error codes**

| ID| Error Message      |
| -------- | ------------- |
| 202 | Not system application.|
| 401 |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | The system service works abnormally. |
| 12300002 | Invalid uid. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
  let testUid: number = 1000000;
  try {
    accountManager.getBundleIdForUid(testUid).then((result: number) => {
      console.info('getBundleIdForUid bundleId:' + JSON.stringify(result));
    }).catch((err: BusinessError) => {
      console.error(`getBundleIdForUid errInfo:code is ${err.code}, message is ${err.message}`);
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`getBundleIdForUid exception: code is ${err.code}, message is ${err.message}`);
  }
  ```

### getBundleIdForUidSync<sup>10+</sup>

getBundleIdForUidSync(uid: number): number

Obtains the bundle ID based on the specified UID. The API returns the result synchronously.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name | Type  | Mandatory| Description        |
| ------- | ------ | ---- | ------------ |
| uid     | number | Yes  |  Process UID.|

**Return value**

| Type  | Description                    |
| ------ | ------------------------ |
| number | Bundle ID obtained.|

**Error codes**

| ID| Error Message      |
| -------- | ------------- |
| 202 | Not system application.|
| 401 |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300002 | Invalid uid. |

**Example**

  ```ts
  let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
  let testUid: number = 1000000;
  try {
    let bundleId : number = accountManager.getBundleIdForUidSync(testUid);
    console.info('getBundleIdForUidSync bundleId:' + bundleId);
  } catch (e) {
    const err = e as BusinessError;
    console.error(`getBundleIdForUidSync exception: code is ${err.code}, message is ${err.message}`);
  }
  ```

### isMainOsAccount<sup>9+</sup>

isMainOsAccount(callback: AsyncCallback&lt;boolean&gt;): void

Checks whether the current process belongs to the main system account. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MANAGE_LOCAL_ACCOUNTS

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name  | Type                         | Mandatory| Description                                                              |
| -------- | ---------------------------- | ---- | ----------------------------------------------------------------- |
| callback | AsyncCallback&lt;boolean&gt; | Yes  | Callback used to return the result. If **true** is returned, the current process belongs to the main system account. If **false** is returned, the current process does not belong to the main system account.|

**Error codes**

| ID| Error Message      |
| -------- | ------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | The system service works abnormally. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
  try {
    accountManager.isMainOsAccount((err: BusinessError,result: boolean)=>{
      if (err) {
        console.error(`isMainOsAccount errInfo:code is ${err.code}, message is ${err.message}`);
      } else {
        console.info('isMainOsAccount result:' + JSON.stringify(result));
      }
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`isMainOsAccount exception: code is ${err.code}, message is ${err.message}`);
  }
  ```

### isMainOsAccount<sup>9+</sup>

isMainOsAccount(): Promise&lt;boolean&gt;;

Checks whether the current process belongs to the main system account. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MANAGE_LOCAL_ACCOUNTS

**System capability**: SystemCapability.Account.OsAccount

**Return value**

| Type                  | Description                                                                 |
| ---------------------- | --------------------------------------------------------------------- |
| Promise&lt;boolean&gt; | Promise used to return the result. If **true** is returned, the current process belongs to the main system account. If **false** is returned, the current process does not belong to the main system account.|

**Error codes**

| ID| Error Message      |
| -------- | ------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 12300001 | The system service works abnormally. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
  try {
    accountManager.isMainOsAccount().then((result: boolean) => {
      console.info('isMainOsAccount result:' + JSON.stringify(result));
    }).catch((err: BusinessError) => {
      console.error(`isMainOsAccount errInfo:code is ${err.code}, message is ${err.message}`);
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`isMainOsAccount exception: code is ${err.code}, message is ${err.message}`);
  }
  ```

### getForegroundOsAccountLocalId<sup>21+</sup>

getForegroundOsAccountLocalId(displayId: number): Promise&lt;number&gt;

Obtains the ID of the foreground system account running on a specified logical display. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name   | Type  | Mandatory| Description        |
| --------- | ------ | ---- | ------------ |
| displayId | number | Yes  | Logical screen ID.|

**Return value**

| Type                 | Description                        |
| --------------------- | ---------------------------- |
| Promise&lt;number&gt; | Promise used to return the system account ID.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Account Management Error Codes](./errorcode-account.md).

| ID| Error Message|
| -------- | -------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 12300001 | The system service works abnormally. |
| 12300017 | The foreground OS account is not found. |

**Example**
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
  let displayId: number = 0;
  try {
    accountManager.getForegroundOsAccountLocalId(displayId).then((localId: number) => {
      console.info('foreground account on display ' + displayId + ' is ' + localId);
    }).catch((err: BusinessError) => {
      console.error(`getForegroundOsAccountLocalId failed: ${err.code} ${err.message}`);
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`getForegroundOsAccountLocalId exception: ${err.code} ${err.message}`);
  }
  ```

### getForegroundOsAccountDisplayId<sup>21+</sup>

getForegroundOsAccountDisplayId(localId: number): Promise&lt;number&gt;

Obtains the logical display ID of the specified foreground system account. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name | Type  | Mandatory| Description      |
| ------- | ------ | ---- | ---------- |
| localId | number | Yes  | ID of the target system account.|

**Return value**

| Type                 | Description                          |
| --------------------- | ------------------------------ |
| Promise&lt;number&gt; | Promise used to return the logical display ID.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Account Management Error Codes](./errorcode-account.md).

| ID| Error Message|
| -------- | -------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 12300001 | The system service works abnormally. |
| 12300017 | The foreground OS account is not found. |

**Example**
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
  let localId: number = 100;
  try {
    accountManager.getForegroundOsAccountDisplayId(localId).then((displayId: number) => {
      console.info('account ' + localId + ' foreground displayId: ' + displayId);
    }).catch((err: BusinessError) => {
      console.error(`getForegroundOsAccountDisplayId failed: ${err.code} ${err.message}`);
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`getForegroundOsAccountDisplayId exception: ${err.code} ${err.message}`);
  }
  ```

### getOsAccountConstraintSourceTypes<sup>9+</sup>

getOsAccountConstraintSourceTypes(localId: number, constraint: string, callback: AsyncCallback&lt;Array&lt;ConstraintSourceTypeInfo&gt;&gt;): void

Obtains the constraint source information of a system account. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MANAGE_LOCAL_ACCOUNTS

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name  | Type                      | Mandatory| Description                                                        |
| -------- | -------------------------- | ---- | ------------------------------------------------------------ |
| localId     | number | Yes  |  ID of the target system account.|
| constraint     | string | Yes  |  [Constraint](js-apis-osAccount.md#constraints) whose source information is to be obtained.|
| callback | AsyncCallback&lt;Array&lt;[ConstraintSourceTypeInfo](#constraintsourcetypeinfo9)&gt;&gt;     | Yes  | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is the [constraint](js-apis-osAccount.md#constraints) source information obtained. Otherwise, **err** is an error object.                     |

**Error codes**

| ID| Error Message      |
| -------- | ------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | The system service works abnormally. |
| 12300002 | Invalid name or constraint. |
| 12300003 | Account not found. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
  try {
    accountManager.getOsAccountConstraintSourceTypes(100, 'constraint.wifi',
      (err: BusinessError,sourceTypeInfos: osAccount.ConstraintSourceTypeInfo[])=>{
      if (err) {
        console.error(`getOsAccountConstraintSourceTypes errInfo:code is ${err.code}, message is ${err.message}`);
      } else {
        console.info('getOsAccountConstraintSourceTypes sourceTypeInfos:' + JSON.stringify(sourceTypeInfos));
      }
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`getOsAccountConstraintSourceTypes exception: code is ${err.code}, message is ${err.message}`);
  }
  ```

### getOsAccountConstraintSourceTypes<sup>9+</sup>

getOsAccountConstraintSourceTypes(localId: number, constraint: string): Promise&lt;Array&lt;ConstraintSourceTypeInfo&gt;&gt;;

Obtains the constraint source information of a system account. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MANAGE_LOCAL_ACCOUNTS

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name | Type  | Mandatory| Description        |
| ------- | ------ | ---- | ------------ |
| localId     | number | Yes  |  ID of the target system account.|
| constraint     | string | Yes  |  [Constraint](js-apis-osAccount.md#constraints) whose source information is to be obtained.|

**Return value**

| Type                 | Description                                                        |
| --------------------- | ------------------------------------------------------------ |
| Promise&lt;Array&lt;[ConstraintSourceTypeInfo](#constraintsourcetypeinfo9)&gt;&gt; | Promise used to return the source information of the specified [constraint](js-apis-osAccount.md#constraints).|

**Error codes**

| ID| Error Message      |
| -------- | ------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | The system service works abnormally. |
| 12300002 | Invalid name or constraint. |
| 12300003 | Account not found. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
  try {
    accountManager.getOsAccountConstraintSourceTypes(100, 'constraint.wifi').then(
      (result: osAccount.ConstraintSourceTypeInfo[]) => {
      console.info('getOsAccountConstraintSourceTypes sourceTypeInfos:' + JSON.stringify(result));
    }).catch((err: BusinessError) => {
      console.error(`getOsAccountConstraintSourceTypes errInfo:code is ${err.code}, message is ${err.message}`);
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`getOsAccountConstraintSourceTypes exception: code is ${err.code}, message is ${err.message}`);
  }
  ```

### getOsAccountType<sup>12+</sup>

getOsAccountType(localId: number): Promise&lt;OsAccountType&gt;;

Obtains the type of a system account. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name | Type  | Mandatory| Description        |
| ------- | ------ | ---- | ------------ |
| localId     | number | Yes  |  ID of the target system account.|

**Return value**

| Type                 | Description                                                        |
| --------------------- | ------------------------------------------------------------ |
| Promise&lt;[OsAccountType](js-apis-osAccount.md#osaccounttype)&gt; | Promise used to return the type of the system account obtained.|

**Error codes**

| ID| Error Message      |
| -------- | ------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | The system service works abnormally. |
| 12300003 | Account not found. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
  try {
    let localId: number = 100;
    accountManager.getOsAccountType(localId).then((type: osAccount.OsAccountType) => {
      console.info('getOsAccountType Type:' + type);
    }).catch((err: BusinessError) => {
      console.error(`getOsAccountType errInfo:code is ${err.code}, message is ${err.message}`);
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`getOsAccountType exception: code is ${err.code}, message is ${err.message}`);
  }
  ```

### bindDomainAccount<sup>20+</sup>

bindDomainAccount(localId: number, domainAccountInfo: DomainAccountInfo): Promise&lt;void&gt;

Binds a domain account to a system account. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MANAGE_LOCAL_ACCOUNTS

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name | Type  | Mandatory| Description        |
| ------- | ------ | ---- | ------------ |
| localId     | number | Yes  |  ID of the target system account.|
| domainAccountInfo | [DomainAccountInfo](#domainaccountinfo8) | Yes  | Domain account information.         |

**Return value**

| Type                 | Description                                                        |
| --------------------- | ------------------------------------------------------------ |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Account Management Error Codes](./errorcode-account.md).

| ID| Error Message      |
| -------- | ------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 801 | Capability not supported.|
| 12300001 | The system service works abnormally. |
| 12300002 | Invalid domain account information. |
| 12300003 | The OS account not found. |
| 12300008 | Restricted OS account. Possible causes: The OS account cannot be bound. |
| 12300010 | Service busy. Possible causes: The target OS account or domain account is being operated. |
| 12300021 | The OS account is already bound. |
| 12300022 | The domain account is already bound. |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let accountManager: osAccount.AccountManager = osAccount.getAccountManager();
  try {
    let localId: number = 100;
    let domainInfo: osAccount.DomainAccountInfo =
      {domain: 'testDomain', accountName: 'testAccountName'};
    accountManager.bindDomainAccount(localId, domainInfo).then(() => {
      console.info('bindDomainAccount success.');
    }).catch((error: BusinessError) => {
      console.error(`bindDomainAccount failed, errCode=${error.code}, errMsg=${error.message}`);
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`bindDomainAccount error, errCode=${error.code}, errMsg=${error.message}`);
  }
  ```

## UserAuth<sup>8+</sup>

Provides APIs for user authentication.

**System API**: This is a system API.

### constructor<sup>8+</sup>

 

A constructor used to create an instance for user authentication.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Error codes**

| ID| Error Message      |
| -------- | ------------- |
| 202 | Not system application.|

**Example**
  ```ts
  let userAuth = new osAccount.UserAuth();
  ```

### getVersion<sup>8+</sup>

getVersion(): number;

Obtains the version number.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Return value**

| Type  | Description        |
| :----- | :----------- |
| number | Version number obtained.|

**Error codes**

| ID| Error Message      |
| -------- | ------------- |
| 202 | Not system application.|

**Example**
  ```ts
  let userAuth = new osAccount.UserAuth();
  let version: number = userAuth.getVersion();
  console.info('getVersion version = ' + version);
  ```

### getAvailableStatus<sup>8+</sup>

getAvailableStatus(authType: AuthType, authTrustLevel: AuthTrustLevel): number;

Obtains the available status of the authentication capability corresponding to the specified authentication type and trust level.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Required permissions**: ohos.permission.ACCESS_USER_AUTH_INTERNAL

**Parameters**

| Name          | Type                              | Mandatory| Description                      |
| --------------- | -----------------------------------| ---- | ------------------------- |
| authType        | [AuthType](#authtype8)             | Yes  | Authentication credential type.    |
| authTrustLevel  | [AuthTrustLevel](#authtrustlevel8) | Yes  | Trust level of the authentication.|

**Return value**

| Type  | Description                          |
| ------ | ----------------------------- |
| number | Available status of the authentication capability.|

**Error codes**

| ID| Error Message                    |
| -------- | --------------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | The system service works abnormally. |
| 12300002 | Invalid authType or authTrustLevel. |

**Example**
  ```ts
  let userAuth = new osAccount.UserAuth();
  let authType: osAccount.AuthType = osAccount.AuthType.PIN;
  let authTrustLevel: osAccount.AuthTrustLevel = osAccount.AuthTrustLevel.ATL1;
  try {
    let status: number = userAuth.getAvailableStatus(authType, authTrustLevel);
    console.info('getAvailableStatus status = ' + status);
  } catch (e) {
    const err = e as BusinessError;
    console.error(`getAvailableStatus exception = code is ${err.code}, message is ${err.message}`);
  }
  ```

### getProperty<sup>8+</sup>

getProperty(request: GetPropertyRequest, callback: AsyncCallback&lt;ExecutorProperty&gt;): void

Obtains the executor property based on the request. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Required permissions**: ohos.permission.ACCESS_USER_AUTH_INTERNAL

**Parameters**

| Name   | Type                                                                   | Mandatory| Description                               |
| -------- | ----------------------------------------------------------- | ---- | ------------------------------------------------------ |
| request  | [GetPropertyRequest](#getpropertyrequest8)                  | Yes  | Request information, including the authentication credential type and property list.|
| callback | AsyncCallback&lt;[ExecutorProperty](#executorproperty8)&gt; | Yes  | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is the executor property information obtained. Otherwise, **err** is an error object.|

**Error codes**

| ID| Error Message                    |
| -------- | --------------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | The system service works abnormally. |
| 12300002 | Invalid request. |
| 12300003 | Account not found. |

**Example**
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let userAuth = new osAccount.UserAuth();
  let keys: Array<osAccount.GetPropertyType>  = [
    osAccount.GetPropertyType.AUTH_SUB_TYPE,
    osAccount.GetPropertyType.REMAIN_TIMES,
    osAccount.GetPropertyType.FREEZING_TIME
  ];
  let request: osAccount.GetPropertyRequest = {
    authType: osAccount.AuthType.PIN,
    keys: keys
  };
  try {
    userAuth.getProperty(request, (err: BusinessError, result: osAccount.ExecutorProperty) => {
      if (err) {
        console.error(`getProperty exception = code is ${err.code}, message is ${err.message}`);
      } else {
        console.info('getProperty result = ' + JSON.stringify(result));
      }
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`getProperty exception = code is ${err.code}, message is ${err.message}`);
  }
  ```

### getProperty<sup>8+</sup>

getProperty(request: GetPropertyRequest): Promise&lt;ExecutorProperty&gt;;

Obtains the executor property based on the request. This API uses a promise to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Required permissions**: ohos.permission.ACCESS_USER_AUTH_INTERNAL

**Parameters**

| Name   | Type                                                  | Mandatory| Description                               |
| -------- | ------------------------------------------------------ | ---- | ---------------------------------- |
| request  | [GetPropertyRequest](#getpropertyrequest8) | Yes  | Request information, including the authentication credential type and property list.|

**Return value**

| Type                                                             | Description                                                |
| :---------------------------------------------------------------- | :-------------------------------------------------- |
| Promise&lt;[ExecutorProperty](#executorproperty8)&gt; | Promise used to return the executor property.|

**Error codes**

| ID| Error Message                    |
| -------- | --------------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | The system service works abnormally. |
| 12300002 | Invalid request. |
| 12300003 | Account not found. |

**Example**
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let userAuth = new osAccount.UserAuth();
  let keys: Array<osAccount.GetPropertyType> = [
    osAccount.GetPropertyType.AUTH_SUB_TYPE,
    osAccount.GetPropertyType.REMAIN_TIMES,
    osAccount.GetPropertyType.FREEZING_TIME
  ];
  let request: osAccount.GetPropertyRequest = {
    authType: osAccount.AuthType.PIN,
    keys: keys
  };
  try {
    userAuth.getProperty(request).then((result: osAccount.ExecutorProperty) => {
      console.info('getProperty result = ' + JSON.stringify(result));
    }).catch((err: BusinessError) => {
      console.error(`getProperty error = code is ${err.code}, message is ${err.message}`);
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`getProperty exception = code is ${err.code}, message is ${err.message}`);
  }
  ```

### getPropertyByCredentialId<sup>14+</sup>

getPropertyByCredentialId(credentialId: Uint8Array, keys: Array&lt;GetPropertyType&gt;): Promise&lt;ExecutorProperty&gt;;

Obtains the specified property information of the associated executor based on the credential ID. This API uses a promise to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Required permissions**: ohos.permission.ACCESS_USER_AUTH_INTERNAL

**Parameters**

| Name   | Type                                                  | Mandatory| Description                               |
| -------- | ------------------------------------------------------ | ---- | ---------------------------------- |
| credentialId  | Uint8Array | Yes  | Credential ID.|
| keys     | Array&lt;[GetPropertyType](#getpropertytype8)&gt; | Yes   | Property type array to be queried.|

**Return value**

| Type                                                             | Description                                                |
| :---------------------------------------------------------------- | :-------------------------------------------------- |
| Promise&lt;[ExecutorProperty](#executorproperty8)&gt; | Promise used to return the executor attributes.|

**Error codes**

| ID| Error Message                    |
| -------- | --------------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | The system service works abnormally. |
| 12300002 | Invalid keys. |
| 12300102 | The credential does not exist. |

**Example**
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let userIDM = new osAccount.UserIdentityManager();
  let credInfo: osAccount.EnrolledCredInfo[] = [];
  async function getProperty() {
    try {
      credInfo = await userIDM.getAuthInfo(osAccount.AuthType.PRIVATE_PIN);
    } catch (e) {
      const err = e as BusinessError;
      console.error(`getAuthInfo exception = code is ${err.code}, message is ${err.message}`);
      return;
    }
    if (credInfo.length == 0) {
      console.info('no credential infos');
      return;
    }
    let testCredentialId: Uint8Array = credInfo[0].credentialId;
    let keys: Array<osAccount.GetPropertyType> = [
      osAccount.GetPropertyType.AUTH_SUB_TYPE,
      osAccount.GetPropertyType.REMAIN_TIMES,
      osAccount.GetPropertyType.FREEZING_TIME
    ];
    try {
      let userAuth = new osAccount.UserAuth();
      userAuth.getPropertyByCredentialId(testCredentialId, keys).then((result: osAccount.ExecutorProperty) => {
        console.info('getPropertyByCredentialId result = ' + JSON.stringify(result));
      }).catch((err: BusinessError) => {
        console.error(`getPropertyByCredentialId error = code is ${err.code}, message is ${err.message}`);
      });
    } catch (e) {
      const err = e as BusinessError;
      console.error(`getPropertyByCredentialId exception = code is ${err.code}, message is ${err.message}`);
    }
  }
  ```

### setProperty<sup>8+</sup>

setProperty(request: SetPropertyRequest, callback: AsyncCallback&lt;void&gt;): void

Sets the property for the initialization algorithm. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Required permissions**: ohos.permission.ACCESS_USER_AUTH_INTERNAL

**Parameters**

| Name   | Type                                                 | Mandatory| Description                                                                   |
| -------- | ----------------------------------------------------- | ---- | ---------------------------------------------------------------------- |
| request  | [SetPropertyRequest](#setpropertyrequest8)| Yes  | Request information, including the authentication credential type and the key value to set.                                  |
| callback | AsyncCallback&lt;void&gt;                           | Yes  | Callback used to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object.|

**Error codes**

| ID| Error Message                    |
| -------- | --------------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | The system service works abnormally. |
| 12300002 | Invalid request. |

**Example**
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let userAuth = new osAccount.UserAuth();
  let request: osAccount.SetPropertyRequest = {
    authType: osAccount.AuthType.PIN,
    key: osAccount.SetPropertyType.INIT_ALGORITHM,
    setInfo: new Uint8Array([0])
  };
  try {
    userAuth.setProperty(request, (err: BusinessError) => {
      if (err) {
        console.error(`setProperty failed, error = code is ${err.code}, message is ${err.message}`);
      } else {
        console.info('setProperty successfully');
      }
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`setProperty exception = code is ${err.code}, message is ${err.message}`);
  }
  ```

### setProperty<sup>8+</sup>

setProperty(request: SetPropertyRequest): Promise&lt;void&gt;;

Sets the property for the initialization algorithm. This API uses a promise to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Required permissions**: ohos.permission.ACCESS_USER_AUTH_INTERNAL

**Parameters**

| Name   | Type                                      | Mandatory| Description                                     |
| -------- | ------------------------------------------ | ---- | ---------------------------------------- |
| request  | [SetPropertyRequest](#setpropertyrequest8) | Yes  | Request information, including the authentication credential type and the key value to set.|

**Return value**

| Type                 | Description                                                          |
| :-------------------- | :------------------------------------------------------------ |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

| ID| Error Message                    |
| -------- | --------------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | The system service works abnormally. |
| 12300002 | Invalid request. |

**Example**
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let userAuth = new osAccount.UserAuth();
  let request: osAccount.SetPropertyRequest = {
    authType: osAccount.AuthType.PIN,
    key: osAccount.SetPropertyType.INIT_ALGORITHM,
    setInfo: new Uint8Array([0])
  };
  try {
    userAuth.setProperty(request).then(() => {
      console.info('setProperty successfully');
    }).catch((err: BusinessError) => {
      console.error(`setProperty failed, error = code is ${err.code}, message is ${err.message}`);
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`setProperty exception = code is ${err.code}, message is ${err.message}`);
  }
  ```

### prepareRemoteAuth<sup>12+</sup>

prepareRemoteAuth(remoteNetworkId: string): Promise&lt;void&gt;;

Prepares for remote authentication. This API uses a promise to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Required permissions**: ohos.permission.ACCESS_USER_AUTH_INTERNAL

**Parameters**

| Name           | Type  | Mandatory| Description            |
| --------         | ------ | ---- | --------------- |
| remoteNetworkId  | string | Yes  | Remote network ID. |

**Return value**

| Type                 | Description                                                          |
| :-------------------- | :------------------------------------------------------------ |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

| ID| Error Message                    |
| -------- | --------------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | System service exception. |
| 12300002 | Invalid remoteNetworkId. |
| 12300090 | Cross-device capability not supported. |
| 12300091 | Cross-device communication failed. |
| 12300111 | Operation timeout. |

**Example**
  ```ts
  import { distributedDeviceManager } from '@kit.DistributedServiceKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  let userAuth = new osAccount.UserAuth();
  let distributedDeviceMgr = distributedDeviceManager.createDeviceManager("com.example.bundleName");
  distributedDeviceMgr.getAvailableDeviceList().then((data: Array<distributedDeviceManager.DeviceBasicInfo>) => {
      try {
        if (data.length > 0 && data[0].networkId != null) {
          userAuth.prepareRemoteAuth(data[0].networkId).then(() => {
            console.info('prepareRemoteAuth successfully');
          }).catch((err: BusinessError) => {
            console.error(`prepareRemoteAuth failed, error = code is ${err.code}, message is ${err.message}`);
          });
        }
      } catch (e) {
        const err = e as BusinessError;
        console.error(`prepareRemoteAuth exception = code is ${err.code}, message is ${err.message}`);
      }
    }
  )
  ```

### auth<sup>8+</sup>

auth(challenge: Uint8Array, authType: AuthType, authTrustLevel: AuthTrustLevel, callback: IUserAuthCallback): Uint8Array;

Performs authentication of the current user. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Required permissions**: ohos.permission.ACCESS_USER_AUTH_INTERNAL

**Parameters**

| Name          | Type                                    | Mandatory| Description                               |
| --------------- | ---------------------------------------- | --- | ------------------------------------ |
| challenge       | Uint8Array                               | Yes | Challenge value, which is a random number used to improve security.|
| authType        | [AuthType](#authtype8)                   | Yes | Authentication credential type.                       |
| authTrustLevel  | [AuthTrustLevel](#authtrustlevel8)       | Yes | Trust level of the authentication result.              |
| callback        | [IUserAuthCallback](#iuserauthcallback8) | Yes | Callback used to return the authentication result. |

**Return value**

| Type       | Description              |
| ---------- | ------------------ |
| Uint8Array | ID of the context for canceling the authentication.|

**Error codes**

| ID| Error Message         |
| -------- | --------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | The system service works abnormally. |
| 12300002 | Invalid challenge, authType or authTrustLevel. |
| 12300013 | Network exception. |
| 12300020 | Device hardware abnormal. |
| 12300090 | Cross-device capability not supported. |
| 12300091 | Cross-device communication failed. |
| 12300101 | The credential is incorrect. |
| 12300102 | The credential does not exist. |
| 12300105 | The trust level is not supported. |
| 12300106 | The authentication type is not supported. |
| 12300109 | The authentication, enrollment, or update operation is canceled. |
| 12300110 | The authentication is locked. |
| 12300111 | The authentication time out. |
| 12300112 | The authentication service is busy. |
| 12300113 | The authentication service does not exist. |
| 12300114 | The authentication service works abnormally. |
| 12300117 | PIN is expired. |
| 12300119 | Multi-factor authentication failed. |
| 12300211 | Server unreachable. |

**Example**
  ```ts
  let userAuth = new osAccount.UserAuth();
  let challenge: Uint8Array = new Uint8Array([0]);
  let authType: osAccount.AuthType = osAccount.AuthType.PIN;
  let authTrustLevel: osAccount.AuthTrustLevel = osAccount.AuthTrustLevel.ATL1;
  try {
    userAuth.auth(challenge, authType, authTrustLevel, {
      onResult: (result: number, extraInfo: osAccount.AuthResult) => {
          console.info('auth result = ' + result);
          console.info('auth extraInfo = ' + JSON.stringify(extraInfo));
      }
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`auth exception = code is ${err.code}, message is ${err.message}`);
  }
  ```

### auth<sup>12+</sup>

auth(challenge: Uint8Array, authType: AuthType, authTrustLevel: AuthTrustLevel, options: AuthOptions, callback: IUserAuthCallback): Uint8Array

Starts user authentication based on the specified challenge value, authentication type (PIN, facial, or fingerprint authentication), authentication trust level, and optional parameters (such as the account ID and authentication intent). This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Required permissions**: ohos.permission.ACCESS_USER_AUTH_INTERNAL

**Parameters**

| Name          | Type                                    | Mandatory| Description                               |
| --------------- | ---------------------------------------- | --- | ------------------------------------ |
| challenge       | Uint8Array                               | Yes | Challenge value, which is a random number used to prevent replay attacks and improve security.|
| authType        | [AuthType](#authtype8)                   | Yes | Authentication credential type.                       |
| authTrustLevel  | [AuthTrustLevel](#authtrustlevel8)       | Yes | Trust level of the authentication result.              |
| options         | [AuthOptions](#authoptions12) | Yes| Optional parameters for the authentication.|
| callback        | [IUserAuthCallback](#iuserauthcallback8) | Yes | Callback used to return the authentication result. |

**Return value**

| Type       | Description              |
| ---------- | ------------------ |
| Uint8Array | ID of the context for canceling the authentication.|

**Error codes**

| ID| Error Message         |
| -------- | --------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | The system service works abnormally. |
| 12300002 | Invalid challenge, authType, authTrustLevel or options. |
| 12300003 | Account not found. |
| 12300013 | Network exception. |
| 12300020 | Device hardware abnormal. |
| 12300090 | Cross-device capability not supported. |
| 12300091 | Cross-device communication failed. |
| 12300101 | The credential is incorrect. |
| 12300102 | The credential does not exist. |
| 12300105 | The trust level is not supported. |
| 12300106 | The authentication type is not supported. |
| 12300109 | The authentication, enrollment, or update operation is canceled. |
| 12300110 | The authentication is locked. |
| 12300111 | The authentication time out. |
| 12300112 | The authentication service is busy. |
| 12300113 | The authentication service does not exist. |
| 12300114 | The authentication service works abnormally. |
| 12300117 | PIN is expired. |
| 12300119 | Multi-factor authentication failed. |
| 12300211 | Server unreachable. |

**Example**
  ```ts
  let userAuth = new osAccount.UserAuth();
  let challenge: Uint8Array = new Uint8Array([0]);
  let authType: osAccount.AuthType = osAccount.AuthType.PIN;
  let authTrustLevel: osAccount.AuthTrustLevel = osAccount.AuthTrustLevel.ATL1;
  let options: osAccount.AuthOptions = {
    accountId: 100
  };
  try {
    userAuth.auth(challenge, authType, authTrustLevel, options, {
      onResult: (result: number, extraInfo: osAccount.AuthResult) => {
          console.info('auth result = ' + result);
          console.info('auth extraInfo = ' + JSON.stringify(extraInfo));
      }
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`auth exception = code is ${err.code}, message is ${err.message}`);
  }
  ```

### authUser<sup>8+</sup>

authUser(userId: number, challenge: Uint8Array, authType: AuthType, authTrustLevel: AuthTrustLevel, callback: IUserAuthCallback): Uint8Array;

Performs authentication of the specified user. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Required permissions**: ohos.permission.ACCESS_USER_AUTH_INTERNAL

**Parameters**

| Name          | Type                                                | Mandatory| Description                               |
| --------------- | ---------------------------------------------------- | --- | ------------------------------------ |
| userId          | number                                               | Yes | User ID.                       |
| challenge       | Uint8Array                                           | Yes | Challenge value, which is a random number used to improve security.                         |
| authType        | [AuthType](#authtype8)                   | Yes | Authentication credential type.                       |
| authTrustLevel  | [AuthTrustLevel](#authtrustlevel8)       | Yes | Trust level of the authentication result.              |
| callback        | [IUserAuthCallback](#iuserauthcallback8) | Yes | Callback used to return the authentication result. |

**Return value**

| Type       | Description              |
| ---------- | ------------------ |
| Uint8Array | ID of the context for canceling the authentication.|

**Error codes**

| ID| Error Message         |
| -------- | --------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | The system service works abnormally. |
| 12300002 | Invalid challenge, authType or authTrustLevel. |
| 12300003 | Account not found. |
| 12300013 | Network exception. |
| 12300020 | Device hardware abnormal. |
| 12300090 | Cross-device capability not supported. |
| 12300091 | Cross-device communication failed. |
| 12300101 | The credential is incorrect. |
| 12300102 | The credential does not exist. |
| 12300105 | The trust level is not supported. |
| 12300106 | The authentication type is not supported. |
| 12300109 | The authentication, enrollment, or update operation is canceled. |
| 12300110 | The authentication is locked. |
| 12300111 | The authentication time out. |
| 12300112 | The authentication service is busy. |
| 12300113 | The authentication service does not exist. |
| 12300114 | The authentication service works abnormally. |
| 12300117 | PIN is expired. |
| 12300119 | Multi-factor authentication failed. |
| 12300211 | Server unreachable. |

**Example**
  ```ts
  let userAuth = new osAccount.UserAuth();
  let userID: number = 100;
  let challenge: Uint8Array = new Uint8Array([0]);
  let authType: osAccount.AuthType = osAccount.AuthType.PIN;
  let authTrustLevel: osAccount.AuthTrustLevel = osAccount.AuthTrustLevel.ATL1;
  try {
    userAuth.authUser(userID, challenge, authType, authTrustLevel, {
      onResult: (result,extraInfo) => {
        console.info('authUser result = ' + result);
        console.info('authUser extraInfo = ' + JSON.stringify(extraInfo));
      }
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`authUser exception = code is ${err.code}, message is ${err.message}`);
  }
  ```

### cancelAuth<sup>8+</sup>

cancelAuth(contextID: Uint8Array): void

Cancels an authentication.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Required permissions**: ohos.permission.ACCESS_USER_AUTH_INTERNAL

**Parameters**

| Name   | Type      | Mandatory | Description                                       |
| ----------| ---------- | ---- | ------------------------------------------ |
| contextID | Uint8Array | Yes  | ID of the authentication context. The context ID is dynamically generated.|

**Error codes**

| ID| Error Message           |
| -------- | ------------------ |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | The system service works abnormally. |
| 12300002 | Invalid contextId. |

**Example**
  ```ts
  let userAuth = new osAccount.UserAuth();
  let pinAuth: osAccount.PINAuth = new osAccount.PINAuth();
  let challenge = new Uint8Array([0]);
  let contextId: Uint8Array = userAuth.auth(challenge, osAccount.AuthType.PIN, osAccount.AuthTrustLevel.ATL1, {
    onResult: (result: number, extraInfo: osAccount.AuthResult) => {
      console.info('auth result = ' + result);
      console.info('auth extraInfo = ' + JSON.stringify(extraInfo));
    }
  });
  try {
    userAuth.cancelAuth(contextId);
  } catch (e) {
    const err = e as BusinessError;
    console.error(`cancelAuth exception = code is ${err.code}, message is ${err.message}`);
  }
  ```

## PINAuth<sup>8+</sup>

Provides APIs for PIN authentication.

**System API**: This is a system API.

### constructor<sup>8+</sup>

 

Creates a PIN authentication instance.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Error codes**

| ID| Error Message      |
| -------- | ------------- |
| 202 | Not system application.|

**Example**
  ```ts
  let pinAuth: osAccount.PINAuth = new osAccount.PINAuth();
  ```

### registerInputer<sup>8+</sup>

registerInputer(inputer: IInputer): void

Registers a PIN inputer.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Required permissions**: ohos.permission.ACCESS_PIN_AUTH

**Parameters**

| Name   | Type                    | Mandatory| Description                     |
| ----------| ----------------------- | --- | -------------------------- |
| inputer   | [IInputer](#iinputer8)  | Yes | PIN inputer, which is used to obtain the PIN.|

**Error codes**

| ID| Error Message                    |
| -------- | --------------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | The system service works abnormally. |
| 12300002 | Invalid inputer. |
| 12300103 | The credential inputer already exists. |

**Example**
  ```ts
  let pinAuth: osAccount.PINAuth = new osAccount.PINAuth();
  let password = new Uint8Array([0, 0, 0, 0, 0]);
  try {
    pinAuth.registerInputer({
        onGetData: (authSubType: osAccount.AuthSubType, callback: osAccount.IInputData) => {
          callback.onSetData(authSubType, password);
        }
    });
    console.info('registerInputer success.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`registerInputer exception = code is ${err.code}, message is ${err.message}`);
  }
  ```

### unregisterInputer<sup>8+</sup>

unregisterInputer(): void

Unregisters this PIN inputer.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Required permissions**: ohos.permission.ACCESS_PIN_AUTH

**Error codes**

| ID| Error Message                    |
| -------- | --------------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|

**Example**
  ```ts
  let pinAuth: osAccount.PINAuth = new osAccount.PINAuth();
  pinAuth.unregisterInputer();
  ```

## InputerManager <sup>9+</sup>

Provides APIs for managing credential inputers.

### registerInputer<sup>9+</sup>

static registerInputer(authType: AuthType, inputer: IInputer): void

Registers a credential inputer.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Required permissions**: ohos.permission.ACCESS_USER_AUTH_INTERNAL or ohos.permission.MANAGE_USER_IDM

**Parameters**

| Name   | Type                    | Mandatory| Description                     |
| ----------| ----------------------- | --- | -------------------------- |
| authType   | [AuthType](#authtype8)  | Yes | Authentication credential type.|
| inputer   | [IInputer](#iinputer8)  | Yes | Credential inputer to register.|

**Error codes**

| ID| Error Message                    |
| -------- | --------------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | The system service works abnormally. |
| 12300002 | Invalid authType or inputer. |
| 12300103 | The credential inputer already exists. |
| 12300106 | The authentication type is not supported. |

**Example**
  ```ts
  let authType: osAccount.AuthType = osAccount.AuthType.DOMAIN;
  let password: Uint8Array = new Uint8Array([0, 0, 0, 0, 0]);
  try {
    osAccount.InputerManager.registerInputer(authType, {
        onGetData: (authSubType: osAccount.AuthSubType, callback: osAccount.IInputData) => {
          callback.onSetData(authSubType, password);
        }
    });
    console.info('registerInputer success.');
  } catch (e) {
    const err = e as BusinessError;
    console.error(`registerInputer exception = code is ${err.code}, message is ${err.message}`);
  }
  ```

### unregisterInputer<sup>9+</sup>

static unregisterInputer(authType: AuthType): void

Unregisters this credential inputer.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Required permissions**: ohos.permission.ACCESS_USER_AUTH_INTERNAL or ohos.permission.MANAGE_USER_IDM

**Parameters**

| Name   | Type                    | Mandatory| Description                     |
| ----------| ----------------------- | --- | -------------------------- |
| authType   | [AuthType](#authtype8)  | Yes | Authentication credential type.|

**Error codes**

| ID| Error Message                    |
| -------- | --------------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300002  | Invalid authType. |

**Example**
  ```ts
  let authType: osAccount.AuthType = osAccount.AuthType.DOMAIN;
  try {
    osAccount.InputerManager.unregisterInputer(authType);
    console.info('unregisterInputer success.');
  } catch(err) {
    console.error(`unregisterInputer code is ${err.code}, message is ${err.message}`);
  }
  ```

## DomainPlugin<sup>9+</sup>

Provides APIs for domain account authentication.

**System API**: This is a system API.

### auth<sup>9+</sup>

auth(domainAccountInfo: DomainAccountInfo, credential: Uint8Array, callback: IUserAuthCallback): void

Authenticates a domain account.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name     | Type                                   | Mandatory| Description            |
| ---------- | --------------------------------------- | ---- | --------------- |
| domainAccountInfo   | [DomainAccountInfo](#domainaccountinfo8)  | Yes  | Domain account information.|
| credential   | Uint8Array  | Yes  | Credentials of the domain account.|
| callback   | [IUserAuthCallback](#iuserauthcallback8)  | Yes  | Callback used to return the authentication result.|

**Example**
  ```ts
  import { AsyncCallback } from '@kit.BasicServicesKit';
  let plugin: osAccount.DomainPlugin = {
    auth: (domainAccountInfo: osAccount.DomainAccountInfo, credential: Uint8Array,
          callback: osAccount.IUserAuthCallback) => {
      // mock authentication
      // notify authentication result
      let result: osAccount.AuthResult = {
        token: new Uint8Array([0]),
        remainTimes: 5,
        freezingTime: 0
      };
      callback.onResult(0, result);
    },
    authWithPopup: (domainAccountInfo: osAccount.DomainAccountInfo,
                    callback: osAccount.IUserAuthCallback) => {},
    authWithToken: (domainAccountInfo: osAccount.DomainAccountInfo, token: Uint8Array,
                    callback: osAccount.IUserAuthCallback) => {},
    getAccountInfo: (options: osAccount.GetDomainAccountInfoPluginOptions,
                    callback: AsyncCallback<osAccount.DomainAccountInfo>) => {},
    getAuthStatusInfo: (domainAccountInfo: osAccount.DomainAccountInfo,
                      callback: AsyncCallback<osAccount.AuthStatusInfo>) => {},
    bindAccount: (domainAccountInfo: osAccount.DomainAccountInfo, localId: number,
                  callback: AsyncCallback<void>) => {},
    unbindAccount: (domainAccountInfo: osAccount.DomainAccountInfo, callback: AsyncCallback<void>) => {},
    isAccountTokenValid: (domainAccountInfo: osAccount.DomainAccountInfo, token: Uint8Array,
                          callback: AsyncCallback<boolean>) => {},
    getAccessToken: (options: osAccount.GetDomainAccessTokenOptions, callback: AsyncCallback<Uint8Array>) => {}
  }
  osAccount.DomainAccountManager.registerPlugin(plugin);
  let userAuth = new osAccount.UserAuth();
  let challenge: Uint8Array = new Uint8Array([0]);
  let authType: osAccount.AuthType = osAccount.AuthType.DOMAIN;
  let authTrustLevel: osAccount.AuthTrustLevel = osAccount.AuthTrustLevel.ATL1;
  try {
    userAuth.auth(challenge, authType, authTrustLevel, {
      onResult: (resultCode: number, authResult: osAccount.AuthResult) => {
          console.info('auth resultCode = ' + resultCode);
          console.info('auth authResult = ' + JSON.stringify(authResult));
      }
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`auth exception = code is ${err.code}, message is ${err.message}`);
  }
  ```

### authWithPopup<sup>10+</sup>

authWithPopup(domainAccountInfo: DomainAccountInfo, callback: IUserAuthCallback): void

Authenticates a domain account in a pop-up window.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name     | Type                                   | Mandatory| Description            |
| ---------- | --------------------------------------- | ---- | --------------- |
| domainAccountInfo   | [DomainAccountInfo](#domainaccountinfo8)  | Yes  | Domain account information.|
| callback   | [IUserAuthCallback](#iuserauthcallback8)  | Yes  | Callback used to return the authentication result.|

**Example**
  ```ts
  import { AsyncCallback } from '@kit.BasicServicesKit';
  let plugin: osAccount.DomainPlugin = {
    auth: (domainAccountInfo: osAccount.DomainAccountInfo, credential: Uint8Array,
          callback: osAccount.IUserAuthCallback) => {},
    authWithPopup: (domainAccountInfo: osAccount.DomainAccountInfo,
                    callback: osAccount.IUserAuthCallback) => {
      // mock authentication
      // notify authentication result
      let result: osAccount.AuthResult = {
        token: new Uint8Array([0]),
        remainTimes: 5,
        freezingTime: 0
      };
      callback.onResult(0, result);
    },
    authWithToken: (domainAccountInfo: osAccount.DomainAccountInfo, token: Uint8Array,
                    callback: osAccount.IUserAuthCallback) => {},
    getAccountInfo: (options: osAccount.GetDomainAccountInfoPluginOptions,
                    callback: AsyncCallback<osAccount.DomainAccountInfo>) => {},
    getAuthStatusInfo: (domainAccountInfo: osAccount.DomainAccountInfo,
                        callback: AsyncCallback<osAccount.AuthStatusInfo>) => {},
    bindAccount: (domainAccountInfo: osAccount.DomainAccountInfo, localId: number,
                  callback: AsyncCallback<void>) => {},
    unbindAccount: (domainAccountInfo: osAccount.DomainAccountInfo, callback: AsyncCallback<void>) => {},
    isAccountTokenValid: (domainAccountInfo: osAccount.DomainAccountInfo, token: Uint8Array,
                          callback: AsyncCallback<boolean>) => {},
    getAccessToken: (options: osAccount.GetDomainAccessTokenOptions, callback: AsyncCallback<Uint8Array>) => {}
  }
  osAccount.DomainAccountManager.registerPlugin(plugin)
  ```

### authWithToken<sup>10+</sup>

authWithToken(domainAccountInfo: DomainAccountInfo, token: Uint8Array, callback: IUserAuthCallback): void

Authenticates a domain account by the authorization token.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name     | Type                                   | Mandatory| Description            |
| ---------- | --------------------------------------- | ---- | --------------- |
| domainAccountInfo   | [DomainAccountInfo](#domainaccountinfo8)  | Yes  | Domain account information.|
| token   | Uint8Array  | Yes  | Authorization token generated when the PIN or biometric authentication is successful.|
| callback   | [IUserAuthCallback](#iuserauthcallback8)  | Yes  | Callback used to return the authentication result.|

**Example**
  ```ts
  import { AsyncCallback } from '@kit.BasicServicesKit';
  let plugin: osAccount.DomainPlugin = {
    auth: (domainAccountInfo: osAccount.DomainAccountInfo, credential: Uint8Array,
          callback: osAccount.IUserAuthCallback) => {},
    authWithPopup: (domainAccountInfo: osAccount.DomainAccountInfo,
                    callback: osAccount.IUserAuthCallback) => {},
    authWithToken: (domainAccountInfo: osAccount.DomainAccountInfo, token: Uint8Array,
                    callback: osAccount.IUserAuthCallback) => {
      // mock authentication
      // notify authentication result
      let result: osAccount.AuthResult = {
        token: new Uint8Array([0]),
        remainTimes: 5,
        freezingTime: 0
      };
      callback.onResult(0, result);
    },
    getAccountInfo: (options: osAccount.GetDomainAccountInfoPluginOptions,
                    callback: AsyncCallback<osAccount.DomainAccountInfo>) => {},
    getAuthStatusInfo: (domainAccountInfo: osAccount.DomainAccountInfo,
                        callback: AsyncCallback<osAccount.AuthStatusInfo>) => {},
    bindAccount: (domainAccountInfo: osAccount.DomainAccountInfo, localId: number,
                  callback: AsyncCallback<void>) => {},
    unbindAccount: (domainAccountInfo: osAccount.DomainAccountInfo, callback: AsyncCallback<void>) => {},
    isAccountTokenValid: (domainAccountInfo: osAccount.DomainAccountInfo, token: Uint8Array,
                          callback: AsyncCallback<boolean>) => {},
    getAccessToken: (options: osAccount.GetDomainAccessTokenOptions, callback: AsyncCallback<Uint8Array>) => {}
  }
  osAccount.DomainAccountManager.registerPlugin(plugin)
  ```

### getAccountInfo<sup>10+</sup>

getAccountInfo(options: GetDomainAccountInfoPluginOptions, callback: AsyncCallback&lt;DomainAccountInfo&gt;): void

Obtains information about a domain account.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name     | Type                                   | Mandatory| Description            |
| ---------- | --------------------------------------- | ---- | --------------- |
| options   | [GetDomainAccountInfoPluginOptions](#getdomainaccountinfopluginoptions10)  | Yes  | Domain account information.|
| callback   | AsyncCallback&lt;[DomainAccountInfo](#domainaccountinfo8)&gt; | Yes  | Callback used to return the result.|

**Example**
  ```ts
  import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
  let plugin: osAccount.DomainPlugin = {
    auth: (domainAccountInfo: osAccount.DomainAccountInfo, credential: Uint8Array,
          callback: osAccount.IUserAuthCallback) => {},
    authWithPopup: (domainAccountInfo: osAccount.DomainAccountInfo,
                    callback: osAccount.IUserAuthCallback) => {},
    authWithToken: (domainAccountInfo: osAccount.DomainAccountInfo, token: Uint8Array,
                    callback: osAccount.IUserAuthCallback) => {},
    getAccountInfo: (options: osAccount.GetDomainAccountInfoPluginOptions,
                    callback: AsyncCallback<osAccount.DomainAccountInfo>) => {
      // mock getting account information
      // notify result
      let code: BusinessError = {
        code: 0,
        name: "",
        message: ""
      };
      let accountInfo: osAccount.DomainAccountInfo = {
        domain: options.domain ? options.domain : "",
        accountName: options.accountName,
        accountId: 'xxxx'
      };
      callback(code, accountInfo);
    },
    getAuthStatusInfo: (domainAccountInfo: osAccount.DomainAccountInfo,
                        callback: AsyncCallback<osAccount.AuthStatusInfo>) => {},
    bindAccount: (domainAccountInfo: osAccount.DomainAccountInfo, localId: number,
                  callback: AsyncCallback<void>) => {},
    unbindAccount: (domainAccountInfo: osAccount.DomainAccountInfo, callback: AsyncCallback<void>) => {},
    isAccountTokenValid: (domainAccountInfo: osAccount.DomainAccountInfo, token: Uint8Array,
                          callback: AsyncCallback<boolean>) => {},
    getAccessToken: (options: osAccount.GetDomainAccessTokenOptions, callback: AsyncCallback<Uint8Array>) => {}
  }
  osAccount.DomainAccountManager.registerPlugin(plugin)
  ```

### getAuthStatusInfo<sup>10+</sup>

getAuthStatusInfo(domainAccountInfo: DomainAccountInfo, callback: AsyncCallback&lt;AuthStatusInfo&gt;): void

Obtains the authentication status of a domain account.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name     | Type                                   | Mandatory| Description            |
| ---------- | --------------------------------------- | ---- | --------------- |
| domainAccountInfo   | [DomainAccountInfo](#domainaccountinfo8)  | Yes  | Domain account information.|
| callback   | AsyncCallback&lt;[AuthStatusInfo](#authstatusinfo10)&gt; | Yes  | Callback used to return the result.|

**Example**
  ```ts
  import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
  let plugin: osAccount.DomainPlugin = {
    auth: (domainAccountInfo: osAccount.DomainAccountInfo, credential: Uint8Array,
          callback: osAccount.IUserAuthCallback) => {},
    authWithPopup: (domainAccountInfo: osAccount.DomainAccountInfo,
                    callback: osAccount.IUserAuthCallback) => {},
    authWithToken: (domainAccountInfo: osAccount.DomainAccountInfo, token: Uint8Array,
                    callback: osAccount.IUserAuthCallback) => {},
    getAccountInfo: (options: osAccount.GetDomainAccountInfoPluginOptions,
                    callback: AsyncCallback<osAccount.DomainAccountInfo>) => {},
    getAuthStatusInfo: (domainAccountInfo: osAccount.DomainAccountInfo,
                        callback: AsyncCallback<osAccount.AuthStatusInfo>) => {
      let code: BusinessError = {
        code: 0,
        name: "",
        message: ""
      };
      let statusInfo: osAccount.AuthStatusInfo = {
        remainTimes: 5,
        freezingTime: 0
      };
      callback(code, statusInfo);
    },
    bindAccount: (domainAccountInfo: osAccount.DomainAccountInfo, localId: number,
                  callback: AsyncCallback<void>) => {},
    unbindAccount: (domainAccountInfo: osAccount.DomainAccountInfo, callback: AsyncCallback<void>) => {},
    isAccountTokenValid: (domainAccountInfo: osAccount.DomainAccountInfo, token: Uint8Array,
                          callback: AsyncCallback<boolean>) => {},
    getAccessToken: (options: osAccount.GetDomainAccessTokenOptions, callback: AsyncCallback<Uint8Array>) => {}
  }
  osAccount.DomainAccountManager.registerPlugin(plugin)
  ```

### bindAccount<sup>10+</sup>

bindAccount(domainAccountInfo: DomainAccountInfo, localId: number, callback: AsyncCallback&lt;void&gt;): void

Binds a domain account.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name     | Type                                   | Mandatory| Description            |
| ---------- | --------------------------------------- | ---- | --------------- |
| domainAccountInfo   | [DomainAccountInfo](#domainaccountinfo8)  | Yes  | Domain account information.|
| localId             | number  | Yes  | ID of the target system account.|
| callback   | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the result.|

**Example**
  ```ts
  import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
  let plugin: osAccount.DomainPlugin = {
    auth: (domainAccountInfo: osAccount.DomainAccountInfo, credential: Uint8Array,
          callback: osAccount.IUserAuthCallback) => {},
    authWithPopup: (domainAccountInfo: osAccount.DomainAccountInfo,
                    callback: osAccount.IUserAuthCallback) => {},
    authWithToken: (domainAccountInfo: osAccount.DomainAccountInfo, token: Uint8Array,
                    callback: osAccount.IUserAuthCallback) => {},
    getAccountInfo: (options: osAccount.GetDomainAccountInfoPluginOptions,
                    callback: AsyncCallback<osAccount.DomainAccountInfo>) => {},
    getAuthStatusInfo: (domainAccountInfo: osAccount.DomainAccountInfo,
                        callback: AsyncCallback<osAccount.AuthStatusInfo>) => {},
    bindAccount: (domainAccountInfo: osAccount.DomainAccountInfo, localId: number,
                  callback: AsyncCallback<void>) => {
      // mock unbinding operation
      // notify binding result
      let code: BusinessError = {
        code: 0,
        name: "",
        message: ""
      };
      callback(code);
    },
    unbindAccount: (domainAccountInfo: osAccount.DomainAccountInfo, callback: AsyncCallback<void>) => {},
    isAccountTokenValid: (domainAccountInfo: osAccount.DomainAccountInfo, token: Uint8Array,
                          callback: AsyncCallback<boolean>) => {},
    getAccessToken: (options: osAccount.GetDomainAccessTokenOptions, callback: AsyncCallback<Uint8Array>) => {}
  }
  osAccount.DomainAccountManager.registerPlugin(plugin)
  ```

### unbindAccount<sup>10+</sup>

unbindAccount(domainAccountInfo: DomainAccountInfo, callback: AsyncCallback&lt;void&gt;): void

Unbinds a domain account.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name     | Type                                   | Mandatory| Description            |
| ---------- | --------------------------------------- | ---- | --------------- |
| domainAccountInfo   | [DomainAccountInfo](#domainaccountinfo8)  | Yes  | Domain account information.|
| callback   | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the result.|

**Example**
  ```ts
  import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
  let plugin: osAccount.DomainPlugin = {
    auth: (domainAccountInfo: osAccount.DomainAccountInfo, credential: Uint8Array,
          callback: osAccount.IUserAuthCallback) => {},
    authWithPopup: (domainAccountInfo: osAccount.DomainAccountInfo,
                    callback: osAccount.IUserAuthCallback) => {},
    authWithToken: (domainAccountInfo: osAccount.DomainAccountInfo, token: Uint8Array,
                    callback: osAccount.IUserAuthCallback) => {},
    getAccountInfo: (options: osAccount.GetDomainAccountInfoPluginOptions,
                    callback: AsyncCallback<osAccount.DomainAccountInfo>) => {},
    getAuthStatusInfo: (domainAccountInfo: osAccount.DomainAccountInfo,
                        callback: AsyncCallback<osAccount.AuthStatusInfo>) => {},
    bindAccount: (domainAccountInfo: osAccount.DomainAccountInfo, localId: number,
                  callback: AsyncCallback<void>) => {},
    unbindAccount: (domainAccountInfo: osAccount.DomainAccountInfo, callback: AsyncCallback<void>) => {
      // mock unbinding operation
      // notify unbinding result
      let code: BusinessError = {
        code: 0,
        name: "",
        message: ""
      };
      callback(code);
    },
    isAccountTokenValid: (domainAccountInfo: osAccount.DomainAccountInfo, token: Uint8Array,
                          callback: AsyncCallback<boolean>) => {},
    getAccessToken: (options: osAccount.GetDomainAccessTokenOptions, callback: AsyncCallback<Uint8Array>) => {}
  }
  osAccount.DomainAccountManager.registerPlugin(plugin)
  ```

### isAccountTokenValid<sup>10+</sup>

isAccountTokenValid(domainAccountInfo: DomainAccountInfo, token: Uint8Array, callback: AsyncCallback&lt;boolean&gt;): void

Checks whether the specified domain account token is valid.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name     | Type                                   | Mandatory| Description            |
| ---------- | --------------------------------------- | ---- | --------------- |
| domainAccountInfo   | [DomainAccountInfo](#domainaccountinfo8)  | Yes  | Domain account information.|
| token | Uint8Array | Yes| Domain account token to check.|
| callback   | AsyncCallback&lt;boolean&gt; | Yes  | Callback used to return the result. The value **true** means that the specified domain account token is valid; the value **false** means the opposite.|

**Example**
  ```ts
  import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
  let plugin: osAccount.DomainPlugin = {
    auth: (domainAccountInfo: osAccount.DomainAccountInfo, credential: Uint8Array,
          callback: osAccount.IUserAuthCallback) => {},
    authWithPopup: (domainAccountInfo: osAccount.DomainAccountInfo,
                    callback: osAccount.IUserAuthCallback) => {},
    authWithToken: (domainAccountInfo: osAccount.DomainAccountInfo, token: Uint8Array,
                    callback: osAccount.IUserAuthCallback) => {},
    getAccountInfo: (options: osAccount.GetDomainAccountInfoPluginOptions,
                    callback: AsyncCallback<osAccount.DomainAccountInfo>) => {},
    getAuthStatusInfo: (domainAccountInfo: osAccount.DomainAccountInfo,
                        callback: AsyncCallback<osAccount.AuthStatusInfo>) => {},
    bindAccount: (domainAccountInfo: osAccount.DomainAccountInfo, localId: number,
                  callback: AsyncCallback<void>) => {},
    unbindAccount: (domainAccountInfo: osAccount.DomainAccountInfo, callback: AsyncCallback<void>) => {},
    isAccountTokenValid: (domainAccountInfo: osAccount.DomainAccountInfo, token: Uint8Array,
                          callback: AsyncCallback<boolean>) => {
      // mock checking operation
      // notify checking result
      let code: BusinessError = {
        code: 0,
        name: "",
        message: ""
      };
      callback(code, true);
    },
    getAccessToken: (options: osAccount.GetDomainAccessTokenOptions, callback: AsyncCallback<Uint8Array>) => {}
  }
  osAccount.DomainAccountManager.registerPlugin(plugin)
  ```

### getAccessToken<sup>10+</sup>

getAccessToken(options: GetDomainAccessTokenOptions, callback: AsyncCallback&lt;Uint8Array&gt;): void

Obtains the domain access token based on the specified conditions.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name     | Type                                   | Mandatory| Description            |
| ---------- | --------------------------------------- | ---- | --------------- |
| options | [GetDomainAccessTokenOptions](#getdomainaccesstokenoptions10)  | Yes  | Options specified for obtaining the domain access token.|
| callback   | AsyncCallback&lt;Uint8Array&gt; | Yes  | Callback used to return the result.|

**Example**
  ```ts
  import { AsyncCallback, BusinessError } from '@kit.BasicServicesKit';
  let plugin: osAccount.DomainPlugin = {
    auth: (domainAccountInfo: osAccount.DomainAccountInfo, credential: Uint8Array,
          callback: osAccount.IUserAuthCallback) => {},
    authWithPopup: (domainAccountInfo: osAccount.DomainAccountInfo,
                    callback: osAccount.IUserAuthCallback) => {},
    authWithToken: (domainAccountInfo: osAccount.DomainAccountInfo, token: Uint8Array,
                    callback: osAccount.IUserAuthCallback) => {},
    getAccountInfo: (options: osAccount.GetDomainAccountInfoPluginOptions,
                    callback: AsyncCallback<osAccount.DomainAccountInfo>) => {},
    getAuthStatusInfo: (domainAccountInfo: osAccount.DomainAccountInfo,
                        callback: AsyncCallback<osAccount.AuthStatusInfo>) => {},
    bindAccount: (domainAccountInfo: osAccount.DomainAccountInfo, localId: number,
                  callback: AsyncCallback<void>) => {},
    unbindAccount: (domainAccountInfo: osAccount.DomainAccountInfo, callback: AsyncCallback<void>) => {},
    isAccountTokenValid: (domainAccountInfo: osAccount.DomainAccountInfo, token: Uint8Array,
                          callback: AsyncCallback<boolean>) => {},
    getAccessToken: (options: osAccount.GetDomainAccessTokenOptions, callback: AsyncCallback<Uint8Array>) => {
      // mock getting operation
      // notify result
      let code: BusinessError = {
        code: 0,
        name: "",
        message: ""
      };
      let token: Uint8Array = new Uint8Array([0]);
      callback(code, token);
    }
  }
  osAccount.DomainAccountManager.registerPlugin(plugin)
  ```

## DomainAccountManager <sup>9+</sup>
Provides APIs for domain account management.

### registerPlugin<sup>9+</sup>

static registerPlugin(plugin: DomainPlugin): void

Registers a domain plug-in.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Required permissions**: ohos.permission.MANAGE_LOCAL_ACCOUNTS

**Parameters**

| Name   | Type                    | Mandatory| Description                     |
| ----------| ----------------------- | --- | -------------------------- |
| plugin   | [DomainPlugin](#domainplugin9)  | Yes | Domain plug-in to register.|

**Error codes**

| ID| Error Message                    |
| -------- | --------------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 801 | Capability not supported.|
| 12300201 | The domain plugin has been registered. |

**Example**
  ```ts
  import { AsyncCallback } from '@kit.BasicServicesKit';
  let plugin: osAccount.DomainPlugin = {
    auth: (domainAccountInfo: osAccount.DomainAccountInfo, credential: Uint8Array,
         callback: osAccount.IUserAuthCallback) => {},
    authWithPopup: (domainAccountInfo: osAccount.DomainAccountInfo,
                  callback: osAccount.IUserAuthCallback) => {},
    authWithToken: (domainAccountInfo: osAccount.DomainAccountInfo, token: Uint8Array,
                  callback: osAccount.IUserAuthCallback) => {},
    getAccountInfo: (options: osAccount.GetDomainAccountInfoPluginOptions,
                   callback: AsyncCallback<osAccount.DomainAccountInfo>) => {},
    getAuthStatusInfo: (domainAccountInfo: osAccount.DomainAccountInfo,
                        callback: AsyncCallback<osAccount.AuthStatusInfo>) => {},
    bindAccount: (domainAccountInfo: osAccount.DomainAccountInfo, localId: number,
                  callback: AsyncCallback<void>) => {},
    unbindAccount: (domainAccountInfo: osAccount.DomainAccountInfo, callback: AsyncCallback<void>) => {},
    isAccountTokenValid: (domainAccountInfo: osAccount.DomainAccountInfo, token: Uint8Array,
                        callback: AsyncCallback<boolean>) => {},
    getAccessToken: (options: osAccount.GetDomainAccessTokenOptions, callback: AsyncCallback<Uint8Array>) => {}
  }
  try {
    osAccount.DomainAccountManager.registerPlugin(plugin);
    console.info('registerPlugin success.');
  } catch(err) {
    console.error(`registerPlugin code is ${err.code}, message is ${err.message}`);
  }
  ```

### unregisterPlugin<sup>9+</sup>

static unregisterPlugin(): void

Unregisters this domain plug-in.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Required permissions**: ohos.permission.MANAGE_LOCAL_ACCOUNTS

**Error codes**

| ID| Error Message                    |
| -------- | --------------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 801 | Capability not supported.|

**Example**
  ```ts
  try {
    osAccount.DomainAccountManager.unregisterPlugin();
    console.info('unregisterPlugin success.');
  } catch(err) {
    console.error(`unregisterPlugin code is ${err.code}, message is ${err.message}`);
  }
  ```

### auth<sup>10+</sup>

auth(domainAccountInfo: DomainAccountInfo, credential: Uint8Array, callback: IUserAuthCallback): void

Authenticates a domain account.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Required permissions**: ohos.permission.ACCESS_USER_AUTH_INTERNAL

**Parameters**

| Name     | Type                                   | Mandatory| Description            |
| ---------- | --------------------------------------- | ---- | --------------- |
| domainAccountInfo   | [DomainAccountInfo](#domainaccountinfo8)  | Yes  | Domain account information.|
| credential   | Uint8Array  | Yes  | Credentials of the domain account.|
| callback   | [IUserAuthCallback](#iuserauthcallback8)  | Yes  | Callback used to return the authentication result.|

**Error codes**

| ID| Error Message                    |
| -------- | --------------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 801 | Capability not supported.|
| 12300001 | The system service works abnormally. |
| 12300002 | Invalid domainAccountInfo or credential. |
| 12300003 | Domain account does not exist. |
| 12300013 | Network exception. |
| 12300101 | Authentication failed. |
| 12300109 | The authentication, enrollment, or update operation is canceled. |
| 12300110 | The authentication is locked. |
| 12300111 | The authentication time out. |
| 12300112 | The authentication service is busy. |
| 12300113 | The account authentication service does not exist. |
| 12300114 | The account authentication service works abnormally. |
| 12300211 | Server unreachable. |

**Example**
  ```ts
  let domainAccountInfo: osAccount.DomainAccountInfo = {
    domain: 'CHINA',
    accountName: 'zhangsan'
  }
  let credential = new Uint8Array([0])
  try {
    osAccount.DomainAccountManager.auth(domainAccountInfo, credential, {
      onResult: (resultCode: number, authResult: osAccount.AuthResult) => {
        console.info('auth resultCode = ' + resultCode);
        console.info('auth authResult = ' + JSON.stringify(authResult));
      }
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`auth exception = code is ${err.code}, message is ${err.message}`);
  }
  ```

### authWithPopup<sup>10+</sup>

authWithPopup(callback: IUserAuthCallback): void

Authenticates this domain account with a dialog box.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Required permissions**: ohos.permission.ACCESS_USER_AUTH_INTERNAL

No permission is required since API version 11. Use the SDK of the latest version.

**Parameters**

| Name     | Type                                   | Mandatory| Description            |
| ---------- | --------------------------------------- | ---- | --------------- |
| callback   | [IUserAuthCallback](#iuserauthcallback8)  | Yes  | Callback used to return the authentication result.|

**Error codes**

| ID| Error Message                    |
| -------- | --------------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 801 | Capability not supported.|
| 12300001 | The system service works abnormally. |
| 12300003 | No domain account is bound. |
| 12300013 | Network exception. |
| 12300101 | Authentication failed. |
| 12300109 | The authentication, enrollment, or update operation is canceled. |
| 12300110 | The authentication is locked. |
| 12300111 | The authentication time out. |
| 12300112 | The authentication service is busy. |
| 12300113 | The account authentication service does not exist. |
| 12300114 | The account authentication service works abnormally. |
| 12300211 | Server unreachable. |

**Example**
  ```ts
  try {
    osAccount.DomainAccountManager.authWithPopup({
      onResult: (resultCode: number, authResult: osAccount.AuthResult) => {
        console.info('auth resultCode = ' + resultCode);
        console.info('auth authResult = ' + JSON.stringify(authResult));
      }
    })
  } catch (e) {
    const err = e as BusinessError;
    console.error(`auth exception = code is ${err.code}, message is ${err.message}`);
  }
  ```

### authWithPopup<sup>10+</sup>

authWithPopup(localId: number, callback: IUserAuthCallback): void

Authenticates this domain account with a dialog box.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Required permissions**: ohos.permission.ACCESS_USER_AUTH_INTERNAL

No permission is required since API version 11. Use the SDK of the latest version.

**Parameters**

| Name     | Type                                   | Mandatory| Description            |
| ---------- | --------------------------------------- | ---- | --------------- |
| localId   | number  | Yes  | Local ID of the system account bound to the domain account.|
| callback   | [IUserAuthCallback](#iuserauthcallback8)  | Yes  | Callback used to return the authentication result.|

**Error codes**

| ID| Error Message                    |
| -------- | --------------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 801 | Capability not supported.|
| 12300001 | The system service works abnormally. |
| 12300002 | Invalid localId. |
| 12300003 | No domain account is bound. |
| 12300013 | Network exception. |
| 12300101 | Authentication failed. |
| 12300109 | The authentication, enrollment, or update operation is canceled. |
| 12300110 | The authentication is locked. |
| 12300111 | The authentication time out. |
| 12300112 | The authentication service is busy. |
| 12300113 | The account authentication service does not exist. |
| 12300114 | The account authentication service works abnormally. |
| 12300211 | Server unreachable. |

**Example**
  ```ts
  try {
    osAccount.DomainAccountManager.authWithPopup(100, {
      onResult: (resultCode: number, authResult: osAccount.AuthResult) => {
        console.info('authWithPopup resultCode = ' + resultCode);
        console.info('authWithPopup authResult = ' + JSON.stringify(authResult));
      }
    })
  } catch (e) {
    const err = e as BusinessError;
    console.error(`authWithPopup exception = code is ${err.code}, message is ${err.message}`);
  }
  ```

### hasAccount<sup>10+</sup>

hasAccount(domainAccountInfo: DomainAccountInfo, callback: AsyncCallback&lt;boolean&gt;): void

Checks whether a domain account exists.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Required permissions**: ohos.permission.MANAGE_LOCAL_ACCOUNTS

**Parameters**

| Name     | Type                                   | Mandatory| Description            |
| ---------- | --------------------------------------- | ---- | --------------- |
| domainAccountInfo   | [DomainAccountInfo](#domainaccountinfo8)  | Yes  | Domain account information.|
| callback   | AsyncCallback&lt;boolean&gt;  | Yes  | Callback used to return the result. The value **true** means that the specified domain account exists; the value **false** means the opposite.|

**Error codes**

| ID| Error Message                    |
| -------- | --------------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 801 | Capability not supported.|
| 12300001 | The system service works abnormally. |
| 12300002 | Invalid domainAccountInfo. |
| 12300013 | Network exception. |
| 12300014 | Not authenticated. |
| 12300111 | The operation time out. |
| 12300114 | The authentication service works abnormally. |
| 12300211 | Server unreachable. |

**Example**
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let domainAccountInfo: osAccount.DomainAccountInfo = {
    domain: 'CHINA',
    accountName: 'zhangsan'
  }
  try {
    osAccount.DomainAccountManager.hasAccount(domainAccountInfo, (err: BusinessError, result: boolean) => {
      if (err) {
        console.error(`call hasAccount failed, code is ${err.code}, message is ${err.message}`);
      } else {
        console.info('hasAccount result: ' + result);
      }
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`hasAccount exception = code is ${err.code}, message is ${err.message}`);
  }
  ```

### hasAccount<sup>10+</sup>

hasAccount(domainAccountInfo: DomainAccountInfo): Promise&lt;boolean&gt;

Checks whether a domain account exists.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Required permissions**: ohos.permission.MANAGE_LOCAL_ACCOUNTS

**Parameters**

| Name     | Type                                   | Mandatory| Description            |
| ---------- | --------------------------------------- | ---- | --------------- |
| domainAccountInfo   | [DomainAccountInfo](#domainaccountinfo8)  | Yes  | Domain account information.|

**Return value**

| Type                     | Description                    |
| :------------------------ | ----------------------- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** means that the specified domain account exists; the value **false** means the opposite.|

**Error codes**

| ID| Error Message                    |
| -------- | --------------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 801 | Capability not supported.|
| 12300001 | The system service works abnormally. |
| 12300002 | Invalid domainAccountInfo. |
| 12300013 | Network exception. |
| 12300014 | Not authenticated. |
| 12300111 | The operation time out. |
| 12300114 | The authentication service works abnormally. |
| 12300211 | Server unreachable. |

**Example**
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let domainAccountInfo: osAccount.DomainAccountInfo = {
    domain: 'CHINA',
    accountName: 'zhangsan'
  }
  try {
    osAccount.DomainAccountManager.hasAccount(domainAccountInfo).then((result: boolean) => {
      console.info('hasAccount result: ' + result);
    }).catch((err: BusinessError) => {
        console.error(`call hasAccount failed, code is ${err.code}, message is ${err.message}`);
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`hasAccount exception = code is ${err.code}, message is ${err.message}`);
  }
  ```

### updateAccountToken<sup>10+</sup>

updateAccountToken(domainAccountInfo: DomainAccountInfo, token: Uint8Array, callback: AsyncCallback&lt;void&gt;): void

Updates the token of a domain account. An empty token means an invalid token. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Required permissions**: ohos.permission.MANAGE_LOCAL_ACCOUNTS

**Parameters**

| Name     | Type                                   | Mandatory| Description            |
| ---------- | --------------------------------------- | ---- | --------------- |
| domainAccountInfo | [DomainAccountInfo](#domainaccountinfo8)  | Yes  | Domain account information.|
| token | Uint8Array  | Yes  | New domain account token.|
| callback | AsyncCallback&lt;void&gt; | Yes| Callback used to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object.|

**Error codes**

| ID| Error Message                    |
| -------- | --------------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | The system service works abnormally. |
| 12300002 | Invalid token. |
| 12300003 | Account not found. |

**Example**
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let domainAccountInfo: osAccount.DomainAccountInfo = {
    domain: 'CHINA',
    accountName: 'zhangsan',
    accountId: '123456'
  }
  let token = new Uint8Array([0])
  try {
    osAccount.DomainAccountManager.updateAccountToken(domainAccountInfo, token, (err: BusinessError) => {
      if (err != null) {
        console.error(`updateAccountToken failed, code is ${err.code}, message is ${err.message}`);
      } else {
        console.info('updateAccountToken successfully');
      }
    })
  } catch (e) {
    const err = e as BusinessError;
    console.error(`updateAccountToken exception = code is ${err.code}, message is ${err.message}`);
  }
  ```

### updateAccountToken<sup>10+</sup>

updateAccountToken(domainAccountInfo: DomainAccountInfo, token: Uint8Array): Promise&lt;void&gt;

Updates the token of a domain account. An empty token means an invalid token. This API uses a promise to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Required permissions**: ohos.permission.MANAGE_LOCAL_ACCOUNTS

**Parameters**

| Name     | Type                                   | Mandatory| Description            |
| ---------- | --------------------------------------- | ---- | --------------- |
| domainAccountInfo | [DomainAccountInfo](#domainaccountinfo8)  | Yes  | Domain account information.|
| token | Uint8Array  | Yes  | New domain account token.|

**Return value**

| Type                     | Description                    |
| :------------------------ | ----------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

| ID| Error Message                    |
| -------- | --------------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | The system service works abnormally. |
| 12300002 | Invalid token. |
| 12300003 | Account not found. |

**Example**
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let domainAccountInfo: osAccount.DomainAccountInfo = {
    domain: 'CHINA',
    accountName: 'zhangsan',
    accountId: '123456'
  }
  let token = new Uint8Array([0])
  try {
    osAccount.DomainAccountManager.updateAccountToken(domainAccountInfo, token).then(() => {
      console.info('updateAccountToken successfully');
    }).catch((err: BusinessError) => {
        console.error(`updateAccountToken failed, code is ${err.code}, message is ${err.message}`);
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`updateAccountToken exception = code is ${err.code}, message is ${err.message}`);
  }
  ```

### getAccountInfo<sup>10+</sup>

getAccountInfo(options: GetDomainAccountInfoOptions, callback: AsyncCallback&lt;DomainAccountInfo&gt;): void

Obtains information about a specified domain account. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Required permissions**: ohos.permission.GET_DOMAIN_ACCOUNTS

**Parameters**

| Name     | Type                                   | Mandatory| Description            |
| ---------- | --------------------------------------- | ---- | --------------- |
| options   | [GetDomainAccountInfoOptions](#getdomainaccountinfooptions10)  | Yes  | Domain account information.|
| callback   | AsyncCallback&lt;DomainAccountInfo&gt;  | Yes  | Callback used to return the result.|

**Error codes**

| ID| Error Message                    |
| -------- | --------------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 801 | Capability not supported.|
| 12300001 | The system service works abnormally. |
| 12300003 | Account not found. |
| 12300013 | Network exception. |
| 12300014 | Not authenticated. |
| 12300111 | The operation time out. |
| 12300114 | The authentication service works abnormally. |
| 12300211 | Server unreachable. |

**Example**
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let domainAccountInfo: osAccount.GetDomainAccountInfoOptions = {
    domain: 'CHINA',
    accountName: 'zhangsan'
  }
  try {
    osAccount.DomainAccountManager.getAccountInfo(domainAccountInfo,
      (err: BusinessError, result: osAccount.DomainAccountInfo) => {
      if (err) {
        console.error(`call getAccountInfo failed, code is ${err.code}, message is ${err.message}`);
      } else {
        console.info('getAccountInfo result: ' + result);
      }
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`getAccountInfo exception = code is ${err.code}, message is ${err.message}`);
  }
  ```

### getAccountInfo<sup>10+</sup>

getAccountInfo(options: GetDomainAccountInfoOptions): Promise&lt;DomainAccountInfo&gt;

Obtains information about a specified domain account. This API uses a promise to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Required permissions**: ohos.permission.GET_DOMAIN_ACCOUNTS

**Parameters**

| Name     | Type                                   | Mandatory| Description            |
| ---------- | --------------------------------------- | ---- | --------------- |
| options   | [GetDomainAccountInfoOptions](#getdomainaccountinfooptions10)  | Yes  | Domain account information.|

**Return value**

| Type                     | Description                    |
| :------------------------ | ----------------------- |
| Promise&lt;DomainAccountInfo&gt; | Promise used to return the domain account information obtained.|

**Error codes**

| ID| Error Message                    |
| -------- | --------------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 801 | Capability not supported.|
| 12300001 | The system service works abnormally. |
| 12300003 | Account not found. |
| 12300013 | Network exception. |
| 12300014 | Not authenticated. |
| 12300111 | The operation time out. |
| 12300114 | The authentication service works abnormally. |
| 12300211 | Server unreachable. |

**Example**
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let domainAccountInfo: osAccount.GetDomainAccountInfoOptions = {
    domain: 'CHINA',
    accountName: 'zhangsan'
  }
  try {
    osAccount.DomainAccountManager.getAccountInfo(domainAccountInfo)
      .then((result: osAccount.DomainAccountInfo) => {
      console.info('getAccountInfo result: ' + result);
    }).catch((err: BusinessError) => {
      console.error(`call getAccountInfo failed, code is ${err.code}, message is ${err.message}`);
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`getAccountInfo exception = code is ${err.code}, message is ${err.message}`);
  }
  ```

### getAccessToken<sup>11+</sup>

getAccessToken(businessParams: Record<string, Object>, callback: AsyncCallback&lt;Uint8Array&gt;): void

Obtains the service access token of this domain account. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name     | Type                                   | Mandatory| Description            |
| ---------- | --------------------------------------- | ---- | --------------- |
| businessParams | Record<string, Object>  | Yes  | Service parameters. The specific formats vary depending on the domain plug-in.|
| callback | AsyncCallback&lt;Uint8Array&gt;  | Yes  | Callback used to return the result. If the operation is successful, **err** is **null**. Otherwise, an error object is returned.|

**Error codes**

| ID| Error Message                    |
| -------- | --------------------------- |
| 202 | Not system application.|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 801 | Capability not supported.|
| 12300001 | The system service works abnormally. |
| 12300002 | Invalid business parameters. |
| 12300003 | Domain account not found. |
| 12300013 | Network exception. |
| 12300014 | The domain account is not authenticated. |
| 12300111 | The operation time out. |
| 12300114 | The authentication service works abnormally. |
| 12300211 | Server unreachable. |

**Example**
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let businessParams: Record<string, Object> = {
    'clientId': 'xxx',
    'secretId': 'yyy'
  };  // depends on the implementation of the domain plugin
  try {
    osAccount.DomainAccountManager.getAccessToken(businessParams,
      (err: BusinessError, result: Uint8Array) => {
      if (err) {
        console.error(`getAccessToken failed, code is ${err.code}, message is ${err.message}`);
      } else {
        console.info('getAccessToken result: ' + result);
      }
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`getAccessToken exception = code is ${err.code}, message is ${err.message}`);
  }
  ```

### getAccessToken<sup>11+</sup>

getAccessToken(businessParams: Record<string, Object>): Promise&lt;Uint8Array&gt;

Obtains the service access token of this domain account. This API uses a promise to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name     | Type                                   | Mandatory| Description            |
| ---------- | --------------------------------------- | ---- | --------------- |
| businessParams | Record<string, Object> | Yes  | Service parameters. The specific formats vary depending on the domain plug-in.|

**Return value**

| Type                     | Description                    |
| :------------------------ | ----------------------- |
| Promise&lt;Uint8Array&gt; | Promise used to return the service access token obtained.|

**Error codes**

| ID| Error Message                    |
| -------- | --------------------------- |
| 202 | Not system application.|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 801 | Capability not supported.|
| 12300001 | The system service works abnormally. |
| 12300002 | Invalid business parameters. |
| 12300003 | Domain account not found. |
| 12300013 | Network exception. |
| 12300014 | The domain account is not authenticated. |
| 12300111 | The operation time out. |
| 12300114 | The authentication service works abnormally. |
| 12300211 | Server unreachable. |

**Example**
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let businessParams: Record<string, Object> = {
    'clientId': 'xxx',
    'secretId': 'yyy'
  };  // depends on the implementation of the domain plugin
  try {
    osAccount.DomainAccountManager.getAccessToken(businessParams)
      .then((result: Uint8Array) => {
      console.info('getAccessToken result: ' + result);
    }).catch((err: BusinessError) => {
      console.error(`getAccessToken failed, code is ${err.code}, message is ${err.message}`);
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`getAccessToken exception = code is ${err.code}, message is ${err.message}`);
  }
  ```

### isAuthenticationExpired<sup>12+</sup>

isAuthenticationExpired(domainAccountInfo: DomainAccountInfo): Promise&lt;boolean&gt;;

Checks whether the authentication of a domain account has expired. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MANAGE_LOCAL_ACCOUNTS or ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name     | Type                                   | Mandatory| Description            |
| ---------- | --------------------------------------- | ---- | --------------- |
| domainAccountInfo   | [DomainAccountInfo](#domainaccountinfo8)  | Yes  | Domain account information.|

**Return value**

| Type                     | Description                    |
| :------------------------ | ----------------------- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** means that the specified domain account has expired; the value **false** means the opposite.|

**Error codes**

| ID| Error Message                    |
| -------- | --------------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 801 | Capability not supported.|
| 12300001 | The system service works abnormally. |
| 12300003 | Domain account not found. |

**Example**
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let domainInfo: osAccount.DomainAccountInfo =
    {domain: 'testDomain', accountName: 'testAccountName'};
  try {
    osAccount.DomainAccountManager.isAuthenticationExpired(domainInfo).then((result: boolean) => {
      console.info('isAuthenticationExpired, result: ' + result);
    }).catch((err: BusinessError) => {
      console.error('isAuthenticationExpired err: ' + err);
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error('isAuthenticationExpired exception: ' + e);
  }
  ```

## UserIdentityManager<sup>8+</sup>

Provides APIs for user IDM.

**System API**: This is a system API.

### constructor<sup>8+</sup>

 

A **constructor()** used to create an instance for user IDM.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Error codes**

| ID| Error Message                    |
| -------- | --------------------------- |
| 202 | Not system application.|

**Example**
  ```ts
  let userIDM = new osAccount.UserIdentityManager();
  ```

### openSession<sup>8+</sup>

openSession(callback: AsyncCallback&lt;Uint8Array&gt;): void

Opens a session to obtain the challenge value. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Required permissions**: ohos.permission.MANAGE_USER_IDM

**Parameters**

| Name   | Type                            | Mandatory| Description                                                           |
| -------- | -------------------------------- | ---- | -------------------------------------------------------------- |
| callback | AsyncCallback&lt;Uint8Array&gt;  | Yes  | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is the challenge value obtained. Otherwise, **err** is an error object.|

**Error codes**

| ID| Error Message                    |
| -------- | --------------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | The system service works abnormally. |

**Example**
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let userIDM = new osAccount.UserIdentityManager();
  try {
    userIDM.openSession((err: BusinessError, challenge: Uint8Array) => {
      if (err) {
        console.error(`openSession exception = code is ${err.code}, message is ${err.message}`);
      } else {
        console.info('openSession challenge = ' + JSON.stringify(challenge));
      }
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`openSession exception = code is ${err.code}, message is ${err.message}`);
  }
  ```

### openSession<sup>8+</sup>

openSession(accountId?: number): Promise&lt;Uint8Array&gt;

Opens a session. This API returns a challenge value, which can be used to determine whether the subsequent identity authentication is in this session. This can prevent replay attacks. This API uses a promise to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Required permissions**: ohos.permission.MANAGE_USER_IDM

**Parameters**

| Name    | Type   | Mandatory| Description       |
| --------- | ------- | ---- | ----------- |
| accountId<sup>12+</sup> | number  | No  | System account ID, which is left blank by default.|

**Return value**

| Type                     | Description                    |
| :------------------------ | ----------------------- |
| Promise&lt;Uint8Array&gt; | Promise used to return the challenge value obtained.|

**Error codes**

| ID| Error Message                    |
| -------- | --------------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 | Parameter error. Possible causes: Incorrect parameter types. |
| 12300001 | The system service works abnormally. |
| 12300003 | Account not found. |
| 12300008 | Restricted account. |

**Example**
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let userIDM = new osAccount.UserIdentityManager();
  let accountId = 100;
  try {
    userIDM.openSession(accountId).then((challenge: Uint8Array) => {
        console.info('openSession challenge = ' + JSON.stringify(challenge));
    }).catch((err: BusinessError) => {
        console.error(`openSession error = code is ${err.code}, message is ${err.message}`);
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`openSession exception = code is ${err.code}, message is ${err.message}`);
  }
  ```

### addCredential<sup>8+</sup>

addCredential(credentialInfo: CredentialInfo, callback: IIdmCallback): void

Adds credential information, including the credential type, subtype, and token (if a non-PIN credential is added).

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Required permissions**: ohos.permission.MANAGE_USER_IDM

**Parameters**

| Name          | Type                                | Mandatory| Description                       |
| --------------- | ------------------------------------ | --- | ---------------------------- |
| credentialInfo  | [CredentialInfo](#credentialinfo8)   | Yes | Credential information to add.               |
| callback        | [IIdmCallback](#iidmcallback8)       | Yes | Callback used to return the result. |

**Error codes**

| ID| Error Message                    |
| -------- | ------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | The system service works abnormally. |
| 12300002 | Invalid credentialInfo, i.e. authType or authSubType. |
| 12300003 | Account not found. |
| 12300008 | Restricted account. |
| 12300101 | The token is invalid. |
| 12300106 | The authentication type is not supported. |
| 12300109 | The authentication, enrollment, or update operation is canceled. |
| 12300111 | The operation time out. |
| 12300115 | The number of credentials reaches the upper limit. |
| 12300116 | Credential complexity verification failed. |

**Example**
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let password: Uint8Array = new Uint8Array([0, 0, 0, 0, 0, 0]);
  let pinAuth: osAccount.PINAuth = new osAccount.PINAuth();
  pinAuth.registerInputer({
    onGetData: (authSubType: osAccount.AuthSubType, callback: osAccount.IInputData) => {
      callback.onSetData(authSubType, password);
    }
  });
  let credentialInfo: osAccount.CredentialInfo = {
    credType: osAccount.AuthType.PIN,
    credSubType: osAccount.AuthSubType.PIN_SIX,
    token: new Uint8Array([]),
  };
  let userIDM = new osAccount.UserIdentityManager();
  userIDM.openSession((err: BusinessError, challenge: Uint8Array) => {
    try {
    userIDM.addCredential(credentialInfo, {
      onResult: (result: number, extraInfo: osAccount.RequestResult) => {
        console.info('addCredential result = ' + result);
        console.info('addCredential extraInfo = ' + extraInfo);
      }
    });
    } catch (e) {
      const err = e as BusinessError;
      console.error(`addCredential exception = code is ${err.code}, message is ${err.message}`);
    }
  });
  ```

### updateCredential<sup>8+</sup>

updateCredential(credentialInfo: CredentialInfo, callback: IIdmCallback): void

Updates credential information. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Required permissions**: ohos.permission.MANAGE_USER_IDM

**Parameters**

| Name          | Type                                 | Mandatory| Description                    |
| --------------- | ------------------------------------- | --- | ------------------------- |
| credentialInfo  | [CredentialInfo](#credentialinfo8)    | Yes | Credential information to add.            |
| callback        | [IIdmCallback](#iidmcallback8)        | Yes | Callback used to return the result.|

**Error codes**

| ID| Error Message                    |
| -------- | ------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | The system service works abnormally. |
| 12300002 | Invalid credentialInfo, i.e. authType or authSubType. |
| 12300003 | Account not found. |
| 12300101 | The token is invalid. |
| 12300102 | The credential does not exist. |
| 12300106 | The authentication type is not supported. |
| 12300109 | The authentication, enrollment, or update operation is canceled. |
| 12300111 | The operation time out. |
| 12300116 | Credential complexity verification failed. |

**Example**
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let userIDM = new osAccount.UserIdentityManager();
  let userAuth: osAccount.UserAuth = new osAccount.UserAuth();
  let pinAuth: osAccount.PINAuth = new osAccount.PINAuth();
  let password: Uint8Array = new Uint8Array([0, 0, 0, 0, 0, 0]);
  let credentialInfo: osAccount.CredentialInfo = {
    credType: osAccount.AuthType.PIN,
    credSubType: osAccount.AuthSubType.PIN_SIX,
    token: new Uint8Array([]),
  };
  pinAuth.registerInputer({
    onGetData: (authSubType: osAccount.AuthSubType, callback: osAccount.IInputData) => {
      callback.onSetData(authSubType, password);
    }
  });
  userIDM.openSession((err: BusinessError, challenge: Uint8Array) => {
    userAuth.auth(challenge, credentialInfo.credType, osAccount.AuthTrustLevel.ATL1, {
      onResult: (result: number, extraInfo: osAccount.AuthResult) => {
        if (result != osAccount.ResultCode.SUCCESS) {
          return;
        }
        if (extraInfo.token != null) {
          credentialInfo.token = extraInfo.token;
        }
        try {
          userIDM.updateCredential(credentialInfo, {
            onResult: (result: number, extraInfo: osAccount.RequestResult) => {
                console.info('updateCredential result = ' + result);
                console.info('updateCredential extraInfo = ' + extraInfo);
            }
          });
        } catch (e) {
          const err = e as BusinessError;
          console.error(`updateCredential exception = code is ${err.code}, message is ${err.message}`);
        }
      }
    });
  });
  ```

### closeSession<sup>8+</sup>

closeSession(accountId?: number): void

Closes this session to terminate IDM.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Required permissions**: ohos.permission.MANAGE_USER_IDM

**Parameters**

| Name    | Type   | Mandatory| Description       |
| --------- | ------- | ---- | ----------- |
| accountId<sup>12+</sup> | number  | No  | System account ID, which is left blank by default.|

**Error codes**

| ID| Error Message                    |
| -------- | --------------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 | Parameter error. Possible causes: Incorrect parameter types. |
| 12300001 | The system service works abnormally. |
| 12300003 | Account not found. |
| 12300008 | Restricted account. |

**Example**
  ```ts
  let userIDM = new osAccount.UserIdentityManager();
  let accountId = 100;
  userIDM.closeSession(accountId);
  ```

### cancel<sup>8+</sup>

cancel(challenge: Uint8Array): void

Cancels an entry based on the challenge value.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Required permissions**: ohos.permission.MANAGE_USER_IDM

**Parameters**

| Name   | Type       | Mandatory| Description  |
| -------- | ----------- | ---- | ----- |
| challenge | Uint8Array | Yes  | Challenge value.|

**Error codes**

| ID| Error Message           |
| -------- | ------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | The system service works abnormally. |
| 12300002 | Invalid challenge. |

**Example**
  ```ts
  let userIDM = new osAccount.UserIdentityManager();
  let challenge: Uint8Array = new Uint8Array([0]);
  try {
    userIDM.cancel(challenge);
  } catch(err) {
    console.error(`cancel code is ${err.code}, message is ${err.message}`);
  }
  ```

### delUser<sup>8+</sup>

delUser(token: Uint8Array, callback: IIdmCallback): void

Deletes a user based on the authentication token. This API uses a callback to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Required permissions**: ohos.permission.MANAGE_USER_IDM

**Parameters**

| Name   | Type                          | Mandatory| Description                     |
| -------- | ------------------------------ | --- | ------------------------- |
| token    | Uint8Array                     | Yes | Authentication token.            |
| callback | [IIdmCallback](#iidmcallback8) | Yes | Callback used to return the result.|

**Error codes**

| ID| Error Message       |
| -------- | ------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | The system service works abnormally. |
| 12300101 | The token is invalid. |

**Example**
  ```ts
  let userIDM = new osAccount.UserIdentityManager();
  let token: Uint8Array = new Uint8Array([0]);
  try {
    userIDM.delUser(token, {
      onResult: (result: number, extraInfo: osAccount.RequestResult) => {
        console.info('delUser result = ' + result);
        console.info('delUser extraInfo = ' + JSON.stringify(extraInfo));
      }
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`delUser exception = code is ${err.code}, message is ${err.message}`);
  }
  ```

### delCred<sup>8+</sup>

delCred(credentialId: Uint8Array, token: Uint8Array, callback: IIdmCallback): void

Deletes user credential information.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Required permissions**: ohos.permission.MANAGE_USER_IDM

**Parameters**

| Name          | Type                                           | Mandatory| Description                     |
| --------------- | ----------------------------------- | --- | ---------------------------|
| credentialId    | Uint8Array                          | Yes | Credential ID.                 |
| token           | Uint8Array                          | Yes | Authentication token.              |
| callback        | [IIdmCallback](#iidmcallback8)      | Yes | Callback used to return the result.|

**Error codes**

| ID| Error Message            |
| -------- | ------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | The system service works abnormally. |
| 12300002 | Invalid credentialId. |
| 12300101 | The token is invalid. |
| 12300102 | The credential does not exist. |

**Example**
  ```ts
  let userIDM = new osAccount.UserIdentityManager();
  let credentialId: Uint8Array = new Uint8Array([0, 0, 0, 0, 0, 0, 0, 0]);
  let token: Uint8Array = new Uint8Array([0]);
  try {
    userIDM.delCred(credentialId, token, {
      onResult: (result: number, extraInfo: osAccount.RequestResult) => {
          console.info('delCred result = ' + result);
          console.info('delCred extraInfo = ' + JSON.stringify(extraInfo));
      }
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`delCred exception = code is ${err.code}, message is ${err.message}`);
  }
  ```

### getAuthInfo<sup>8+</sup>

getAuthInfo(callback: AsyncCallback&lt;Array&lt;EnrolledCredInfo&gt;&gt;): void

Obtains authentication information. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Required permissions**: ohos.permission.USE_USER_IDM

**Parameters**

| Name   | Type                                                                    | Mandatory| Description                                                |
| -------- | ------------------------------------------------------------------------ | ---- | --------------------------------------------- |
| callback | AsyncCallback&lt;Array&lt;[EnrolledCredInfo](#enrolledcredinfo8)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is information about all registered credentials of the user. Otherwise, **err** is an error object.|

**Error codes**

| ID| Error Message              |
| -------- | --------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | The system service works abnormally. |

**Example**
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let userIDM = new osAccount.UserIdentityManager();
  try {
    userIDM.getAuthInfo((err: BusinessError, result: osAccount.EnrolledCredInfo[]) => {
      if (err) {
        console.error(`getAuthInfo exception = code is ${err.code}, message is ${err.message}`);
      } else {
        console.info('getAuthInfo result = ' + JSON.stringify(result));
      }
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`getAuthInfo exception = code is ${err.code}, message is ${err.message}`);
  }
  ```

### getAuthInfo<sup>8+</sup>

getAuthInfo(authType: AuthType, callback: AsyncCallback&lt;Array&lt;EnrolledCredInfo&gt;&gt;): void

Obtains authentication information of the specified type. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Required permissions**: ohos.permission.USE_USER_IDM

**Parameters**

| Name   | Type                                              | Mandatory| Description                                               |
| -------- | -------------------------------------------------- | ---- | -------------------------------------------------- |
| authType | [AuthType](#authtype8) | Yes  | Authentication credential type.                                         |
| callback | AsyncCallback&lt;Array&lt;[EnrolledCredInfo](#enrolledcredinfo8)&gt;&gt; | Yes  | Callback used to return the result. If the operation is successful, **err** is **null** and **data** is the information about all enrolled credentials of the specified type. Otherwise, **err** is an error object.|

**Error codes**

| ID| Error Message              |
| -------- | ------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300001 | The system service works abnormally. |
| 12300002 | Invalid authType. |

**Example**
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let userIDM = new osAccount.UserIdentityManager();
  try {
    userIDM.getAuthInfo(osAccount.AuthType.PIN,
      (err: BusinessError, result: osAccount.EnrolledCredInfo[]) => {
      if (err) {
        console.error(`getAuthInfo exception = code is ${err.code}, message is ${err.message}`);
      } else {
        console.info('getAuthInfo result = ' + JSON.stringify(result));
      }
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`getAuthInfo exception = code is ${err.code}, message is ${err.message}`);
  }
  ```

### getAuthInfo<sup>8+</sup>

getAuthInfo(authType?: AuthType): Promise&lt;Array&lt;EnrolledCredInfo&gt;&gt;;

Obtains authentication information. This API uses a promise to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Required permissions**: ohos.permission.USE_USER_IDM

**Parameters**

| Name   | Type                               | Mandatory| Description     |
| -------- | ----------------------------------- | ---- | -------- |
| authType | [AuthType](#authtype8)              | No  | Authentication type. By default, this parameter is left blank, which means to obtain information about all authentication types.|

**Return value**

| Type                                        | Description                                                                    |
| :------------------------------------------- | :----------------------------------------------------------------------- |
| Promise&lt;Array&lt;[EnrolledCredInfo](#enrolledcredinfo8)&gt;&gt; | Promise used to return the information about all the enrolled credentials of the specified type.|

**Error codes**

| ID| Error Message              |
| -------- | ------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 | Parameter error. Possible causes: Incorrect parameter types. |
| 12300001 | The system service works abnormally. |
| 12300002 | Invalid authType. |

**Example**
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let userIDM = new osAccount.UserIdentityManager();
  try {
    userIDM.getAuthInfo(osAccount.AuthType.PIN).then((result: osAccount.EnrolledCredInfo[]) => {
      console.info('getAuthInfo result = ' + JSON.stringify(result))
    }).catch((err: BusinessError) => {
      console.error(`getAuthInfo error = code is ${err.code}, message is ${err.message}`);
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`getAuthInfo exception = code is ${err.code}, message is ${err.message}`);
  }
  ```

### getAuthInfo<sup>12+</sup>

getAuthInfo(options?: GetAuthInfoOptions): Promise&lt;Array&lt;EnrolledCredInfo&gt;&gt;

Obtains authentication information. This API uses a promise to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Required permissions**: ohos.permission.USE_USER_IDM

**Parameters**

| Name   | Type                               | Mandatory| Description     |
| -------- | ----------------------------------- | ---- | -------- |
| options | [GetAuthInfoOptions](#getauthinfooptions12)          | No  | Optional parameters for obtaining authentication information. This parameter is left empty by default, indicating that all enrolled credential information of the current user is obtained.|

**Return value**

| Type                                        | Description                                                                    |
| :------------------------------------------- | :----------------------------------------------------------------------- |
| Promise&lt;Array&lt;[EnrolledCredInfo](#enrolledcredinfo8)&gt;&gt; | Promise used to return the information about all the enrolled credentials of the specified type.|

**Error codes**

| ID| Error Message              |
| -------- | ------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401 | Parameter error. Possible causes: Incorrect parameter types. |
| 12300001 | The system service works abnormally. |
| 12300002 | Invalid options. |
| 12300003 | Account not found. |

**Example**
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let userIDM = new osAccount.UserIdentityManager();
  let options: osAccount.GetAuthInfoOptions = {
    authType: osAccount.AuthType.PIN,
    accountId: 100,
  };
  try {
    userIDM.getAuthInfo(options).then((result: osAccount.EnrolledCredInfo[]) => {
      console.info('getAuthInfo result = ' + JSON.stringify(result))
    }).catch((err: BusinessError) => {
      console.error(`getAuthInfo error = code is ${err.code}, message is ${err.message}`);
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`getAuthInfo exception = code is ${err.code}, message is ${err.message}`);
  }
  ```

### getEnrolledId<sup>12+</sup>

getEnrolledId(authType: AuthType, accountId?: number): Promise&lt;Uint8Array&gt;

Obtains the ID of the enrolled credential based on the credential type and account ID (optional). This API uses a promise to return the result.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Required permissions**: ohos.permission.USE_USER_IDM

**Parameters**

| Name    | Type                  | Mandatory| Description     |
| --------  | ---------------------- | ---- | -------- |
| authType  | [AuthType](#authtype8) | Yes  | Credential type.|
| accountId | number                 | No  | System account ID, which is left blank by default.|

**Return value**

| Type                      | Description                                                                    |
| :------------------------ | :----------------------------------------------------------------------- |
| Promise&lt;Uint8Array&gt; | Promise used to return the credential ID obtained.|

**Error codes**

| ID| Error Message              |
| -------- | ------------------- |
| 201 | Permission denied.|
| 202 | Not system application.|
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 12300001 | The system service works abnormally. |
| 12300002 | Invalid authType. |
| 12300003 | Account not found. |
| 12300102 | The credential does not exist. |
| 12300106 | The authentication type is not supported. |

**Example**
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let userIDM = new osAccount.UserIdentityManager();
  let authType: osAccount.AuthType = osAccount.AuthType.PIN;
  let accountId = 100;
  try {
    userIDM.getEnrolledId(authType, accountId).then((enrolledId: Uint8Array) => {
        console.info('getEnrolledId enrolledId = ' + JSON.stringify(enrolledId));
    }).catch((err: BusinessError) => {
        console.error(`getEnrolledId error = code is ${err.code}, message is ${err.message}`);
    });
  } catch (e) {
    const err = e as BusinessError;
    console.error(`getEnrolledId exception = code is ${err.code}, message is ${err.message}`);
  }
  ```

## IInputData<sup>8+</sup>

Provides callbacks for PIN operations.

**System API**: This is a system API.

### onSetData<sup>8+</sup>

onSetData: (authSubType: AuthSubType, data: Uint8Array) => void;

**System API**: This is a system API.

Called to notify the caller the data is set.

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name     | Type                                    | Mandatory| Description                                           |
| ---------- | ---------------------------------------- | ---- | ----------------------------------------------- |
| authSubType | [AuthSubType](#authsubtype8)             | Yes  | Credential subtype.                           |
| data       | Uint8Array                               | Yes  | Data (credential) to set. The data is used for authentication and operations for adding and modifying credentials.|

**Error codes**

| ID| Error Message              |
| -------- | ------------------- |
| 202 | Not system application.|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| 12300002 | Invalid pinSubType. |

**Example**
  ```ts
  let password: Uint8Array = new Uint8Array([0, 0, 0, 0, 0, 0]);
  let passwordNumber: Uint8Array = new Uint8Array([1, 2, 3, 4]);
  let inputer: osAccount.IInputer = {
    onGetData: (authSubType: osAccount.AuthSubType, callback: osAccount.IInputData) => {
        if (authSubType == osAccount.AuthSubType.PIN_NUMBER) {
          callback.onSetData(authSubType, passwordNumber);
        } else {
          callback.onSetData(authSubType, password);
        }
    }
  };
  ```

## IInputer<sup>8+</sup>

Provides callbacks for credential inputers.

**System API**: This is a system API.

### onGetData<sup>8+</sup>

onGetData: (authSubType: AuthSubType, callback: IInputData, options: GetInputDataOptions) => void;

Called to notify the caller that data is obtained.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name     | Type                                   | Mandatory| Description            |
| ---------- | --------------------------------------- | ---- | --------------- |
| authSubType | [AuthSubType](#authsubtype8) | Yes| Authentication credential subtype.|
| callback   | [IInputData](#iinputdata8)  | Yes  | Callback used to return the PIN data.|
| options | [GetInputDataOptions](#getinputdataoptions12) | Yes| Optional parameters for the callback function.|

**Example**
  ```ts
  let password: Uint8Array = new Uint8Array([0, 0, 0, 0, 0, 0]);
  let passwordNumber: Uint8Array = new Uint8Array([1, 2, 3, 4]);
  let inputer: osAccount.IInputer = {
    onGetData: (authSubType: osAccount.AuthSubType,
      callback: osAccount.IInputData, options: osAccount.GetInputDataOptions) => {
        if (authSubType == osAccount.AuthSubType.PIN_NUMBER) {
          callback.onSetData(authSubType, passwordNumber);
        } else {
          callback.onSetData(authSubType, password);
        }
    }
  };
  let pinAuth: osAccount.PINAuth = new osAccount.PINAuth();
  let result = pinAuth.registerInputer(inputer);
  console.info('registerInputer result: ' + result);
  ```

## IUserAuthCallback<sup>8+</sup>

Provides callbacks for user authentication.

**System API**: This is a system API.

### onResult<sup>8+</sup>

onResult: (result: number, extraInfo: AuthResult) => void;

Called to return the result code and authentication result.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name    | Type                                   | Mandatory| Description                |
| --------- | --------------------------------------- | ---- | ------------------- |
| result    | number                                   | Yes  | Authentication result code.|
| extraInfo | [AuthResult](#authresult8)  | Yes  | Specific authentication result information. If the authentication is successful, the authentication token is returned in **extrainfo**. If the authentication fails, the remaining authentication time is returned. If the authentication executor is locked, the freezing time is returned.|

**Example**
  ```ts
  let authCallback: osAccount.IUserAuthCallback = {
    onResult: (result: number, extraInfo: osAccount.AuthResult) => {
      console.info('auth result = ' + result);
      console.info('auth extraInfo = ' + JSON.stringify(extraInfo));
    }
  };
  ```

### onAcquireInfo?<sup>8+</sup>

onAcquireInfo?: (module: number, acquire: number, extraInfo: Uint8Array) => void;

Called to acquire identity authentication information.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name   | Type    | Mandatory| Description                          |
| --------- | ------- | ---- | ----------------------------- |
| module    | number  | Yes  | Type of authentication executor.  |
| acquire   | number  | Yes  | Tip code of the authentication executor.|
| extraInfo | Uint8Array     | Yes  | Reserved.                    |

**Example**
  ```ts
  let authCallback: osAccount.IUserAuthCallback = {
    onResult: (result: number, extraInfo: osAccount.AuthResult) => {
      console.info('auth result = ' + result)
      console.info('auth extraInfo = ' + JSON.stringify(extraInfo));
    },
    onAcquireInfo: (module: number, acquire: number, extraInfo: Uint8Array) => {
      console.info('auth module = ' + module);
      console.info('auth acquire = ' + acquire);
      console.info('auth extraInfo = ' + JSON.stringify(extraInfo));
    }
  };
  ```

## IIdmCallback<sup>8+</sup>

Provides callbacks for IDM.

**System API**: This is a system API.

### onResult<sup>8+</sup>

onResult: (result: number, extraInfo: RequestResult) => void;

Called to return the result code and request result information.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name    | Type                                   | Mandatory| Description                    |
| --------- | --------------------------------------- | ---- | ----------------------- |
| result    | number                                  | Yes  | Authentication result code.   |
| extraInfo | [RequestResult](#requestresult8)  | Yes  | Specific information to be transferred.|

**Example**
  ```ts
  let idmCallback: osAccount.IIdmCallback = {
    onResult: (result: number, extraInfo: osAccount.RequestResult) => {
      console.info('callback result = ' + result)
      console.info('callback extraInfo = ' + JSON.stringify(extraInfo));
    }
  };
  ```

### onAcquireInfo?<sup>8+</sup>

onAcquireInfo?: (module: number, acquire: number, extraInfo: Uint8Array) => void;

Called to acquire IDM information.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

**Parameters**

| Name   | Type    | Mandatory| Description                          |
| --------- | ------- | ---- | ----------------------------- |
| module    | number  | Yes  | Type of authentication executor.  |
| acquire   | number  | Yes  | Tip code of the authentication executor.|
| extraInfo | Uint8Array | Yes  | Reserved.                    |

**Example**
  ```ts
  let idmCallback: osAccount.IIdmCallback = {
    onResult: (result: number, extraInfo: Object) => {
      console.info('callback result = ' + result)
      console.info('callback onResult = ' + JSON.stringify(extraInfo));
    },
    onAcquireInfo: (module: number, acquire: number, extraInfo: Uint8Array) => {
      console.info('callback module = ' + module);
      console.info('callback acquire = ' + acquire);
      console.info('callback onacquireinfo = ' + JSON.stringify(extraInfo));
    }
  };
  ```

## GetPropertyRequest<sup>8+</sup>

Defines the request for obtaining property information.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

| Name   | Type                                                        | Read-Only | Optional| Description                  |
| -------- | ------------------------------------------------------------ | ----- | ----- | ----------------------- |
| authType | [AuthType](#authtype8)                            | No| No | Authentication credential type.       |
| keys     | Array&lt;[GetPropertyType](#getpropertytype8)&gt; | No| No | An array of the types of the properties to obtain.|
| accountId<sup>12+</sup> | number | No| Yes | System account ID, which is **undefined** by default.|

## SetPropertyRequest<sup>8+</sup>

Defines the request for setting property information.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

| Name   | Type                                            | Read-Only | Optional| Description                |
| -------- | ------------------------------------------------ | ----- | ----- | -------------------- |
| authType | [AuthType](#authtype8)               | No| No | Authentication credential type.    |
| key     | [SetPropertyType](#setpropertytype8) | No| No | Type of the property to set.|
| setInfo  | Uint8Array                                       | No| No | Information to set.    |

## ExecutorProperty<sup>8+</sup>

Defines the executor property.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

| Name        | Type                        |  Read-Only| Optional| Description             |
| ------------ | ---------------------------- | ----- | -----|----------------- |
| result       | number                       | No   | No  | Result.        |
| authSubType  | [AuthSubType](#authsubtype8) | No   | No  | Authentication credential subtype.|
| remainTimes  | number                       | No   | Yes  | Number of remaining authentication times, which is **-1** by default.    |
| freezingTime | number                       | No   | Yes  | Freezing time, which is **-1** by default.    |
| enrollmentProgress<sup>10+</sup> | string   | No   | Yes  | Enrollment progress, which is left blank by default.|
| sensorInfo<sup>10+</sup> | string           | No   | Yes  | Sensor information, which is left blank by default.|
| nextPhaseFreezingTime<sup>12+</sup> | number | No   | Yes  | Next freezing time, which is **undefined** by default.|
| credentialLength<sup>20+</sup> | number | No   | Yes  | Credential length, which is **undefined** by default. When credentials with indefinite-length attributes such as biometric information are queried, **undefined** is returned.|

## AuthResult<sup>8+</sup>

Defines the authentication result information.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

| Name       | Type       |  Read-Only| Optional| Description             |
| ------------ | ----------- | ----- | ----- | ----------------- |
| token        | Uint8Array  | No   | Yes  | Authentication token, which is left blank by default.     |
| remainTimes  | number      | No   | Yes  | Number of remaining authentication times, which is left blank by default.     |
| freezingTime | number      | No   | Yes  | Freezing time. By default, no value is passed in.     |
| nextPhaseFreezingTime<sup>12+</sup> | number | No   | Yes  | Next freezing time, which is **undefined** by default.|
| credentialId<sup>12+</sup> | Uint8Array  | No   | Yes  | Credential ID, which is left blank by default.|
| accountId<sup>12+</sup>         | number | No   | Yes  | System account ID, which is **undefined** by default.|
| pinValidityPeriod<sup>12+</sup> | number | No   | Yes  | Authentication validity period, which is **undefined** by default.|

## CredentialInfo<sup>8+</sup>

Defines the credential information.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

| Name       | Type                                    |  Read-Only| Optional| Description             |
| ------------ | ---------------------------------------- | ----- | ----- | ----------------- |
| credType     | [AuthType](#authtype8)       | No   | No  | Authentication credential type.    |
| credSubType  | [AuthSubType](#authsubtype8) | No   | No  | Authentication credential subtype.  |
| token        | Uint8Array                           | No   | No  | Authentication token.    |
| accountId<sup>12+</sup>    | number | No   | Yes  | System account ID, which is **undefined** by default.|

## RequestResult<sup>8+</sup>

Defines the request result information.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

| Name       | Type       |  Read-Only| Optional| Description             |
| ------------ | ----------- | ----- | ----- | ----------------- |
| credentialId | Uint8Array  | No   | Yes  | Credential ID, which is left blank by default.     |

## EnrolledCredInfo<sup>8+</sup>

Defines enrolled credential information.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

| Name       | Type                                    |  Read-Only| Optional| Description             |
| ------------ | ---------------------------------------- | ----- | ----- | ------------------- |
| credentialId | Uint8Array                               | No   | No  | Credential ID.      |
| authType     | [AuthType](#authtype8)       | No   | No  | Authentication credential type.  |
| authSubType  | [AuthSubType](#authsubtype8) | No   | No  | Authentication credential subtype.|
| templateId   | Uint8Array                               | No   | No  | Authentication credential template ID.    |
| isAbandoned<sup>20+</sup>   | boolean                      | No   | Yes  | Whether the credential is abandoned. The abandoned credential may be stored as a backup credential for a period of time. The value **true** indicates that the credential is abandoned, and the value **false** indicates the opposite. The default value is **undefined**.  |
| validityPeriod<sup>20+</sup>   | number                    | No   | Yes  | Validity period of the credential. The default value is **undefined**.    |

## GetPropertyType<sup>8+</sup>

Enumerates the types of properties to obtain.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

| Name          | Value| Description     |
| ------------- | ------ | --------- |
| AUTH_SUB_TYPE | 1      | Authentication credential subtype.|
| REMAIN_TIMES  | 2      | Number of remaining times.  |
| FREEZING_TIME | 3      | Freezing time.  |
| ENROLLMENT_PROGRESS<sup>10+</sup> | 4      | Enrollment progress.  |
| SENSOR_INFO<sup>10+</sup> | 5      | Sensor information.  |
| NEXT_PHASE_FREEZING_TIME<sup>12+</sup> | 6 | Next freezing time.|
| CREDENTIAL_LENGTH<sup>20+</sup> | 7 | Credential length.|

## SetPropertyType<sup>8+</sup>

Enumerates the types of properties to set.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

| Name          | Value| Description       |
| -------------- | ----- | ----------- |
| INIT_ALGORITHM | 1     | Initialization algorithm.|

## AuthType<sup>8+</sup>

Enumerates the authentication credential types.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

| Name | Value| Description            |
| ----- | ----- | ---------------- |
| PIN   | 1     | PIN authentication.|
| FACE  | 2     | Facial authentication.|
| FINGERPRINT<sup>10+</sup>   | 4     | Fingerprint authentication.|
| RECOVERY_KEY<sup>12+</sup> | 8 | Key recovery type.|
| PRIVATE_PIN<sup>14+</sup> | 16 | Private PIN type.|
| DOMAIN<sup>9+</sup>  | 1024     | Domain authentication.|

## AuthSubType<sup>8+</sup>

Enumerates the authentication credential subtypes.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

| Name      | Value| Description              |
| ---------- | ----- | ------------------ |
| PIN_SIX    | 10000 | Six-digit PIN.      |
| PIN_NUMBER | 10001 | Custom PIN.|
| PIN_MIXED  | 10002 | Custom mixed credentials.|
| PIN_FOUR<sup>12+</sup>   | 10003 | 4-digit credential.|
| PIN_PATTERN<sup>12+</sup>  | 10004 | Pattern credential.|
| PIN_QUESTION<sup>14+</sup>  | 10005 | Security question credential.|
| FACE_2D    | 20000 | 2D face credential.  |
| FACE_3D    | 20001 | 3D face credential.  |
| FINGERPRINT_CAPACITIVE<sup>10+</sup>    | 30000 | Capacitive fingerprint.  |
| FINGERPRINT_OPTICAL<sup>10+</sup>    | 30001 | Optical fingerprint.  |
| FINGERPRINT_ULTRASONIC<sup>10+</sup>    | 30002 | Ultrasonic fingerprint.  |
| DOMAIN_MIXED<sup>9+</sup>    | 10240001 | Mixed domain authentication credentials.  |

## AuthTrustLevel<sup>8+</sup>

Enumerates the trust levels of the authentication result.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

| Name | Value| Description       |
| ---- | ------ | ----------- |
| ATL1 | 10000  | Trust level 1.|
| ATL2 | 20000  | Trust level 2.|
| ATL3 | 30000  | Trust level 3.|
| ATL4 | 40000  | Trust level 4.|

## Module<sup>8+</sup>

Enumerates the modules from which information is obtained.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

| Name      | Value| Description                    |
| --------- | ------ | ------------------------ |
| FACE_AUTH | 1      | Facial authentication module.|

## ResultCode<sup>8+</sup>

Enumerates the authentication result codes.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

| Name                   | Value| Description                                    |
| ----------------------- | ----- | ---------------------------------------- |
| SUCCESS                 | 0     | The authentication is successful or the authentication feature is supported.            |
| FAIL                    | 1     | The authentication executor failed to identify the user.                  |
| GENERAL_ERROR           | 2     | Other errors.                           |
| CANCELED                | 3     | The authentication is canceled.                      |
| TIMEOUT                 | 4     | The authentication timed out.                      |
| TYPE_NOT_SUPPORT        | 5     | The authentication credential type is not supported.                |
| TRUST_LEVEL_NOT_SUPPORT | 6     | The authentication trust level is not supported.              |
| BUSY                    | 7     | The authentication executor is busy. Try again after a few seconds.|
| INVALID_PARAMETERS      | 8     | Incorrect parameters are detected.                         |
| LOCKED                  | 9     | The authentication executor is locked.                    |
| NOT_ENROLLED            | 10    | The authentication executor is not enrolled.                  |

## FaceTipsCode<sup>8+</sup>

Enumerates the tip codes for facial authentication.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

| Name                         | Value| Description                                    |
| ----------------------------- | ----- | ---------------------------------------- |
| FACE_AUTH_TIP_TOO_BRIGHT      | 1     | The obtained face image is too bright.        |
| FACE_AUTH_TIP_TOO_DARK        | 2     | The obtained face image is too dark.      |
| FACE_AUTH_TIP_TOO_CLOSE       | 3     | The face is too close to the device.                      |
| FACE_AUTH_TIP_TOO_FAR         | 4     | The face is too far away from the device.                      |
| FACE_AUTH_TIP_TOO_HIGH        | 5     | Only the upper part of the face is captured because the device is angled too high.             |
| FACE_AUTH_TIP_TOO_LOW         | 6     | Only the lower part of the face is captured because the device is angled too low.             |
| FACE_AUTH_TIP_TOO_RIGHT       | 7     | Only the right part of the face is captured because the device is angled too much to the right.|
| FACE_AUTH_TIP_TOO_LEFT        | 8     | Only the left part of the face is captured because the device is angled too much to the left.|
| FACE_AUTH_TIP_TOO_MUCH_MOTION | 9     | The face moves too fast during facial information collection.        |
| FACE_AUTH_TIP_POOR_GAZE       | 10    | The face is not facing the device.                        |
| FACE_AUTH_TIP_NOT_DETECTED    | 11    | No face is detected.                        |

## FingerprintTips<sup>8+</sup>

Enumerates the tip codes for fingerprint authentication.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

| Name                         | Value| Description                                           |
| ----------------------------- | ----- | ----------------------------------------------- |
| FINGERPRINT_TIP_GOOD          | 0     | The captured image is clear.                             |
| FINGERPRINT_TIP_IMAGER_DIRTY  | 1     | The fingerprint image has big noise due to dirt on the sensor.|
| FINGERPRINT_TIP_INSUFFICIENT  | 2     | Failed to process the fingerprint image due to big noise.  |
| FINGERPRINT_TIP_PARTIAL       | 3     | Only part of the fingerprint image is detected.                        |
| FINGERPRINT_TIP_TOO_FAST      | 4     | The fingerprint image is incomplete due to quick motion.                 |
| FINGERPRINT_TIP_TOO_SLOW      | 5     | Failed to read the fingerprint image due to lack of motion.               |
| FINGERPRINT_TIP_FINGER_DOWN<sup>10+</sup>   | 6     | Press your finger.                 |
| FINGERPRINT_TIP_FINGER_UP<sup>10+</sup>     | 7     | Lift your finger.               |

## OsAccountInfo

Represents the system account information.

**System capability**: SystemCapability.Account.OsAccount

| Name     | Type  | Read-Only | Optional | Description      |
| ----------- | ------ | ---- | ---- | ---------- |
| shortName<sup>12+</sup> | string | No| Yes | Short name of the system account.<br>**System API**: This is a system API and is left blank by default.|
| isLoggedIn<sup>12+</sup> | boolean | No| Yes | Whether the system account is logged in. The value **true** means that the system account has logged in; the value **false** means the opposite.<br>**System API**: This is a system API. The default value is **false**.|

## OsAccountType

Enumerates the system account types.

**System capability**: SystemCapability.Account.OsAccount

| Name  | Value| Description        |
| ------ | ------ | ----------- |
| PRIVATE<sup>12+</sup> | 1024  | Privacy account. Only one privacy account is allowed.<br>**System API**: This is a system API.  |

## DomainAccountInfo<sup>8+</sup>

Represents domain account information.

**System capability**: SystemCapability.Account.OsAccount

| Name     | Type  | Read-Only | Optional | Description      |
| ----------- | ------ | ---- | ---- | ---------- |
| accountId<sup>10+</sup> | string | No| Yes | Domain account ID.<br>**System API**: This is a system API and is **undefined** by default.|
| isAuthenticated<sup>11+</sup>| boolean | No| Yes | Whether the domain account has been authenticated. The value **true** means that the specified domain account has been authenticated; the value **false** means the opposite.<br>**System API**: This is a system API. The default value is **false**.|

## ConstraintSourceTypeInfo<sup>9+</sup>

Defines the constraint source type.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

| Name     | Type  | Read-Only | Optional | Description      |
| ----------- | ------ | ---- | ---- | ---------- |
| localId      | number | No| No | ID of the target system account.    |
| type | [ConstraintSourceType](#constraintsourcetype9) | No| No | Type of the constraint source.|

## ConstraintSourceType<sup>9+</sup>

Enumerates the constraint sources.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

| Name  | Value| Description        |
| ------ | ------ | ------------ |
| CONSTRAINT_NOT_EXIST  | 0      | The constraint does not exist.|
| CONSTRAINT_TYPE_BASE | 1      | Constraint from system settings.  |
| CONSTRAINT_TYPE_DEVICE_OWNER  | 2   | Constraint from the device owners' settings.  |
| CONSTRAINT_TYPE_PROFILE_OWNER  | 3  | Constraint from the profile owners' settings.  |

## AuthStatusInfo<sup>10+</sup>

Presents the authentication status information.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

| Name     | Type  | Read-Only | Optional| Description      |
| ----------- | ------ | ---- | ---- | ---------- |
| remainTimes  | number | No| No | Number of remaining times.  |
| freezingTime | number | No| No | Freezing time.|

## GetDomainAccessTokenOptions<sup>10+</sup>

Defines the options for obtaining a domain access token.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

| Name     | Type  | Read-Only | Optional| Description      |
| ----------- | ------ | ---- | ---- | ---------- |
| domainAccountInfo  | [DomainAccountInfo](#domainaccountinfo8) | No| No | Domain account information.  |
| domainAccountToken | Uint8Array | No| No | Token of the domain account.|
| businessParams | Record<string, Object> | No| No | Service parameters customized by the service party based on the request protocol.|
| callerUid | number | No| No | Unique identifier of the caller.|

## GetDomainAccountInfoOptions<sup>10+</sup>

Defines the options for obtaining domain account information.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

| Name     | Type  | Read-Only | Optional| Description      |
| ----------- | ------ | ---- | ---- | ---------- |
| accountName | string | No| No | Domain account name.|
| domain      | string | No| Yes | Domain name, which is **undefined** by default.|
| serverConfigId<sup>12+</sup>| string | No| Yes | ID of the server to which the domain account belongs, which is **undefined** by default.|

## GetDomainAccountInfoPluginOptions<sup>10+</sup>

Defines the options for the domain plug-in to obtain the domain account information. The **GetDomainAccountInfoPluginOptions** class inherits from [**GetDomainAccountInfoOptions**](#getdomainaccountinfooptions10).

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

| Name     | Type  | Read-Only | Optional| Description      |
| ----------- | ------ | ---- | ---- | ---------- |
| callerUid | number | No| No | Unique identifier of the caller.|

## OsAccountSwitchEventData<sup>12+</sup>

Defines the event that indicates the start or end of a foreground-background system account switchover.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

| Name     | Type  | Read-Only| Optional| Description      |
| ----------- | ------ | ---- | ---- | ---------- |
| fromAccountId | number | No| No| ID of the source system account.|
| toAccountId | number | No| No| ID of the target system account.|
| displayId<sup>21+</sup> | number | No| Yes| ID of the logical display where the switchover occurs. The default value is **0**.|

## CreateOsAccountOptions<sup>12+</sup>

Represents the optional parameter used to create a system account.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

| Name     | Type  | Read-Only | Optional  | Description      |
| ----------- | ------ | ---- | ---- | ---------- |
| shortName | string | No| No  | Short name of the account (used as the name of the personal folder).<br>**The short name cannot**:<br>1. Contain any of the following characters: \< \>\| : " * ? / \\<br>2. Contain any of the following: . or ..<br>3. Exceed 255 characters.|
| disallowedPreinstalledBundles<sup>19+</sup> | Array&lt;string&gt; | No| Yes  | Forbidden list of the preinstalled applications, which cannot be installed on the device. The value is empty by default.|
| allowedPreinstalledBundles<sup>19+</sup> | Array&lt;string&gt; | No| Yes  | Trustlist of the preinstalled applications, which can be installed on the device. The default value is **std::nullopt**.|

## CreateOsAccountForDomainOptions<sup>12+</sup>

Represents a set of optional parameters for creating a system account bound to the specified domain account. It inherits from [CreateOsAccountOptions](#createosaccountoptions12).

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

| Name     | Type  | Read-Only | Optional  | Description      |
| ----------- | ------ | ---- | ---- | ---------- |
| shortName | string | No| No  | Short name of the account (used as the name of the personal folder).<br>**The short name cannot**:<br>1. Contain any of the following characters: \< \>\| : " * ? / \\<br>2. Contain any of the following: . or ..<br>3. Exceed 255 characters.|

## GetAuthInfoOptions<sup>12+</sup>

Represents a set of optional parameters for [GetAuthInfo](#getauthinfo12).

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

| Name     | Type                   | Read-Only | Optional  | Description      |
| --------- | ---------------------- | ---- | ---- | ---------- |
| authType  | [AuthType](#authtype8) | No| Yes  | Authentication type, which is **undefined** by default.|
| accountId | number                 | No| Yes  | System account ID, which is **undefined** by default.|

## AuthIntent<sup>12+</sup>

Enumerates the authentication intents.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

| Name    | Value  | Description      |
| -------- | --- | ---------- |
| UNLOCK   | 1   | Unlock.|
| SILENT_AUTH<sup>14+</sup>  | 2   | Silent authentication.|
| QUESTION_AUTH<sup>14+</sup>   | 3   | Security question authentication.|
| ABANDONED_PIN_AUTH<sup>20+</sup>   | 4   | Abandoned PIN authentication. After a user changes the lock screen password, the old PIN is abandoned. If a user forgets the current password, the user can reset the lock screen password after passing the authentication with the abandoned PIN.|

## RemoteAuthOptions<sup>12+</sup>

Represents a set of optional parameters for remote authentication.

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

| Name              | Type   | Read-Only | Optional| Description      |
| ------------------ | ------ | ---- | ---- | ---------- |
| verifierNetworkId  | string | No| Yes | Network ID of the credential verifier, which is left blank by default.|
| collectorNetworkId | string | No| Yes | Network ID of the credential collector, which is left blank by default.|
| collectorTokenId   | number | No| Yes | Token ID of the credential collector, which is **undefined** by default.|

## AuthOptions<sup>12+</sup>

Represents a set of optional parameters for [auth](#auth12).

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

| Name              | Type   | Read-Only | Optional| Description      |
| ------------------ | ------ | ---- | ---- | ---------- |
| accountId          | number | No| Yes | System account ID, which is **undefined** by default.|
| authIntent         | [AuthIntent](#authintent12) | No| Yes | Authentication intent, which is **undefined** by default.|
| remoteAuthOptions  | [RemoteAuthOptions](#remoteauthoptions12) | No| Yes | Remote authentication options, which is **undefined** by default.|

## GetInputDataOptions<sup>12+</sup>

Represents a set of optional parameters for [onGetData](#ongetdata8).

**System API**: This is a system API.

**System capability**: SystemCapability.Account.OsAccount

| Name              | Type   | Read-Only | Optional| Description      |
| ------------------ | ------ | ---- | ---- | ---------- |
| challenge          | Uint8Array | No| Yes | Challenge value, which is **undefined** by default.|
