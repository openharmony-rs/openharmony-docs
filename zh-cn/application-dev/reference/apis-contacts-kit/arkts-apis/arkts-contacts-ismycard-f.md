# isMyCard

## isMyCard

```TypeScript
function isMyCard(id: number, callback: AsyncCallback<boolean>): void
```

判断是否为“我的名片”。使用callback异步回调。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** isMyCard(context:

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | number | 是 | 名片对象的id属性。 |
| callback | AsyncCallback&lt;boolean&gt; | 是 | 回调函数。成功返回是否为“我的名片”的布尔值。true代表的是“我的名片”，false则代表不是；失败返回具体的错误码信息。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { contact } from '@kit.ContactsKit';

// 判断id为1的名片是否为“我的名片”
contact.isMyCard(1, (err: BusinessError, data) => {
  if (err) {
    console.error(`Failed to isMyCard. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in isMyCard. data->${JSON.stringify(data)}`);
});

```


## isMyCard

```TypeScript
function isMyCard(context: Context, id: number, callback: AsyncCallback<boolean>): void
```

判断是否为“我的名片”。使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | 应用上下文Context。 |
| id | number | 是 | 名片对象的id属性。 |
| callback | AsyncCallback&lt;boolean&gt; | 是 | 回调函数。成功返回是否为“我的名片”的布尔值。true代表的是“我的名片”，false代表不是；失败时则返回错误码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |

**示例：**

在本文档的示例中，通过this.context来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需要在界面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // 请在组件内获取context。
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  contact.isMyCard(context, 1, (err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to isMyCard. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in isMyCard. data->${JSON.stringify(data)}`);
  });

```


## isMyCard

```TypeScript
function isMyCard(id: number): Promise<boolean>
```

判断是否为“我的名片”。使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** isMyCard(context:

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | number | 是 | 名片对象的id属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示是“我的名片”，返回false代表不是。 |

**示例：**

```TypeScript
import { contact } from '@kit.ContactsKit';

// 判断id为1的名片是否为“我的名片”
let promise = contact.isMyCard(1);
promise.then((data) => {
  console.info(`Succeeded in isMyCard. data->${JSON.stringify(data)}`);
});

```


## isMyCard

```TypeScript
function isMyCard(context: Context, id: number): Promise<boolean>
```

判断是否为“我的名片”。使用Promise异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | 应用上下文Context。 |
| id | number | 是 | 名片对象的id属性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。返回true表示是“我的名片”，返回false代表不是。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |

**示例：**

在本文档的示例中，通过this.context来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需要在界面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // 请在组件内获取context。
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let promise = contact.isMyCard(context, 1);
  promise.then((data) => {
    console.info(`Succeeded in isMyCard. data->${JSON.stringify(data)}`);
  });

```

