# AuthorizationResultCode (System API)

```TypeScript
enum AuthorizationResultCode
```

Enumerates authorization result codes.

**Since:** 24

<!--Device-osAccount-enum AuthorizationResultCode--><!--Device-osAccount-enum AuthorizationResultCode-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## AUTHORIZATION_CANCELED

```TypeScript
AUTHORIZATION_CANCELED = 12300301
```

The authorization is canceled.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-AuthorizationResultCode-AUTHORIZATION_CANCELED = 12300301--><!--Device-AuthorizationResultCode-AUTHORIZATION_CANCELED = 12300301-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## AUTHORIZATION_DENIED

```TypeScript
AUTHORIZATION_DENIED = 12300303
```

Authorization is rejected because the authorization rules are not met. For example, the account is not an administrator or the device type is not supported.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-AuthorizationResultCode-AUTHORIZATION_DENIED = 12300303--><!--Device-AuthorizationResultCode-AUTHORIZATION_DENIED = 12300303-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## AUTHORIZATION_INTERACTION_NOT_ALLOWED

```TypeScript
AUTHORIZATION_INTERACTION_NOT_ALLOWED = 12300302
```

Authorization is rejected because user interaction is not allowed.

Possible causes:

1. The caller is in the background.
2. The value of **isInteractionAllowed** is **false**.
3. The specified interaction context is invalid.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-AuthorizationResultCode-AUTHORIZATION_INTERACTION_NOT_ALLOWED = 12300302--><!--Device-AuthorizationResultCode-AUTHORIZATION_INTERACTION_NOT_ALLOWED = 12300302-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## AUTHORIZATION_SERVICE_BUSY

```TypeScript
AUTHORIZATION_SERVICE_BUSY = 12300304
```

Authorization service is busy.

Possible cause: Another authorization is being processed.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-AuthorizationResultCode-AUTHORIZATION_SERVICE_BUSY = 12300304--><!--Device-AuthorizationResultCode-AUTHORIZATION_SERVICE_BUSY = 12300304-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## AUTHORIZATION_SUCCESS

```TypeScript
AUTHORIZATION_SUCCESS = 0
```

The authorization is successful.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-AuthorizationResultCode-AUTHORIZATION_SUCCESS = 0--><!--Device-AuthorizationResultCode-AUTHORIZATION_SUCCESS = 0-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.
