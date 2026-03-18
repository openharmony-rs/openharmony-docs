# Account Subsystem Changelog

## cl.account_os_account.1 Allowing Spaces in Application Account Names

Before the change, when an account name containing a space is passed in, an error indicating invalid parameters will be returned. Now, the account names can contain spaces.

**Change Impact**

Applications developed based on earlier versions are not affected.
From this version, the application account names are no longer checked for spaces when account APIs of API version 9 or later are called.

**Key API/Component Changes**

Involved APIs:
- AppAccountManager
  - createAccount(name: string, callback: AsyncCallback&lt;void&gt;): void;
  - auth(name: string, owner: string, authType: string, callback: AuthCallback): void;
  - setAppAccess(name: string, bundleName: string, isAccessible: boolean, callback: AsyncCallback&lt;void&gt;): void;
  - setCredential(name: string, credentialType: string, credential: string, callback: AsyncCallback&lt;void&gt;): void;
  - setCustomData(name: string, key: string, value: string, callback: AsyncCallback&lt;void&gt;): void;
  - setAuthToken(name: string, authType: string, token: string, callback: AsyncCallback&lt;void&gt;): void;
  - setAuthTokenVisibility(name: string, authType: string, bundleName: string, isVisible: boolean, callback: AsyncCallback&lt;void&gt;): void;
