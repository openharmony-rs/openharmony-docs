# stopAppTraceCapture

## 导入模块

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

<a id="stopapptracecapture"></a>
## stopAppTraceCapture

```TypeScript
function stopAppTraceCapture(): void
```

ֹͣӦ��trace�ɼ�������ǰ�����ȵ���`startAppTraceCapture()`������ʼ�ɼ����ر�ǰδ�������ظ��رջᵼ�½ӿ��쳣������startAppTraceCapture�ӿڣ����û�к�������limitSize����������trace�Ĵ�С���ڴ����limitSize��С��ϵͳ�ڲ����Զ�����stopAppTraceCapture���ٴ��ֶ�����stopAppTraceCapture�ͻ��׳�������11400105��

**起始版本：** 12

<!--Device-hidebug-function stopAppTraceCapture(): void--><!--Device-hidebug-function stopAppTraceCapture(): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [11400104](../errorcode-hiviewdfx-hidebug-cpuusage.md#11400104-cpuusage统计异常) | The status of the trace is abnormal |
| [11400105](../errorcode-hiviewdfx-hidebug-trace.md#11400105-未开启trace采集) | No capture trace running |

**示例：**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

let tags: number[] = [hidebug.tags.ABILITY_MANAGER, hidebug.tags.ARKUI];
let flag: hidebug.TraceFlag = hidebug.TraceFlag.MAIN_THREAD;
let limitSize: number = 1024 * 1024;
try {
  let fileName: string = hidebug.startAppTraceCapture(tags, flag, limitSize);
  console.info(`fileName = ${fileName}`);
  // code block
  // ...
  // code block
  hidebug.stopAppTraceCapture();
} catch (error) {
  console.error(`error code: ${(error as BusinessError).code}, error msg: ${(error as BusinessError).message}`);
}

```

