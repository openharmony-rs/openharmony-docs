# queryKey

## queryKey

```TypeScript
function queryKey(id: number, callback: AsyncCallback<string>): void
```

������ϵ�˵�id��ѯ��ϵ�˵�Ψһ��ѯ��key��ʹ��callback�첽�ص���

**起始版本：** 7

**废弃版本：** 10

**替代接口：** queryKey(context:

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | number | 是 | ��ϵ�˶����id���ԡ� |
| callback | AsyncCallback&lt;string&gt; | 是 | �ص��������ɹ����ز�ѯ������ϵ�˶�Ӧ��key��ʧ�ܷ��ؾ���Ĵ�������Ϣ�� |

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

������ϵ�˵�id��ѯ��ϵ�˵�Ψһ��ѯ��key��ʹ��callback�첽�ص���

**起始版本：** 10

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | Ӧ��������Context�� |
| id | number | 是 | ��ϵ�˶����id���ԣ�����ϵ�˶��������ݿ��е�Ψһ��ʶ���� |
| callback | AsyncCallback&lt;string&gt; | 是 | �ص��������ɹ����ز�ѯ������ϵ�˶�Ӧ��key��ʧ�ܷ��ؾ���Ĵ�������Ϣ�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/>1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |

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

������ϵ�˵�id��holder��ѯ��ϵ�˵�Ψһ��ѯ��key��ʹ��callback�첽�ص���

**起始版本：** 7

**废弃版本：** 10

**替代接口：** queryKey(context:

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | number | 是 | ��ϵ�˶����id���ԡ� |
| holder | Holder | 是 | ������ϵ�˵�Ӧ����Ϣ�࣬����������Ϊ����Ĭ��ʹ��ϵͳ��ϵ��Ӧ�ò�ѯ�� |
| callback | AsyncCallback&lt;string&gt; | 是 | �ص��������ɹ����ز�ѯ������ϵ�˶�Ӧ��key��ʧ�ܷ��ؾ���Ĵ�������Ϣ�� |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { contact } from '@kit.ContactsKit';

contact.queryKey(1, {
  holderId: 1,
  bundleName: "",
  displayName: ""
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

������ϵ�˵�id��holder��ѯ��ϵ�˵�Ψһ��ѯ��key��ʹ��callback�첽�ص���

**起始版本：** 10

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | Ӧ��������Context�� |
| id | number | 是 | ��ϵ�˶����id���ԡ� |
| holder | Holder | 是 | ������ϵ�˵�Ӧ����Ϣ�࣬����������Ϊ����Ĭ��ʹ��ϵͳ��ϵ��Ӧ�ò�ѯ�� |
| callback | AsyncCallback&lt;string&gt; | 是 | �ص��������ɹ����ز�ѯ������ϵ�˶�Ӧ��key��ʧ�ܷ��ؾ���Ĵ�������Ϣ�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/>1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |

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
  bundleName: "",
  displayName: ""
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

������ϵ�˵�id��holder��ѯ��ϵ�˵�Ψһ��ѯ��key��ʹ��Promise�첽�ص���

**起始版本：** 7

**废弃版本：** 10

**替代接口：** queryKey(context:

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | number | 是 | ��ϵ�˶����id���ԡ� |
| holder | Holder | 否 | ������ϵ�˵�Ӧ����Ϣ�࣬�����ò�������Ĭ��ʹ��ϵͳ��ϵ��Ӧ�ò�ѯ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise���󡣷��ز�ѯ������ϵ�˶�Ӧ��key�� |

**示例：**

```TypeScript
import { contact } from '@kit.ContactsKit';

let promise = contact.queryKey(1, {
  holderId: 1,
  bundleName: "",
  displayName: ""
});
promise.then((data) => {
  console.info(`Succeeded in querying Key. data->${JSON.stringify(data)}`);
});

```


## queryKey

```TypeScript
function queryKey(context: Context, id: number, holder?: Holder): Promise<string>
```

������ϵ�˵�id��holder��ѯ��ϵ�˵�Ψһ��ѯ��key��ʹ��Promise�첽�ص���

**起始版本：** 10

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | Ӧ��������Context�� |
| id | number | 是 | ��ϵ�˶����id���ԡ� |
| holder | Holder | 否 | ������ϵ�˵�Ӧ����Ϣ�࣬�����ò�������Ĭ��ʹ��ϵͳ��ϵ��Ӧ�ò�ѯ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string&gt; | Promise���󡣷��ز�ѯ������ϵ�˶�Ӧ��key�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/>1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |

**示例：**

在本文档的示例中，通过this.context来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需要在界面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
import { common } from '@kit.AbilityKit';
import { contact } from '@kit.ContactsKit';

// 请在组件内获取context。
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let promise = contact.queryKey(context, 1, {
  holderId: 1,
  bundleName: "",
  displayName: ""
});
promise.then((data) => {
  console.info(`Succeeded in querying Key. data->${JSON.stringify(data)}`);
});

```

