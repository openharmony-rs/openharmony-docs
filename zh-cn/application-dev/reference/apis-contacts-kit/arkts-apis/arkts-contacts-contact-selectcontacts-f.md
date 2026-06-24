# selectContacts

## selectContacts

```TypeScript
function selectContacts(callback: AsyncCallback<Array<Contact>>): void
```

����ѡ����ϵ�˽ӿڣ���ѡ����ϵ��UI���档ʹ��callback�첽�ص���

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Applications.Contacts

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;Array&lt;Contact&gt;&gt; | 是 | �ص��������ɹ�����ѡ�����ϵ�˶������飻ʧ�ܷ��ؾ���Ĵ�������Ϣ�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: Mandatory parameters are left unspecified. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { contact } from '@kit.ContactsKit';

// 打开选择联系人UI界面
contact.selectContacts((err: BusinessError, data) => {
  if (err) {
    console.error(`Failed to select Contacts. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in selecting Contacts. data->${JSON.stringify(data)}`);
});

```


## selectContacts

```TypeScript
function selectContacts(): Promise<Array<Contact>>
```

����ѡ����ϵ�˽ӿڣ���ѡ����ϵ��UI���档ʹ��Promise�첽�ص���

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Applications.Contacts

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;Contact&gt;&gt; | Promise���󡣷���ѡ�����ϵ��������� |

**示例：**

```TypeScript
import { contact } from '@kit.ContactsKit';

// 打开选择联系人UI界面
let promise = contact.selectContacts();
promise.then((data) => {
  console.info(`Succeeded in selecting Contacts. data->${JSON.stringify(data)}`);
});

```


## selectContacts

```TypeScript
function selectContacts(options: ContactSelectionOptions, callback: AsyncCallback<Array<Contact>>): void
```

����ѡ����ϵ�˽ӿڣ���ѡ����ϵ��UI���棨ѡ����ϵ��ʱ֧�ִ���[ɸѡ����](arkts-contacts-contact-contactselectionoptions-i.md#ContactSelectionOptions)����ʹ��callback�첽�ص���

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Applications.Contacts

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | ContactSelectionOptions | 是 | ѡ����ϵ��ʱ��ɸѡ��������ʾ��ѡ���ѡ�� |
| callback | AsyncCallback&lt;Array&lt;Contact&gt;&gt; | 是 | �ص��������ɹ�����ѡ�����ϵ�˶������飻ʧ�ܷ��ؾ���Ĵ�������Ϣ�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: Mandatory parameters are left unspecified. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { contact } from '@kit.ContactsKit';

// 打开选择联系人UI界面，支持选择一个联系人
contact.selectContacts({
  isMultiSelect:false
}, (err: BusinessError, data) => {
  if (err) {
    console.error(`Failed to select Contacts. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in selecting Contacts. data->${JSON.stringify(data)}`);
});

```


## selectContacts

```TypeScript
function selectContacts(options: ContactSelectionOptions): Promise<Array<Contact>>
```

����ѡ����ϵ�˽ӿڣ���ѡ����ϵ��UI���棨ѡ����ϵ��ʱ֧�ִ���ɸѡ��������ʹ��Promise�첽�ص���

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Applications.Contacts

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | ContactSelectionOptions | 是 | ѡ����ϵ��ʱ��ɸѡ����������ָ���ǵ�ѡ���Ƕ�ѡ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;Contact&gt;&gt; | Promise���󡣷���ѡ�����ϵ��������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: Mandatory parameters are left unspecified. |

**示例：**

```TypeScript
import { contact } from '@kit.ContactsKit';

// 打开选择联系人UI界面，支持选择一个联系人
let promise = contact.selectContacts({isMultiSelect:false});
promise.then((data) => {
  console.info(`Succeeded in selecting Contacts. data->${JSON.stringify(data)}`);
});

```

