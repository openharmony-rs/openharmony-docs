# getSystemMemInfo

## 导入模块

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

<a id="getsystemmeminfo"></a>
## getSystemMemInfo

```TypeScript
function getSystemMemInfo(): SystemMemInfo
```

��ȡϵͳ�ڴ���Ϣ����ȡ/proc/meminfo�ڵ�����ݡ�

**起始版本：** 12

<!--Device-hidebug-function getSystemMemInfo(): SystemMemInfo--><!--Device-hidebug-function getSystemMemInfo(): SystemMemInfo-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [SystemMemInfo](arkts-performanceanalysis-hidebug-systemmeminfo-i.md) | ϵͳ�ڴ���Ϣ�� |

**示例：**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';

let systemMemInfo: hidebug.SystemMemInfo = hidebug.getSystemMemInfo();

console.info(`totalMem: ${systemMemInfo.totalMem}, freeMem: ${systemMemInfo.freeMem}, ` +
  `availableMem: ${systemMemInfo.availableMem}`);

```

