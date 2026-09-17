# AuthTipCallback

```TypeScript
type AuthTipCallback = (authTipInfo: AuthTipInfo) => void
```

Defines the callback to return the intermediate authentication status. This callback is used to obtain various intermediate status information during authentication, including authentication failure, lockout, and loading and release of the authentication screen. By subscribing to these intermediate statuses, the application can provide more refined user interaction and status management during the authentication process.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| authTipInfo | [AuthTipInfo](arkts-userauthentication-userauth-authtipinfo-i.md) | Yes | Intermediate authentication status. It contains the authentication type (**tipType**) and status code (**tipCode**). The application should perform the corresponding processing based on the value of **tipCode**:<br>- **COMPARE_FAILURE(1)**: Prompt the user to try again. <br>- **TIMEOUT(2)**: Prompt the user that the operation has timed out. <br>- **TEMPORARILY_LOCKED(3)**: Prompt the user to wait for unlocking. <br>- **PERMANENTLY_LOCKED(4)**: Prompt the user to use PIN authentication. <br>- **WIDGET_LOADED(5)**: The authentication screen has been loaded and initialization can be performed. <br>- **WIDGET_RELEASED(6)**: The authentication screen has been released, and the subsequent operations can be performed. <br>- **COMPARE_FAILURE_WITH_FROZEN(7)**: Prompt the user that the authentication fails and the authenticator is locked. |
