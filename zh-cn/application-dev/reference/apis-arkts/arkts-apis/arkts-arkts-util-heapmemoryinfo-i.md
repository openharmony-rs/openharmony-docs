# HeapMemoryInfo

描述 ArkTS-VM 的堆内存信息，或当前进程的共享堆内存信息。

**起始版本：** 24

<!--Device-util-interface HeapMemoryInfo--><!--Device-util-interface HeapMemoryInfo-End-->

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { util } from '@kit.ArkTS';
```

## heapObjectSize

```TypeScript
heapObjectSize: number
```

该值为整数，表示来自 ArkTS-VM 的 local 堆或 shared 堆的所有堆对象的总大小（KB）。

**类型：** number

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HeapMemoryInfo-heapObjectSize: number--><!--Device-HeapMemoryInfo-heapObjectSize: number-End-->

**系统能力：** SystemCapability.Utils.Lang

## heapType

```TypeScript
heapType: string
```

该值为字符串，表示此内存信息是来自 ArkTS-VM 的 local 堆还是 shared 堆。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HeapMemoryInfo-heapType: string--><!--Device-HeapMemoryInfo-heapType: string-End-->

**系统能力：** SystemCapability.Utils.Lang

## threadId

```TypeScript
threadId?: number
```

如果此内存信息描述的是 ArkTS-VM 的 local 堆，该值为表示运行线程 ID 的整数；如果此内存信息描述的是 shared 堆，则该值为 undefined。

**类型：** number

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HeapMemoryInfo-threadId?: number--><!--Device-HeapMemoryInfo-threadId?: number-End-->

**系统能力：** SystemCapability.Utils.Lang

## threadName

```TypeScript
threadName?: string
```

如果此内存信息描述的是 ArkTS-VM 的 local 堆，该值为表示运行线程名称的字符串；如果此内存信息描述的是 shared 堆，则该值为 undefined。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HeapMemoryInfo-threadName?: string--><!--Device-HeapMemoryInfo-threadName?: string-End-->

**系统能力：** SystemCapability.Utils.Lang

