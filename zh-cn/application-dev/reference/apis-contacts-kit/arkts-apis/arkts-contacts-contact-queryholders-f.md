# queryHolders

## 导入模块

```TypeScript
import { contact } from '@kit.ContactsKit';
```

## queryHolders

```TypeScript
function queryHolders(callback: AsyncCallback<Array<Holder>>): void
```

查询所有创建联系人的应用信息类。使用callback异步回调。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [queryHolders(context:](arkts-contacts-contact-queryholders-f.md#queryholders)

**需要权限：** ohos.permission.READ_CONTACTS

<!--Device-contact-function queryHolders(callback: AsyncCallback<Array<Holder>>): void--><!--Device-contact-function queryHolders(callback: AsyncCallback<Array<Holder>>): void-End-->

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;Holder&gt;&gt; | 是 | 回调函数。成功返回查询到的创建联系人应用信息的对象数组；失败返回具体的错误码信息。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { contact } from '@kit.ContactsKit';

contact.queryHolders((err: BusinessError, data) => {
  if (err) {
    console.error(`Failed to query Holders. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in querying Holders. data->${JSON.stringify(data)}`);
});

```


## queryHolders

```TypeScript
function queryHolders(context: Context, callback: AsyncCallback<Array<Holder>>): void
```

查询所有创建联系人的应用信息类。使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.READ_CONTACTS

<!--Device-contact-function queryHolders(context: Context, callback: AsyncCallback<Array<Holder>>): void--><!--Device-contact-function queryHolders(context: Context, callback: AsyncCallback<Array<Holder>>): void-End-->

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 应用上下文Context。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;Holder&gt;&gt; | 是 | 回调函数。成功返回查询到的创建联系人应用信息的对象数组；失败返回具体的错误码信息。 |

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
contact.queryHolders(context, (err: BusinessError, data) => {
  if (err) {
    console.error(`Failed to query Holders. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in querying Holders. data->${JSON.stringify(data)}`);
});

```


## queryHolders

```TypeScript
function queryHolders(): Promise<Array<Holder>>
```

查询所有创建联系人的应用信息类。使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** [queryHolders(context:](arkts-contacts-contact-queryholders-f.md#queryholders)

**需要权限：** ohos.permission.READ_CONTACTS

<!--Device-contact-function queryHolders(): Promise<Array<Holder>>--><!--Device-contact-function queryHolders(): Promise<Array<Holder>>-End-->

**系统能力：** SystemCapability.Applications.ContactsData

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;Holder&gt;&gt; | Promise对象。返回查询到的创建联系人应用信息的对象数组。 |

**示例：**

```TypeScript
import { contact } from '@kit.ContactsKit';

let promise = contact.queryHolders();
promise.then((data) => {
  console.info(`Succeeded in querying Holders. data->${JSON.stringify(data)}`);
});

```


## queryHolders

```TypeScript
function queryHolders(context: Context): Promise<Array<Holder>>
```

查询所有创建联系人的应用信息类。使用Promise异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.READ_CONTACTS

<!--Device-contact-function queryHolders(context: Context): Promise<Array<Holder>>--><!--Device-contact-function queryHolders(context: Context): Promise<Array<Holder>>-End-->

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | [Context](../../apis-arkui/arkts-components/arkts-arkui-context-t.md) | 是 | 应用上下文Context。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;Holder&gt;&gt; | Promise对象。返回查询到的创建联系人应用信息的对象数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: Mandatory parameters are left unspecified. |

**示例：**

在本文档的示例中，通过this.context来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需要在界面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
import { common } from '@kit.AbilityKit';
import { contact } from '@kit.ContactsKit';

// 请在组件内获取context。
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let promise = contact.queryHolders(context);
promise.then((data) => {
  console.info(`Succeeded in querying Holders. data->${JSON.stringify(data)}`);
});

```

