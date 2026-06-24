# queryContacts

## queryContacts

```TypeScript
function queryContacts(callback: AsyncCallback<Array<Contact>>): void
```

��ѯ������ϵ�ˡ�ʹ��callback�첽�ص���

**起始版本：** 7

**废弃版本：** 10

**替代接口：** queryContacts(context:

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;Array&lt;Contact&gt;&gt; | 是 | �ص��������ɹ����ز�ѯ������ϵ�˶������飻ʧ�ܷ��ؾ���Ĵ�������Ϣ�� |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { contact } from '@kit.ContactsKit';

// 异步回调查询联系人
contact.queryContacts((err: BusinessError, data) => {
  if (err) {
    console.error(`Failed to query Contacts. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in querying Contacts. data->${JSON.stringify(data)}`);
});

```


## queryContacts

```TypeScript
function queryContacts(context: Context, callback: AsyncCallback<Array<Contact>>): void
```

��ѯ������ϵ�ˡ�ʹ��callback�첽�ص���

**起始版本：** 10

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | Ӧ��������Context�� |
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
contact.queryContacts(context, (err: BusinessError, data) => {
  if (err) {
    console.error(`Failed to query Contacts. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in querying Contacts. data->${JSON.stringify(data)}`);
});

```


## queryContacts

```TypeScript
function queryContacts(holder: Holder, callback: AsyncCallback<Array<Contact>>): void
```

����holder��ѯ������ϵ�ˡ�ʹ��callback�첽�ص���

**起始版本：** 7

**废弃版本：** 10

**替代接口：** queryContacts(context:

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| holder | Holder | 是 | ������ϵ�˵�Ӧ����Ϣ�࣬����������Ϊ����Ĭ��ʹ��ϵͳ��ϵ��Ӧ�ò�ѯ�� |
| callback | AsyncCallback&lt;Array&lt;Contact&gt;&gt; | 是 | �ص��������ɹ����ز�ѯ������ϵ�˶������飻ʧ�ܷ��ؾ���Ĵ�������Ϣ�� |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { contact } from '@kit.ContactsKit';

// 异步回调查询联系人
contact.queryContacts({
  holderId: 1,
  bundleName: "",
  displayName: ""
}, (err: BusinessError, data) => {
  if (err) {
    console.error(`Failed to query Contacts. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in querying Contacts. data->${JSON.stringify(data)}`);
});

```


## queryContacts

```TypeScript
function queryContacts(context: Context, holder: Holder, callback: AsyncCallback<Array<Contact>>): void
```

����holder��ѯ������ϵ�ˡ�ʹ��callback�첽�ص���

**起始版本：** 10

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | Ӧ��������Context�� |
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
contact.queryContacts(context, {
  holderId: 1,
  bundleName: "",
  displayName: ""
}, (err: BusinessError, data) => {
  if (err) {
    console.error(`Failed to query Contacts. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in querying Contacts. data->${JSON.stringify(data)}`);
});

```


## queryContacts

```TypeScript
function queryContacts(attrs: ContactAttributes, callback: AsyncCallback<Array<Contact>>): void
```

����attrs��ѯ������ϵ�ˡ�ʹ��callback�첽�ص���

**起始版本：** 7

**废弃版本：** 10

**替代接口：** queryContacts(context:

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| attrs | ContactAttributes | 是 | ��ϵ�˵������б������Ϊ�գ����ѯ��ϵ�˵����������ֶΣ������������绰������ȣ��� |
| callback | AsyncCallback&lt;Array&lt;Contact&gt;&gt; | 是 | �ص��������ɹ����ز�ѯ������ϵ�˶������飻ʧ�ܷ��ؾ���Ĵ�������Ϣ�� |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { contact } from '@kit.ContactsKit';

// 异步回调查询联系人
contact.queryContacts({
  attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
}, (err: BusinessError, data) => {
  if (err) {
    console.error(`Failed to query Contacts. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in querying Contacts. data->${JSON.stringify(data)}`);
});

```


## queryContacts

```TypeScript
function queryContacts(context: Context, attrs: ContactAttributes, callback: AsyncCallback<Array<Contact>>): void
```

����attrs��ѯ������ϵ�ˡ�ʹ��callback�첽�ص���

**起始版本：** 10

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | Ӧ��������Context�� |
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
contact.queryContacts(context, {
  attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
}, (err: BusinessError, data) => {
  if (err) {
    console.error(`Failed to query Contacts. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in querying Contacts. data->${JSON.stringify(data)}`);
});

```


## queryContacts

```TypeScript
function queryContacts(holder: Holder, attrs: ContactAttributes, callback: AsyncCallback<Array<Contact>>): void
```

����holder��attrs��ѯ������ϵ�ˡ�ʹ��callback�첽�ص���

**起始版本：** 7

**废弃版本：** 10

**替代接口：** queryContacts(context:

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| holder | Holder | 是 | ������ϵ�˵�Ӧ����Ϣ�࣬����������Ϊ����Ĭ��ʹ��ϵͳ��ϵ��Ӧ�ò�ѯ�� |
| attrs | ContactAttributes | 是 | ��ϵ�˵������б������Ϊ�գ����ѯ��ϵ�˵����������ֶΣ������������绰������ȣ��� |
| callback | AsyncCallback&lt;Array&lt;Contact&gt;&gt; | 是 | �ص��������ɹ����ز�ѯ������ϵ�˶������飻ʧ�ܷ��ؾ���Ĵ�������Ϣ�� |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { contact } from '@kit.ContactsKit';

// 异步回调查询联系人
contact.queryContacts({
  holderId: 1,
  bundleName: "",
  displayName: ""
}, {
  attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
}, (err: BusinessError, data) => {
  if (err) {
    console.error(`Failed to query Contacts. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in querying Contacts. data->${JSON.stringify(data)}`);
});

```


## queryContacts

```TypeScript
function queryContacts(context: Context, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback<Array<Contact>>): void
```

����holder��attrs��ѯ������ϵ�ˡ�ʹ��callback�첽�ص���

**起始版本：** 10

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | Ӧ��������Context�� |
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
contact.queryContacts(context, {
  holderId: 1,
  bundleName: "",
  displayName: ""
}, {
  attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
}, (err: BusinessError, data) => {
  if (err) {
    console.error(`Failed to query Contacts. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in querying Contacts. data->${JSON.stringify(data)}`);
});

```


## queryContacts

```TypeScript
function queryContacts(holder?: Holder, attrs?: ContactAttributes): Promise<Array<Contact>>
```

����holder��attrs��ѯ������ϵ�ˡ�ʹ��Promise�첽�ص���

**起始版本：** 7

**废弃版本：** 10

**替代接口：** queryContacts(context:

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| holder | Holder | 否 | ������ϵ�˵�Ӧ����Ϣ�࣬�����ò�������Ĭ��ʹ��ϵͳ��ϵ��Ӧ�ò�ѯ�� |
| attrs | ContactAttributes | 否 | ��ϵ�˵������б�������Ĭ�ϲ�ѯ������ϵ�����ԡ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;Contact&gt;&gt; | Promise���󡣷��ز�ѯ������ϵ��������� |

**示例：**

```TypeScript
  import { contact } from '@kit.ContactsKit';

  // 根据holder和attrs查询所有联系人
  let promise = contact.queryContacts({
    holderId: 1,
    bundleName: "",
    displayName: ""
  }, {
    attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
  });
  promise.then((data) => {
    console.info(`Succeeded in querying Contacts. data->${JSON.stringify(data)}`);
  });

```


## queryContacts

```TypeScript
function queryContacts(context: Context, holder?: Holder, attrs?: ContactAttributes): Promise<Array<Contact>>
```

����holder��attrs��ѯ������ϵ�ˡ�ʹ��Promise�첽�ص���

**起始版本：** 10

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | Ӧ��������Context�� |
| holder | Holder | 否 | ������ϵ�˵�Ӧ����Ϣ�࣬���Ϊ�գ�Ĭ��ʹ��ϵͳ��ϵ��Ӧ�ò�ѯ�� |
| attrs | ContactAttributes | 否 | ��ϵ�˵������б��������ò���Ĭ�ϲ�ѯ������ϵ�����ԡ� |

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
let promise = contact.queryContacts(context, {
  holderId: 1,
  bundleName: "",
  displayName: ""
}, {
  attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
});
promise.then((data) => {
  console.info(`Succeeded in querying Contacts. data: ${JSON.stringify(data)}`);
});

```

