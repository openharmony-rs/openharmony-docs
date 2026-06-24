# updateContact

## updateContact

```TypeScript
function updateContact(contact: Contact, callback: AsyncCallback<void>): void
```

������ϵ�ˡ�ʹ��callback�첽�ص���

**起始版本：** 7

**废弃版本：** 10

**替代接口：** updateContact(context:

**需要权限：** ohos.permission.WRITE_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| contact | Contact | 是 | ��ϵ����Ϣ��id�����ͨ��[selectContacts](arkts-contacts-contact-selectcontacts-f.md#selectContacts-2)�ӿڻ�ȡ�� |
| callback | AsyncCallback&lt;void&gt; | 是 | �ص��������ɹ����ظ��µ���ϵ��id��ʧ�ܷ��ؾ���Ĵ�������Ϣ�� |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { contact } from '@kit.ContactsKit';

// 通过selectContacts接口选择联系人。
contact.selectContacts().then((data) => {
  // 请在组件内获取context。
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  contact.updateContact(context, {
    id: data[0].id, // 选择联系人的id。
    name: {
      fullName: 'xxx'
    },
    phoneNumbers: [{
      phoneNumber: '138xxxxxxxx'
    }]
  }, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to update Contact. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in updating Contact.');
  });
});

```


## updateContact

```TypeScript
function updateContact(context: Context, contact: Contact, callback: AsyncCallback<void>): void
```

������ϵ�ˡ�ʹ��callback�첽�ص���

**起始版本：** 10

**需要权限：** ohos.permission.WRITE_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | Ӧ��������Context�� |
| contact | Contact | 是 | ��ϵ����Ϣ��id�����ͨ��[selectContacts](arkts-contacts-contact-selectcontacts-f.md#selectContacts-2)�ӿڻ�ȡ�� |
| callback | AsyncCallback&lt;void&gt; | 是 | �ص��������ɹ����ظ��µ���ϵ��id��ʧ�ܷ��ؾ���Ĵ�������Ϣ�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: Mandatory parameters are left unspecified. |

**示例：**

在本文档的示例中，通过this.context来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需要在界面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { contact } from '@kit.ContactsKit';
import { common } from '@kit.AbilityKit';

// 通过selectContacts接口选择联系人。
contact.selectContacts().then((data) => {
  // 请在组件内获取context。
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;

  contact.updateContact(context, {
    id: data[0].id, // 选择联系人的id。
    name: {
      fullName: 'xxx'
    },
    phoneNumbers: [{
      phoneNumber: '138xxxxxxxx'
    }]
  }, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to update Contact. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in updating Contact.');
  });
});

```


## updateContact

```TypeScript
function updateContact(contact: Contact, attrs: ContactAttributes, callback: AsyncCallback<void>): void
```

������ϵ�ˣ�֧�ִ�����ϵ�˵������б���ʹ��callback�첽�ص���

**起始版本：** 7

**废弃版本：** 10

**替代接口：** updateContact(context:

**需要权限：** ohos.permission.WRITE_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| contact | Contact | 是 | ��ϵ����Ϣ��id�����ͨ��[selectContacts](arkts-contacts-contact-selectcontacts-f.md#selectContacts-2)�ӿڻ�ȡ�� |
| attrs | ContactAttributes | 是 | ��ϵ�˵������б������Ϊ�գ����ѯ��ϵ�˵����������ֶΣ������������绰������ȣ��� |
| callback | AsyncCallback&lt;void&gt; | 是 | �ص��������ɹ����ظ��µ���ϵ��id��ʧ�ܷ��ؾ���Ĵ�������Ϣ�� |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { contact } from '@kit.ContactsKit';


// 通过selectContacts接口选择联系人。
contact.selectContacts().then((data) => {
  contact.updateContact({
    id: data[0].id, // 选择联系人的id。
    name: {
      fullName: 'xxx'
    },
    phoneNumbers: [{
      phoneNumber: '138xxxxxxxx'
    }]
  }, {
    attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
  }, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to update Contact. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in updating Contact.');
  });
});

```


## updateContact

```TypeScript
function updateContact(context: Context, contact: Contact, attrs: ContactAttributes, callback: AsyncCallback<void>): void
```

������ϵ�ˣ�֧�ִ�����ϵ�˵������б�����ʹ��callback�첽�ص���

**起始版本：** 10

**需要权限：** ohos.permission.WRITE_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | Ӧ��������Context�� |
| contact | Contact | 是 | ��ϵ����Ϣ��id�����ͨ��[selectContacts](arkts-contacts-contact-selectcontacts-f.md#selectContacts-2)�ӿڻ�ȡ�� |
| attrs | ContactAttributes | 是 | ��ϵ�˵������б������Ϊ�գ����ѯ��ϵ�˵����������ֶΣ������������绰������ȣ��� |
| callback | AsyncCallback&lt;void&gt; | 是 | �ص��������ɹ����ظ��µ���ϵ��id��ʧ�ܷ��ؾ���Ĵ�������Ϣ�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: Mandatory parameters are left unspecified. |

**示例：**

在本文档的示例中，通过this.context来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需要在界面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { contact } from '@kit.ContactsKit';
import { common } from '@kit.AbilityKit';

// 通过selectContacts接口选择联系人。
contact.selectContacts().then((data) => {
  // 请在组件内获取context。
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  contact.updateContact(context, {
    id: data[0].id, // 选择联系人的id。
    name: {
      fullName: 'xxx'
    },
    phoneNumbers: [{
      phoneNumber: '138xxxxxxxx'
    }]
  }, {
    attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
  }, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to update Contact. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in updating Contact.');
  });
});

```


## updateContact

```TypeScript
function updateContact(contact: Contact, attrs?: ContactAttributes): Promise<void>
```

������ϵ�ˣ�֧�ִ�����ϵ�˵������б���ʹ��Promise�첽�ص���

**起始版本：** 7

**废弃版本：** 10

**替代接口：** updateContact(context:

**需要权限：** ohos.permission.WRITE_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| contact | Contact | 是 | ��ϵ����Ϣ��id�����ͨ��[selectContacts](arkts-contacts-contact-selectcontacts-f.md#selectContacts-2)�ӿڻ�ȡ�� |
| attrs | ContactAttributes | 否 | ��ϵ�˵������б������Ϊ�գ����ѯ��ϵ�˵����������ֶΣ������������绰������ȣ��� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise�����޷��ؽ����Promise���� |

**示例：**

```TypeScript
import { contact } from '@kit.ContactsKit';

// 通过selectContacts接口选择联系人。
contact.selectContacts().then((data) => {
  let promise = contact.updateContact({
    id: data[0].id, // 选择联系人的id。
    name: {
      fullName: 'xxx'
    },
    phoneNumbers: [{
      phoneNumber: '138xxxxxxxx'
    }]
  }, {
    attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
  });
  promise.then(() => {
    console.info('Succeeded in updating Contact.');
  });
});

```


## updateContact

```TypeScript
function updateContact(context: Context, contact: Contact, attrs?: ContactAttributes): Promise<void>
```

������ϵ�ˣ�֧�ִ�����ϵ�˵������б�����ʹ��Promise�첽�ص���

**起始版本：** 10

**需要权限：** ohos.permission.WRITE_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | Ӧ��������Context�� |
| contact | Contact | 是 | ��ϵ����Ϣ��id�����ͨ��[selectContacts](arkts-contacts-contact-selectcontacts-f.md#selectContacts-2)�ӿڻ�ȡ�� |
| attrs | ContactAttributes | 否 | ��ϵ�˵������б������Ϊ�գ����ѯ��ϵ�˵����������ֶΣ������������绰������ȣ��� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise�����޷��ؽ����Promise���� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: Mandatory parameters are left unspecified. |

**示例：**

在本文档的示例中，通过this.context来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需要在界面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // 通过selectContacts接口选择联系人。
  contact.selectContacts().then((data) => {
    // 请在组件内获取context。
    let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
    let promise = contact.updateContact(context, {
      id: data[0].id, // 选择联系人的id。
      name: {
        fullName: 'xxx'
      },
      phoneNumbers: [{
        phoneNumber: '138xxxxxxxx'
      }]
    }, {
      attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
    });
    promise.then(() => {
      console.info('Succeeded in updating Contact.');
    });
  });

```

