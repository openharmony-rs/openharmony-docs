# requestTrace

## 导入模块

```TypeScript
```

## requestTrace

```TypeScript
function requestTrace(config: RequestTraceConfig): Promise<string>
```

获取当前进程的trace信息，包含应用tag、图像窗口tag、cpu调度和binder内核信息。使用Promise异步回调。采集trace返回的.sys文件在目录下最多存储3份，数量大于等于3份时再次调用接口会抛出错误码11400120。接口不支持在输入法应用中使用。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [RequestTraceConfig](arkts-performanceanalysis-hidebug-requesttraceconfig-i.md) | 是 | trace采集配置信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;string & gt; | Promise对象，返回以.sys作为后缀的trace文件的应用沙箱路径。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [11400104](../errorcode-hiviewdfx-hidebug-cpuusage.md#11400104-cpuusage统计异常) | Remote service exception. |
| [11400120](../errorcode-hiviewdfx-hidebug-trace.md#11400120-trace文件存储达到限制) | Trace storage limit reached. |
| [11400302](../errorcode-hiviewdfx-hidebug-trace.md#11400302-trace采集超出资源配额) | Resource unavailable. |

**示例**

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
