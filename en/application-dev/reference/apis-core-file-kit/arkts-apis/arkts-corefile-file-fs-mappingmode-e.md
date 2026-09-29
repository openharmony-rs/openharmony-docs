# MappingMode

```TypeScript
declare enum MappingMode
```

Enumerated type of the file memory mapping mode, which can be used by the mmap API.

**Since:** 26.0.0

<!--Device-unnamed-declare enum MappingMode--><!--Device-unnamed-declare enum MappingMode-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

## READ_ONLY

```TypeScript
READ_ONLY = 0
```

Read-only mode. The file mapping area is not writable. An exception is thrown when the file mapping area is modified.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-MappingMode-READ_ONLY = 0--><!--Device-MappingMode-READ_ONLY = 0-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

## READ_WRITE

```TypeScript
READ_WRITE = 1
```

Read/Write mode. The modification is written to the file mapping area and then synchronized to the file by the operating system (non-real-time).

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-MappingMode-READ_WRITE = 1--><!--Device-MappingMode-READ_WRITE = 1-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

## PRIVATE

```TypeScript
PRIVATE = 2
```

Private mode. It is a copy-on-write mapping mechanism. Modifications to the mapping area are visible only to the current process and do not affect the raw file.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-MappingMode-PRIVATE = 2--><!--Device-MappingMode-PRIVATE = 2-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO
