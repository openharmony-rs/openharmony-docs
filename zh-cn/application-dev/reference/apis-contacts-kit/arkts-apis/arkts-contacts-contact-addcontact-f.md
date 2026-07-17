# addContact

## 导入模块

```TypeScript
import { contact } from '@kit.ContactsKit';
```

## addContact

```TypeScript
function addContact(contact: Contact, callback: AsyncCallback<number>): void
```

添加联系人。使用callback异步回调。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** addContact(context:

**需要权限：** ohos.permission.WRITE_CONTACTS

<!--Device-contact-function addContact(contact: Contact, callback: AsyncCallback<number>): void--><!--Device-contact-function addContact(contact: Contact, callback: AsyncCallback<number>): void-End-->

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| contact | [Contact](arkts-contacts-contact-contact-c.md) | 是 | 联系人信息。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<number> | 是 | 回调函数。成功返回添加的联系人id；失败返回具体的错误码信息。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import { contact } from '@kit.ContactsKit';

// 请在组件内获取context。
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
contact.addContact(context, {
  name: {
    fullName: 'xxx'
  },
  phoneNumbers: [{
    phoneNumber: '138xxxxxxxx'
  }]
}, (err: BusinessError, data) => {
  if (err) {
    console.error(`Failed to add Contact. Code:${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in adding Contact. data: ${JSON.stringify(data)}`);
});

```


## addContact

```TypeScript
function addContact(context: Context, contact: Contact, callback: AsyncCallback<number>): void
```

添加联系人。使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.WRITE_CONTACTS

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-contact-function addContact(context: Context, contact: Contact, callback: AsyncCallback<number>): void--><!--Device-contact-function addContact(context: Context, contact: Contact, callback: AsyncCallback<number>): void-End-->

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 应用上下文Context。 |
| contact | [Contact](arkts-contacts-contact-contact-c.md) | 是 | 联系人信息。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<number> | 是 | 回调函数。成功返回添加的联系人id；失败返回具体的错误码信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: Mandatory parameters are left unspecified. |

**示例：**

在本文档的示例中，通过this.context来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需要在界面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';
  import { contact } from '@kit.ContactsKit';

  // 请在组件内获取context。
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  contact.addContact(context, {
    name: {
      fullName: 'xxx'
    },
    phoneNumbers: [{
      phoneNumber: '138xxxxxxxx'
    }]
  }, (err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to add Contact. Code:${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in adding Contact. data: ${JSON.stringify(data)}`);
  });

```


## addContact

```TypeScript
function addContact(contact: Contact): Promise<number>
```

添加联系人。使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** addContact(context:

**需要权限：** ohos.permission.WRITE_CONTACTS

<!--Device-contact-function addContact(contact: Contact): Promise<number>--><!--Device-contact-function addContact(contact: Contact): Promise<number>-End-->

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| contact | [Contact](arkts-contacts-contact-contact-c.md) | 是 | 联系人信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<number> | Promise对象，返回添加的联系人id。 |

**示例：**

```TypeScript
import { contact } from '@kit.ContactsKit';

// Promise 成功时返回添加成功后的数据。
let promise = contact.addContact({
  name: {
    fullName: 'xxx'
  },
  phoneNumbers: [{
    phoneNumber: '138xxxxxxxx'
  }]
});
// 成功回调：Promise resolve 时执行
promise.then((data) => {
  console.info(`Succeeded in adding Contact. data: ${JSON.stringify(data)}`);
});

```


## addContact

```TypeScript
function addContact(context: Context, contact: Contact): Promise<number>
```

添加联系人。使用Promise异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.WRITE_CONTACTS

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-contact-function addContact(context: Context, contact: Contact): Promise<number>--><!--Device-contact-function addContact(context: Context, contact: Contact): Promise<number>-End-->

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 应用上下文Context。 |
| contact | [Contact](arkts-contacts-contact-contact-c.md) | 是 | 联系人信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<number> | Promise对象，返回添加的联系人id。 |

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
  let promise = contact.addContact(context, {
    name: {
      fullName: 'xxx'
    },
    phoneNumbers: [{
      phoneNumber: '138xxxxxxxx'
    }]
  });
  promise.then((data) => {
    console.info(`Succeeded in adding Contact. data: ${JSON.stringify(data)}`);
  });

```

