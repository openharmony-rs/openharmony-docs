# queryContactSyncInfo

## 导入模块

```TypeScript
import { contact } from '@kit.ContactsKit';
```

<a id="querycontactsyncinfo"></a>
## queryContactSyncInfo

```TypeScript
function queryContactSyncInfo(context: Context): Promise<Array<ContactSyncInfo>>
```

查询调用应用程序正在进行的联系人同步信息。

如果返回的联系人同步信息为空，则调用方不进行联系人同步或联系人同步已完成。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.READ_CONTACTS

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-contact-function queryContactSyncInfo(context: Context): Promise<Array<ContactSyncInfo>>--><!--Device-contact-function queryContactSyncInfo(context: Context): Promise<Array<ContactSyncInfo>>-End-->

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 应用上下文Context。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;ContactSyncInfo&gt;&gt; | 返回调用应用程序的联系人同步信息数组。如果没有正在同步的联系人，则返回null。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [16700001](../errorcode-contacts.md#16700001-系统内部错误) | General error. |

**示例：**

在本文档的示例中，通过this.context来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需要在界面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
import { contact } from '@kit.ContactsKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context
const context = this.getUIContext().getHostContext() as common.UIAbilityContext;
const syncInfoList: contact.ContactSyncInfo[] = await contact.queryContactSyncInfo(context) as contact.ContactSyncInfo[];
console.info('queryContactSyncInfo syncInfoList '  + JSON.stringify(syncInfoList));

```

