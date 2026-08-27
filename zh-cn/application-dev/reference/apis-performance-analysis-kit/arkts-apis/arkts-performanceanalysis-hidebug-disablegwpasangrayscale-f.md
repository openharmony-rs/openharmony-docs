# disableGwpAsanGrayscale

## 导入模块

```TypeScript
```

## disableGwpAsanGrayscale

```TypeScript
function disableGwpAsanGrayscale(): void
```

停止使能GWP-ASan。调用该接口将取消自定义配置，恢复默认参数[GwpAsanOptions](arkts-performanceanalysis-hidebug-gwpasanoptions-i.md)。

> **说明：**
> 
> 由于该接口涉及跨进程通信，耗时较长，为了避免引入性能问题，建议不要在主线程中直接调用该接口。可以通过[@ohos.taskpool](../../apis-arkts/arkts-apis/arkts-taskpool.md)或
> [@ohos.worker](../../apis-arkts/arkts-apis/arkts-arkts-worker-n.md)开启异步线程，以避免应用卡顿。

**起始版本：** 20

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**示例**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
import { taskpool } from '@kit.ArkTS';

@Concurrent
function disableGwpAsanTask(): void {
  hidebug.disableGwpAsanGrayscale();
}
taskpool.execute(disableGwpAsanTask).then(() => {
  console.info(`Disable GWP-ASan succeeded.`);
})
```
