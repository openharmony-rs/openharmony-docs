# selectContact

## selectContact

```TypeScript
function selectContact(callback: AsyncCallback<Array<Contact>>): void
```

����ѡ����ϵ�˽ӿڣ���ѡ����ϵ��UI���档ʹ��callback�첽�ص���

**起始版本：** 7

**废弃版本：** 10

**替代接口：** selectContacts(callback:

**系统能力：** SystemCapability.Applications.Contacts

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;Array&lt;Contact&gt;&gt; | 是 | �ص��������ɹ�����ѡ�����ϵ�˶������飻ʧ�ܷ��ؾ���Ĵ�������Ϣ�� |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { contact } from '@kit.ContactsKit';

// 打开选择联系人UI界面
contact.selectContact((err: BusinessError, data) => {
  if (err) {
    console.error(`Failed to select Contact. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in selecting Contact. data->${JSON.stringify(data)}`);
});

```


## selectContact

```TypeScript
function selectContact(): Promise<Array<Contact>>
```

����ѡ����ϵ�˽ӿڣ���ѡ����ϵ��UI���档ʹ��Promise�첽�ص���

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [selectContacts()](arkts-contacts-contact-selectcontacts-f.md#selectContacts-2)

**系统能力：** SystemCapability.Applications.Contacts

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;Contact&gt;&gt; | Promise���󡣷���ѡ�����ϵ��������� |

**示例：**

```TypeScript
import { contact } from '@kit.ContactsKit';

// 打开选择联系人UI界面
let promise = contact.selectContact();
promise.then((data) => {
  console.info(`Succeeded in selecting Contact. data->${JSON.stringify(data)}`);
});

```

