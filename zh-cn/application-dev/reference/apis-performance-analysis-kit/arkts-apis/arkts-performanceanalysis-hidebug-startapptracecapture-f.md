# startAppTraceCapture

## startAppTraceCapture

```TypeScript
function startAppTraceCapture(tags: long[], flag: TraceFlag, limitSize: int): string
```

该接口补充了hitrace功能，开发者可通过该接口完成指定范围的trace自动化采集。由于该接口中trace采集过程中消耗的性能与需要采集的范围成正相关，建议开发者在使用该接口前，通过hitrace命令抓取应用的trace日志，从中筛选出所需trace采集的关键范围，以提高该接口性能。 `startAppTraceCapture()`方法的调用需要与`stopAppTraceCapture()`方法的调用一一对应，重复开启trace采集将导致接口调用异常，由于trace采集过程中会消耗较多性能，开发者应在完成采集后及时关闭。 应用调用startAppTraceCapture接口启动采集trace，当采集的trace大小超过了limitSize，系统将自动调用stopAppTraceCapture接口停止采集。因此limitSize大小设置不当，将导致生成trace数据不足，无法满足故障分析。所以要求开发者根据实际情况，评估limitSize大小。 评估方法：limitSize = 预期trace采集时长 * trace单位流量。 预期trace采集时长：开发者根据分析的故障场景自行决定，单位秒。 trace单位流量：应用每秒产生的trace大小，系统推荐值为300KB/s，建议开发者采用自身应用的实测值，单位KB/s。 trace单位流量实测方法：limitSize设置为最大值500M，调用startAppTraceCapture接口，在应用上操作N秒后，调用stopAppTraceCapture停止采集，然后查看trace大小S（KB）。那么trace单位流量 = S/N（KB/s）。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-hidebug-function startAppTraceCapture(tags: long[], flag: TraceFlag, limitSize: int): string--><!--Device-hidebug-function startAppTraceCapture(tags: long[], flag: TraceFlag, limitSize: int): string-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| tags | long[] | 是 | trace范围，详情请见tags。 |
| flag | [TraceFlag](arkts-performanceanalysis-hidebug-traceflag-e.md) | 是 | 详情请见TraceFlag。 |
| limitSize | int | 是 | 开启trace文件大小限制，单位为Byte，取值范围（0, 500MB]。超出范围时返回错误码401。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回trace文件名路径（接口返回真实物理路径，若应用内需要访问，请参考应用沙箱路径和真实物理路径的对应关系进行路径转换）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid argument, Possible causes: 1.The limit parameter is too small 2.The parameter is not within the enumeration type 3.The parameter type error or parameter order error |
| [11400104](../errorcode-hiviewdfx-hidebug-cpuusage.md#11400104-cpuusage统计异常) | Abnormal trace status. |
| [11400103](../errorcode-hiviewdfx-hidebug-trace.md#11400103-权限校验失败) | No write permission on the file. |
| [11400102](../errorcode-hiviewdfx-hidebug-trace.md#11400102-重复采集) | Capture trace already enabled. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tags: number[] = [hidebug.tags.ABILITY_MANAGER, hidebug.tags.ARKUI];
let flag: hidebug.TraceFlag = hidebug.TraceFlag.MAIN_THREAD;
let limitSize: number = 1024 * 1024;

try {
  let fileName: string = hidebug.startAppTraceCapture(tags, flag, limitSize);
  // code block
  // ...
  // code block
  hidebug.stopAppTraceCapture();
} catch (error) {
  console.error(`error code: ${(error as BusinessError).code}, error msg: ${(error as BusinessError).message}`);
}
```

ArkTS-Sta示例：

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tags: long[] = [hidebug.tags.ABILITY_MANAGER, hidebug.tags.ARKUI];
let flag: hidebug.TraceFlag = hidebug.TraceFlag.MAIN_THREAD;
let limitSize: int = 1024 * 1024;

try {
  let fileName: string = hidebug.startAppTraceCapture(tags, flag, limitSize);
  // code block
  // ...
  // code block
  hidebug.stopAppTraceCapture();
} catch (error) {
  console.error(`error code: ${(error as BusinessError).code}, error msg: ${(error as BusinessError).message}`);
}
```

