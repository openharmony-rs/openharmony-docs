# @ohos.userIAM.userAccessCtrl(User Access Control)

The **userAccessCtrl** module is a core component of the OpenHarmony user identity and access management (UserIAM) system. It is dedicated to the verification and management of authentication tokens. This module provides APIs for verifying authentication tokens (**AuthToken**). It can parse and verify user authentication results and return detailed authentication information.

This module applies to the following scenarios:

- System-level applications need to verify the validity of user authentication tokens to ensure access security.  
- Detailed information about the authentication token needs to be obtained, such as the authentication type, trust  
level, and user ID, for precise user identity identification.  
- Access control decisions need to be made based on the authentication result to implement fine-grained permission  
management.

**Since:** 18

**System capability:** SystemCapability.UserIAM.UserAuth.Core

## Modules to Import

```TypeScript
import { userAccessCtrl } from '@kit.UserAuthenticationKit';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [verifyAuthToken](arkts-userauthentication-useraccessctrl-verifyauthtoken-f-sys.md) | Verifies an authentication token. This API is used to verify the validity of an **AuthToken**, including the integrity and validity check. After the verification is successful, the detailed information about the parsed **AuthToken** is returned. This API uses a promise to return the result. |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [AuthToken](arkts-userauthentication-useraccessctrl-authtoken-i-sys.md) | Defines the authentication token data. It indicates the parsed **AuthToken** data returned after the verification is successful, including detailed authentication information such as the challenge value, authentication trust level, authentication type, and user ID. |
<!--DelEnd-->

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [AuthTokenType](arkts-userauthentication-useraccessctrl-authtokentype-e-sys.md) | Enumerates the authentication token types. They are used to identify the source of the token. |
<!--DelEnd-->
