# ReturnStatus

Return codes for the compression/decompression functions.

**Since:** 12

**System capability:** SystemCapability.BundleManager.Zlib

## OK

```TypeScript
OK = 0
```

The API is successfully called. This API is supported for use in atomic services.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.Zlib

## STREAM_END

```TypeScript
STREAM_END = 1
```

The API is successfully called, indicating that the entire data has been processed.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.Zlib

## NEED_DICT

```TypeScript
NEED_DICT = 2
```

The API is successfully called, indicating that a preset dictionary is required to continue decompression.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.Zlib

## ERRNO

```TypeScript
ERRNO = -1
```

The API fails to be called, indicating that the file operation is incorrect.

**Since:** 23

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.BundleManager.Zlib

## STREAM_ERROR

```TypeScript
STREAM_ERROR = -2
```

The API fails to be called, indicating that the compression or decompression stream is incorrect.

**Since:** 23

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.BundleManager.Zlib

## DATA_ERROR

```TypeScript
DATA_ERROR = -3
```

The API fails to be called, indicating that the input data is incorrect.

**Since:** 23

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.BundleManager.Zlib

## MEM_ERROR

```TypeScript
MEM_ERROR = -4
```

The API fails to be called, indicating that the memory allocation fails.

**Since:** 23

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.BundleManager.Zlib

## BUF_ERROR

```TypeScript
BUF_ERROR = -5
```

The API fails to be called, indicating that the input buffer is incorrect.

**Since:** 23

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.BundleManager.Zlib
