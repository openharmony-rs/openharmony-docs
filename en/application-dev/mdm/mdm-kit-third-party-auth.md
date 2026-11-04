# Third-Party Custom Authentication

<!--Kit: MDM Kit-->
<!--Subsystem: Customization-->
<!--Owner: @huanleima; @weizai16-->
<!--Designer: @hp_guo-->
<!--Tester: @lpw_work-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=96c2d0c230554b6ff9846320199a7223b0bf888c translatedAt=2026-11-03T09:28:36.110Z pushedAt=2026-11-03T09:28:36.110Z nl=1 -->

Starting from API version 26.0.1, the system supports third-party custom authentication extensions for device unlocking and login. The lock screen provides a USB Key unlock and login interface that supports third-party custom USB Key authentication.

A USB Key (USB security key) is a hardware-based authentication device that resembles a USB flash drive. It contains a security chip that can store digital certificates and keys. After the user inserts the device, authentication is performed using hardware-level encryption, providing greater security than passwords or biometrics alone. USB Keys are widely used in enterprise offices, finance, government services, and other scenarios with high security requirements.

Mobile Device Management (MDM) applications can add, remove, and query third-party custom authentication credentials for accounts. They can also configure device unlock policies to use only built-in system authentication, only third-party custom authentication, or a combination of both.

## Available APIs

The following APIs are used for third-party custom authentication:

