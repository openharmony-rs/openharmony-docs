# ResultCode (System API)

```TypeScript
enum ResultCode
```

Enumerates the authentication result codes.

**Since:** 8

<!--Device-osAccount-enum ResultCode--><!--Device-osAccount-enum ResultCode-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## BUSY

```TypeScript
BUSY = 7
```

The authentication executor is busy. Try again after a few seconds.

**Since:** 8

<!--Device-ResultCode-BUSY = 7--><!--Device-ResultCode-BUSY = 7-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## CANCELED

```TypeScript
CANCELED = 3
```

The authentication is canceled.

**Since:** 8

<!--Device-ResultCode-CANCELED = 3--><!--Device-ResultCode-CANCELED = 3-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## FAIL

```TypeScript
FAIL = 1
```

The authentication executor failed to identify the user.

**Since:** 8

<!--Device-ResultCode-FAIL = 1--><!--Device-ResultCode-FAIL = 1-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## GENERAL_ERROR

```TypeScript
GENERAL_ERROR = 2
```

Other errors.

**Since:** 8

<!--Device-ResultCode-GENERAL_ERROR = 2--><!--Device-ResultCode-GENERAL_ERROR = 2-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## INVALID_PARAMETERS

```TypeScript
INVALID_PARAMETERS = 8
```

Incorrect parameters are detected.

**Since:** 8

<!--Device-ResultCode-INVALID_PARAMETERS = 8--><!--Device-ResultCode-INVALID_PARAMETERS = 8-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## LOCKED

```TypeScript
LOCKED = 9
```

The authentication executor is locked.

**Since:** 8

<!--Device-ResultCode-LOCKED = 9--><!--Device-ResultCode-LOCKED = 9-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## NOT_ENROLLED

```TypeScript
NOT_ENROLLED = 10
```

The authentication executor is not enrolled.

**Since:** 8

<!--Device-ResultCode-NOT_ENROLLED = 10--><!--Device-ResultCode-NOT_ENROLLED = 10-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## SUCCESS

```TypeScript
SUCCESS = 0
```

The authentication is successful or the authentication feature is supported.

**Since:** 8

<!--Device-ResultCode-SUCCESS = 0--><!--Device-ResultCode-SUCCESS = 0-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## TIMEOUT

```TypeScript
TIMEOUT = 4
```

The authentication timed out.

**Since:** 8

<!--Device-ResultCode-TIMEOUT = 4--><!--Device-ResultCode-TIMEOUT = 4-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## TRUST_LEVEL_NOT_SUPPORT

```TypeScript
TRUST_LEVEL_NOT_SUPPORT = 6
```

The authentication trust level is not supported.

**Since:** 8

<!--Device-ResultCode-TRUST_LEVEL_NOT_SUPPORT = 6--><!--Device-ResultCode-TRUST_LEVEL_NOT_SUPPORT = 6-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## TYPE_NOT_SUPPORT

```TypeScript
TYPE_NOT_SUPPORT = 5
```

The authentication credential type is not supported.

**Since:** 8

<!--Device-ResultCode-TYPE_NOT_SUPPORT = 5--><!--Device-ResultCode-TYPE_NOT_SUPPORT = 5-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.
