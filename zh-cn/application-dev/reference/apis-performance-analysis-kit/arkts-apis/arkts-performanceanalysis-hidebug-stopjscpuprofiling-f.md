# stopJsCpuProfiling

## 导入模块

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## stopJsCpuProfiling

```TypeScript
function stopJsCpuProfiling() : void
```

停止虚拟机Profiling方法跟踪，`stopJsCpuProfiling()`方法的调用需要与`startJsCpuProfiling(filename: string)`方法的调用一一对应，先开启后关闭，请避免重复开启或重复关闭的调用方式，否则会接口调用异常。

**起始版本：** 23

<!--Device-hidebug-function stopJsCpuProfiling() : void--><!--Device-hidebug-function stopJsCpuProfiling() : void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**示例**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  hidebug.startJsCpuProfiling("cpu_profiling");
  // ...
  hidebug.stopJsCpuProfiling();
} catch (error) {
  console.error(`error code: ${(error as BusinessError).code}, error msg: ${(error as BusinessError).message}`);
}
```

