# enableGwpAsanGrayscale

## enableGwpAsanGrayscale

```TypeScript
function enableGwpAsanGrayscale(options?: GwpAsanOptions, duration?: int): void
```

使能GWP-ASan，用于检测堆内存使用中的非法行为。 该接口主要用于动态配置并启用GWP-ASan，以适配应用自定义的GWP-ASan检测策略。配置在应用重新启动后生效。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-hidebug-function enableGwpAsanGrayscale(options?: GwpAsanOptions, duration?: int): void--><!--Device-hidebug-function enableGwpAsanGrayscale(options?: GwpAsanOptions, duration?: int): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [GwpAsanOptions](arkts-performanceanalysis-hidebug-gwpasanoptions-i.md) | 否 | GWP-ASan配置项。未设置时，使用默认参数。 |
| duration | int | 否 | GWP-ASan持续时间，单位为天，默认值为7。需传入大于0的正整数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [11400114](../errorcode-hiviewdfx-hidebug.md#11400114-使能gwpasan失败) | The number of GWP-ASAN applications of this device overflowed after last boot. |

## 示例

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


## enableGwpAsanGrayscale

```TypeScript
function enableGwpAsanGrayscale(options?: GwpAsanOptions, duration?: number): void
```

使能GWP-ASan，用于检测堆内存使用中的非法行为。

**起始版本：** 22

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为22。

**废弃版本：** -1

<!--Device-hidebug-function enableGwpAsanGrayscale(options?: GwpAsanOptions, duration?: number): void--><!--Device-hidebug-function enableGwpAsanGrayscale(options?: GwpAsanOptions, duration?: number): void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [GwpAsanOptions](arkts-performanceanalysis-hidebug-gwpasanoptions-i.md) | 否 | GWP-ASan配置项。未设置时，使用默认参数。 |
| duration | number | 否 | GWP-ASan持续时间，单位为天，默认值为7。需传入大于0的正整数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [11400114](../errorcode-hiviewdfx-hidebug.md#11400114-使能gwpasan失败) | The number of GWP-ASAN applications of this device overflowed after last boot. |

## 示例

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

