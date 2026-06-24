# queryContactSyncInfo

## queryContactSyncInfo

```TypeScript
function queryContactSyncInfo(context: Context): Promise<Array<ContactSyncInfo>>
```

��ѯ����Ӧ�ó������ڽ��е���ϵ��ͬ����Ϣ��

������ص���ϵ��ͬ����ϢΪ�գ�����÷���������ϵ��ͬ������ϵ��ͬ������ɡ�

**起始版本：** 26.0.0

**需要权限：** ohos.permission.READ_CONTACTS

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | Ӧ��������Context�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;ContactSyncInfo&gt;&gt; | ���ص���Ӧ�ó������ϵ��ͬ����Ϣ���顣���û������ͬ������ϵ�ˣ��򷵻�null�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [16700001](../../errorcode-universal.md#16700001-General) | General error. |

**示例：**

在本文档的示例中，通过this.context来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需要在界面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
import { contact } from '@kit.ContactsKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context
const context = this.getUIContext().getHostContext() as common.UIAbilityContext;
const syncInfoList: ContactSyncInfo[] = await contact.queryContactSyncInfo(context) as ContactSyncInfo[];
console.info('queryContactSyncInfo syncInfoList '  + JSON.stringify(syncInfoList));

```

