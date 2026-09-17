# CompressFlushMode

CompressFlushMode

**Since:** 12

**System capability:** SystemCapability.BundleManager.Zlib

## NO_FLUSH

```TypeScript
NO_FLUSH = 0
```

Default value, indicating a normal operation.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.Zlib

## PARTIAL_FLUSH

```TypeScript
PARTIAL_FLUSH = 1
```

Generates some refresh points in the stream.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.Zlib

## SYNC_FLUSH

```TypeScript
SYNC_FLUSH = 2
```

Forcibly outputs all compressed data while maintaining the compression stream state.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.Zlib

## FULL_FLUSH

```TypeScript
FULL_FLUSH = 3
```

Resets the compression state.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.Zlib

## FINISH

```TypeScript
FINISH = 4
```

Ends the compression or decompression process.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.Zlib

## BLOCK

```TypeScript
BLOCK = 5
```

Allows more precise control.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.Zlib

## TREES

```TypeScript
TREES = 6
```

Implements special purposes.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.BundleManager.Zlib
