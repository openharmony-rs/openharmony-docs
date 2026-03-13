# Account Subsystem Changelog

## cl.accountaccount_os_account.1 The Error Code of setAppAccess Is Changed
**Access Level**

Public API

**Change Reason**

To prevent resource waste, applications are not allowed to call this API to grant permissions to third-party applications without restrictions. When the number of authorized applications exceeds 1024, the new error code 12400005 is returned.

**Change Impact**

This change is a non-compatible change.

Before change: If the third-party application bundle name passed to **setAppAccess** is not installed, the error code 12400001 is returned, indicating that the application is not found.

After change: If the third-party application bundle name passed to **setAppAccess** is not installed, and the number of authorized applications does not exceed the upper limit, a success message is returned. If the number of authorized applications exceeds the upper limit, the error code 12400005 is returned.


**Start API Level**

9

**Change Since**

OpenHarmony 5.0.2.1

**Key API/Component Changes**

The following APIs in [@ohos.account.appAccount.d.ts](https://gitcode.com/openharmony/interface_sdk-js/blob/master/api/@ohos.account.appAccount.d.ts):

- setAppAccess(name: string, bundleName: string, isAccessible: boolean, callback: AsyncCallback\<void>): void

- setAppAccess(name: string, bundleName: string, isAccessible: boolean): Promise\<void>

**Adaptation Guide**

The error code 12400005 is added to the **setAppAccess** API. The following is an example:
```ts
import { BusinessError } from '@ohos.base';
import account_appAccount from '@ohos.account.appAccount';

let appAccountManager: account_appAccount.AppAccountManager = account_appAccount.createAppAccountManager();

try {
  appAccountManager.setAppAccess('ZhangSan', 'com.example.accountjsdemo', true, (err: BusinessError) => {
	if (err.code === 12400005) {
	  // Handle the issue that the number of authorized applications exceeds the upper limit, for example, by revoking authorization from previously authorized applications.
	} else if (err) {
	  console.log('setAppAccess failed: ' + JSON.stringify(err));
	} else {
	  console.log('setAppAccess successfully');
	}
  });
} catch (err) {
  console.log('setAppAccess exception: ' + JSON.stringify(err));
}
```
