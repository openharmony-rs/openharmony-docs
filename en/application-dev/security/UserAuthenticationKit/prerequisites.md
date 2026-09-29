# Before You Start

<!--Kit: User Authentication Kit-->
<!--Subsystem: UserIAM-->
<!--Owner: @WALL_EYE-->
<!--Designer: @lichangting518-->
<!--Tester: @jane_lz-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=1771c176eaebe95e0c5dbb4354b7f33c29e58cfc translatedAt=2026-09-20T11:04:13.106Z pushedAt=2026-09-20T11:12:05.402Z -->

Before you get started, learn about the development process.

- [Obtain supported authentication capabilities](obtain-supported-authentication-capabilities.md).

- [Initiate a request for user authentication and obtain the authentication result](start-authentication.md).

- Verify and use the authentication result. For details, see [Key Access Control via Secondary Authentication](../UniversalKeystoreKit/huks-identity-authentication-overview.md).

- (Optional) [Cancel authentication](cancel-authentication.md).

- (Optional) [Apply custom authentication](apply-custom-authentication.md).

## Requesting Permissions

Before developing an application capable of user authentication based on biometric features (such as face and fingerprints), you must apply for the ohos.permission.ACCESS_BIOMETRIC permission.

This permission is a system_grant permission and must be declared in the **requestPermissions** tag in the **module.json5** file. For details, see [Declaring Permissions](../AccessToken/declare-permissions.md).

To query and subscribe to user recognition results, you must request ohos.permission.ACCESS_USER_PASSIVE_RECOGNITION, which is also authorized in system_grant mode.
