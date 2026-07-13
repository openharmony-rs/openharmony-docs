# enableGwpAsanGrayscale

## enableGwpAsanGrayscale

```TypeScript
function enableGwpAsanGrayscale(options?: GwpAsanOptions, duration?: number): void
```

ʹ��GWP-ASan�����ڼ����ڴ�ʹ���еķǷ���Ϊ��
�ýӿ���Ҫ���ڶ�̬���ò�����GWP-ASan��������Ӧ���Զ����GWP-ASan�����ԡ�������Ӧ��������������Ч��

**起始版本：** 20

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | GwpAsanOptions | 否 | GWP-ASan�����δ����ʱ��ʹ��Ĭ�ϲ����� |
| duration | number | 否 | GWP-ASan����ʱ�䣬��λΪ�죬Ĭ��ֵΪ7���贫�����0���������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [11400114](../errorcode-hiviewdfx-hidebug.md#11400114-使能gwpasan失败) | The number of GWP-ASAN applications of this device overflowed after last boot. |

**示例：**

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

ʹ��GWP-ASan�����ڼ����ڴ�ʹ���еķǷ���Ϊ��

**起始版本：** 20

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | GwpAsanOptions | 否 | GWP-ASan�����δ����ʱ��ʹ��Ĭ�ϲ����� |
| duration | number | 否 | GWP-ASan����ʱ�䣬��λΪ�죬Ĭ��ֵΪ7���贫�����0���������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [11400114](../errorcode-hiviewdfx-hidebug.md#11400114-使能gwpasan失败) | The number of GWP-ASAN applications of this device overflowed after last boot. |

**示例：**

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

