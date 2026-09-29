# ReturnStatus

```TypeScript
export enum ReturnStatus
```

Return codes for the compression/decompression functions.

**Since:** 12

<!--Device-zlib-export enum ReturnStatus--><!--Device-zlib-export enum ReturnStatus-End-->

**System capability:** SystemCapability.BundleManager.Zlib

## OK

```TypeScript
OK = 0
```

The API is successfully called. This API is supported for use in atomic services.

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ReturnStatus-OK = 0--><!--Device-ReturnStatus-OK = 0-End-->

**System capability:** SystemCapability.BundleManager.Zlib

## STREAM_END

```TypeScript
STREAM_END = 1
```

The API is successfully called, indicating that the entire data has been processed.

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ReturnStatus-STREAM_END = 1--><!--Device-ReturnStatus-STREAM_END = 1-End-->

**System capability:** SystemCapability.BundleManager.Zlib

## NEED_DICT

```TypeScript
NEED_DICT = 2
```

The API is successfully called, indicating that a preset dictionary is required to continue decompression.

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-ReturnStatus-NEED_DICT = 2--><!--Device-ReturnStatus-NEED_DICT = 2-End-->

**System capability:** SystemCapability.BundleManager.Zlib

## ERRNO

```TypeScript
ERRNO = -1
```

The API fails to be called, indicating that the file operation is incorrect.

**Since:** 23

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 23.

<!--Device-ReturnStatus-ERRNO = -1--><!--Device-ReturnStatus-ERRNO = -1-End-->

**System capability:** SystemCapability.BundleManager.Zlib

## STREAM_ERROR

```TypeScript
STREAM_ERROR = -2
```

The API fails to be called, indicating that the compression or decompression stream is incorrect.

**Since:** 23

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 23.

<!--Device-ReturnStatus-STREAM_ERROR = -2--><!--Device-ReturnStatus-STREAM_ERROR = -2-End-->

**System capability:** SystemCapability.BundleManager.Zlib

## DATA_ERROR

```TypeScript
DATA_ERROR = -3
```

The API fails to be called, indicating that the input data is incorrect.

**Since:** 23

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 23.

<!--Device-ReturnStatus-DATA_ERROR = -3--><!--Device-ReturnStatus-DATA_ERROR = -3-End-->

**System capability:** SystemCapability.BundleManager.Zlib

## MEM_ERROR

```TypeScript
MEM_ERROR = -4
```

The API fails to be called, indicating that the memory allocation fails.

**Since:** 23

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 23.

<!--Device-ReturnStatus-MEM_ERROR = -4--><!--Device-ReturnStatus-MEM_ERROR = -4-End-->

**System capability:** SystemCapability.BundleManager.Zlib

## BUF_ERROR

```TypeScript
BUF_ERROR = -5
```

The API fails to be called, indicating that the input buffer is incorrect.

**Since:** 23

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 23.

<!--Device-ReturnStatus-BUF_ERROR = -5--><!--Device-ReturnStatus-BUF_ERROR = -5-End-->

**System capability:** SystemCapability.BundleManager.Zlib
