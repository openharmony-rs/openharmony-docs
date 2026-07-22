# getNativeHeapFreeSize

## 导入模块

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## getNativeHeapFreeSize

```TypeScript
function getNativeHeapFreeSize() : bigint
```

��ȡ�ڴ������ͳ�ƵĽ��̳��еĿ��е���ͨ����ռ�õ����ֽ�����

**起始版本：** 8

<!--Device-hidebug-function getNativeHeapFreeSize() : bigint--><!--Device-hidebug-function getNativeHeapFreeSize() : bigint-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**返回值：**

| 类型 | 说明 |
| --- | --- |
| bigint | �����ڴ������ͳ�ƵĽ��̳��еĿ��е���ͨ����ռ���ڴ��С����λΪByte�� |

**示例：**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';

let nativeHeapFreeSize: bigint = hidebug.getNativeHeapFreeSize();
console.info(`nativeHeapFreeSize = ${nativeHeapFreeSize}`);

```

