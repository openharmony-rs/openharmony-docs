# getSystemMemInfo

## getSystemMemInfo

```TypeScript
function getSystemMemInfo(): SystemMemInfo
```

��ȡϵͳ�ڴ���Ϣ����ȡ/proc/meminfo�ڵ�����ݡ�

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-hidebug-function getSystemMemInfo(): SystemMemInfo--><!--Device-hidebug-function getSystemMemInfo(): SystemMemInfo-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | ϵͳ�ڴ���Ϣ�� |

**示例：**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';

let systemMemInfo: hidebug.SystemMemInfo = hidebug.getSystemMemInfo();

console.info(`totalMem: ${systemMemInfo.totalMem}, freeMem: ${systemMemInfo.freeMem}, ` +
  `availableMem: ${systemMemInfo.availableMem}`);
```

