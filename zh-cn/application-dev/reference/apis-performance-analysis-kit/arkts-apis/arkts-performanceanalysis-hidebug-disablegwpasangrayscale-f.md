# disableGwpAsanGrayscale

## 导入模块

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## disableGwpAsanGrayscale

```TypeScript
function disableGwpAsanGrayscale(): void
```

停止使能GWP-ASan。调用该接口将取消自定义配置，恢复默认参数GwpAsanOptions。

**起始版本：** 23

<!--Device-hidebug-function disableGwpAsanGrayscale(): void--><!--Device-hidebug-function disableGwpAsanGrayscale(): void-End-->

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

