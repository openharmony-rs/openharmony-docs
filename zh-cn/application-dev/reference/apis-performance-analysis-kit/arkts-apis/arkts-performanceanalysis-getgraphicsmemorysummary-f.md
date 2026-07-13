# getGraphicsMemorySummary

## getGraphicsMemorySummary

```TypeScript
function getGraphicsMemorySummary(interval?: number): Promise<GraphicsMemorySummary>
```

��ȡӦ���Դ����ݣ�ʹ��Promise�����첽�ص���

**起始版本：** 21

**元服务API：** 从API版本21开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| interval | number | 否 | �Դ����ݻ���ֵ��Чʱ�䣬��λΪ�롣Ĭ��ֵ��300��ȡֵ��ΧΪ[2-3600]��������ֵ����ȡֵ��Χʱ����ʹ��Ĭ��ֵ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;GraphicsMemorySummary&gt; | promise���󣬷���Ӧ���Դ����ݡ� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [11400104](../errorcode-hiviewdfx-hidebug-cpuusage.md#11400104-cpuusage统计异常) | Failed to get the application memory due to a remote exception. |

**示例：**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

hidebug.getGraphicsMemorySummary().then((ret: hidebug.GraphicsMemorySummary) => {
  console.info(`get graphicsMemory gl: ${ret.gl} graph: ${ret.graph}.`)
}).catch((error: BusinessError) => {
  console.error(`error code: ${error.code}, error msg: ${error.message}.`);
})

```

