# closeToast

## 导入模块

```TypeScript
import { LevelMode, ImmersiveMode, LevelOrder } from '@kit.ArkUI';
```

<a id="closetoast"></a>
## closeToast

```TypeScript
function closeToast(toastId: number): void
```

关闭即时反馈。

> **说明：**  
>  
> 直接使用closeToast可能导致[UI上下文不明确](docroot://ui/arkts-global-interface.md#ui上下文不明确)的问题，建议使用UIContext中的getPromptAction方法获取  
> 到PromptAction对象，再通过该对象调用  
> [closeToast](docroot://reference/apis-arkui/arkts-apis-uicontext-promptaction.md#closetoast18)实现。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-promptAction-function closeToast(toastId: number): void--><!--Device-promptAction-function closeToast(toastId: number): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| toastId | number | 是 | openToast返回的id。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified.<br> 2. Incorrect parameters types.<br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-接口调用异常错误码) | Internal error. |
| [103401](../errorcode-promptAction.md#103401-无法找到对应的文本提示框) | Cannot find the toast. |

