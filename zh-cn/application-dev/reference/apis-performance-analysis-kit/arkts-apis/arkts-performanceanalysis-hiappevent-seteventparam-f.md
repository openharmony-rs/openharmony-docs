# setEventParam

## 导入模块

```TypeScript
import { hiAppEvent } from '@kit.PerformanceAnalysisKit';
```

## setEventParam

```TypeScript
function setEventParam(params: Record<string, ParamType>, domain: string, name?: string): Promise<void>
```

事件自定义参数设置方法，使用Promise方式作为异步回调。在同一生命周期中，可以通过事件领域和事件名称关联系统事件和应用事件。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-hiAppEvent-function setEventParam(params: Record<string, ParamType>, domain: string, name?: string): Promise<void>--><!--Device-hiAppEvent-function setEventParam(params: Record<string, ParamType>, domain: string, name?: string): Promise<void>-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | Record&lt;string, ParamType&gt; | 是 | 事件自定义参数对象。参数名和参数值规格定义如下：<br>- 参数名为string类型，首字符必须为字母字符或$字符。中间字符必须为数字字符、字母字符或下划线字符。结尾字符必须为数字字符或字母字符。长度非空且不超过32个字符。<br>- 参数值为[ParamType](arkts-performanceanalysis-hiappevent-paramtype-t.md)类型，参数值长度需在1024个字符以内。<br>- 参数个数需在64个以内。 |
| domain | string | 是 | 事件领域。事件领域可支持关联应用事件和系统事件（hiAppEvent.domain.OS）。 |
| name | string | 否 | 事件名称。默认为空字符串，空字符串表示关联事件领域下的所有事件名称。事件名称可支持关联应用事件和系统事件，其中系统事件仅支持关联：<br>-[崩溃事件](../../../dfx/hiappevent-watcher-crash-events.md)（hiAppEvent.event.APP_CRASH）<br>-[应用冻屏事件](../../../dfx/hiappevent-watcher-freeze-events.md)（hiAppEvent.event.APP_FREEZE）<br>-[资源泄漏事件](../../../dfx/hiappevent-watcher-resourceleak-events.md)（hiAppEvent.event.RESOURCE_OVERLIMIT）。<br>**注意**：从API version 20开始，支持[资源泄漏事件](../../../dfx/hiappevent-watcher-resourceleak-events.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |
| [11100001](../errorcode-hiappevent.md#11100001-打点功能被关闭) | Function disabled. Possibly caused by the param disable in ConfigOption is true. |
| [11101001](../errorcode-hiappevent.md#11101001-非法的事件领域名称) | Invalid event domain. Possible causes: 1. Contain invalid characters;<br>2. Length is invalid. |
| [11101002](../errorcode-hiappevent.md#11101002-非法的事件名称) | Invalid event name. Possible causes: 1. Contain invalid characters;<br>2. Length is invalid. |
| [11101004](../errorcode-hiappevent.md#11101004-非法的事件参数字符串长度) | Invalid string length of the event parameter. |
| [11101005](../errorcode-hiappevent.md#11101005-非法的事件参数名称) | Invalid event parameter name. Possible causes: 1. Contain invalid characters;<br>2. Length is invalid. |
| [11101007](../errorcode-hiappevent.md#11101007-非法的事件自定义参数数量) | The number of parameter keys exceeds the limit. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let params: Record<string, hiAppEvent.ParamType> = {
  "int_data": 100,
  "str_data": "strValue",
};

// 给应用事件追加自定义参数
hiAppEvent.setEventParam(params, "test_domain", "test_event").then(() => {
  hilog.info(0x0000, 'hiAppEvent', `success to set event param`);
}).catch((err: BusinessError) => {
  hilog.error(0x0000, 'hiAppEvent', `code: ${err.code}, message: ${err.message}`);
});

```

