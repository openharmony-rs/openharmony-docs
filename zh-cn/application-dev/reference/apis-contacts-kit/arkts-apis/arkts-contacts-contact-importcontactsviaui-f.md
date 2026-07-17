# importContactsViaUI

## 导入模块

```TypeScript
import { contact } from '@kit.ContactsKit';
```

## importContactsViaUI

```TypeScript
function importContactsViaUI(context: Context, contacts: Array<Contact>): Promise<Array<number>>
```

通过UI交互批量导入多个联系人。

每次最多可导入100个联系人。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-contact-function importContactsViaUI(context: Context, contacts: Array<Contact>): Promise<Array<int>>--><!--Device-contact-function importContactsViaUI(context: Context, contacts: Array<Contact>): Promise<Array<int>>-End-->

**系统能力：** SystemCapability.Applications.Contacts

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 应用上下文Context。 |
| contacts | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<Contact> | 是 | 表示待导入数据库的联系人信息数组。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Array<number>> | 返回联系人创建结果的数组。返回的联系人id有效（可通过[getId](Contact#getId())获取）表示创建成功。返回值为-1[INVALID_CONTACT_ID](arkts-contacts-contact-contact-c.md#invalid_contact_id) 表示创建失败。-2表示用户未选择该联系人。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | The specified SystemCapability name was not found. |
| [16700001](../errorcode-contacts.md#16700001-系统内部错误) | General error. |
| [16700002](../errorcode-contacts.md#16700002-参数检查失败) | Invalid parameter value. |
| [16700004](../errorcode-contacts.md#16700004-联系人数量超过限制) | The number of contacts exceeds the limit. |
| [16700103](../errorcode-contacts.md#16700103-用户取消) | User cancel. |

**示例：**

在本文档的示例中，通过this.context来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需要在界面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
import { contact } from '@kit.ContactsKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context
const context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let contactList: contact.Contact[] = [];
let contactInfo: contact.Contact = {
  name: {
    fullName: 'xxx'
  },
  phoneNumbers: [{
    phoneNumber: '138xxxxxx'
  }]
}
contactList.push(contactInfo);
let promise = contact.importContactsViaUI(context, contactList);
promise.then((data) => {
  console.info(`Succeeded in importing Contact via UI: data -> ${JSON.stringify(data)}`);
});

```

