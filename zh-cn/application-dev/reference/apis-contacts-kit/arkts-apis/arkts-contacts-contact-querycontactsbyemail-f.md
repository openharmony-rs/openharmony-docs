# queryContactsByEmail

## queryContactsByEmail

```TypeScript
function queryContactsByEmail(email: string, callback: AsyncCallback<Array<Contact>>): void
```

����email��ѯ��ϵ�ˡ�ʹ��callback�첽�ص����ýӿڷ��ص��б���������ϵ����Ϣ�е�id��key��Emails���ԡ����Ҫ��ѯ��ϵ�˵�������Ϣ������ʹ��
[queryContact](arkts-contacts-contact-querycontact-f.md#queryContact-8)
�ӿڣ����ݸýӿڷ��ص�����key��ѯ��

**起始版本：** 7

**废弃版本：** 10

**替代接口：** queryContactsByEmail(context:

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| email | string | 是 | ��ϵ�˵������ַ�� |
| callback | AsyncCallback&lt;Array&lt;Contact&gt;&gt; | 是 | �ص��������ɹ����ز�ѯ������ϵ�˶������飻ʧ�ܷ��ؾ���Ĵ�������Ϣ�� |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { contact } from '@kit.ContactsKit';

contact.queryContactsByEmail('xxx@email.com', (err: BusinessError, data) => {
  if (err) {
    console.error(`Failed to query Contacts By Email. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in querying Contacts By Email. data->${JSON.stringify(data)}`);
});

```


## queryContactsByEmail

```TypeScript
function queryContactsByEmail(context: Context, email: string, callback: AsyncCallback<Array<Contact>>): void
```

����email��ѯ��ϵ�ˡ�ʹ��callback�첽�ص����ýӿڷ��ص��б���������ϵ����Ϣ�е�id��key��Emails���ԡ����Ҫ��ѯ��ϵ�˵�������Ϣ������ʹ��
[queryContact](arkts-contacts-contact-querycontact-f.md#queryContact-8)
�ӿڣ����ݸýӿڷ��ص�����key��ѯ��

**起始版本：** 10

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | Ӧ��������Context�� |
| email | string | 是 | ��ϵ�˵������ַ�� |
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
contact.queryContactsByEmail(context, 'xxx@email.com', (err: BusinessError, data) => {
  if (err) {
    console.error(`Failed to query Contacts By Email. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in querying Contacts By Email. data->${JSON.stringify(data)}`);
});

```


## queryContactsByEmail

```TypeScript
function queryContactsByEmail(email: string, holder: Holder, callback: AsyncCallback<Array<Contact>>): void
```

����email��holder��ѯ��ϵ�ˡ�ʹ��callback�첽�ص����ýӿڷ��ص��б���������ϵ����Ϣ�е�id��key��Emails���ԡ����Ҫ��ѯ��ϵ�˵�������Ϣ������ʹ��
[queryContact](arkts-contacts-contact-querycontact-f.md#queryContact-8)
�ӿڣ����ݸýӿڷ��ص�����key��ѯ��

**起始版本：** 7

**废弃版本：** 10

**替代接口：** queryContactsByEmail(context:

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| email | string | 是 | ��ϵ�˵������ַ�� |
| holder | Holder | 是 | ������ϵ�˵�Ӧ����Ϣ�࣬����������Ϊ��Ĭ��ʹ��ϵͳ��ϵ��Ӧ�ò�ѯ�� |
| callback | AsyncCallback&lt;Array&lt;Contact&gt;&gt; | 是 | �ص��������ɹ����ز�ѯ������ϵ�˶������飻ʧ�ܷ��ؾ���Ĵ�������Ϣ�� |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { contact } from '@kit.ContactsKit';

contact.queryContactsByEmail('xxx@email.com', {
  holderId: 1,
  bundleName: "",
  displayName: ""
}, (err: BusinessError, data) => {
  if (err) {
    console.error(`Failed to query Contacts By Email. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in querying Contacts By Email. data->${JSON.stringify(data)}`);
});

```


## queryContactsByEmail

```TypeScript
function queryContactsByEmail(context: Context, email: string, holder: Holder,
    callback: AsyncCallback<Array<Contact>>): void
```

����email��holder��ѯ��ϵ�ˡ�ʹ��callback�첽�ص����ýӿڷ��ص��б���������ϵ����Ϣ�е�id��key��Emails���ԡ����Ҫ��ѯ��ϵ�˵�������Ϣ������ʹ��
[queryContact](arkts-contacts-contact-querycontact-f.md#queryContact-8)
�ӿڣ����ݸýӿڷ��ص�����key��ѯ��

**起始版本：** 10

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | Ӧ��������Context�� |
| email | string | 是 | ��ϵ�˵������ַ�� |
| holder | Holder | 是 | ������ϵ�˵�Ӧ����Ϣ�࣬����������Ϊ����ʹ��ϵͳ��ϵ��Ӧ�á� |
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
contact.queryContactsByEmail(context, 'xxx@email.com', {
  holderId: 1,
  bundleName: '',
  displayName: ''
}, (err: BusinessError, data) => {
  if (err) {
    console.error(`Failed to query Contacts By Email. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in querying Contacts By Email. data->${JSON.stringify(data)}`);
});

```


## queryContactsByEmail

```TypeScript
function queryContactsByEmail(email: string, attrs: ContactAttributes, callback: AsyncCallback<Array<Contact>>): void
```

����email��attrs��ѯ��ϵ�ˡ�ʹ��callback�첽�ص����ýӿڷ��ص��б���������ϵ����Ϣ�е�id��key��Emails���ԡ����Ҫ��ѯ��ϵ�˵�������Ϣ������ʹ��
[queryContact](arkts-contacts-contact-querycontact-f.md#queryContact-8)
�ӿڣ����ݸýӿڷ��ص�����key��ѯ��

**起始版本：** 7

**废弃版本：** 10

**替代接口：** queryContactsByEmail(context:

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| email | string | 是 | ��ϵ�˵������ַ�� |
| attrs | ContactAttributes | 是 | ��ϵ�˵������б������Ϊ�գ����ѯ��ϵ�˵����������ֶΣ������������绰������ȣ��� |
| callback | AsyncCallback&lt;Array&lt;Contact&gt;&gt; | 是 | �ص��������ɹ����ز�ѯ������ϵ�˶������飻ʧ�ܷ��ؾ���Ĵ�������Ϣ�� |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { contact } from '@kit.ContactsKit';

contact.queryContactsByEmail('xxx@email.com', {
  attributes: [contact.Attribute.ATTR_EMAIL, contact.Attribute.ATTR_NAME]
}, (err: BusinessError, data) => {
  if (err) {
    console.error(`Failed to query Contacts By Email. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in querying Contacts By Email. data->${JSON.stringify(data)}`);
});

```


## queryContactsByEmail

```TypeScript
function queryContactsByEmail(context: Context, email: string, attrs: ContactAttributes,
    callback: AsyncCallback<Array<Contact>>): void
```

����email��attrs��ѯ��ϵ�ˡ�ʹ��callback�첽�ص����ýӿڷ��ص��б���������ϵ����Ϣ�е�id��key��Emails���ԡ����Ҫ��ѯ��ϵ�˵�������Ϣ������ʹ��
[queryContact](arkts-contacts-contact-querycontact-f.md#queryContact-8)
�ӿڣ����ݸýӿڷ��ص�����key��ѯ��

**起始版本：** 10

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | Ӧ��������Context�� |
| email | string | 是 | ��ϵ�˵������ַ�� |
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
contact.queryContactsByEmail(context, 'xxx@email.com', {
  attributes: [contact.Attribute.ATTR_EMAIL, contact.Attribute.ATTR_NAME]
}, (err: BusinessError, data) => {
  if (err) {
    console.error(`Failed to query Contacts By Email. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in querying Contacts By Email. data->${JSON.stringify(data)}`);
});

```


## queryContactsByEmail

```TypeScript
function queryContactsByEmail(email: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback<Array<Contact>>): void
```

����email��holder��attrs��ѯ��ϵ�ˡ�ʹ��callback�첽�ص����ýӿڷ��ص��б���������ϵ����Ϣ�е�id��key��Emails���ԡ����Ҫ��ѯ��ϵ�˵�������Ϣ������ʹ��
[queryContact](arkts-contacts-contact-querycontact-f.md#queryContact-8)
�ӿڣ����ݸýӿڷ��ص�����key��ѯ��

**起始版本：** 7

**废弃版本：** 10

**替代接口：** queryContactsByEmail(context:

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| email | string | 是 | ��ϵ�˵������ַ�� |
| holder | Holder | 是 | ������ϵ�˵�Ӧ����Ϣ�࣬����������Ϊ����Ĭ��ʹ��ϵͳ��ϵ��Ӧ�ò�ѯ�� |
| attrs | ContactAttributes | 是 | ��ϵ�˵������б������Ϊ�գ����ѯ��ϵ�˵����������ֶΣ������������绰������ȣ��� |
| callback | AsyncCallback&lt;Array&lt;Contact&gt;&gt; | 是 | �ص��������ɹ����ز�ѯ������ϵ�˶������飻ʧ�ܷ��ؾ���Ĵ�������Ϣ�� |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { contact } from '@kit.ContactsKit';

contact.queryContactsByEmail('xxx@email.com', {
  holderId: 1,
  bundleName: "",
  displayName: ""
}, {
  attributes: [contact.Attribute.ATTR_EMAIL, contact.Attribute.ATTR_NAME]
}, (err: BusinessError, data) => {
  if (err) {
    console.error(`Failed to query Contacts By Email. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in querying Contacts By Email. data->${JSON.stringify(data)}`);
});

```


## queryContactsByEmail

```TypeScript
function queryContactsByEmail(context: Context, email: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback<Array<Contact>>): void
```

����email��holder��attrs��ѯ��ϵ�ˡ�ʹ��callback�첽�ص����ýӿڷ��ص��б���������ϵ����Ϣ�е�id��key��Emails���ԡ����Ҫ��ѯ��ϵ�˵�������Ϣ������ʹ��
[queryContact](arkts-contacts-contact-querycontact-f.md#queryContact-8)
�ӿڣ����ݸýӿڷ��ص�����key��ѯ��

**起始版本：** 10

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | Ӧ��������Context�� |
| email | string | 是 | ��ϵ�˵������ַ�� |
| holder | Holder | 是 | ������ϵ�˵�Ӧ����Ϣ�࣬����������Ϊ����Ĭ��ʹ��ϵͳ��ϵ��Ӧ�ò�ѯ�� |
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
contact.queryContactsByEmail(context, 'xxx@email.com', {
  holderId: 1,
  bundleName: '',
  displayName: ''
}, {
  attributes: [contact.Attribute.ATTR_EMAIL, contact.Attribute.ATTR_NAME]
}, (err: BusinessError, data) => {
  if (err) {
    console.error(`Failed to query Contacts By Email. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in querying Contacts By Email. data->${JSON.stringify(data)}`);
});

```


## queryContactsByEmail

```TypeScript
function queryContactsByEmail(email: string, holder?: Holder, attrs?: ContactAttributes): Promise<Array<Contact>>
```

����email��holder��attrs��ѯ��ϵ�ˡ�ʹ��Promise�첽�ص����ýӿڷ��ص��б���������ϵ����Ϣ�е�id��key��Emails���ԡ����Ҫ��ѯ��ϵ�˵�������Ϣ������ʹ��
[queryContact](arkts-contacts-contact-querycontact-f.md#queryContact-8)
�ӿڣ����ݸýӿڷ��ص�����key��ѯ��

**起始版本：** 7

**废弃版本：** 10

**替代接口：** queryContactsByEmail(context:

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| email | string | 是 | ��ϵ�˵������ַ�� |
| holder | Holder | 否 | ������ϵ�˵�Ӧ����Ϣ�࣬�����ò�������Ĭ��ʹ��ϵͳ��ϵ��Ӧ�ò�ѯ�� |
| attrs | ContactAttributes | 否 | ��ϵ�˵������б�������Ĭ�ϲ�ѯ������ϵ�����ԡ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;Contact&gt;&gt; | Promise���󡣷��ز�ѯ������ϵ��������� |

**示例：**

```TypeScript
import { contact } from '@kit.ContactsKit';

let promise = contact.queryContactsByEmail('xxx@email.com', {
  holderId: 1,
  bundleName: "",
  displayName: ""
}, {
  attributes: [contact.Attribute.ATTR_EMAIL, contact.Attribute.ATTR_NAME]
});
promise.then((data) => {
  console.info(`Succeeded in querying Contacts By Email. data->${JSON.stringify(data)}`);
});

```


## queryContactsByEmail

```TypeScript
function queryContactsByEmail(context: Context, email: string, holder?: Holder, attrs?: ContactAttributes): Promise<Array<Contact>>
```

����email��holder��attrs��ѯ��ϵ�ˡ�ʹ��Promise�첽�ص����ýӿڷ��ص��б���������ϵ����Ϣ�е�id��key��Emails���ԡ����Ҫ��ѯ��ϵ�˵�������Ϣ������ʹ��
[queryContact](arkts-contacts-contact-querycontact-f.md#queryContact-8)
�ӿڣ����ݸýӿڷ��ص�����key��ѯ��

**起始版本：** 10

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | Ӧ��������Context�� |
| email | string | 是 | ��ϵ�˵������ַ�� |
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
import { common } from '@kit.AbilityKit';

// 请在组件内获取context。
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let promise = contact.queryContactsByEmail(context, 'xxx@email.com', {
  holderId: 1,
  bundleName: '',
  displayName: ''
}, {
  attributes: [contact.Attribute.ATTR_EMAIL, contact.Attribute.ATTR_NAME]
});
promise.then((data) => {
  console.info(`Succeeded in querying Contacts By Email. data->${JSON.stringify(data)}`);
});

```

