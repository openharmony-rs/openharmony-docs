# ReuseMode

```TypeScript
enum ReuseMode
```

Enumerates the modes for reusing authentication results. This enum defines four modes for reusing authentication results and is used to control which authentication results can be reused under what conditions. The application can select a proper reuse mode based on the service scenario to balance security and user experience.

**Since:** 12

<!--Device-userAuth-enum ReuseMode--><!--Device-userAuth-enum ReuseMode-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## AUTH_TYPE_IRRELEVANT

```TypeScript
AUTH_TYPE_IRRELEVANT = 2
```

Irrelevant to the authentication type. The device unlock authentication result can be reused within the validity period regardless of the authentication type.

For example, after a user uses face authentication to unlock the device, the authentication result can be reused within the validity period if the user initiates a service operation that requires fingerprint or PIN authentication.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ReuseMode-AUTH_TYPE_IRRELEVANT = 2--><!--Device-ReuseMode-AUTH_TYPE_IRRELEVANT = 2-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## AUTH_TYPE_RELEVANT

```TypeScript
AUTH_TYPE_RELEVANT = 1
```

Related to the authentication type. The device unlock authentication result can be reused only when it is within the validity period and the authentication type used for device unlock matches one of the authentication types specified for the current authentication.

For example, after a user uses face authentication to unlock the device, the unlock result can be reused directly if the user initiates a service operation that requires face authentication within the validity period; however, it cannot be reused if the user initiates a service operation that requires fingerprint authentication.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ReuseMode-AUTH_TYPE_RELEVANT = 1--><!--Device-ReuseMode-AUTH_TYPE_RELEVANT = 1-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## CALLER_IRRELEVANT_AUTH_TYPE_IRRELEVANT

```TypeScript
CALLER_IRRELEVANT_AUTH_TYPE_IRRELEVANT = 4
```

Irrelevant to the authentication type. The result of any identity authentication (including device unlock) can be reused within the validity period regardless of the authentication type.

For example, after a user completes an operation using face authentication in an application, another application can reuse the previous authentication result within the validity period if it initiates an authentication operation of any type.

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-ReuseMode-CALLER_IRRELEVANT_AUTH_TYPE_IRRELEVANT = 4--><!--Device-ReuseMode-CALLER_IRRELEVANT_AUTH_TYPE_IRRELEVANT = 4-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## CALLER_IRRELEVANT_AUTH_TYPE_RELEVANT

```TypeScript
CALLER_IRRELEVANT_AUTH_TYPE_RELEVANT = 3
```

Related to the authentication type. The result of any identity authentication (including device unlock) can be reused only when it is within the validity period and the authentication type of the identity authentication matches one of the authentication types specified for the current authentication.

For example, after a user completes a payment using face authentication in an application, another application can reuse the previous authentication result within the validity period if it initiates an operation that requires face authentication; however, it cannot be reused if the operation requires fingerprint authentication.

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-ReuseMode-CALLER_IRRELEVANT_AUTH_TYPE_RELEVANT = 3--><!--Device-ReuseMode-CALLER_IRRELEVANT_AUTH_TYPE_RELEVANT = 3-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core