| API | Module | Description |
| -------- | -------- | -------- |
| [openSession](../reference/apis-mdm-kit/js-apis-enterprise-securityManager.md#securitymanageropensession) | @kit.MDMKit | Opens a session for changing user authentication credentials and obtains a challenge to prevent replay attacks. |
| [closeSession](../reference/apis-mdm-kit/js-apis-enterprise-securityManager.md#securitymanagerclosesession) | @kit.MDMKit | Closes a session for changing user authentication credentials. |
| [addUserExtendCredential](../reference/apis-mdm-kit/js-apis-enterprise-securityManager.md#securitymanageradduserextendcredential) | @kit.MDMKit | Adds a third-party custom authentication credential. |
| [removeUserExtendCredential](../reference/apis-mdm-kit/js-apis-enterprise-securityManager.md#securitymanagerremoveuserextendcredential) | @kit.MDMKit | Removes a third-party custom authentication credential. |
| [getUserExtendCredential](../reference/apis-mdm-kit/js-apis-enterprise-securityManager.md#securitymanagergetuserextendcredential) | @kit.MDMKit | Queries the list of third-party custom authentication credentials that have been added. |
| [setUnlockPolicy](../reference/apis-mdm-kit/js-apis-enterprise-securityManager.md#securitymanagersetunlockpolicy) | @kit.MDMKit | Configures the device unlock policy to use only built-in system authentication, only third-party custom authentication, or a combination of both. |
| [getUnlockPolicy](../reference/apis-mdm-kit/js-apis-enterprise-securityManager.md#securitymanagergetunlockpolicy) | @kit.MDMKit | Queries the current device unlock policy. |
| [getUserAuthInstance](../reference/apis-user-authentication-kit/js-apis-useriam-userauth.md#userauthgetuserauthinstance10) | @kit.UserAuthenticationKit | Provides a user authentication instance for obtaining authToken after successful authentication. |

## Constraints

- Third-party custom authentication is supported only on PC and 2-in-1 devices.
- The application must have been activated as a super device administrator application.
- All APIs can be used only in the stage model.
- After each call to **openSession**, call **closeSession** promptly when the operation is complete to release session resources.
- Only one session can exist in the system at a time. Calling **openSession** again automatically closes the previous session. A session also closes automatically when it expires (10 minutes by default). After a session closes, its challenge and authToken become invalid and must be obtained again.

## Developing Third-Party Custom Authentication

1. Request permissions. Declare the following permissions in the `requestPermissions` field of the [module.json5](../quick-start/module-configuration-file.md) file for the project module:

   ``` JSON5
   "requestPermissions": [
     {
       "name": "ohos.permission.ENTERPRISE_MANAGE_SECURITY"
     },
     {
       "name": "ohos.permission.ACCESS_BIOMETRIC"
     }
   ]
   ```

   The permissions are used as follows:

   - `ohos.permission.ENTERPRISE_MANAGE_SECURITY`: required to call the securityManager APIs.
   - `ohos.permission.ACCESS_BIOMETRIC`: required to start user authentication through userAuth. For details, see [Requesting Permissions](../security/UserAuthenticationKit/prerequisites.md#requesting-permissions).

2. Import the modules.

   <!-- @[import_usb_key](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/MDMKit/UsbKeyAuth/entry/src/main/ets/service/UsbKeyAuthService.ets) -->

   ``` TypeScript
   import { securityManager } from '@kit.MDMKit';
   import { userAuth } from '@kit.UserAuthenticationKit';
   ```

3. Call [openSession](../reference/apis-mdm-kit/js-apis-enterprise-securityManager.md#securitymanageropensession) to open a session for changing user authentication credentials and obtain the challenge.

4. (Optional) Set the authentication parameters in [AuthParam](../reference/apis-user-authentication-kit/js-apis-useriam-userauth.md#authparam10), using the challenge obtained in the previous step, and call [getUserAuthInstance](../reference/apis-user-authentication-kit/js-apis-useriam-userauth.md#userauthgetuserauthinstance10) to obtain an authentication instance.

   > **NOTE**
   >
   > - [UserAuthType](../reference/apis-user-authentication-kit/js-apis-useriam-userauth.md#userauthtype8) supports only `PIN` (lock screen password authentication). Other types, such as face or fingerprint authentication, are not supported.
   > - [AuthTrustLevel](../reference/apis-user-authentication-kit/js-apis-useriam-userauth.md#authtrustlevel8) supports only `ATL4`, the highest security level.
   > - `UserAuthInstance.start` displays the system password authentication widget, and the call blocks until the user completes authentication. System actions, such as locking the screen, may also close the widget.
   > - Steps 4 and 5 are optional. Credentials can be added successfully without completing user authentication. However, the first time third-party custom authentication is used to unlock the device, the user must complete local PIN or domain account password authentication. This is because third-party custom authentication must inherit the root key used to decrypt the file system from successful local PIN or domain account password authentication.

5. (Optional) Call [UserAuthInstance.on('result')](../reference/apis-user-authentication-kit/js-apis-useriam-userauth.md#onresult10-1) to subscribe to the authentication result, and call [UserAuthInstance.start](../reference/apis-user-authentication-kit/js-apis-useriam-userauth.md#start10) to start authentication. Obtain authToken in the callback upon successful authentication.

6. Depending on your requirements, call [addUserExtendCredential](../reference/apis-mdm-kit/js-apis-enterprise-securityManager.md#securitymanageradduserextendcredential) to add a credential or [removeUserExtendCredential](../reference/apis-mdm-kit/js-apis-enterprise-securityManager.md#securitymanagerremoveuserextendcredential) to remove a credential, passing authToken. When adding a credential, also pass `pluginInfo`, the identifier of the third-party custom authenticator supplied by the authenticator provider.

7. Call [closeSession](../reference/apis-mdm-kit/js-apis-enterprise-securityManager.md#securitymanagerclosesession) to close the session for changing user authentication credentials.

8. (Optional) Call [setUnlockPolicy](../reference/apis-mdm-kit/js-apis-enterprise-securityManager.md#securitymanagersetunlockpolicy) to configure the device unlock policy.

> **NOTE**
>
> The code snippets in this guide are taken from the [UsbKeyAuth sample project](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/MDMKit/UsbKeyAuth). The `accountId` and `pluginInfo` definitions outside the snippets are provided in [Constants.ets](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/MDMKit/UsbKeyAuth/entry/src/main/ets/common/Constants.ets). The logging and retry helpers `Logger`, `MAX_RETRIES`, `isRetryable`, `buildFailureMessage`, and `resolveStringResource` are defined in [UsbKeyAuthService.ets](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/MDMKit/UsbKeyAuth/entry/src/main/ets/service/UsbKeyAuthService.ets). You can replace them as needed. The `uiContext` parameter is the current page's UI context (`UIContext` from `@kit.ArkUI`), used to resolve the authentication widget's title text.

## Adding Third-Party Custom Authentication Credentials

Adding a third-party custom authentication credential is required to enable this authentication method. Without a credential, third-party custom authentication cannot be used to unlock the device. The procedure in this section corresponds to steps 3 through 8 in [Developing Third-Party Custom Authentication](#developing-third-party-custom-authentication) for adding a credential. User authentication in steps 4 and 5 and the device unlock policy in step 8 are optional.

To add a credential:

1. The MDM application calls `openSession` to open a session for changing user authentication credentials and obtain a challenge.
2. (Optional) The MDM application calls `getUserAuthInstance` to start user authentication, passing the challenge, the PIN authentication type, and the ATL4 trust level. The system authentication widget is displayed. After the user completes PIN authentication, authToken is obtained through the callback.
3. The MDM application calls `addUserExtendCredential`, passing pluginInfo and authToken, to add a third-party custom authentication credential.
4. The MDM application calls `closeSession` to close the session and complete credential addition.
5. (Optional) Call `setUnlockPolicy` to configure the device unlock policy.

![Adding a third-party custom authentication credential](figures/third_party_auth_add.png)

> **NOTE**
>
> - `authType` supports only `PIN`, and `authTrustLevel` supports only `ATL4`.
> - `UserAuthInstance.start` displays the system password authentication widget, and the call blocks until the user completes authentication. System actions, such as locking the screen, may also close the widget.

If user authentication is performed to obtain authToken when adding or removing credentials, the sample project encapsulates this process in `requestAuthToken`:

<!-- @[request_auth_token](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/MDMKit/UsbKeyAuth/entry/src/main/ets/service/UsbKeyAuthService.ets) -->

``` TypeScript
// Start user authentication and return authToken.
function requestAuthToken(challenge: Uint8Array, title: string): Promise<Uint8Array> {
  return new Promise((resolve, reject) => {
    const authParam: userAuth.AuthParam = {
      challenge: challenge,
      authType: [userAuth.UserAuthType.PIN],
      authTrustLevel: userAuth.AuthTrustLevel.ATL4,
    };
    const widgetParam: userAuth.WidgetParam = { title };
    const instance: userAuth.UserAuthInstance = userAuth.getUserAuthInstance(authParam, widgetParam);
    instance.on('result', {
      onResult: (result: userAuth.UserAuthResult) => {
        instance.off('result');
        if (result.result === userAuth.UserAuthResultCode.SUCCESS && result.token) {
          resolve(result.token);
        } else {
          reject(new Error(`Authentication failed, result code: ${result.result}`));
        }
      }
    });
    // start displays the password authentication widget and blocks until the user completes authentication.
    instance.start();
  });
}
```

The following example adds a credential:

<!-- @[bind_usb_key](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/MDMKit/UsbKeyAuth/entry/src/main/ets/service/UsbKeyAuthService.ets) -->

``` TypeScript
export async function bindUsbKey(uiContext: UIContext): Promise<string> {
  let retryCount: number = 0;

  while (retryCount < MAX_RETRIES) {
    try {
      // Step 1: Open a session and obtain the challenge.
      const challenge: Uint8Array = await securityManager.openSession(accountId);
      Logger.info('Succeeded in opening session.');

      // Step 2: Start user authentication and obtain the authentication token.
      const dialogTitle: string = resolveStringResource(uiContext, $r('app.string.bind_auth_dialog_title'));
      const authToken: Uint8Array = await requestAuthToken(challenge, dialogTitle);
      Logger.info('Authentication succeeded.');

      // Step 3: Bind the USB Key credential.
      const addInfo: securityManager.AddCredentialInfo = { pluginInfo, authToken };
      await securityManager.addUserExtendCredential(addInfo, accountId);
      Logger.info('Succeeded in adding USB Key credential.');

      // Step 4: Close the session.
      securityManager.closeSession(accountId);
      Logger.info('USB Key binding completed.');

      // Optional: Configure the USB Key unlock mode. EXTENDED_AUTH_REQUIRED combines USB Key and lock screen password authentication.
      securityManager.setUnlockPolicy(
        securityManager.UnlockPolicy.EXTENDED_AUTH_REQUIRED,
        accountId
      );
      Logger.info('Succeeded in setting unlock policy.');
      return 'USB Key binding succeeded.';
    } catch (err) {
      const error: BusinessError = err as BusinessError;
      if (isRetryable(error.code) && retryCount < MAX_RETRIES - 1) {
        retryCount++;
        Logger.warn(`Operation failed with code ${error.code}, retrying... (${retryCount}/${MAX_RETRIES})`);
        await new Promise<void>(resolve => setTimeout(resolve, RETRY_INTERVAL));
        continue;
      }
      const failureMessage: string = buildFailureMessage('USB Key binding', error);
      try {
        securityManager.closeSession(accountId);
      } catch (closeErr) {
        // Ignore errors when closing the session.
      }
      return failureMessage;
    }
  }
  return 'USB Key binding failed.';
}
```

## Removing Third-Party Custom Authentication Credentials

Remove a previously added third-party custom authentication credential only when you need to revoke this authentication method. The procedure in this section corresponds to steps 3 through 8 in [Developing Third-Party Custom Authentication](#developing-third-party-custom-authentication) for removing a credential. Unlike credential addition, you must first query the credentials to obtain credentialId. In step 8, you can optionally reset the device unlock policy to built-in system authentication.

To remove a credential:

1. The MDM application calls `getUserExtendCredential` to query the list of third-party custom authentication credentials and obtains the target credentialId from the returned list.
2. The MDM application calls `openSession` to open a session for changing user authentication credentials and obtain a challenge.
3. (Optional) The MDM application calls `getUserAuthInstance` to start user authentication, passing the challenge, the PIN authentication type, and the ATL4 trust level. After the user completes PIN authentication, authToken is obtained through the callback.
4. The MDM application calls `removeUserExtendCredential`, passing credentialId and authToken, to remove the third-party custom authentication credential.
5. The MDM application calls `closeSession` to close the session and complete credential removal.
6. (Optional) Call `setUnlockPolicy` to reset the device unlock policy to built-in system authentication.

![Removing a third-party custom authentication credential](figures/third_party_auth_remove.png)

> **NOTE**
>
> - `authType` supports only `PIN`, and `authTrustLevel` supports only `ATL4`.
> - `UserAuthInstance.start` displays the system password authentication widget, and the call blocks until the user completes authentication. System actions, such as locking the screen, may also close the widget.

The following example removes a credential:

<!-- @[unbind_usb_key](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/MDMKit/UsbKeyAuth/entry/src/main/ets/service/UsbKeyAuthService.ets) -->

``` TypeScript
export async function unbindUsbKey(uiContext: UIContext): Promise<string> {
  let retryCount: number = 0;

  // Step 1: Query bound USB Key credentials.
  let credentials: securityManager.UserExtCredentialInfo[];
  try {
    credentials = await securityManager.getUserExtendCredential(accountId);
  } catch (err) {
    const error: BusinessError = err as BusinessError;
    return buildFailureMessage('USB Key unbinding', error);
  }
  if (credentials.length === 0) {
    Logger.info('No USB Key credential found.');
    return 'No USB Key credential found.';
  }
  const targetCredentialId: Uint8Array = credentials[0].credentialId;

  while (retryCount < MAX_RETRIES) {
    try {
      // Step 2: Open a session and obtain the challenge.
      const challenge: Uint8Array = await securityManager.openSession(accountId);
      Logger.info('Succeeded in opening session.');

      // Step 3: Start user authentication and obtain the authentication token.
      const dialogTitle: string = resolveStringResource(uiContext, $r('app.string.unbind_auth_dialog_title'));
      const authToken: Uint8Array = await requestAuthToken(challenge, dialogTitle);
      Logger.info('Authentication succeeded.');

      // Step 4: Unbind the USB Key credential.
      const removeInfo: securityManager.RemoveCredentialInfo = {
        credentialId: targetCredentialId,
        authToken: authToken,
      };
      securityManager.removeUserExtendCredential(removeInfo, accountId);
      Logger.info('Succeeded in removing USB Key credential.');

      securityManager.closeSession(accountId);
      Logger.info('USB Key unbinding completed.');

      // Optional: Reset the unlock mode to the system default.
      securityManager.setUnlockPolicy(
        securityManager.UnlockPolicy.DEFAULT,
        accountId
      );
      Logger.info('Succeeded in resetting unlock policy.');
      return 'USB Key unbinding succeeded.';
    } catch (err) {
      const error: BusinessError = err as BusinessError;
      if (isRetryable(error.code) && retryCount < MAX_RETRIES - 1) {
        retryCount++;
        Logger.warn(`Operation failed with code ${error.code}, retrying... (${retryCount}/${MAX_RETRIES})`);
        await new Promise<void>(resolve => setTimeout(resolve, RETRY_INTERVAL));
        continue;
      }
      const failureMessage: string = buildFailureMessage('USB Key unbinding', error);
      try {
        securityManager.closeSession(accountId);
      } catch (closeErr) {
        // Ignore errors when closing the session.
      }
      return failureMessage;
    }
  }
  return 'USB Key unbinding failed.';
}
```

## Querying Third-Party Custom Authentication Credentials

Call [getUserExtendCredential](../reference/apis-mdm-kit/js-apis-enterprise-securityManager.md#securitymanagergetuserextendcredential) to query third-party custom authentication credentials that have been added. The returned credentialId is used to remove a credential.

<!-- @[query_credentials](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/MDMKit/UsbKeyAuth/entry/src/main/ets/service/UsbKeyAuthService.ets) -->

``` TypeScript
export async function queryCredentials(): Promise<string> {
  try {
    const credentials: securityManager.UserExtCredentialInfo[] =
      await securityManager.getUserExtendCredential(accountId);
    Logger.info(`Found ${credentials.length} USB Key credential(s).`);
    credentials.forEach((cred: securityManager.UserExtCredentialInfo, index: number) => {
      Logger.info(`Credential ${index}: pluginInfo=${cred.pluginInfo}`);
    });
    return `Found ${credentials.length} USB Key credential(s).`;
  } catch (err) {
    const error: BusinessError = err as BusinessError;
    return buildFailureMessage('Query credentials', error);
  }
}
```

## Configuring and Querying Unlock Policies

securityManager provides APIs for setting and querying device unlock policies. The following examples show how to use them:

### Setting the Unlock Policy

<!-- @[set_unlock_policy](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/MDMKit/UsbKeyAuth/entry/src/main/ets/service/UsbKeyAuthService.ets) -->

``` TypeScript
export function setUnlockPolicy(): string {
  try {
    securityManager.setUnlockPolicy(securityManager.UnlockPolicy.EXTENDED_AUTH_ONLY, accountId);
    Logger.info('Succeeded in setting unlock policy to EXTENDED_AUTH_ONLY.');
    return 'Set unlock policy succeeded.';
  } catch (err) {
    const error: BusinessError = err as BusinessError;
    return buildFailureMessage('Set unlock policy', error);
  }
}
```

### Querying the Unlock Policy

<!-- @[get_unlock_policy](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/MDMKit/UsbKeyAuth/entry/src/main/ets/service/UsbKeyAuthService.ets) -->

``` TypeScript
export function getUnlockPolicy(): string {
  try {
    const policy: securityManager.UnlockPolicy = securityManager.getUnlockPolicy(accountId);
    switch (policy) {
      case securityManager.UnlockPolicy.DEFAULT:
        Logger.info('Current unlock policy: DEFAULT (system default).');
        break;
      case securityManager.UnlockPolicy.EXTENDED_AUTH_ONLY:
        Logger.info('Current unlock policy: EXTENDED_AUTH_ONLY (USB Key only).');
        break;
      case securityManager.UnlockPolicy.EXTENDED_AUTH_REQUIRED:
        Logger.info('Current unlock policy: EXTENDED_AUTH_REQUIRED (USB Key + password).');
        break;
      default:
        Logger.info(`Unknown unlock policy: ${policy}`);
    }
    return `Current unlock policy: ${policy}`;
  } catch (err) {
    const error: BusinessError = err as BusinessError;
    return buildFailureMessage('Get unlock policy', error);
  }
}
```

## Error Handling

For details about errors returned by the third-party custom authentication APIs, see [Enterprise Device Management Error Codes](../reference/apis-mdm-kit/errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../reference/errorcode-universal.md).

## Recommended Retry Strategy

| Error Scenario | Retryable | Recommended Action |
| -------- | ---------- | ------------ |
| Session or authentication token expiration | Yes | Obtain a new session and authToken, and retry. |
| Service timeout | Yes | Wait 1-2 seconds before retrying, with a maximum of 3 retries. |
| Invalid parameters | No | Check and correct the parameters before trying again. |
| Permission or administrator errors | No | Check the permissions and administrator status. |
| Unsupported platform | No | Check the device type. |

## Samples

The following sample is available for third-party custom authentication development:

- [USB Key Authentication (ArkTS)](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/MDMKit/UsbKeyAuth)
