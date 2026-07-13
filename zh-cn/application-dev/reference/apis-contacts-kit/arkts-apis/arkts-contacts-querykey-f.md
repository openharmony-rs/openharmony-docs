# queryKey

## queryKey

```TypeScript
function queryKey(id: number, callback: AsyncCallback<string>): void
```

根据联系人的id查询联系人的唯一查询键key。使用callback异步回调。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** queryKey(context:

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | number | 是 | 联系人对象的id属性。 |
| callback | AsyncCallback&lt;string&gt; | 是 | 回调函数。成功返回查询到的联系人对应的key；失败返回具体的错误码信息。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { contact } from '@kit.ContactsKit';

contact.queryKey(1, (err: BusinessError, data) => {
  if (err) {
    console.error(`Failed to query Key. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in querying Key. data->${JSON.stringify(data)}`);
});

```


## queryKey

```TypeScript
function queryKey(context: Context, id: number, callback: AsyncCallback<string>): void
```

根据联系人的id查询联系人的唯一查询键key。使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | 应用上下文Context。 |
| id | number | 是 | 联系人对象的id属性，是联系人对象在数据库中的唯一标识符。 |
| callback | AsyncCallback&lt;string&gt; | 是 | 回调函数。成功返回查询到的联系人对应的key；失败返回具体的错误码信息。 |

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
contact.queryKey(context, 1, (err: BusinessError, data) => {
  if (err) {
    console.error(`Failed to query Key. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in querying Key. data->${JSON.stringify(data)}`);
});

```


## queryKey

```TypeScript
function queryKey(id: number, holder: Holder, callback: AsyncCallback<string>): void
```

根据联系人的id和holder查询联系人的唯一查询键key。使用callback异步回调。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** queryKey(context:

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | number | 是 | 联系人对象的id属性。 |
| holder | Holder | 是 | 创建联系人的应用信息类，如果传入参数为空则默认使用系统联系人应用查询。 |
| callback | AsyncCallback&lt;string&gt; | 是 | 回调函数。成功返回查询到的联系人对应的key；失败返回具体的错误码信息。 |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { contact } from '@kit.ContactsKit';

contact.queryKey(1, {
  holderId: 1,
  bundleName: '',
  displayName: ''
}, (err: BusinessError, data) => {
  if (err) {
    console.error(`Failed to query Key. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in querying Key. data->${JSON.stringify(data)}`);
});

```


## queryKey

```TypeScript
function queryKey(context: Context, id: number, holder: Holder, callback: AsyncCallback<string>): void
```

根据联系人的id和holder查询联系人的唯一查询键key。使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | 应用上下文Context。 |
| id | number | 是 | 联系人对象的id属性。 |
| holder | Holder | 是 | 创建联系人的应用信息类，如果传入参数为空则默认使用系统联系人应用查询。 |
| callback | AsyncCallback&lt;string&gt; | 是 | 回调函数。成功返回查询到的联系人对应的key；失败返回具体的错误码信息。 |

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
contact.queryKey(context, 1, {
  holderId: 1,
  bundleName: '',
  displayName: ''
}, (err: BusinessError, data) => {
  if (err) {
    console.error(`Failed to query Key. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in querying Key. data->${JSON.stringify(data)}`);
});

```


## queryKey

```TypeScript
function queryKey(id: number, holder?: Holder): Promise<string>
```

根据联系人的id和holder查询联系人的唯一查询键key。使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 10

**替代接口：** queryKey(context:

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | number | 是 | 联系人对象的id属性。 |
| holder | Holder | 否 | 创建联系人的应用信息类，不传该参数，则默认使用系统联系人应用查询。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象。返回查询到的联系人对应的key。 |

**示例：**

```TypeScript
import { contact } from '@kit.ContactsKit';

let promise = contact.queryKey(1, {
  holderId: 1,
  bundleName: '',
  displayName: ''
});
promise.then((data) => {
  console.info(`Succeeded in querying Key. data->${JSON.stringify(data)}`);
});

```


## queryKey

```TypeScript
function queryKey(context: Context, id: number, holder?: Holder): Promise<string>
```

根据联系人的id和holder查询联系人的唯一查询键key。使用Promise异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | 应用上下文Context。 |
| id | number | 是 | 联系人对象的id属性。 |
| holder | Holder | 否 | 创建联系人的应用信息类，不传该参数，则默认使用系统联系人应用查询。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise对象。返回查询到的联系人对应的key。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes:1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |

**示例：**

在本文档的示例中，通过this.context来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需要在界面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
import { common } from '@kit.AbilityKit';
import { contact } from '@kit.ContactsKit';

// 请在组件内获取context。
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let promise = contact.queryKey(context, 1, {
  holderId: 1,
  bundleName: '',
  displayName: ''
});
promise.then((data) => {
  console.info(`Succeeded in querying Key. data->${JSON.stringify(data)}`);
});

```

