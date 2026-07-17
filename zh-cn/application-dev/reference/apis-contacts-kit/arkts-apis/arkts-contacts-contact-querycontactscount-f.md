# queryContactsCount

## 导入模块

```TypeScript
import { contact } from '@kit.ContactsKit';
```

## queryContactsCount

```TypeScript
function queryContactsCount(context: Context): Promise<number>
```

查询所有联系人的数量。使用Promise异步回调。

**起始版本：** 22

**需要权限：** ohos.permission.READ_CONTACTS

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-contact-function queryContactsCount(context: Context): Promise<int>--><!--Device-contact-function queryContactsCount(context: Context): Promise<int>-End-->

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 应用上下文Context。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<number> | Promise对象。返回查询到的联系人数量。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [16700001](../errorcode-contacts.md#16700001-系统内部错误) | General error. |

**示例：**

在本文档的示例中，通过this.context来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需要在界面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
import { common } from '@kit.AbilityKit';
import { contact } from '@kit.ContactsKit';

// 请在组件内获取context。
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let promise = contact.queryContactsCount(context);
promise.then((data) => {
  console.info(`Succeeded in querying ContactsCount. data->${JSON.stringify(data)}`);
});

```

