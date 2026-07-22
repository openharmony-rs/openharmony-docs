# getGwpAsanGrayscaleState

## 导入模块

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## getGwpAsanGrayscaleState

```TypeScript
function getGwpAsanGrayscaleState(): number
```

��ȡ��ǰGWP-ASanʣ��ʹ��������

**起始版本：** 20

<!--Device-hidebug-function getGwpAsanGrayscaleState(): number--><!--Device-hidebug-function getGwpAsanGrayscaleState(): number-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | ��ȡ��ǰGWP-ASanʣ��ʹ������������ǰδʹ�ܣ�����ֵ0�� |

**示例：**

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


## getGwpAsanGrayscaleState

```TypeScript
function getGwpAsanGrayscaleState(): number
```

��ȡ��ǰGWP-ASanʣ��ʹ��������

**起始版本：** 20

<!--Device-hidebug-function getGwpAsanGrayscaleState(): int--><!--Device-hidebug-function getGwpAsanGrayscaleState(): int-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | ��ȡ��ǰGWP-ASanʣ��ʹ������������ǰδʹ�ܣ�����ֵ0�� |

**示例：**

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

