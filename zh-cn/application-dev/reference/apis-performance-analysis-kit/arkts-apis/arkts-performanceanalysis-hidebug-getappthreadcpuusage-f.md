# getAppThreadCpuUsage

## 导入模块

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## getAppThreadCpuUsage

```TypeScript
function getAppThreadCpuUsage(): ThreadCpuUsage[]
```

��ȡӦ���߳�CPUʹ�������
> **ע��**  
>  
> ���ڸýӿ��漰�����ͨ�ţ���ʱ�ϳ���Ϊ�˱��������������⣬���鲻Ҫ�����߳���ֱ�ӵ��øýӿڡ�

**起始版本：** 12

<!--Device-hidebug-function getAppThreadCpuUsage(): ThreadCpuUsage[]--><!--Device-hidebug-function getAppThreadCpuUsage(): ThreadCpuUsage[]-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ThreadCpuUsage](arkts-performanceanalysis-hidebug-threadcpuusage-i.md)[] | ���ص�ǰӦ�ý���������ThreadCpuUsage���顣 |

**示例：**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';

let appThreadCpuUsage: hidebug.ThreadCpuUsage[] = hidebug.getAppThreadCpuUsage();
for (let i = 0; i < appThreadCpuUsage.length; i++) {
  console.info(`threadId=${appThreadCpuUsage[i].threadId}, cpuUsage=${appThreadCpuUsage[i].cpuUsage}`);
}

```

