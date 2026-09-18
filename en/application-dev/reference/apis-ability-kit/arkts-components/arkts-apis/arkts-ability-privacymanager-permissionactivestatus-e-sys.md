# PermissionActiveStatus (System API)

Enumerates the types of permission usage status changes. It is used to describe the change type of permission usage status, returned in the callback of subscribing to permission usage status change events (via [on('activeStateChange')](arkts-ability-privacymanager-on-f-sys.md)), helping system applications sense the status switch of a permission from unused to foreground use and background use.

**Since:** 9

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## PERM_INACTIVE

```TypeScript
PERM_INACTIVE = 0
```

The permission is not used.

**Since:** 9

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## PERM_ACTIVE_IN_FOREGROUND

```TypeScript
PERM_ACTIVE_IN_FOREGROUND = 1
```

The permission is being used by an application running in the foreground.

**Since:** 9

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.

## PERM_ACTIVE_IN_BACKGROUND

```TypeScript
PERM_ACTIVE_IN_BACKGROUND = 2
```

The permission is being used by an application running in the background.

**Since:** 9

**System capability:** SystemCapability.Security.AccessToken

**System API:** This is a system API.
