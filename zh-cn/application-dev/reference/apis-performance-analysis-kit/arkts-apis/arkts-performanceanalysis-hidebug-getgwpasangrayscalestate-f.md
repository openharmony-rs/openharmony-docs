# getGwpAsanGrayscaleState

## 导入模块

```TypeScript
```

## getGwpAsanGrayscaleState

```TypeScript
function getGwpAsanGrayscaleState(): number
```

获取当前GWP-ASan剩余使能天数。

> **说明：**
> 
> 由于该接口涉及跨进程通信，耗时较长，为了避免引入性能问题，建议不要在主线程中直接调用该接口。可以通过[@ohos.taskpool](../../apis-arkts/arkts-apis/arkts-taskpool.md)或
> [@ohos.worker](../../apis-arkts/arkts-apis/arkts-arkts-worker-n.md)开启异步线程，以避免应用卡顿。

**起始版本：** 20

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 获取当前GWP-ASan剩余使能天数。若当前未使能，返回值0。 |

**示例**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
import { taskpool } from '@kit.ArkTS';

@Concurrent
function getGwpAsanStateTask(): number {
  return hidebug.getGwpAsanGrayscaleState();
}
taskpool.execute(getGwpAsanStateTask).then((remainDays: Object) => {
  console.info(`GWP-ASan remain days: ${remainDays as number}.`);
})
```
