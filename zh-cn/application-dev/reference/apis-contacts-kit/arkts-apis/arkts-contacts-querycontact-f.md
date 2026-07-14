# queryContact

## queryContact

```TypeScript
function queryContact(key: string, callback: AsyncCallback<Contact>): void
```

根据联系人唯一标识符key查询联系人。使用callback异步回调。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** queryContact(context:

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 联系人的唯一查询键key，是新建联系人时系统自动生成的唯一标识，一个联系人对应一个key,可以通过[queryKey](contact.queryKey(context: Context, id: number, callback: AsyncCallback&lt;string&gt;): void)获取。 |
| callback | AsyncCallback&lt;Contact&gt; | 是 | 回调函数。成功返回查询的联系人对象；失败返回具体的错误码信息。 |

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

根据key查询联系人。使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | 应用上下文Context。 |
| key | string | 是 | 联系人的唯一查询键key，是新建联系人时系统自动生成的唯一标识，一个联系人对应一个key,可以通过[queryKey](contact.queryKey(context: Context, id: number, callback: AsyncCallback&lt;string&gt;): void)获取。 |
| callback | AsyncCallback&lt;Contact&gt; | 是 | 回调函数。成功返回查询的联系人对象；失败返回具体的错误码信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: Mandatory parameters are left unspecified. |

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

根据key和holder查询联系人。使用callback异步回调。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** queryContact(context:

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 联系人的唯一查询键key，是新建联系人时系统自动生成的唯一标识，一个联系人对应一个key,可以通过[queryKey](contact.queryKey(context: Context, id: number, callback: AsyncCallback&lt;string&gt;): void)获取。 |
| holder | Holder | 是 | 创建联系人的应用信息类，如果传入参数为空则默认使用系统联系人应用查询。 |
| callback | AsyncCallback&lt;Contact&gt; | 是 | 回调函数。成功返回查询的联系人对象；失败返回具体的错误码信息。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { contact } from '@kit.ContactsKit';

// 查询key='xxx'，holderId为1的联系人
contact.queryContact('xxx', {
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
function queryContact(context: Context, key: string, holder: Holder, callback: AsyncCallback<Contact>): void
```

根据key和holder查询联系人。使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | 应用上下文Context。 |
| key | string | 是 | 联系人的唯一查询键key，是新建联系人时系统自动生成的唯一标识，一个联系人对应一个key,可以通过[queryKey](contact.queryKey(context: Context, id: number, callback: AsyncCallback&lt;string&gt;): void)获取。 |
| holder | Holder | 是 | 创建联系人的应用信息类，如果传入参数为空则默认使用系统联系人应用查询。 |
| callback | AsyncCallback&lt;Contact&gt; | 是 | 回调函数。成功返回查询的联系人对象；失败返回具体的错误码信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: Mandatory parameters are left unspecified. |

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

根据key和指定属性(attrs)查询联系人。使用callback异步回调。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** queryContact(context:

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 联系人的唯一查询键key，是新建联系人时系统自动生成的唯一标识，一个联系人对应一个key,可以通过[queryKey](contact.queryKey(context: Context, id: number, callback: AsyncCallback&lt;string&gt;): void)获取。 |
| attrs | ContactAttributes | 是 | 联系人的属性列表，如果为空，则查询联系人的所有属性字段（包括姓名、电话、邮箱等）。 |
| callback | AsyncCallback&lt;Contact&gt; | 是 | 回调函数。成功返回查询的联系人对象；失败返回具体的错误码信息。 |

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

根据key和attrs查询联系人。使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | 应用上下文Context。 |
| key | string | 是 | 联系人的唯一查询键key，是新建联系人时系统自动生成的唯一标识，一个联系人对应一个key,可以通过[queryKey](contact.queryKey(context: Context, id: number, callback: AsyncCallback&lt;string&gt;): void)获取。 |
| attrs | ContactAttributes | 是 | 联系人的属性列表，如果为空，则查询联系人的所有属性字段（包括姓名、电话、邮箱等）。 |
| callback | AsyncCallback&lt;Contact&gt; | 是 | 回调函数。成功返回查询的联系人对象；失败返回具体的错误码信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: Mandatory parameters are left unspecified. |

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

根据key、holder和attrs查询联系人。使用callback异步回调。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** queryContact(context:

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 联系人的唯一查询键key，是新建联系人时系统自动生成的唯一标识，一个联系人对应一个key,可以通过[queryKey](contact.queryKey(context: Context, id: number, callback: AsyncCallback&lt;string&gt;): void)获取。 |
| holder | Holder | 是 | 创建联系人的应用信息类，为空则默认使用系统联系人应用查询。 |
| attrs | ContactAttributes | 是 | 联系人的属性列表，当该参数为空时，则查询联系人的所有属性字段（包括姓名、电话、邮箱等）。 |
| callback | AsyncCallback&lt;Contact&gt; | 是 | 回调函数。成功返回查询的联系人对象；失败返回具体的错误码信息。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { contact } from '@kit.ContactsKit';

// 查询key,holder,attrs满足条件的联系人
contact.queryContact('xxx', {
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
function queryContact(context: Context, key: string, holder: Holder, attrs: ContactAttributes, callback: AsyncCallback<Contact>): void
```

根据key、holder和attrs查询联系人。使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | 应用上下文Context。 |
| key | string | 是 | 联系人的唯一查询键key，是新建联系人时系统自动生成的唯一标识，一个联系人对应一个key,可以通过[queryKey](contact.queryKey(context: Context, id: number, callback: AsyncCallback&lt;string&gt;): void)获取。 |
| holder | Holder | 是 | 创建联系人的应用信息类，如果传入参数为空则默认使用系统联系人应用查询。 |
| attrs | ContactAttributes | 是 | 联系人的属性列表，如果为空，则查询联系人的所有属性字段（包括姓名、电话、邮箱等）。 |
| callback | AsyncCallback&lt;Contact&gt; | 是 | 回调函数。成功返回查询的联系人对象；失败返回具体的错误码信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: Mandatory parameters are left unspecified. |

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

根据key、holder和attrs查询联系人。使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** queryContact(context:

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 联系人的唯一查询键key，是新建联系人时自动生成的唯一标识，一个联系人对应一个key,可以通过[queryKey](contact.queryKey(context: Context, id: number, callback: AsyncCallback&lt;string&gt;): void)获取。 |
| holder | Holder | 否 | 创建联系人的应用信息类，不传该参数则默认使用系统联系人应用查询。 |
| attrs | ContactAttributes | 否 | 联系人的属性列表，不传默认查询所有联系人属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Contact&gt; | Promise对象。返回查询到的联系人对象。 |

**示例：**

```TypeScript
import { contact } from '@kit.ContactsKit';

// 异步回调，查询联系人
let promise = contact.queryContact('xxx', {
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


## queryContact

```TypeScript
function queryContact(context: Context, key: string, holder?: Holder, attrs?: ContactAttributes): Promise<Contact>
```

根据key、holder和attrs查询联系人。使用Promise异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | 应用上下文Context。 |
| key | string | 是 | 联系人的唯一查询键key，是新建联系人时系统自动生成的唯一标识，一个联系人对应一个key,可以通过[queryKey](contact.queryKey(context: Context, id: number, callback: AsyncCallback&lt;string&gt;): void)获取。 |
| holder | Holder | 否 | 创建联系人的应用信息类，不传该参数，则默认使用系统联系人应用查询。 |
| attrs | ContactAttributes | 否 | 联系人的属性列表，不传该参数，则默认查询所有联系人属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Contact&gt; | Promise对象。返回查询到的联系人对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: Mandatory parameters are left unspecified. |

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

