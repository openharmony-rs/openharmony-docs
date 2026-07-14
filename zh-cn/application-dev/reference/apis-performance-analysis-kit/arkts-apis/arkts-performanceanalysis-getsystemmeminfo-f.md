# getSystemMemInfo

## getSystemMemInfo

```TypeScript
function getSystemMemInfo(): SystemMemInfo
```

��ȡϵͳ�ڴ���Ϣ����ȡ/proc/meminfo�ڵ�����ݡ�

**起始版本：** 12

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**返回值：**

| 类型 | 说明 |
| --- | --- |
| SystemMemInfo | ϵͳ�ڴ���Ϣ�� |

**示例：**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';

let systemMemInfo: hidebug.SystemMemInfo = hidebug.getSystemMemInfo();

console.info(`totalMem: ${systemMemInfo.totalMem}, freeMem: ${systemMemInfo.freeMem}, ` +
  `availableMem: ${systemMemInfo.availableMem}`);

```

