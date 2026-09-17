# ReuseMode

Enumerates the modes for reusing authentication results. This enum defines four modes for reusing authentication results and is used to control which authentication results can be reused under what conditions. The application can select a proper reuse mode based on the service scenario to balance security and user experience.

**Since:** 12

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## AUTH_TYPE_RELEVANT

```TypeScript
AUTH_TYPE_RELEVANT = 1
```

The device unlock authentication result can be reused within the validity period if the authentication type matches any of the authentication types specified for this authentication.

For example, after a user uses face authentication to unlock the device, the authentication result can be reused within the validity period if the user initiates a service operation that requires face authentication. However, if the user initiates a service operation that requires fingerprint authentication, the authentication result cannot be reused.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## AUTH_TYPE_IRRELEVANT

```TypeScript
AUTH_TYPE_IRRELEVANT = 2
```

The device unlock authentication result can be reused within the validity period regardless of the authentication type.

For example, after a user uses face authentication to unlock the device, the authentication result can be reused within the validity period if the user initiates a service operation that requires fingerprint or PIN authentication.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## CALLER_IRRELEVANT_AUTH_TYPE_RELEVANT

```TypeScript
CALLER_IRRELEVANT_AUTH_TYPE_RELEVANT = 3
```

Any identity authentication result (including device unlock authentication result) can be reused within the validity period if the authentication type matches any of the authentication types specified for this authentication.

For example, after a user uses face authentication to complete payment in an application, the authentication result can be reused within the validity period if the user initiates an operation that requires face authentication in another application. However, if the user initiates an operation that requires fingerprint authentication, the authentication result cannot be reused.

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## CALLER_IRRELEVANT_AUTH_TYPE_IRRELEVANT

```TypeScript
CALLER_IRRELEVANT_AUTH_TYPE_IRRELEVANT = 4
```

Any identity authentication result (including device unlock authentication result) can be reused within the validity period regardless of the authentication type.

For example, after a user uses face authentication to complete an operation in an application, the authentication result can be reused within the validity period if the user initiates an authentication operation of any type in another application.

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.UserIAM.UserAuth.Core
