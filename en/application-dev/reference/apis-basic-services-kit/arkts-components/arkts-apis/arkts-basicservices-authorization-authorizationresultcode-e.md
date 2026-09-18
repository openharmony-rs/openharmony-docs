# AuthorizationResultCode

Enumerates authorization result codes.

**Since:** 26.1.0

**System capability:** SystemCapability.Account.OsAccount

## AUTHORIZATION_GRANTED

```TypeScript
AUTHORIZATION_GRANTED = 0
```

The authorization is granted.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Account.OsAccount

## AUTHORIZATION_CANCELED

```TypeScript
AUTHORIZATION_CANCELED = 12300301
```

The authorization is canceled by the user or the user's agent.

Possible causes: The user explicitly dismissed the authorization dialog (e.g., clicking the 'Cancel'button, clicking the window close action).

> **NOTE:** 
> Suggested solutions:
> 1. Treat this as an expected human-driven workflow discontinuation rather than a system fault.
> 2. Implement a non-intrusive UX notification or status fallback (e.g., smoothly roll back the UI and update a status label to "Authorization Canceled" or "Action Dismissed").

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Account.OsAccount

## AUTHORIZATION_DENIED

```TypeScript
AUTHORIZATION_DENIED = 12300303
```

The authorization is denied by the system policy.

Possible causes: The authorization policy for the privilege is not met. For example, the privilege requires the caller to possess the specified application permissions and run under an administrative OS account session.

> **NOTE:** 
> Suggested solutions:
> 1. Check the authorization policy configurations for the target privilege.
> 2. Implement appropriate fallback handling or graceful degradation(e.g., suggesting the user switch to an administrative environment, or prompting that the feature is temporarily unavailable).

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Account.OsAccount

## AUTHORIZATION_NOT_SUPPORTED

```TypeScript
AUTHORIZATION_NOT_SUPPORTED = 12300305
```

Authorization is not supported. This indicates that the requested target privilege is entirely unregistered or missing in the current system version, and the associated functionality is generally also unsupported.

Possible causes: A newer application version containing cutting-edge system features is running on an unupgraded, legacy host OS that has no definition of this newly introduced privilege.

> **NOTE:** 
> Suggested solutions: A fallback mechanism should be implemented,
> such as prompting that the feature is unavailable or skipping the operation.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Account.OsAccount
