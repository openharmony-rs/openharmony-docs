# Account Subsystem ChangeLog

## cl.account_os_account.1 Change in Error Message Return Method of Account System APIs

Certain system APIs of the account subsystem use service logic return values to indicate error messages, which does not comply with the API error code specifications of OpenHarmony. The following changes are made in API version 9 and later:

Asynchronous API: An error message is returned via **AsyncCallback** or the **error** object of **Promise**.

Synchronous API: An error message is returned via an exception.

**Change Impact**

The application developed based on earlier versions needs to be adapted. Otherwise, the service logic will be affected.

**Key API/Component Changes**

Before change:
  - class UserAuth
    - setProperty(request: SetPropertyRequest, callback: AsyncCallback&lt;number&gt;): void;
    - setProperty(request: SetPropertyRequest): Promise&lt;number&gt;;
    - cancelAuth(contextID: Uint8Array): number;
  - class PINAuth
    - registerInputer(inputer: Inputer): boolean;
  - UserIdentityManager
    - cancel(challenge: Uint8Array): number;

After change:
  - class UserAuth
    - setProperty(request: SetPropertyRequest, callback: AsyncCallback&lt;void&gt;): void;
    - setProperty(request: SetPropertyRequest): Promise&lt;void&gt;;
    - cancelAuth(contextID: Uint8Array): void;
  - class PINAuth
    - registerInputer(inputer: Inputer): void;
  - UserIdentityManager
    - cancel(challenge: Uint8Array): void;

**Adaptation Guide**

The following uses **setProperty** as an example for asynchronous APIs:

```
import account_osAccount from "@ohos.account.osAccount"
userAuth.setProperty({
    authType: account_osAccount.AuthType.PIN,
    key: account_osAccount.SetPropertyType.INIT_ALGORITHM,
    setInfo: new Uint8Array([0])
}, (err) => {
    if (err) {
        console.log("setProperty failed, error: " + JSON.stringify(err));
    } else {
        console.log("setProperty successfully");
    }
});

userAuth.setProperty({
    authType: account_osAccount.AuthType.PIN,
    key: account_osAccount.SetPropertyType.INIT_ALGORITHM,
    setInfo: new Uint8Array([0])
}).catch((err) => {
    if (err) {
        console.log("setProperty failed, error: " + JSON.stringify(err));
    } else {
        console.log("setProperty successfully");
    }
});
```

The following uses **registerInputer** as an example for synchronous APIs:

```
import account_osAccount from "@ohos.account.osAccount"
let pinAuth = new account_osAccount.PINAuth()
let inputer = {
    onGetData: (authType, passwordRecipient) => {
        let password = new Uint8Array([0]);
        passwordRecipient.onSetData(authType, password);
    }
}
try {
    pinAuth.registerInputer(inputer);
} catch (err) {
    console.log("registerInputer failed, error: " + JSON.stringify(err));
}
```

## cl.account_os_account.2 ACTION Definition Change for the Application Account Authentication Service

**Change Impact**

For the application developed based on an earlier version, you need to modify **ACTION** in the application configuration file (**config.json** for the FA model or **module.json5** for the stage model). Otherwise, the application authentication service will be affected.

**Key API/Component Changes**

Involved constant:

@ohos.ability.wantConstant.ACTION_APP_ACCOUNT_AUTH

Before change:

ACTION_APP_ACCOUNT_AUTH = "account.appAccount.action.auth"

After change:

ACTION_APP_ACCOUNT_AUTH = "ohos.appAccount.action.auth"

**Adaptation Guide**

For a third-party application providing the account authentication service, change **ACTION** in the **ServiceAbility** configuration file (**config.json** for the FA module or **module.json5** for the stage module). The following is an example:
```
"abilities": [
    {
        "name": "ServiceAbility",
        "srcEntrance": "./ets/ServiceAbility/ServiceAbility.ts",
        ...
        "visible": true,
        "skills": {
            {
                "actions": [
                    "ohos.appAccount.action.auth"
                ]
            }
        }
    }]
}
