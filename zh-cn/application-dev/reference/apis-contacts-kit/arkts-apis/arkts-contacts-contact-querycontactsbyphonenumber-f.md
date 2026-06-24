# queryContactsByPhoneNumber

## queryContactsByPhoneNumber

```TypeScript
function queryContactsByPhoneNumber(phoneNumber: string, callback: AsyncCallback<Array<Contact>>): void
```

���ݵ绰�����ѯ��ϵ�ˡ�ʹ��callback�첽�ص����ýӿڽ�������ϵ����Ϣ�е�id��key��phoneNumbers���ԡ����Ҫ��ѯ��ϵ�˵�������Ϣ������ʹ��
[queryContact](arkts-contacts-contact-querycontact-f.md#queryContact-8)
�ӿڣ����ݸýӿڷ��ص�����key��ѯ��Ӧ���ں�̨���ô˽ӿڻ�ȡ��ϵ����Ϣ����Ҫ�����Ӧ�ĳ�ʱ����

**起始版本：** 7

**废弃版本：** 10

**替代接口：** queryContactsByPhoneNumber(context:

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| phoneNumber | string | 是 | ��ϵ�˵ĵ绰���룬��֧��ȫƥ�䣬��֧��ͨ���ƥ�䡣 |
| callback | AsyncCallback&lt;Array&lt;Contact&gt;&gt; | 是 | �ص��������ɹ����ز�ѯ������ϵ�˶������飻ʧ�ܷ��ؾ���Ĵ�������Ϣ�� |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { contact } from '@kit.ContactsKit';

// 根据电话号码138xxxxxxxx查询联系人
contact.queryContactsByPhoneNumber('138xxxxxxxx', (err: BusinessError, data) => {
  if (err) {
    console.error(`Failed to query Contacts By PhoneNumber. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in querying Contacts By PhoneNumber. data->${JSON.stringify(data)}`);
});

```


## queryContactsByPhoneNumber

```TypeScript
function queryContactsByPhoneNumber(context: Context, phoneNumber: string, callback: AsyncCallback<Array<Contact>>): void
```

���ݵ绰�����ѯ��ϵ�ˡ�ʹ��callback�첽�ص����ýӿڽ�������ϵ����Ϣ�е�id��key��phoneNumbers���ԡ����Ҫ��ѯ��ϵ�˵�������Ϣ������ʹ��
[queryContact](arkts-contacts-contact-querycontact-f.md#queryContact-8)
�ӿڣ����ݸýӿڷ��ص�����key��ѯ��Ӧ���ں�̨���ô˽ӿڻ�ȡ��ϵ����Ϣ����Ҫ�����Ӧ�ĳ�ʱ����

**起始版本：** 10

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | Ӧ��������Context�� |
| phoneNumber | string | 是 | ��ϵ�˵ĵ绰���룬��֧��ȫƥ�䣬��֧��ͨ���ƥ�䡣 |
| callback | AsyncCallback&lt;Array&lt;Contact&gt;&gt; | 是 | �ص��������ɹ����ز�ѯ������ϵ�˶������飻ʧ�ܷ��ؾ���Ĵ�������Ϣ�� |

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

// 请在组件内获取context。
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
contact.queryContactsByPhoneNumber(context, '138xxxxxxxx', (err: BusinessError, data) => {
  if (err) {
    console.error(`Failed to query Contacts By PhoneNumber. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in querying Contacts By PhoneNumber. data->${JSON.stringify(data)}`);
});

```


## queryContactsByPhoneNumber

```TypeScript
function queryContactsByPhoneNumber(phoneNumber: string, holder: Holder, callback: AsyncCallback<Array<Contact>>): void
```

���ݵ绰�����holder��ѯ��ϵ�ˣ�ʹ��callback�첽�ص����ýӿڷ��ص��б���������ϵ����Ϣ�е�id��key��phoneNumbers���ԡ����Ҫ��ѯ��ϵ�˵�������Ϣ������ʹ��
[queryContact](arkts-contacts-contact-querycontact-f.md#queryContact-8)
�ӿڣ����ݸýӿڷ��ص�����key��ѯ��Ӧ���ں�̨���ô˽ӿڻ�ȡ��ϵ����Ϣ����Ҫ�����Ӧ�ĳ�ʱ����

**起始版本：** 7

**废弃版本：** 10

**替代接口：** queryContactsByPhoneNumber(context:

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| phoneNumber | string | 是 | ��ϵ�˵ĵ绰���룬��֧��ȫƥ�䣬��֧��ͨ���ƥ�䡣 |
| holder | Holder | 是 | ������ϵ�˵�Ӧ����Ϣ�࣬����������Ϊ��Ĭ��ʹ��ϵͳ��ϵ��Ӧ�ò�ѯ�� |
| callback | AsyncCallback&lt;Array&lt;Contact&gt;&gt; | 是 | �ص��������ɹ����ز�ѯ������ϵ�˶������飻ʧ�ܷ��ؾ���Ĵ�������Ϣ�� |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { contact } from '@kit.ContactsKit';

// 根据电话号码138xxxxxxxx和holderId查询联系人
contact.queryContactsByPhoneNumber('138xxxxxxxx', {
  holderId: 1,
  bundleName: "",
  displayName: ""
}, (err: BusinessError, data) => {
  if (err) {
    console.error(`Failed to query Contacts By PhoneNumber. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in querying Contacts By PhoneNumber. data->${JSON.stringify(data)}`);
});

```


## queryContactsByPhoneNumber

```TypeScript
function queryContactsByPhoneNumber(context: Context, phoneNumber: string, holder: Holder, callback: AsyncCallback<Array<Contact>>): void
```

���ݵ绰�����holder��ѯ��ϵ�ˡ�ʹ��callback�첽�ص����ýӿڷ��ص��б���������ϵ����Ϣ�е�id��key��phoneNumbers���ԡ����Ҫ��ѯ��ϵ�˵�������Ϣ������ʹ��
[queryContact](arkts-contacts-contact-querycontact-f.md#queryContact-8)
�ӿڣ����ݸýӿڷ��ص�����key��ѯ��Ӧ���ں�̨���ô˽ӿڻ�ȡ��ϵ����Ϣ����Ҫ�����Ӧ�ĳ�ʱ����

**起始版本：** 10

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | Ӧ��������Context�� |
| phoneNumber | string | 是 | ��ϵ�˵ĵ绰���룬��֧��ȫƥ�䣬��֧��ͨ���ƥ�䡣 |
| holder | Holder | 是 | ������ϵ�˵�Ӧ����Ϣ�࣬����������Ϊ����Ĭ��ʹ��ϵͳ��ϵ��Ӧ�ò�ѯ�� |
| callback | AsyncCallback&lt;Array&lt;Contact&gt;&gt; | 是 | �ص��������ɹ����ز�ѯ������ϵ�˶������飻ʧ�ܷ��ؾ���Ĵ�������Ϣ�� |

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

// 请在组件内获取context。
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
contact.queryContactsByPhoneNumber(context, '138xxxxxxxx', {
  holderId: 1,
  bundleName: '',
  displayName: ''
}, (err: BusinessError, data) => {
  if (err) {
    console.error(`Failed to query Contacts By PhoneNumber. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in querying Contacts By PhoneNumber. data->${JSON.stringify(data)}`);
});

```


## queryContactsByPhoneNumber

```TypeScript
function queryContactsByPhoneNumber(phoneNumber: string, attrs: ContactAttributes, callback: AsyncCallback<Array<Contact>>): void
```

���ݵ绰�����attrs��ѯ��ϵ�ˡ�ʹ��callback�첽�ص����ýӿڷ��ص��б���������ϵ����Ϣ�е�id��key��phoneNumbers���ԡ����Ҫ��ѯ��ϵ�˵�������Ϣ������ʹ��
[queryContact](arkts-contacts-contact-querycontact-f.md#queryContact-8)
�ӿڣ����ݸýӿڷ��ص�����key��ѯ��Ӧ���ں�̨���ô˽ӿڻ�ȡ��ϵ����Ϣ����Ҫ�����Ӧ�ĳ�ʱ����

**起始版本：** 7

**废弃版本：** 10

**替代接口：** queryContactsByPhoneNumber(context:

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| phoneNumber | string | 是 | ��ϵ�˵ĵ绰���룬��֧��ȫƥ�䣬��֧��ͨ���ƥ�䡣 |
| attrs | ContactAttributes | 是 | ��ϵ�˵������б������Ϊ�գ����ѯ��ϵ�˵����������ֶΣ������������绰������ȣ��� |
| callback | AsyncCallback&lt;Array&lt;Contact&gt;&gt; | 是 | �ص��������ɹ����ز�ѯ������ϵ�˶������飻ʧ�ܷ��ؾ���Ĵ�������Ϣ�� |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { contact } from '@kit.ContactsKit';

contact.queryContactsByPhoneNumber('138xxxxxxxx', {
  attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
}, (err: BusinessError, data) => {
  if (err) {
    console.error(`Failed to query Contacts By PhoneNumber. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in querying Contacts By PhoneNumber. data->${JSON.stringify(data)}`);
});

```


## queryContactsByPhoneNumber

```TypeScript
function queryContactsByPhoneNumber(context: Context, phoneNumber: string, attrs: ContactAttributes, callback: AsyncCallback<Array<Contact>>): void
```

���ݵ绰�����attrs��ѯ��ϵ�ˡ�ʹ��callback�첽�ص����ýӿڷ��ص��б���������ϵ����Ϣ�е�id��key��phoneNumbers���ԡ����Ҫ��ѯ��ϵ�˵�������Ϣ������ʹ��
[queryContact](arkts-contacts-contact-querycontact-f.md#queryContact-8)
�ӿڣ����ݸýӿڷ��ص�����key��ѯ��Ӧ���ں�̨���ô˽ӿڻ�ȡ��ϵ����Ϣ����Ҫ�����Ӧ�ĳ�ʱ����

**起始版本：** 10

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | Ӧ��������Context�� |
| phoneNumber | string | 是 | ��ϵ�˵ĵ绰���룬��֧��ȫƥ�䣬��֧��ͨ���ƥ�䡣 |
| attrs | ContactAttributes | 是 | ��ϵ�˵������б������Ϊ�գ����ѯ��ϵ�˵����������ֶΣ������������绰������ȣ��� |
| callback | AsyncCallback&lt;Array&lt;Contact&gt;&gt; | 是 | �ص��������ɹ����ز�ѯ������ϵ�˶������飻ʧ�ܷ��ؾ���Ĵ�������Ϣ�� |

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

// 请在组件内获取context。
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
contact.queryContactsByPhoneNumber(context, '138xxxxxxxx', {
  attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
}, (err: BusinessError, data) => {
  if (err) {
    console.error(`Failed to query Contacts By PhoneNumber. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in querying Contacts By PhoneNumber. data->${JSON.stringify(data)}`);
});

```


## queryContactsByPhoneNumber

```TypeScript
function queryContactsByPhoneNumber(phoneNumber: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback<Array<Contact>>): void
```

���ݵ绰���롢holder��attrs��ѯ��ϵ�ˡ�ʹ��callback�첽�ص����ýӿڷ��ص��б���������ϵ����Ϣ�е�id��key��phoneNumbers���ԡ����Ҫ��ѯ��ϵ�˵�������Ϣ������ʹ��
[queryContact](arkts-contacts-contact-querycontact-f.md#queryContact-8)
�ӿڣ����ݸýӿڷ��ص�����key��ѯ��Ӧ���ں�̨���ô˽ӿڻ�ȡ��ϵ����Ϣ����Ҫ�����Ӧ�ĳ�ʱ����

**起始版本：** 7

**废弃版本：** 10

**替代接口：** queryContactsByPhoneNumber(context:

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| phoneNumber | string | 是 | ��ϵ�˵ĵ绰���룬��֧��ȫƥ�䣬��֧��ͨ���ƥ�䡣 |
| holder | Holder | 是 | ������ϵ�˵�Ӧ����Ϣ�࣬����ò���Ϊ�գ���Ĭ��ʹ��ϵͳ��ϵ��Ӧ�ò�ѯ�� |
| attrs | ContactAttributes | 是 | ��ϵ�˵������б�������ò���Ϊ�գ����ѯ��ϵ�˵����������ֶΡ� |
| callback | AsyncCallback&lt;Array&lt;Contact&gt;&gt; | 是 | �ص��������ɹ����ز�ѯ������ϵ�˶������飻ʧ�ܷ��ؾ���Ĵ�������Ϣ�� |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { contact } from '@kit.ContactsKit';

contact.queryContactsByPhoneNumber('138xxxxxxxx', {
  holderId: 1,
  bundleName: "",
  displayName: ""
}, {
  attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
}, (err: BusinessError, data) => {
  if (err) {
    console.error(`Failed to query Contacts By PhoneNumber. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in querying Contacts By PhoneNumber. data->${JSON.stringify(data)}`);
});

```


## queryContactsByPhoneNumber

```TypeScript
function queryContactsByPhoneNumber(context: Context, phoneNumber: string, holder: Holder, attrs: ContactAttributes,
    callback: AsyncCallback<Array<Contact>>): void
```

���ݵ绰���롢holder��attrs��ѯ��ϵ�ˡ�ʹ��callback�첽�ص����ýӿڷ��ص��б���������ϵ����Ϣ�е�id��key��phoneNumbers���ԡ����Ҫ��ѯ��ϵ�˵�������Ϣ������ʹ��
[queryContact](arkts-contacts-contact-querycontact-f.md#queryContact-8)
�ӿڣ����ݸýӿڷ��ص�����key��ѯ��Ӧ���ں�̨���ô˽ӿڻ�ȡ��ϵ����Ϣ����Ҫ�����Ӧ�ĳ�ʱ����

**起始版本：** 10

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | Ӧ��������Context�� |
| phoneNumber | string | 是 | ��ϵ�˵ĵ绰���룬��֧��ȫƥ�䣬��֧��ͨ���ƥ�䡣 |
| holder | Holder | 是 | ������ϵ�˵�Ӧ����Ϣ�࣬����ò���Ϊ�գ���Ĭ��ʹ��ϵͳ��ϵ��Ӧ�ò�ѯ�� |
| attrs | ContactAttributes | 是 | ��ϵ�˵������б������Ϊ�գ����ѯ��ϵ�˵����������ֶΣ������������绰������ȣ��� |
| callback | AsyncCallback&lt;Array&lt;Contact&gt;&gt; | 是 | �ص��������ɹ����ز�ѯ������ϵ�˶������飻ʧ�ܷ��ؾ���Ĵ�������Ϣ�� |

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

// 请在组件内获取context。
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
contact.queryContactsByPhoneNumber(context, '138xxxxxxxx', {
  holderId: 1,
  bundleName: '',
  displayName: ''
}, {
  attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
}, (err: BusinessError, data) => {
  if (err) {
    console.error(`Failed to query Contacts By PhoneNumber. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in querying Contacts By PhoneNumber. data->${JSON.stringify(data)}`);
});

```


## queryContactsByPhoneNumber

```TypeScript
function queryContactsByPhoneNumber(phoneNumber: string, holder?: Holder, attrs?: ContactAttributes): Promise<Array<Contact>>
```

���ݵ绰���롢holder��attrs��ѯ��ϵ�ˡ�ʹ��Promise�첽�ص����ýӿڷ��ص��б���������ϵ����Ϣ�е�id��key��phoneNumbers���ԡ����Ҫ��ѯ��ϵ�˵�������Ϣ������ʹ��
[queryContact](arkts-contacts-contact-querycontact-f.md#queryContact-8)
�ӿڣ����ݸýӿڷ��ص�����key��ѯ��Ӧ���ں�̨���ô˽ӿڻ�ȡ��ϵ����Ϣ����Ҫ�����Ӧ�ĳ�ʱ����

**起始版本：** 7

**废弃版本：** 10

**替代接口：** queryContactsByPhoneNumber(context:

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| phoneNumber | string | 是 | ��ϵ�˵ĵ绰���룬��֧��ȫƥ�䣬��֧��ͨ���ƥ�䡣 |
| holder | Holder | 否 | ������ϵ�˵�Ӧ����Ϣ�࣬�����ò�������Ĭ��ʹ��ϵͳ��ϵ��Ӧ�ò�ѯ�� |
| attrs | ContactAttributes | 否 | ��ϵ�˵������б�������Ĭ�ϲ�ѯ������ϵ�����ԡ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;Contact&gt;&gt; | Promise���󡣷��ز�ѯ������ϵ��������� |

**示例：**

```TypeScript
import { contact } from '@kit.ContactsKit';

let promise = contact.queryContactsByPhoneNumber('138xxxxxxxx', {
  holderId: 1,
  bundleName: "",
  displayName: ""
}, {
  attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
});
promise.then((data) => {
  console.info(`Succeeded in querying Contacts By PhoneNumber. data->${JSON.stringify(data)}`);
});

```


## queryContactsByPhoneNumber

```TypeScript
function queryContactsByPhoneNumber(context: Context, phoneNumber: string, holder?: Holder, attrs?: ContactAttributes): Promise<Array<Contact>>
```

���ݵ绰���롢holder��attrs��ѯ��ϵ�ˡ�ʹ��Promise�첽�ص����ýӿڷ��ص��б���������ϵ����Ϣ�е�id��key��phoneNumbers���ԡ����Ҫ��ѯ��ϵ�˵�������Ϣ������ʹ��
[queryContact](arkts-contacts-contact-querycontact-f.md#queryContact-8)
�ӿڣ����ݸýӿڷ��ص�����key��ѯ��Ӧ���ں�̨���ô˽ӿڻ�ȡ��ϵ����Ϣ����Ҫ�����Ӧ�ĳ�ʱ����

**起始版本：** 10

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | Ӧ��������Context�� |
| phoneNumber | string | 是 | ��ϵ�˵ĵ绰���룬��֧��ȫƥ�䣬��֧��ͨ���ƥ�䡣 |
| holder | Holder | 否 | ������ϵ�˵�Ӧ����Ϣ�࣬�����ò�������Ĭ��ʹ��ϵͳ��ϵ��Ӧ�ò�ѯ�� |
| attrs | ContactAttributes | 否 | ��ϵ�˵������б�������Ĭ�ϲ�ѯ������ϵ�����ԡ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;Contact&gt;&gt; | Promise���󡣷��ز�ѯ������ϵ��������� |

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

// 请在组件内获取context。
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let promise = contact.queryContactsByPhoneNumber(context, '138xxxxxxxx', {
  holderId: 1,
  bundleName: '',
  displayName: ''
}, {
  attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
});
promise.then((data) => {
  console.info(`Succeeded in querying Contacts By PhoneNumber. data->${JSON.stringify(data)}`);
});

```

