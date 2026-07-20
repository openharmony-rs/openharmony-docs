# hasMatchedCallLog

## 导入模块

```TypeScript
import { contact } from '@kit.ContactsKit';
```

<a id="hasmatchedcalllog"></a>
## hasMatchedCallLog

```TypeScript
function hasMatchedCallLog(context: Context, phoneNumber: string, minDuration: number): Promise<boolean>
```

检查是否有符合条件的通话记录，默认查询6小时以内的通话记录，仅针对运营商通话。使用Promise异步回调。

**起始版本：** 24

**需要权限：** ohos.permission.CHECK_CALL_LOG

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-contact-function hasMatchedCallLog(context: Context, phoneNumber: string, minDuration: int): Promise<boolean>--><!--Device-contact-function hasMatchedCallLog(context: Context, phoneNumber: string, minDuration: int): Promise<boolean>-End-->

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 应用上下文Context。 |
| phoneNumber | string | 是 | 联系人的电话号码。 |
| minDuration | number | 是 | 最短通话时长，单位为秒，取值范围大于0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象，返回是否有符合条件的通话记录，true代表有符合条件的，false代表没有。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [16700001](../errorcode-contacts.md#16700001-系统内部错误) | General error. |
| [16700002](../errorcode-contacts.md#16700002-参数检查失败) | Invalid parameter value. |

**示例：**

在本文档的示例中，通过this.context来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需要在界面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
import { contact } from '@kit.ContactsKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context
const context = this.getUIContext().getHostContext() as common.UIAbilityContext;

const phoneNumber = '138xxxxxxxx';
const minDuration = 60;
// 调用接口查询，默认查询6小时以内的通话记录
contact.hasMatchedCallLog(context, phoneNumber, minDuration).then((hasMatch:boolean) => {
  console.info(`Has matched call log: ${hasMatch}`);
});

```


<a id="hasmatchedcalllog-1"></a>
## hasMatchedCallLog

```TypeScript
function hasMatchedCallLog(context: Context, phoneNumber: string, minDuration: number, withinTime: number): Promise<boolean>
```

检查是否有符合条件的通话记录，仅针对运营商通话。使用Promise异步回调。

**起始版本：** 24

**需要权限：** ohos.permission.CHECK_CALL_LOG

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-contact-function hasMatchedCallLog(context: Context, phoneNumber: string, minDuration: int, withinTime: int): Promise<boolean>--><!--Device-contact-function hasMatchedCallLog(context: Context, phoneNumber: string, minDuration: int, withinTime: int): Promise<boolean>-End-->

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 应用上下文Context。 |
| phoneNumber | string | 是 | 联系人的电话号码。 |
| minDuration | number | 是 | 最短通话时长，单位为秒，取值范围大于0。 |
| withinTime | number | 是 | 表示从当前时间开始计算，通话的起始时间和结束时间应在此时间范围内，单位为秒。最多可设置6小时，超过6小时的默认以6小时查询。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象，返回是否有符合条件的通话记录，true代表有符合条件的，false代表没有。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [16700001](../errorcode-contacts.md#16700001-系统内部错误) | General error. |
| [16700002](../errorcode-contacts.md#16700002-参数检查失败) | Invalid parameter value. |

**示例：**

在本文档的示例中，通过this.context来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需要在界面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
import { contact } from '@kit.ContactsKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context
const context = this.getUIContext().getHostContext() as common.UIAbilityContext;

const phoneNumber = '138xxxxxxxx';
const minDuration = 60;
const withinTime = 2 * 60 *60;

// 调用接口查询
contact.hasMatchedCallLog(context, phoneNumber, minDuration, withinTime).then((hasMatch:boolean) => {
  console.info(`Has matched call log: ${hasMatch}`);
});

```

