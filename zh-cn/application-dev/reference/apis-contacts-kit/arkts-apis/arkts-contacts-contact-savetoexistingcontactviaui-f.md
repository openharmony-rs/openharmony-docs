# saveToExistingContactViaUI

## saveToExistingContactViaUI

```TypeScript
function saveToExistingContactViaUI(context: Context, contact: Contact): Promise<number>
```

���ñ�����������ϵ�˽ӿڣ�ѡ����ϵ��UI���沢��ɱ༭��ʹ��Promise�첽�ص���

**起始版本：** 15

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Applications.Contacts

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | Ӧ��������Context�� |
| contact | Contact | 是 | ��ϵ����Ϣ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise���󡣷������ӵ���ϵ��id�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: Mandatory parameters are left unspecified. |
| [801](../../errorcode-universal.md#801-The) | The specified SystemCapability name was not found. |
| [16700001](../../errorcode-universal.md#16700001-General) | General error. |
| [16700101](../../errorcode-universal.md#16700101-Failed) | Failed to get value from contacts data. |
| [16700102](../../errorcode-universal.md#16700102-Failed) | Failed to set value to contacts data. |
| [16700103](../../errorcode-universal.md#16700103-User) | User cancel. |

**示例：**

在本文档的示例中，通过this.context来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需要在界面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
import { common } from '@kit.AbilityKit';
import { contact } from '@kit.ContactsKit';

// 请在组件内获取context。
let contactInfo: contact.Contact = {
  id: 1,
  name: {
    fullName: 'xxx'
  },
  phoneNumbers: [{
    phoneNumber: '138xxxxxx'
  }]
}
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let promise = contact.saveToExistingContactViaUI(context, contactInfo);
promise.then((data) => {
    console.info(`Succeeded in save to existing Contact via UI.data->${JSON.stringify(data)}`);
  });

```

