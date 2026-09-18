# RawFileDescriptor

This module provides file descriptor information of the HAP where the `rawfile` file is located, including the file descriptor, start offset, and file length.

**Since:** 8

**System capability:** SystemCapability.Global.ResourceManager

## fd

```TypeScript
fd: number
```

File descriptor.

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

## length

```TypeScript
length: number
```

File length, indicating the size of the `rawfile` file. The unit is bytes.

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager

## offset

```TypeScript
offset: number
```

Start offset, indicating the start position of the `rawfile` file in the HAP. The unit is bytes.

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Global.ResourceManager
