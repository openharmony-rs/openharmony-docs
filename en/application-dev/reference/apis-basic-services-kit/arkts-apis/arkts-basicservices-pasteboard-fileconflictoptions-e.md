# FileConflictOptions

Enumerates options for file copy conflicts.

**Since:** 15

**System capability:** SystemCapability.MiscServices.Pasteboard

## OVERWRITE

```TypeScript
OVERWRITE = 0
```

Overwrites the file with the same name in the destination path.

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.MiscServices.Pasteboard

## SKIP

```TypeScript
SKIP = 1
```

Skips the file with the same name in the destination path. If **SKIP** is set, the copied data of the skipped file is not pasted to the application.

**Since:** 15

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.MiscServices.Pasteboard
