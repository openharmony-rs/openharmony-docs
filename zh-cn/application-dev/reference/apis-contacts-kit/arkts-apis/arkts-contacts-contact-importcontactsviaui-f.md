# importContactsViaUI

## importContactsViaUI

```TypeScript
function importContactsViaUI(context: Context, contacts: Array<Contact>): Promise<Array<number>>
```

ͨ��UI����������������ϵ�ˡ�

ÿ�����ɵ���100����ϵ�ˡ�

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Applications.Contacts

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | Ӧ��������Context�� |
| contacts | Array&lt;Contact&gt; | 是 | ��ʾ���������ݿ����ϵ����Ϣ���顣 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;number&gt;&gt; | ������ϵ�˴�����������顣���ص���ϵ��id��Ч����ͨ��[getId](Contact#getId())��ȡ����ʾ�����ɹ���<br/>����ֵΪ-1[INVALID_CONTACT_ID](arkts-contacts-contact-contact-c.md#INVALID_CONTACT_ID) ��ʾ����ʧ�ܡ�-2��ʾ�û�δѡ�����ϵ�ˡ� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-The) | The specified SystemCapability name was not found. |
| [16700001](../../errorcode-universal.md#16700001-General) | General error. |
| [16700002](../../errorcode-universal.md#16700002-Invalid) | Invalid parameter value. |
| [16700004](../../errorcode-universal.md#16700004-The) | The number of contacts exceeds the limit. |
| [16700103](../../errorcode-universal.md#16700103-User) | User canceled. |

**示例：**

在本文档的示例中，通过this.context来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需要在界面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
import { contact } from '@kit.ContactsKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context
const context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let contactList: contact.Contact[] = [];
let contactInfo: contact.Contact = {
  name: {
    fullName: 'xxx'
  },
  phoneNumbers: [{
    phoneNumber: '138xxxxxx'
  }]
}
contactList.push(contactInfo);
let promise = contact.importContactsViaUI(context, contactList);
promise.then((data) => {
  console.info(`Succeeded in importing Contact via UI: data -> ${JSON.stringify(data)}`);
});

```

