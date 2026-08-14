# getNativeHeapAllocatedSize

## getNativeHeapAllocatedSize

```TypeScript
function getNativeHeapAllocatedSize() : bigint
```

获取内存分配器统计的进程持有的已使用的普通块所占用的总字节数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-hidebug-function getNativeHeapAllocatedSize() : bigint--><!--Device-hidebug-function getNativeHeapAllocatedSize() : bigint-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**返回值：**

| 类型 | 说明 |
| --- | --- |
| bigint | 返回内存分配器统计的进程持有的已使用的普通块所占用内存大小，单位为Byte。 |

## 示例

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';

let nativeHeapAllocatedSize: bigint = hidebug.getNativeHeapAllocatedSize();
console.info(`nativeHeapAllocatedSize = ${nativeHeapAllocatedSize}`);
```

