# Obtaining Supported Authentication Capabilities

<!--Kit: User Authentication Kit-->
<!--Subsystem: UserIAM-->
<!--Owner: @WALL_EYE-->
<!--Designer: @lichangting518-->
<!--Tester: @jane_lz-->
<!--Adviser: @zengyawen-->

Different devices support different authentication capabilities (facial authentication, fingerprint authentication, and password authentication). Before you start coding, obtain the authentication capabilities supported by the target device.

## Available APIs

For details about the parameters, return value, and error codes, see [getAvailableStatus](../../reference/apis-user-authentication-kit/js-apis-useriam-userauth.md#userauthgetavailablestatus9).

| API| Description| 
| -------- | -------- |
| getAvailableStatus(authType : UserAuthType, authTrustLevel : AuthTrustLevel): void | Checks whether the specified authentication type and authentication trust level are supported by the device.| 

## How to Develop

1. [Request](prerequisites.md#requesting-permissions) the ohos.permission.ACCESS_BIOMETRIC permission.

2. Call [getAvailableStatus](../../reference/apis-user-authentication-kit/js-apis-useriam-userauth.md#userauthgetavailablestatus9) to check whether the device supports the specified authentication type ([UserAuthType](../../reference/apis-user-authentication-kit/js-apis-useriam-userauth.md#userauthtype8)) and authentication trust level ([AuthTrustLevel](../../reference/apis-user-authentication-kit/js-apis-useriam-userauth.md#authtrustlevel8)).

   For details about the authentication trust levels, see [Principles for Classifying Biometric Authentication Trust Levels](../../security/UserAuthenticationKit/user-authentication-overview.md#principles-for-classifying-biometric-authentication-trust-levels).

Example: Check whether the device supports facial authentication of ATL3 or higher.

<!-- @[obtain_supported_capabilities](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/UserAuthentication/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
  obtainingSupported() {
    try {
      // Check whether the specified authentication capabilities are supported.
      userAuth.getAvailableStatus(userAuth.UserAuthType.PIN, userAuth.AuthTrustLevel.ATL1);
      Logger.info('current auth trust level is supported');
      return true;
    } catch (error) {
      const err: BusinessError = error as BusinessError;
      Logger.error(`current auth trust level is not supported, code is ${err?.code}, message is ${err?.message}`);
      return false;
    }
  }

```


## Sample Code

  - [Querying supported authentication capabilities](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/UserAuthentication)
