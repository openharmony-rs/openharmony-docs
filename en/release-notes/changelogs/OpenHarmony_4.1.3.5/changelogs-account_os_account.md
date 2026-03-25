# Account Subsystem Changelog

## cl.account_os_account.1 Deprecation of Some osAccount APIs

**Access Level**

Public API

**Reason for Change**

The APIs can be called only by system applications.

**Change Impact**

This change has no impact on system applications. For third-party applications, error code 201 is reported when the API is called in the old version, and error code 202 is reported when the API is called in the new version.

**API Level**

9

**Change Since**

OpenHarmony SDK OpenHarmony_4.1.3.5

**Deprecated APIs/Components**

Involved APIs:

interface/sdk-js/api/@ohos.account.osAccount.d.ts:

```js
    checkOsAccountActivated(localId: number, callback: AsyncCallback<boolean>): void;
    checkOsAccountActivated(localId: number): Promise<boolean>;

    checkOsAccountConstraintEnabled(localId: number, constraint: string, callback: AsyncCallback<boolean>): void;
    checkOsAccountConstraintEnabled(localId: number, constraint: string): Promise<boolean>;

    checkOsAccountVerified(localId: number, callback: AsyncCallback<boolean>): void;
    checkOsAccountVerified(localId: number): Promise<boolean>;

    getOsAccountConstraints(localId: number, callback: AsyncCallback<Array<string>>): void;
    getOsAccountConstraints(localId: number): Promise<Array<string>>;

    getCurrentOsAccount(callback: AsyncCallback<OsAccountInfo>): void;
    getCurrentOsAccount(): Promise<OsAccountInfo>;
```

After change:

All the above APIs are deprecated, without substitute APIs.

**Adaptation Guide**

No adaptation is required for system applications. If a third-party application calls the deprecated APIs, error code 202 and related processing logic need to be provided.


## cl.account_os_account.2 Deprecation of Some osAccount APIs

**Access Level**

Public API

**Reason for Change**

1. The APIs have spelling errors.

2. Similar APIs are named in different formats.

**Change Impact**

The deprecated APIs will not be maintained after five versions. Use substitute APIs.

**API Level**

checkOsAccountVerified(9)

isVerified(8)

isActived(8)

**Change Since**

OpenHarmony SDK OpenHarmony_4.1.3.5

**Deprecated APIs/Components**

Deprecated APIs:

interface/sdk-js/api/@ohos.account.osAccount.d.ts:

```js
    checkOsAccountVerified(callback: AsyncCallback<boolean>): void;
    checkOsAccountVerified(): Promise<boolean>;
```
Substitute APIs:
```js
    isOsAccountUnlocked(): Promise<boolean>;
```

Deprecated APIs:
```js
    interface OsAccountInfo {
        ...
        isVerified: boolean;
        isActived: boolean;
        ...
    }
```
Substitute APIs:
```js
    interface OsAccountInfo {
        ...
        isUnlocked: boolean;
        isActivated: boolean;
        ...
    }
```

**Adaptation Guide**

Since API version 11, use the substitute APIs.
