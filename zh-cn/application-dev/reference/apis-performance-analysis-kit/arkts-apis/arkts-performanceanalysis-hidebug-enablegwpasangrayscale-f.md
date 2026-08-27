# enableGwpAsanGrayscale

## 导入模块

```TypeScript
```

## enableGwpAsanGrayscale

```TypeScript
function enableGwpAsanGrayscale(options?: GwpAsanOptions, duration?: number): void
```

使能GWP-ASan，用于检测堆内存使用中的非法行为。该接口主要用于动态配置并启用GWP-ASan，以适配应用自定义的GWP-ASan检测策略。配置在应用重新启动后生效。更多关于GWP-ASan的说明，请参见 [使用GWP-ASan检测内存错误](https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-stability-gwpasan-detection)。

> **说明：**
> 
> 1. 若设备运行期间通过本接口设置的GWP-ASan应用数量超过配额限制，调用该接口将会失败并抛出错误码。请使用try-catch捕获异常，以避免应用异常退出。
> 
> 2. 设备重启后，本接口设置的GWP-ASan参数将会失效。
> 
> 3. 由于该接口涉及跨进程通信，耗时较长，为了避免引入性能问题，建议不要在主线程中直接调用该接口。可以通过[@ohos.taskpool](../../apis-arkts/arkts-apis/arkts-taskpool.md)或
> [@ohos.worker](../../apis-arkts/arkts-apis/arkts-arkts-worker-n.md)开启异步线程，以避免应用卡顿。

**起始版本：** 20

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [GwpAsanOptions](arkts-performanceanalysis-hidebug-gwpasanoptions-i.md) | 否 | GWP-ASan配置项。未设置时，使用默认参数。 |
| duration | number | 否 | GWP-ASan持续时间，单位为天，默认值为7。需传入大于0的正整数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [11400114](../errorcode-hiviewdfx-hidebug.md#11400114-使能gwp-asan失败) | The number of GWP-ASAN applications of this device overflowed after last boot. |

**示例**

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
import { taskpool } from '@kit.ArkTS';
import { BusinessError } from '@kit.BasicServicesKit';

@Concurrent
function enableGwpAsanTask(): void {
  let options: hidebug.GwpAsanOptions = {
    alwaysEnabled: true,
    sampleRate: 2500,
    maxSimutaneousAllocations: 5000,
  };
  let duration: number = 4;
  hidebug.enableGwpAsanGrayscale(options, duration);
}

taskpool.execute(enableGwpAsanTask).then(() => {
  console.info(`Succeeded in enabling GWP-ASan.`);
}).catch((error: BusinessError) => {
  const err: BusinessError = error as BusinessError;
  console.error(`Failed to enable GWP-ASan. Code: ${err.code}, message: ${err.message}`);
})
```
