# StrongAuthReasonFlags (System API)

Indicates the strong authentication reason flags used to request.

@enum { int }

**Since:** 12

**System capability:** SystemCapability.MiscServices.ScreenLock

**System API:** This is a system API.

## NONE

```TypeScript
NONE = 0x00000000
```

Indicates that there are no strong authentication reason flags.

**Since:** 12

**System capability:** SystemCapability.MiscServices.ScreenLock

**System API:** This is a system API.

## AFTER_BOOT

```TypeScript
AFTER_BOOT = 0x00000001
```

Indicates the strong authentication reason requested after boot.

**Since:** 12

**System capability:** SystemCapability.MiscServices.ScreenLock

**System API:** This is a system API.

## AFTER_TIMEOUT

```TypeScript
AFTER_TIMEOUT = 0x00000002
```

Indicates the strong authentication reason requested after timeout.

**Since:** 12

**System capability:** SystemCapability.MiscServices.ScreenLock

**System API:** This is a system API.

## ACTIVE_REQUEST

```TypeScript
ACTIVE_REQUEST = 0x00000004
```

Indicates the strong authentication reason requested by active request.

**Since:** 12

**System capability:** SystemCapability.MiscServices.ScreenLock

**System API:** This is a system API.

## POLICY_RESTRICTION

```TypeScript
POLICY_RESTRICTION = 0x00000008
```

Indicates the strong authentication reason requested by policy restriction.

**Since:** 12

**System capability:** SystemCapability.MiscServices.ScreenLock

**System API:** This is a system API.
