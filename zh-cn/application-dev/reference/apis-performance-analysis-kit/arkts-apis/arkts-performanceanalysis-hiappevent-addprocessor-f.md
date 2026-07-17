# addProcessor

## 导入模块

```TypeScript
import { hiAppEvent } from '@kit.PerformanceAnalysisKit';
```

## addProcessor

```TypeScript
function addProcessor(processor: Processor): number
```

添加数据处理者配置信息，用于配置处理者接收的事件名等信息。事件发生后处理者可以接收事件。

该接口为同步接口，包含耗时操作。为了确保性能，建议使用[addProcessorFromConfig](arkts-performanceanalysis-hiappevent-addprocessorfromconfig-f.md#addprocessorfromconfig-1)异步接口或者交由子线程执行。

**起始版本：** 11

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-hiAppEvent-function addProcessor(processor: Processor): long--><!--Device-hiAppEvent-function addProcessor(processor: Processor): long-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| processor | [Processor](arkts-performanceanalysis-hiappevent-processor-i.md) | 是 | 上报事件的数据处理者。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 所添加上报事件数据处理者的ID，标识唯一数据处理者，可用于移除数据处理者。 添加失败返回-1，添加成功返回大于0的值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

**示例：**

```TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';

try {
  let processor: hiAppEvent.Processor = {
    name: 'analytics_demo'
  };
  let id: number = hiAppEvent.addProcessor(processor);
  hilog.info(0x0000, 'hiAppEvent', `addProcessor event was successful, id=${id}`);
} catch (error) {
  hilog.error(0x0000, 'hiAppEvent', `failed to addProcessor event, code=${error.code}`);
}

```

