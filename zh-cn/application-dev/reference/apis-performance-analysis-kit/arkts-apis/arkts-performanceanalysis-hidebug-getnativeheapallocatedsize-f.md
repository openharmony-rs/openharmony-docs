# getNativeHeapAllocatedSize

## getNativeHeapAllocatedSize

```TypeScript
function getNativeHeapAllocatedSize() : bigint
```

��ȡ�ڴ������ͳ�ƵĽ��̳��е���ʹ�õ���ͨ����ռ�õ����ֽ�����

**起始版本：** 8

**ArkTS模式：** ArkTS-Dyn起始版本为8；ArkTS-Sta起始版本为23。

<!--Device-hidebug-function getNativeHeapAllocatedSize() : bigint--><!--Device-hidebug-function getNativeHeapAllocatedSize() : bigint-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**返回值：**

| 类型 | 说明 |
| --- | --- |
| bigint | �����ڴ������ͳ�ƵĽ��̳��е���ʹ�õ���ͨ����ռ���ڴ��С����λΪByte�� |

**示例：**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';

let nativeHeapAllocatedSize: bigint = hidebug.getNativeHeapAllocatedSize();
console.info(`nativeHeapAllocatedSize = ${nativeHeapAllocatedSize}`);
```

