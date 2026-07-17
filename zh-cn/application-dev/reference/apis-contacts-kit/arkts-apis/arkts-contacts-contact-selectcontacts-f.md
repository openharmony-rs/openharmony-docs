# selectContacts

## 导入模块

```TypeScript
import { contact } from '@kit.ContactsKit';
```

## selectContacts

```TypeScript
function selectContacts(callback: AsyncCallback<Array<Contact>>): void
```

调用选择联系人接口，打开选择联系人UI界面。使用callback异步回调。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-contact-function selectContacts(callback: AsyncCallback<Array<Contact>>): void--><!--Device-contact-function selectContacts(callback: AsyncCallback<Array<Contact>>): void-End-->

**系统能力：** SystemCapability.Applications.Contacts

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<Array<Contact>> | 是 | 回调函数。成功返回选择的联系人对象数组；失败返回具体的错误码信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: Mandatory parameters are left unspecified. |

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

调用选择联系人接口，打开选择联系人UI界面。使用Promise异步回调。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-contact-function selectContacts(): Promise<Array<Contact>>--><!--Device-contact-function selectContacts(): Promise<Array<Contact>>-End-->

**系统能力：** SystemCapability.Applications.Contacts

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Array<Contact>> | Promise对象。返回选择的联系人数组对象。 |

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

调用选择联系人接口，打开选择联系人UI界面（选择联系人时支持传入[筛选条件](arkts-contacts-contact-contactselectionoptions-i.md)）。使用callback异步回调。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-contact-function selectContacts(options: ContactSelectionOptions, callback: AsyncCallback<Array<Contact>>): void--><!--Device-contact-function selectContacts(options: ContactSelectionOptions, callback: AsyncCallback<Array<Contact>>): void-End-->

**系统能力：** SystemCapability.Applications.Contacts

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ContactSelectionOptions](arkts-contacts-contact-contactselectionoptions-i.md) | 是 | 选择联系人时的筛选条件，表示单选或多选。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<Array<Contact>> | 是 | 回调函数。成功返回选择的联系人对象数组；失败返回具体的错误码信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: Mandatory parameters are left unspecified. |

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

调用选择联系人接口，打开选择联系人UI界面（选择联系人时支持传入筛选条件）。使用Promise异步回调。

**起始版本：** 10

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-contact-function selectContacts(options: ContactSelectionOptions): Promise<Array<Contact>>--><!--Device-contact-function selectContacts(options: ContactSelectionOptions): Promise<Array<Contact>>-End-->

**系统能力：** SystemCapability.Applications.Contacts

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ContactSelectionOptions](arkts-contacts-contact-contactselectionoptions-i.md) | 是 | 选择联系人时的筛选条件，用于指定是单选还是多选。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Array<Contact>> | Promise对象。返回选择的联系人数组对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: Mandatory parameters are left unspecified. |

**示例：**

```TypeScript
import { contact } from '@kit.ContactsKit';

// 打开选择联系人UI界面，支持选择一个联系人
let promise = contact.selectContacts({isMultiSelect:false});
promise.then((data) => {
  console.info(`Succeeded in selecting Contacts. data->${JSON.stringify(data)}`);
});

```

