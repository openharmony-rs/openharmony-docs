# getNativeHeapSize

## getNativeHeapSize

```TypeScript
function getNativeHeapSize() : bigint
```

��ȡ�ڴ������ͳ�ƵĽ��̳��е���ͨ����ռ�õ����ֽ�����

**起始版本：** 8

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**返回值：**

| 类型 | 说明 |
| --- | --- |
| bigint | �ڴ������ͳ�ƵĽ��̳��е���ͨ����ռ���ڴ�Ĵ�С����������Ԫ���ݣ�����λΪByte�� |

**示例：**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';

let nativeHeapSize: bigint = hidebug.getNativeHeapSize();
console.info(`nativeHeapSize = ${nativeHeapSize}`);

```

