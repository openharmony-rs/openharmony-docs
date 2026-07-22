# getSystemCpuUsage

## 导入模块

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## getSystemCpuUsage

```TypeScript
function getSystemCpuUsage(): number
```

��ȡϵͳ��CPU��Դռ�������
> **ע��**  
>  
> ���ڸýӿ��漰�����ͨ�ţ���ʱ�ϳ���Ϊ�˱��������������⣬���鲻Ҫ�����߳���ֱ�ӵ��øýӿڡ�

**起始版本：** 12

<!--Device-hidebug-function getSystemCpuUsage(): double--><!--Device-hidebug-function getSystemCpuUsage(): double-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | ϵͳCPU��Դռ���������ռ����Ϊ50%���򷵻�0.5�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [11400104](../errorcode-hiviewdfx-hidebug-cpuusage.md#11400104-cpuusage统计异常) | The status of the system CPU usage is abnormal. |

**示例：**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  console.info(`getSystemCpuUsage: ${hidebug.getSystemCpuUsage()}`)
} catch (error) {
  console.error(`error code: ${(error as BusinessError).code}, error msg: ${(error as BusinessError).message}`);
}

```

