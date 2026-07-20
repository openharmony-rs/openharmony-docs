# saveToExistingContactViaUI

## 导入模块

```TypeScript
import { contact } from '@kit.ContactsKit';
```

<a id="savetoexistingcontactviaui"></a>
## saveToExistingContactViaUI

```TypeScript
function saveToExistingContactViaUI(context: Context, contact: Contact): Promise<number>
```

调用保存至已有联系人接口，选择联系人UI界面并完成编辑。使用Promise异步回调。

**起始版本：** 15

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-contact-function saveToExistingContactViaUI(context: Context, contact: Contact): Promise<number>--><!--Device-contact-function saveToExistingContactViaUI(context: Context, contact: Contact): Promise<number>-End-->

**系统能力：** SystemCapability.Applications.Contacts

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 应用上下文Context。 |
| contact | [Contact](arkts-contacts-contact-contact-c.md) | 是 | 联系人信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象。返回添加的联系人id。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: Mandatory parameters are left unspecified. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | The specified SystemCapability name was not found. |
| [16700001](../errorcode-contacts.md#16700001-系统内部错误) | General error. |
| [16700101](../errorcode-contacts.md#16700101-查询数据库失败) | Failed to get value from contacts data. |
| [16700102](../errorcode-contacts.md#16700102-增删改数据库失败) | Failed to set value to contacts data. |
| [16700103](../errorcode-contacts.md#16700103-用户取消) | User cancel. |

**示例：**

在本文档的示例中，通过this.context来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需要在界面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
import { common } from '@kit.AbilityKit';
import { contact } from '@kit.ContactsKit';

// 请在组件内获取context。
let contactInfo: contact.Contact = {
  id: 1,
  name: {
    fullName: 'xxx'
  },
  phoneNumbers: [{
    phoneNumber: '138xxxxxx'
  }]
}
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let promise = contact.saveToExistingContactViaUI(context, contactInfo);
promise.then((data) => {
    console.info(`Succeeded in save to existing Contact via UI.data->${JSON.stringify(data)}`);
  });

```

