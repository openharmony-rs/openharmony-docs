# getGraphicsMemorySync

## getGraphicsMemorySync

```TypeScript
function getGraphicsMemorySync(): number
```

ʹ��ͬ����ʽ��ȡӦ���Դ��ܴ�С��gl + graph����

> **ע��**
>
> ���ڸýӿ��漰��ο����ͨ�ţ����ʱ���ܴﵽ�뼶��Ϊ�˱��������������⣬���鲻Ҫ�����̵߳��øýӿڣ��Ƽ�ʹ���첽�ӿ�`getGraphicsMemory`��

**起始版本：** 14

**元服务API：** 从API版本14开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | Ӧ���Դ��ܴ�С����λΪKB�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [11400104](../errorcode-hiviewdfx-hidebug-cpuusage.md#11400104-cpuusage统计异常) | Failed to get the application memory due to a remote exception. |

**示例：**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  console.info(`graphicsMemory: ${hidebug.getGraphicsMemorySync()}`)
} catch (error) {
  console.error(`error code: ${(error as BusinessError).code}, error msg: ${(error as BusinessError).message}`);
}

```

