# selectContact

## 导入模块

```TypeScript
import { contact } from '@kit.ContactsKit';
```

## selectContact

```TypeScript
function selectContact(callback: AsyncCallback<Array<Contact>>): void
```

调用选择联系人接口，打开选择联系人UI界面。使用callback异步回调。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** selectContacts(callback:

<!--Device-contact-function selectContact(callback: AsyncCallback<Array<Contact>>): void--><!--Device-contact-function selectContact(callback: AsyncCallback<Array<Contact>>): void-End-->

**系统能力：** SystemCapability.Applications.Contacts

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<Array<Contact>> | 是 | 回调函数。成功返回选择的联系人对象数组；失败返回具体的错误码信息。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { contact } from '@kit.ContactsKit';

// 打开选择联系人UI界面
contact.selectContact((err: BusinessError, data) => {
  if (err) {
    console.error(`Failed to select Contact. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in selecting Contact. data->${JSON.stringify(data)}`);
});

```


## selectContact

```TypeScript
function selectContact(): Promise<Array<Contact>>
```

调用选择联系人接口，打开选择联系人UI界面。使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [selectContacts()](arkts-contacts-contact-selectcontacts-f.md#selectcontacts-2)

<!--Device-contact-function selectContact(): Promise<Array<Contact>>--><!--Device-contact-function selectContact(): Promise<Array<Contact>>-End-->

**系统能力：** SystemCapability.Applications.Contacts

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Array<Contact>> | Promise对象。返回选择的联系人数组对象。 |

**示例：**

```TypeScript
import { contact } from '@kit.ContactsKit';

// 打开选择联系人UI界面
let promise = contact.selectContact();
promise.then((data) => {
  console.info(`Succeeded in selecting Contact. data->${JSON.stringify(data)}`);
});

```

