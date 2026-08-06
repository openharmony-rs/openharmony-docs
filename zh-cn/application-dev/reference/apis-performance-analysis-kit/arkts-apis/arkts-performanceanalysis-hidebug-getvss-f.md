# getVss

## getVss

```TypeScript
function getVss(): bigint
```

��ȡӦ�ý���ռ�õ������ڴ��С���ӿ�ʵ�ַ�ʽ����ȡ/proc/{pid}/statm�ڵ��е�sizeֵ���ڴ�ҳ������vss = size * ҳ��С��4KB/ҳ����

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-hidebug-function getVss(): bigint--><!--Device-hidebug-function getVss(): bigint-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**返回值：**

| 类型 | 说明 |
| --- | --- |
| bigint | ����Ӧ�ý���ռ�õ������ڴ��С����λΪKB�� |

**示例：**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';

let vss: bigint = hidebug.getVss();
console.info(`vss = ${vss}`);
```

