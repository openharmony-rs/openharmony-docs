# AccessModeType

Enumerates the access modes to verify. If this parameter is left blank, the system checks whether the file exists.

**Since:** 12

**System capability:** SystemCapability.FileManagement.File.FileIO

## EXIST

```TypeScript
EXIST = 0
```

Whether the file exists.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.File.FileIO

## WRITE

```TypeScript
WRITE = 2
```

Verify the write permission on the file.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.File.FileIO

## READ

```TypeScript
READ = 4
```

Verify the read permission on the file.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.File.FileIO

## READ_WRITE

```TypeScript
READ_WRITE = 6
```

Verify the read/write permission on the file.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.FileManagement.File.FileIO
