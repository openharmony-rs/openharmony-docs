# updateContact

## 导入模块

```TypeScript
import { contact } from '@kit.ContactsKit';
```

## updateContact

```TypeScript
function updateContact(contact: Contact, callback: AsyncCallback<void>): void
```

更新联系人。使用callback异步回调。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** updateContact(context:

**需要权限：** ohos.permission.WRITE_CONTACTS

<!--Device-contact-function updateContact(contact: Contact, callback: AsyncCallback<void>): void--><!--Device-contact-function updateContact(contact: Contact, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| contact | [Contact](arkts-contacts-contact-contact-c.md) | 是 | 联系人信息。id必填，可通过[selectContacts](arkts-contacts-contact-selectcontacts-f.md#selectcontacts-2)接口获取。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。成功返回更新的联系人id；失败返回具体的错误码信息。 |

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

更新联系人。使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.WRITE_CONTACTS

<!--Device-contact-function updateContact(context: Context, contact: Contact, callback: AsyncCallback<void>): void--><!--Device-contact-function updateContact(context: Context, contact: Contact, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 应用上下文Context。 |
| contact | [Contact](arkts-contacts-contact-contact-c.md) | 是 | 联系人信息。id必填，可通过[selectContacts](arkts-contacts-contact-selectcontacts-f.md#selectcontacts-2)接口获取。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。成功返回更新的联系人id；失败返回具体的错误码信息。 |

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

更新联系人，支持传入联系人的属性列表。使用callback异步回调。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** updateContact(context:

**需要权限：** ohos.permission.WRITE_CONTACTS

<!--Device-contact-function updateContact(contact: Contact, attrs: ContactAttributes, callback: AsyncCallback<void>): void--><!--Device-contact-function updateContact(contact: Contact, attrs: ContactAttributes, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| contact | [Contact](arkts-contacts-contact-contact-c.md) | 是 | 联系人信息。id必填，可通过[selectContacts](arkts-contacts-contact-selectcontacts-f.md#selectcontacts-2)接口获取。 |
| attrs | [ContactAttributes](arkts-contacts-contact-contactattributes-c.md) | 是 | 联系人的属性列表，如果为空，则查询联系人的所有属性字段（包括姓名、电话、邮箱等）。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。成功返回更新的联系人id；失败返回具体的错误码信息。 |

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

更新联系人（支持传入联系人的属性列表）。使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.WRITE_CONTACTS

<!--Device-contact-function updateContact(context: Context, contact: Contact, attrs: ContactAttributes, callback: AsyncCallback<void>): void--><!--Device-contact-function updateContact(context: Context, contact: Contact, attrs: ContactAttributes, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 应用上下文Context。 |
| contact | [Contact](arkts-contacts-contact-contact-c.md) | 是 | 联系人信息。id必填，可通过[selectContacts](arkts-contacts-contact-selectcontacts-f.md#selectcontacts-2)接口获取。 |
| attrs | [ContactAttributes](arkts-contacts-contact-contactattributes-c.md) | 是 | 联系人的属性列表，如果为空，则查询联系人的所有属性字段（包括姓名、电话、邮箱等）。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。成功返回更新的联系人id；失败返回具体的错误码信息。 |

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

更新联系人，支持传入联系人的属性列表。使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** updateContact(context:

**需要权限：** ohos.permission.WRITE_CONTACTS

<!--Device-contact-function updateContact(contact: Contact, attrs?: ContactAttributes): Promise<void>--><!--Device-contact-function updateContact(contact: Contact, attrs?: ContactAttributes): Promise<void>-End-->

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| contact | [Contact](arkts-contacts-contact-contact-c.md) | 是 | 联系人信息。id必填，可通过[selectContacts](arkts-contacts-contact-selectcontacts-f.md#selectcontacts-2)接口获取。 |
| attrs | [ContactAttributes](arkts-contacts-contact-contactattributes-c.md) | 否 | 联系人的属性列表，如果为空，则查询联系人的所有属性字段（包括姓名、电话、邮箱等）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象。无返回结果的Promise对象。 |

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

更新联系人（支持传入联系人的属性列表）。使用Promise异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.WRITE_CONTACTS

<!--Device-contact-function updateContact(context: Context, contact: Contact, attrs?: ContactAttributes): Promise<void>--><!--Device-contact-function updateContact(context: Context, contact: Contact, attrs?: ContactAttributes): Promise<void>-End-->

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 应用上下文Context。 |
| contact | [Contact](arkts-contacts-contact-contact-c.md) | 是 | 联系人信息。id必填，可通过[selectContacts](arkts-contacts-contact-selectcontacts-f.md#selectcontacts-2)接口获取。 |
| attrs | [ContactAttributes](arkts-contacts-contact-contactattributes-c.md) | 否 | 联系人的属性列表，如果为空，则查询联系人的所有属性字段（包括姓名、电话、邮箱等）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象。无返回结果的Promise对象。 |

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

