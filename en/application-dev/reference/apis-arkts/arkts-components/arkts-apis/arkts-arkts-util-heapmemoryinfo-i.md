# HeapMemoryInfo

Describes heap memory information of either an ArkTS-VM, or the shared heap memory of current process.

**Since:** 24

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { util } from '@kit.ArkTS';
```

## heapObjectSize

```TypeScript
heapObjectSize: number
```

The value is a number representing the total size of all heap objects in KB, from either an ArkTS-VM local heap or the shared heap.

**Type:** number

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Utils.Lang

## heapType

```TypeScript
heapType: string
```

The value is a string representing whether this memory information is from an ArkTS-VM local heap, or the shared heap.

**Type:** string

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Utils.Lang

## threadId

```TypeScript
threadId?: number
```

If this memory information describes an ArkTS-VM local heap, the value is a number representing the running thread; If this memory information describes the shared heap, the value is undefined.

**Type:** number

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Utils.Lang

## threadName

```TypeScript
threadName?: string
```

If this memory information describes an ArkTS-VM local heap, the value is a string representing the name of the running thread; If this memory information describes the shared heap, the value is undefined.

**Type:** string

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Utils.Lang
