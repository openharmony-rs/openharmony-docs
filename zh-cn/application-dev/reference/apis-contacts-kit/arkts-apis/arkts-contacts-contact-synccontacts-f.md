# syncContacts

## 导入模块

```TypeScript
import { contact } from '@kit.ContactsKit';
```

## syncContacts

```TypeScript
function syncContacts(context: Context, mode: ContactSyncMode, progress: ContactSyncProgress, contacts: Array<Contact>): Promise<Array<number>>
```

批量同步多个联系人至联系人数据库。

最多可批量同步400个联系人。调用方必须处于前台。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.WRITE_CONTACTS

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-contact-function syncContacts(context: Context, mode: ContactSyncMode, progress: ContactSyncProgress, contacts: Array<Contact>): Promise<Array<int>>--><!--Device-contact-function syncContacts(context: Context, mode: ContactSyncMode, progress: ContactSyncProgress, contacts: Array<Contact>): Promise<Array<int>>-End-->

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 应用上下文Context。 |
| mode | [ContactSyncMode](arkts-contacts-contact-contactsyncmode-e.md) | 是 | 表示联系人同步模式的类型。 |
| progress | [ContactSyncProgress](arkts-contacts-contact-contactsyncprogress-i.md) | 是 | 表示联系人同步进度的相关信息。 |
| contacts | Array&lt;Contact&gt; | 是 | 表示需要同步至数据库的联系人信息数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;number&gt;&gt; | 返回联系人创建结果的数组。有效的联系人ID (可为通过 {@link Contact#getId()})获得的值表示创建成功。{@link Contact#INVALID_CONTACT_ID} 表示创建失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [16700001](../errorcode-contacts.md#16700001-系统内部错误) | General error. |
| [16700002](../errorcode-contacts.md#16700002-参数检查失败) | Invalid parameter value. |
| [16700003](../errorcode-contacts.md#16700003-禁止后台调用) | Background usage is prohibited. |
| [16700004](../errorcode-contacts.md#16700004-联系人数量超过限制) | The number of contacts exceeds the limit. |
| [16700103](../errorcode-contacts.md#16700103-用户取消) | User cancel. |

**示例：**

在本文档的示例中，通过this.context来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需要在界面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
import { contact } from '@kit.ContactsKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context
const context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let mode = contact.ContactSyncMode.MODE_INCREMENTAL;
const totalBatches: number = 3;
const syncId: number = Date.now() / 1000;
const totalCount = 300;
const batchSize = 100;
for (let batch: number = 1; batch <= totalBatches; batch++) {
  try {
    const remaining: number = totalCount - (batch - 1) * batchSize;
    const currentBatchSize: number = Math.min(batchSize, remaining);
    const contacts: contact.Contact[] = [];
    for (let i: number = 0; i < currentBatchSize; i++) {
      const contactData: contact.Contact = {
        name: {
          fullName: `同步联系人${i + 1}_${batch}批次`
          },
        phoneNumbers: [{
          phoneNumber: `1380000${String(i + 1).padStart(4, '0')}`,
          labelName: '手机'
        }],
        emails: [{
          email: `contact${i + 1}@example.com`,
          labelName: '工作'
          }]
        };
      contacts.push(contactData);
    }
    const progress: contact.ContactSyncProgress = {
      syncId: syncId,
      currentBatch: batch,
      totalBatches: totalBatches
    };
    console.info(`同步批次 ${batch}/${totalBatches}, 联系人数量: ${currentBatchSize}`);
    let result = await contact.syncContacts(context, mode, progress, contacts);
    console.info(`批次 ${batch} 同步成功，result: `  + JSON.stringify(result));
  }
  catch (err) {
    const e = err as BusinessError;
    console.error(`syncContacts 失败: code=${e.code}, message=${e.message}`);
  }
}

```

