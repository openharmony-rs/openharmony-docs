# addContacts

## addContacts

```TypeScript
function addContacts(context: Context, contacts: Array<Contact>): Promise<Array<number>>
```

����������ϵ�ˡ�ʹ��Promise�첽�ص���

**起始版本：** 23

**需要权限：** ohos.permission.WRITE_CONTACTS

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | Ӧ��������Context�� |
| contacts | Array&lt;Contact&gt; | 是 | ��ϵ����Ϣ���顣 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;number&gt;&gt; | Promise���󣬷����������ӵ���ϵ��id���顣 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [16700001](../../errorcode-universal.md#16700001-General) | General error. |
| [16700002](../../errorcode-universal.md#16700002-Invalid) | Invalid parameter value. |

**示例：**

在本文档的示例中，通过this.context来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需要在界面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
import { common } from '@kit.AbilityKit';
import { contact } from '@kit.ContactsKit';

const contactInfo1: contact.Contact = {
  name: { fullName: 'xxx1'},
  phoneNumbers: [{ phoneNumber: '138xxxxxx' }]
};
const contactInfo2: contact.Contact = {
  name: { fullName: 'xxx2'},
  phoneNumbers: [{ phoneNumber: '139xxxxxx' }]
};
// 请在组件内获取context。
const context = this.getUIContext().getHostContext() as common.UIAbilityContext;
contact.addContacts(context, [contactInfo1, contactInfo2]).then((data) => {
  console.info(`Succeeded in addContacts.data->${JSON.stringify(data)}`);
});

```

