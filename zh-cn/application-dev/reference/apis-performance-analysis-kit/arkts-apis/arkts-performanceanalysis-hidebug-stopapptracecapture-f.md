# stopAppTraceCapture

## stopAppTraceCapture

```TypeScript
function stopAppTraceCapture(): void
```

停止应用trace采集。调用前，需先调用`startAppTraceCapture()`方法开始采集。关闭前未开启或重复关闭会导致接口异常。 调用startAppTraceCapture接口，如果没有合理传入limitSize参数，生成trace的大小大于传入的limitSize大小，系统内部会自动调用stopAppTraceCapture，再次手动调用stopAppTraceCapture就会抛出错误码11400105。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-hidebug-function stopAppTraceCapture(): void--><!--Device-hidebug-function stopAppTraceCapture(): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [11400105](../errorcode-hiviewdfx-hidebug-trace.md#11400105-未开启trace采集) | No capture trace running |
| [11400104](../errorcode-hiviewdfx-hidebug-cpuusage.md#11400104-cpuusage统计异常) | The status of the trace is abnormal |

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

