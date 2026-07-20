# getAppVMMemoryInfo

## 导入模块

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

<a id="getappvmmemoryinfo"></a>
## getAppVMMemoryInfo

```TypeScript
function getAppVMMemoryInfo(): VMMemoryInfo
```

��ȡVM�ڴ������Ϣ��

**起始版本：** 12

<!--Device-hidebug-function getAppVMMemoryInfo(): VMMemoryInfo--><!--Device-hidebug-function getAppVMMemoryInfo(): VMMemoryInfo-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [VMMemoryInfo](arkts-performanceanalysis-hidebug-vmmemoryinfo-i.md) | ����VM�ڴ���Ϣ�� |

**示例：**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';

let vmMemory: hidebug.VMMemoryInfo = hidebug.getAppVMMemoryInfo();
console.info(`totalHeap = ${vmMemory.totalHeap}, heapUsed = ${vmMemory.heapUsed},` +
  `allArraySize = ${vmMemory.allArraySize}` );

```

