# addProcessorFromConfig

## 导入模块

```TypeScript
import { hiAppEvent } from '@kit.PerformanceAnalysisKit';
```

<a id="addprocessorfromconfig"></a>
## addProcessorFromConfig

```TypeScript
function addProcessorFromConfig(processorName: string, configName?: string): Promise<number>
```

添加数据处理者配置信息，通过配置文件配置处理者接收的事件名等信息，事件发生后处理者可以接收事件，使用Promise异步回调。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-hiAppEvent-function addProcessorFromConfig(processorName: string, configName?: string): Promise<long>--><!--Device-hiAppEvent-function addProcessorFromConfig(processorName: string, configName?: string): Promise<long>-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| processorName | string | 是 | 数据处理者的名称。名称只能包含大小写字母、数字、下划线和$，不能以数字开头，长度非空且不超过256个字符。 |
| configName | string | 否 | 数据处理者的配置名称，支持从配置文件中加载对应配置，默认为“SDK_OCG”。只能包含大小写字母、数字、下划线和$，不能以数字开头，长度非空且不超过256个字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象。返回添加的事件数据处理者的唯一ID，可用于移除该数据处理者。 添加失败返回11105001错误码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [11105001](../errorcode-hiappevent.md#11105001-非法的参数值) | Invalid parameter value. Possible causes: 1. Incorrect parameter length;2. Incorrect parameter format. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

hiAppEvent.addProcessorFromConfig("test_name").then((processorId) => {
  hilog.info(0x0000, 'hiAppEvent', `Succeeded in adding processor from config, processorId=${processorId}`);
}).catch((err: BusinessError) => {
  hilog.error(0x0000, 'hiAppEvent', `Failed to add processor from config, code: ${err.code}, message: ${err.message}`);
});

```

