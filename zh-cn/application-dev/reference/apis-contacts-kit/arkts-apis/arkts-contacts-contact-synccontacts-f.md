# syncContacts

## syncContacts

```TypeScript
function syncContacts(context: Context, mode: ContactSyncMode, progress: ContactSyncProgress, contacts: Array<Contact>): Promise<Array<number>>
```

����ͬ�������ϵ������ϵ�����ݿ⡣

��������ͬ��400����ϵ�ˡ����÷����봦��ǰ̨��

**起始版本：** 26.0.0

**需要权限：** ohos.permission.WRITE_CONTACTS

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | Ӧ��������Context�� |
| mode | ContactSyncMode | 是 | ��ʾ��ϵ��ͬ��ģʽ�����͡� |
| progress | ContactSyncProgress | 是 | ��ʾ��ϵ��ͬ�����ȵ������Ϣ�� |
| contacts | Array&lt;Contact&gt; | 是 | ��ʾ��Ҫͬ�������ݿ����ϵ����Ϣ���顣 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;number&gt;&gt; | ������ϵ�˴�����������顣��Ч����ϵ��ID (��Ϊͨ�� {@link Contact#getId()})<br/>��õ�ֵ��ʾ�����ɹ���<br/>{@link Contact#INVALID_CONTACT_ID} ��ʾ����ʧ�ܡ� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [16700001](../../errorcode-universal.md#16700001-General) | General error. |
| [16700002](../../errorcode-universal.md#16700002-Invalid) | Invalid parameter value. |
| [16700003](../../errorcode-universal.md#16700003-Background) | Background usage is prohibited. |
| [16700004](../../errorcode-universal.md#16700004-The) | The number of contacts exceeds the limit. |
| [16700103](../../errorcode-universal.md#16700103-User) | User canceled. |

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
    const progress: ContactSyncProgress = {
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

