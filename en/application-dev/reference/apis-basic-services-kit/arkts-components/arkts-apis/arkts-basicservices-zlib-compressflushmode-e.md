# CompressFlushMode

```TypeScript
export enum CompressFlushMode
```

CompressFlushMode

**Since:** 12

<!--Device-zlib-export enum CompressFlushMode--><!--Device-zlib-export enum CompressFlushMode-End-->

**System capability:** SystemCapability.BundleManager.Zlib

## NO_FLUSH

```TypeScript
NO_FLUSH = 0
```

Default value, indicating a normal operation.

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-CompressFlushMode-NO_FLUSH = 0--><!--Device-CompressFlushMode-NO_FLUSH = 0-End-->

**System capability:** SystemCapability.BundleManager.Zlib

## PARTIAL_FLUSH

```TypeScript
PARTIAL_FLUSH = 1
```

Generates some refresh points in the stream.

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-CompressFlushMode-PARTIAL_FLUSH = 1--><!--Device-CompressFlushMode-PARTIAL_FLUSH = 1-End-->

**System capability:** SystemCapability.BundleManager.Zlib

## SYNC_FLUSH

```TypeScript
SYNC_FLUSH = 2
```

Forcibly outputs all compressed data while maintaining the compression stream state.

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-CompressFlushMode-SYNC_FLUSH = 2--><!--Device-CompressFlushMode-SYNC_FLUSH = 2-End-->

**System capability:** SystemCapability.BundleManager.Zlib

## FULL_FLUSH

```TypeScript
FULL_FLUSH = 3
```

Resets the compression state.

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-CompressFlushMode-FULL_FLUSH = 3--><!--Device-CompressFlushMode-FULL_FLUSH = 3-End-->

**System capability:** SystemCapability.BundleManager.Zlib

## FINISH

```TypeScript
FINISH = 4
```

Ends the compression or decompression process.

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-CompressFlushMode-FINISH = 4--><!--Device-CompressFlushMode-FINISH = 4-End-->

**System capability:** SystemCapability.BundleManager.Zlib

## BLOCK

```TypeScript
BLOCK = 5
```

Allows more precise control.

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-CompressFlushMode-BLOCK = 5--><!--Device-CompressFlushMode-BLOCK = 5-End-->

**System capability:** SystemCapability.BundleManager.Zlib

## TREES

```TypeScript
TREES = 6
```

Implements special purposes.

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 12.

<!--Device-CompressFlushMode-TREES = 6--><!--Device-CompressFlushMode-TREES = 6-End-->

**System capability:** SystemCapability.BundleManager.Zlib
