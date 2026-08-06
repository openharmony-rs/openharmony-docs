# getAppThreadCpuUsage

## getAppThreadCpuUsage

```TypeScript
function getAppThreadCpuUsage(): ThreadCpuUsage[]
```

��ȡӦ���߳�CPUʹ������� > **ע��** > > ���ڸýӿ��漰�����ͨ�ţ���ʱ�ϳ���Ϊ�˱��������������⣬���鲻Ҫ�����߳���ֱ�ӵ��øýӿڡ�

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-hidebug-function getAppThreadCpuUsage(): ThreadCpuUsage[]--><!--Device-hidebug-function getAppThreadCpuUsage(): ThreadCpuUsage[]-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_[] | ���ص�ǰӦ�ý���������ThreadCpuUsage���顣 |

**示例：**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';

let appThreadCpuUsage: hidebug.ThreadCpuUsage[] = hidebug.getAppThreadCpuUsage();
for (let i = 0; i < appThreadCpuUsage.length; i++) {
  console.info(`threadId=${appThreadCpuUsage[i].threadId}, cpuUsage=${appThreadCpuUsage[i].cpuUsage}`);
}
```

