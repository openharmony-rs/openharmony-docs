# ActionType

Enumerates the actions to be performed when the file's permission expiration time is reached. The default value is **NOT_OPEN**.

**Since:** 21

**System capability:** SystemCapability.Security.DataLossPrevention

## NOT_OPEN

```TypeScript
NOT_OPEN = 0
```

Users are not allowed to open the DLP file when the file's permission expiration time is reached.

**Since:** 21

**System capability:** SystemCapability.Security.DataLossPrevention

## OPEN

```TypeScript
OPEN = 1
```

Logged-in accounts can still open and edit the DLP file when the file's permission expiration time is reached.

**Since:** 21

**System capability:** SystemCapability.Security.DataLossPrevention
