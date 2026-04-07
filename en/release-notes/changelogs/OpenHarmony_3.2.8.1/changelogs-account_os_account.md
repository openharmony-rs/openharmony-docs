# Account Subsystem Changelog

## cl.account_os_account.1 Change of Definition and Return Mode of Error Codes

To ensure consistent error codes and normalized return of error codes in the account subsystem APIs, the following changes are made in API version 9:

- Added the following error code definitions:
  - [Account Error Codes](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/errorcodes/errorcode-account.md)
  - [Application Account Error Codes](https://gitcode.com/openharmony/docs/blob/master/en/application-dev/reference/errorcodes/errorcode-account.md)

- Changed the error code return modes as follows:
  - Asynchronous APIs: Return error message in the **error** object of **AsyncCallback** or **Promise**. An error message related to the parameter type or quantity is returned via an exception.
  - Synchronous APIs: Throw an exception to return an error message.

**Change Impact**

The application developed based on earlier versions needs to adapt the method for returning API error message. Otherwise, the original service logic will be affected.

**Key API/Component Changes**

Involved APIs:
  - class AccountManager
    - activateOsAccount(localId: number, callback: AsyncCallback&lt;void&gt;): void;
    - removeOsAccount(localId: number, callback: AsyncCallback&lt;void&gt;): void;
    - setOsAccountConstraints(localId: number, constraints: Array&lt;string&gt;, enable: boolean, callback: AsyncCallback&lt;void&gt;): void;
    - setOsAccountName(localId: number, localName: string, callback: AsyncCallback&lt;void&gt;): void;
    - queryMaxOsAccountNumber(callback: AsyncCallback&lt;number&gt;): void;
    - queryAllCreatedOsAccounts(callback: AsyncCallback&lt;Array&lt;OsAccountInfo&gt;&gt;): void;
    - createOsAccount(localName: string, type: OsAccountType, callback: AsyncCallback&lt;OsAccountInfo&gt;): void;
    - createOsAccountForDomain(type: OsAccountType, domainInfo: DomainAccountInfo, callback: AsyncCallback&lt;OsAccountInfo&gt;): void;
    - queryOsAccountById(localId: number, callback: AsyncCallback&lt;OsAccountInfo&gt;): void;
    - getOsAccountProfilePhoto(localId: number, callback: AsyncCallback&lt;string&gt;): void;
    - setOsAccountProfilePhoto(localId: number, photo: string, callback: AsyncCallback&lt;void&gt;): void;
    - on(type: 'activate' | 'activating', name: string, callback: Callback&lt;number&gt;): void;
    - off(type: 'activate' | 'activating', name: string, callback?: Callback&lt;number&gt;): void;
    - isMainOsAccount(callback: AsyncCallback&lt;boolean&gt;): void;
    - queryOsAccountConstraintSourceTypes(localId: number, constraint: string, callback: AsyncCallback&lt;Array&lt;ConstraintSourceTypeInfo&gt;&gt;): void;
  - class UserAuth
    - constructor();
    - getVersion(): number;
    - getAvailableStatus(authType: AuthType, authTrustLevel: AuthTrustLevel): number;
    - getProperty(request: GetPropertyRequest, callback: AsyncCallback&lt;ExecutorProperty&gt;): void;
    - setProperty(request: SetPropertyRequest, callback: AsyncCallback&lt;number&gt;): void;
    - auth(challenge: Uint8Array, authType: AuthType, authTrustLevel: AuthTrustLevel, callback: IUserAuthCallback): Uint8Array;
    - authUser(userId: number, challenge: Uint8Array, authType: AuthType, authTrustLevel: AuthTrustLevel, callback: IUserAuthCallback): Uint8Array;
    - cancelAuth(contextID: Uint8Array): number;
  - class PINAuth
    - constructor();
    - registerInputer(inputer: IInputer): boolean;
    - unregisterInputer(authType: AuthType): void;
  - class UserIdentityManager
    - constructor();
    - openSession(callback: AsyncCallback&lt;Uint8Array&gt;): void;
    - addCredential(credentialInfo: CredentialInfo, callback: IIdmCallback): void;
    - updateCredential(credentialInfo: CredentialInfo, callback: IIdmCallback): void;
    - closeSession(): void;
    - cancel(challenge: Uint8Array): number;
    - delUser(token: Uint8Array, callback: IIdmCallback): void;
    - delCred(credentialId: Uint8Array, token: Uint8Array, callback: IIdmCallback): void;
    - getAuthInfo(callback: AsyncCallback&lt;Array&lt;EnrolledCredInfo&gt;&gt;): void;
  - interface IInputData
    - onSetData: (authSubType: AuthSubType, data: Uint8Array) =&gt; void;

**Adaptation Guide**

The following uses **activateOsAccount** as an example to describe the error message processing logic of an asynchronous API:

```ts
import account_osAccount from "@ohos.account.osAccount"
let accountMgr = account_osAccount.getAccountManager()
let callbackFunc = (err) => {
  if (err != null) {  // Handle the business error.
    console.log("account_osAccount failed, error: " + JSON.stringify(err));
  } else {
    console.log("account_osAccount successfully");
  }
}
try {
  accountMgr.activateOsAccount("100", callbackFunc);
} catch (err) {  // Handle the error that is related to the parameter type.
  console.log("account_osAccount failed for incorrect parameter type, error: " + JSON.stringify(err));
}
try {
  accountMgr.activateOsAccount();
} catch (err) {  // Handle the error that is related to the parameter quantity.
  console.log("account_osAccount failed for incorrect parameter number, error: " + JSON.stringify(err));
}
```

The following uses **registerInputer** as an example to describe the error message processing logic of a synchronous API:

```ts
import account_osAccount from "@ohos.account.osAccount"
let pinAuth = new account_osAccount.PINAuth()
try {
    pinAuth.registerInputer({})
} catch (err) {  // Handle the error that is related to the parameter type.
  console.log("account_osAccount failed for incorrect parameter type, error: " + JSON.stringify(err));
}
try {
    pinAuth.registerInputer()
} catch (err) {  // Handle the error that is related to the parameter quantity.
  console.log("account_osAccount failed for incorrect parameter number, error: " + JSON.stringify(err));
}
```
