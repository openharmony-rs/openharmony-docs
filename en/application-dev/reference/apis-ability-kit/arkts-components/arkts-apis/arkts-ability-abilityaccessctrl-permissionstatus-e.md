# PermissionStatus

Enumerates the permission states.

**Since:** 20

**System capability:** SystemCapability.Security.AccessToken

## DENIED

```TypeScript
DENIED = -1
```

The permission is not granted.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Security.AccessToken

## GRANTED

```TypeScript
GRANTED = 0
```

The permission is granted.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Security.AccessToken

## NOT_DETERMINED

```TypeScript
NOT_DETERMINED = 1
```

Indicates not operated. The app declares a [user authorization permission](arkts-ability-permissions-t.md) but has not yet called the [requestPermissionsFromUser](arkts-ability-abilityaccessctrl-atmanager-i.md#requestpermissionsfromuser) API to request authorization, or the user has changed the permission status to asking eve this value is returned when querying the permission status.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Security.AccessToken

## INVALID

```TypeScript
INVALID = 2
```

The permission is invalid. The application does not [declare permissions](../../../security/AccessToken/declare-permissions.md) or cannot process the request. For example, if the status of the approximate location permission is **NOT_DETERMINED**, this value will be returned when the status of the precise location permission is queried.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Security.AccessToken

## RESTRICTED

```TypeScript
RESTRICTED = 3
```

Indicates restricted. &lt;!--RP2--&gt;The app is prohibited from requesting user authorization through the [requestPermissionsFromUser](arkts-ability-abilityaccessctrl-atmanager-i.md#requestpermissionsfromuser) API. &lt;!--RP2End--&gt;

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Security.AccessToken
