# getCpuUsage

## 导入模块

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

<a id="getcpuusage"></a>
## getCpuUsage

```TypeScript
function getCpuUsage() : number
```

��ȡ���̵�CPUʹ���ʡ�

> **ע��**  
>  
> ���ڸýӿ��漰�����ͨ�ţ���ʱ�ϳ���Ϊ�˱��������������⣬���鲻Ҫ�����߳���ֱ�ӵ��øýӿڡ�

**起始版本：** 9

<!--Device-hidebug-function getCpuUsage() : double--><!--Device-hidebug-function getCpuUsage() : double-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | ��ȡ���̵�CPUʹ���ʡ���ռ����Ϊ50%���򷵻�0.5�� |

**示例：**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';

let cpuUsage: number = hidebug.getCpuUsage();
console.info(`cpuUsage = ${cpuUsage}`);

```

