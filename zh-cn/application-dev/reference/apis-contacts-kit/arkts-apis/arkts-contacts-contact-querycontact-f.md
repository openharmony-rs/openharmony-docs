# queryContact

## queryContact

```TypeScript
function queryContact(key: string, callback: AsyncCallback<Contact>): void
```

������ϵ��Ψһ��ʶ��key��ѯ��ϵ�ˡ�ʹ��callback�첽�ص���

**起始版本：** 7

**废弃版本：** 10

**替代接口：** queryContact(context:

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | ��ϵ�˵�Ψһ��ѯ��key�����½���ϵ��ʱϵͳ�Զ����ɵ�Ψһ��ʶ��һ����ϵ�˶�Ӧһ��key,����ͨ��[queryKey](contact.queryKey(context: Context, id: number, callback: AsyncCallback): void)��ȡ�� |
| callback | AsyncCallback&lt;Contact&gt; | 是 | �ص��������ɹ����ز�ѯ����ϵ�˶���ʧ�ܷ��ؾ���Ĵ�������Ϣ�� |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { contact } from '@kit.ContactsKit';

// 查询key='xxx'的联系人
contact.queryContact('xxx', (err: BusinessError, data) => {
  if (err) {
    console.error(`Failed to query Contact. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in querying Contact. data->${JSON.stringify(data)}`);
});

```


## queryContact

```TypeScript
function queryContact(context: Context, key: string, callback: AsyncCallback<Contact>): void
```

����key��ѯ��ϵ�ˡ�ʹ��callback�첽�ص���

**起始版本：** 10

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | Ӧ��������Context�� |
| key | string | 是 | ��ϵ�˵�Ψһ��ѯ��key�����½���ϵ��ʱϵͳ�Զ����ɵ�Ψһ��ʶ��һ����ϵ�˶�Ӧһ��key,����ͨ��[queryKey](contact.queryKey(context: Context, id: number, callback: AsyncCallback): void)��ȡ�� |
| callback | AsyncCallback&lt;Contact&gt; | 是 | �ص��������ɹ����ز�ѯ����ϵ�˶���ʧ�ܷ��ؾ���Ĵ�������Ϣ�� |

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
contact.queryContact(context, 'xxx', (err: BusinessError, data) => {
  if (err) {
    console.error(`Failed to query Contact. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in querying Contact. data->${JSON.stringify(data)}`);
});

```


## queryContact

```TypeScript
function queryContact(key: string, holder: Holder, callback: AsyncCallback<Contact>): void
```

����key��holder��ѯ��ϵ�ˡ�ʹ��callback�첽�ص���

**起始版本：** 7

**废弃版本：** 10

**替代接口：** queryContact(context:

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | ��ϵ�˵�Ψһ��ѯ��key�����½���ϵ��ʱϵͳ�Զ����ɵ�Ψһ��ʶ��һ����ϵ�˶�Ӧһ��key,����ͨ��[queryKey](contact.queryKey(context: Context, id: number, callback: AsyncCallback): void)��ȡ�� |
| holder | Holder | 是 | ������ϵ�˵�Ӧ����Ϣ�࣬����������Ϊ����Ĭ��ʹ��ϵͳ��ϵ��Ӧ�ò�ѯ�� |
| callback | AsyncCallback&lt;Contact&gt; | 是 | �ص��������ɹ����ز�ѯ����ϵ�˶���ʧ�ܷ��ؾ���Ĵ�������Ϣ�� |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { contact } from '@kit.ContactsKit';

// 查询key='xxx'，holderId为1的联系人
contact.queryContact('xxx', {
  holderId: 1,
  bundleName: "",
  displayName: ""
}, (err: BusinessError, data) => {
  if (err) {
    console.error(`Failed to query Contact. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in querying Contact. data->${JSON.stringify(data)}`);
});

```


## queryContact

```TypeScript
function queryContact(context: Context, key: string, holder: Holder, callback: AsyncCallback<Contact>): void
```

����key��holder��ѯ��ϵ�ˡ�ʹ��callback�첽�ص���

**起始版本：** 10

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | Ӧ��������Context�� |
| key | string | 是 | ��ϵ�˵�Ψһ��ѯ��key�����½���ϵ��ʱϵͳ�Զ����ɵ�Ψһ��ʶ��һ����ϵ�˶�Ӧһ��key,����ͨ��[queryKey](contact.queryKey(context: Context, id: number, callback: AsyncCallback): void)��ȡ�� |
| holder | Holder | 是 | ������ϵ�˵�Ӧ����Ϣ�࣬����������Ϊ����Ĭ��ʹ��ϵͳ��ϵ��Ӧ�ò�ѯ�� |
| callback | AsyncCallback&lt;Contact&gt; | 是 | �ص��������ɹ����ز�ѯ����ϵ�˶���ʧ�ܷ��ؾ���Ĵ�������Ϣ�� |

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
contact.queryContact(context, 'xxx', {
  holderId: 1,
  bundleName: '',
  displayName: ''
}, (err: BusinessError, data) => {
  if (err) {
    console.error(`Failed to query Contact. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in querying Contact. data->${JSON.stringify(data)}`);
});

```


## queryContact

```TypeScript
function queryContact(key: string, attrs: ContactAttributes, callback: AsyncCallback<Contact>): void
```

����key��ָ������(attrs)��ѯ��ϵ�ˡ�ʹ��callback�첽�ص���

**起始版本：** 7

**废弃版本：** 10

**替代接口：** queryContact(context:

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | ��ϵ�˵�Ψһ��ѯ��key�����½���ϵ��ʱϵͳ�Զ����ɵ�Ψһ��ʶ��һ����ϵ�˶�Ӧһ��key,����ͨ��[queryKey](contact.queryKey(context: Context, id: number, callback: AsyncCallback): void)��ȡ�� |
| attrs | ContactAttributes | 是 | ��ϵ�˵������б������Ϊ�գ����ѯ��ϵ�˵����������ֶΣ������������绰������ȣ��� |
| callback | AsyncCallback&lt;Contact&gt; | 是 | �ص��������ɹ����ز�ѯ����ϵ�˶���ʧ�ܷ��ؾ���Ĵ�������Ϣ�� |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { contact } from '@kit.ContactsKit';

// 传入key='xxx'以及联系人的属性列表查询
contact.queryContact('xxx', {
  attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
}, (err: BusinessError, data) => {
  if (err) {
    console.error(`Failed to query Contact. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in querying Contact. data->${JSON.stringify(data)}`);
});

```


## queryContact

```TypeScript
function queryContact(context: Context, key: string, attrs: ContactAttributes, callback: AsyncCallback<Contact>): void
```

����key��attrs��ѯ��ϵ�ˡ�ʹ��callback�첽�ص���

**起始版本：** 10

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | Ӧ��������Context�� |
| key | string | 是 | ��ϵ�˵�Ψһ��ѯ��key�����½���ϵ��ʱϵͳ�Զ����ɵ�Ψһ��ʶ��һ����ϵ�˶�Ӧһ��key,����ͨ��[queryKey](contact.queryKey(context: Context, id: number, callback: AsyncCallback): void)��ȡ�� |
| attrs | ContactAttributes | 是 | ��ϵ�˵������б������Ϊ�գ����ѯ��ϵ�˵����������ֶΣ������������绰������ȣ��� |
| callback | AsyncCallback&lt;Contact&gt; | 是 | �ص��������ɹ����ز�ѯ����ϵ�˶���ʧ�ܷ��ؾ���Ĵ�������Ϣ�� |

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
contact.queryContact(context, 'xxx', {
  attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
}, (err: BusinessError, data) => {
  if (err) {
    console.error(`Failed to query Contact. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in querying Contact. data->${JSON.stringify(data)}`);
});

```


## queryContact

```TypeScript
function queryContact(key: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback<Contact>): void
```

����key��holder��attrs��ѯ��ϵ�ˡ�ʹ��callback�첽�ص���

**起始版本：** 7

**废弃版本：** 10

**替代接口：** queryContact(context:

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | ��ϵ�˵�Ψһ��ѯ��key�����½���ϵ��ʱϵͳ�Զ����ɵ�Ψһ��ʶ��һ����ϵ�˶�Ӧһ��key,����ͨ��[queryKey](contact.queryKey(context: Context, id: number, callback: AsyncCallback): void)��ȡ�� |
| holder | Holder | 是 | ������ϵ�˵�Ӧ����Ϣ�࣬Ϊ����Ĭ��ʹ��ϵͳ��ϵ��Ӧ�ò�ѯ�� |
| attrs | ContactAttributes | 是 | ��ϵ�˵������б������ò���Ϊ��ʱ�����ѯ��ϵ�˵����������ֶΣ������������绰������ȣ��� |
| callback | AsyncCallback&lt;Contact&gt; | 是 | �ص��������ɹ����ز�ѯ����ϵ�˶���ʧ�ܷ��ؾ���Ĵ�������Ϣ�� |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { contact } from '@kit.ContactsKit';

// 查询key,holder,attrs满足条件的联系人
contact.queryContact('xxx', {
  holderId: 1,
  bundleName: "",
  displayName: ""
}, {
  attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
}, (err: BusinessError, data) => {
  if (err) {
    console.error(`Failed to query Contact. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in querying Contact. data->${JSON.stringify(data)}`);
});

```


## queryContact

```TypeScript
function queryContact(context: Context, key: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback<Contact>): void
```

����key��holder��attrs��ѯ��ϵ�ˡ�ʹ��callback�첽�ص���

**起始版本：** 10

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | Ӧ��������Context�� |
| key | string | 是 | ��ϵ�˵�Ψһ��ѯ��key�����½���ϵ��ʱϵͳ�Զ����ɵ�Ψһ��ʶ��һ����ϵ�˶�Ӧһ��key,����ͨ��[queryKey](contact.queryKey(context: Context, id: number, callback: AsyncCallback): void)��ȡ�� |
| holder | Holder | 是 | ������ϵ�˵�Ӧ����Ϣ�࣬����������Ϊ����Ĭ��ʹ��ϵͳ��ϵ��Ӧ�ò�ѯ�� |
| attrs | ContactAttributes | 是 | ��ϵ�˵������б������Ϊ�գ����ѯ��ϵ�˵����������ֶΣ������������绰������ȣ��� |
| callback | AsyncCallback&lt;Contact&gt; | 是 | �ص��������ɹ����ز�ѯ����ϵ�˶���ʧ�ܷ��ؾ���Ĵ�������Ϣ�� |

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
  contact.queryContact(context, 'xxx', {
    holderId: 1,
    bundleName: '',
    displayName: ''
  }, {
    attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
  }, (err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to query Contact. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in querying Contact. data->${JSON.stringify(data)}`);
  });

```


## queryContact

```TypeScript
function queryContact(key: string, holder?: Holder, attrs?: ContactAttributes): Promise<Contact>
```

����key��holder��attrs��ѯ��ϵ�ˡ�ʹ��Promise�첽�ص���

**起始版本：** 7

**废弃版本：** 10

**替代接口：** queryContact(context:

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | ��ϵ�˵�Ψһ��ѯ��key�����½���ϵ��ʱ�Զ����ɵ�Ψһ��ʶ��һ����ϵ�˶�Ӧһ��key,����ͨ��[queryKey](contact.queryKey(context: Context, id: number, callback: AsyncCallback): void)��ȡ�� |
| holder | Holder | 否 | ������ϵ�˵�Ӧ����Ϣ�࣬�����ò�����Ĭ��ʹ��ϵͳ��ϵ��Ӧ�ò�ѯ�� |
| attrs | ContactAttributes | 否 | ��ϵ�˵������б�������Ĭ�ϲ�ѯ������ϵ�����ԡ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Contact&gt; | Promise���󡣷��ز�ѯ������ϵ�˶��� |

**示例：**

```TypeScript
import { contact } from '@kit.ContactsKit';

// 异步回调，查询联系人
let promise = contact.queryContact('xxx', {
  holderId: 1,
  bundleName: "",
  displayName: ""
}, {
  attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
});
promise.then((data) => {
  console.info(`Succeeded in querying Contact. data->${JSON.stringify(data)}`);
});

```


## queryContact

```TypeScript
function queryContact(context: Context, key: string, holder?: Holder, attrs?: ContactAttributes): Promise<Contact>
```

����key��holder��attrs��ѯ��ϵ�ˡ�ʹ��Promise�첽�ص���

**起始版本：** 10

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | Ӧ��������Context�� |
| key | string | 是 | ��ϵ�˵�Ψһ��ѯ��key�����½���ϵ��ʱϵͳ�Զ����ɵ�Ψһ��ʶ��һ����ϵ�˶�Ӧһ��key,����ͨ��[queryKey](contact.queryKey(context: Context, id: number, callback: AsyncCallback): void)��ȡ�� |
| holder | Holder | 否 | ������ϵ�˵�Ӧ����Ϣ�࣬�����ò�������Ĭ��ʹ��ϵͳ��ϵ��Ӧ�ò�ѯ�� |
| attrs | ContactAttributes | 否 | ��ϵ�˵������б��������ò�������Ĭ�ϲ�ѯ������ϵ�����ԡ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Contact&gt; | Promise���󡣷��ز�ѯ������ϵ�˶��� |

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
let promise = contact.queryContact(context, 'xxx', {
  holderId: 1,
  bundleName: '',
  displayName: ''
}, {
  attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
});
promise.then((data) => {
  console.info(`Succeeded in querying Contact. data->${JSON.stringify(data)}`);
});

```

