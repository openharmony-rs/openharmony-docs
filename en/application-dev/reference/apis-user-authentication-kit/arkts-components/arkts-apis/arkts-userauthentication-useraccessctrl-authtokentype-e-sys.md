# AuthTokenType (System API)

Enumerates the authentication token types. They are used to identify the source of the token.

**Since:** 18

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**System API:** This is a system API.

## TOKEN_TYPE_LOCAL_AUTH

```TypeScript
TOKEN_TYPE_LOCAL_AUTH = 0
```

Local authentication token. It is an authentication token issued based on the local authentication result, indicating that the user has been authenticated on the local device.

**Since:** 18

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**System API:** This is a system API.

## TOKEN_TYPE_LOCAL_RESIGN

```TypeScript
TOKEN_TYPE_LOCAL_RESIGN = 1
```

Local resigning token. It is an authentication token signed based on the reused authentication result, indicating that the current authentication result is reused from a previous authentication result.

**Since:** 18

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**System API:** This is a system API.

## TOKEN_TYPE_COAUTH

```TypeScript
TOKEN_TYPE_COAUTH = 2
```

Collaborative authentication token. It is an authentication token issued based on multiple device collaboration authentication results, indicating that the user has completed authentication through multi-device collaboration.

**Since:** 18

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**System API:** This is a system API.
