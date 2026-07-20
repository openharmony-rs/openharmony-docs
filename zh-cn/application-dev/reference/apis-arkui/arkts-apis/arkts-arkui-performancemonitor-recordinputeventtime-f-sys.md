# recordInputEventTime（系统接口）

## 导入模块

```TypeScript
import { performanceMonitor } from '@kit.ArkUI';
```

<a id="recordinputeventtime"></a>
## recordInputEventTime

```TypeScript
function recordInputEventTime(type: ActionType, sourceType: SourceType, time: number): void
```

记录动效场景开始前，用户输入触发事件类型与时间。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-performanceMonitor-function recordInputEventTime(type: ActionType, sourceType: SourceType, time: number): void--><!--Device-performanceMonitor-function recordInputEventTime(type: ActionType, sourceType: SourceType, time: number): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [ActionType](../../apis-avsession-kit/arkts-apis/arkts-avsession-avmusictemplate-actiontype-t.md) | 是 | 用户场景触发模式。 |
| sourceType | [SourceType](../../apis-arkweb/arkts-apis/arkts-arkweb-webview-sourcetype-e.md) | 是 | 用户场景触发源。 |
| time | number | 是 | 场景触发时间（ms），时间戳，例如1751508570794。若传零或负值将自动转化为当前系统时间，若传正值则正常使用。不正确的传参会导致用户操作响应时延指标异常。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | not system application. |

**示例：**

```TypeScript
import { systemDateTime, BusinessError } from '@kit.BasicServicesKit';
import { performanceMonitor } from '@kit.ArkUI';

// 获取当前系统时间
let time = systemDateTime.getTime(false);
// 更新用户触发事件类型与时间
performanceMonitor.recordInputEventTime(performanceMonitor.ActionType.LAST_UP, performanceMonitor.SourceType.PERF_MOUSE_EVENT, time);

```

