# requestTrace

## 导入模块

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## requestTrace

```TypeScript
function requestTrace(config: RequestTraceConfig): Promise<string>
```

��ȡ��ǰ���̵�trace��Ϣ������Ӧ��tag��ͼ�񴰿�tag��cpu���Ⱥ�binder�ں���Ϣ��ʹ��Promise�첽�ص����ɼ�trace���ص�.sys�ļ���Ŀ¼�����洢3�ݣ��������ڵ���3��ʱ�ٴε��ýӿڻ��׳�������11400120��

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-hidebug-function requestTrace(config: RequestTraceConfig): Promise<string>--><!--Device-hidebug-function requestTrace(config: RequestTraceConfig): Promise<string>-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [RequestTraceConfig](arkts-performanceanalysis-hidebug-requesttraceconfig-i.md) | 是 | trace�ɼ�������Ϣ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise���󣬷�����.sys��Ϊ��׺��trace�ļ���Ӧ��ɳ��·���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [11400104](../errorcode-hiviewdfx-hidebug-cpuusage.md#11400104-cpuusage统计异常) | Remote service exception. |
| [11400120](../errorcode-hiviewdfx-hidebug-trace.md#11400120-trace文件存储达到限制) | Trace storage limit reached. |
| [11400302](../errorcode-hiviewdfx-hidebug-trace.md#11400302-trace采集超出资源配额) | Resource unavailable. |

**示例：**

```TypeScript
import { hidebug, hilog } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  hidebug.requestTrace({
    identifier: "trace_name",
    bufferSizeKb: 1024,
    durationMs: 1000,
    reserved: 0,
  }).then((tracePath: string) => {
    hilog.info(0x0000, 'hidebug', `tracePath: ${tracePath}`)
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'hidebug', `error code: ${err.code}, message: ${err.message}`)
  })
} catch (error) {
  hilog.error(0x0000, 'hidebug', `error code: ${(error as BusinessError).code}, message: ${(error as BusinessError).message}`)
}

```

