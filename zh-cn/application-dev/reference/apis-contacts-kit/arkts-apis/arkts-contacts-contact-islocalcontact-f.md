# isLocalContact

## isLocalContact

```TypeScript
function isLocalContact(id: number, callback: AsyncCallback<boolean>): void
```

�жϵ�ǰ��ϵ��id�Ƿ��ڵ绰���С�ʹ��callback�첽�ص���

**起始版本：** 7

**废弃版本：** 10

**替代接口：** isLocalContact(context:

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | number | 是 | ��ϵ�˶����id���ԣ�һ����ϵ�˶�Ӧһ��id�� |
| callback | AsyncCallback&lt;boolean&gt; | 是 | �ص��������ɹ����ز���ֵ��true������ϵ��id�ڱ��ص绰���У�false�������ϵ��id���ڱ��ص绰���У�ʧ�ܷ��ؾ���Ĵ�������Ϣ�� |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { contact } from '@kit.ContactsKit';

// 判断id为1的联系人是否在本地电话簿中
contact.isLocalContact(1, (err: BusinessError, data) => {
  if (err) {
    console.error(`Failed to isLocalContact. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in isLocalContact. data->${JSON.stringify(data)}`);
});

```


## isLocalContact

```TypeScript
function isLocalContact(context: Context, id: number, callback: AsyncCallback<boolean>): void
```

�жϵ�ǰ��ϵ��id�Ƿ��ڵ绰���С�ʹ��callback�첽�ص���

**起始版本：** 10

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | Ӧ��������Context�� |
| id | number | 是 | ��ϵ�˶����id���ԣ�һ����ϵ�˶�Ӧһ��id�� |
| callback | AsyncCallback&lt;boolean&gt; | 是 | �ص��������ɹ����ز���ֵ��true������ϵ��id�ڱ��ص绰���У�false�������ϵ��id���ڱ��ص绰���У�ʧ�ܷ��ؾ���Ĵ�������Ϣ�� |

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
contact.isLocalContact(context, 1, (err: BusinessError, data) => {
  if (err) {
    console.error(`Failed to isLocalContact. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in isLocalContact. data->${JSON.stringify(data)}`);
});

```


## isLocalContact

```TypeScript
function isLocalContact(id: number): Promise<boolean>
```

�жϵ�ǰ��ϵ��id�Ƿ��ڵ绰���С�ʹ��Promise�첽�ص���

**起始版本：** 7

**废弃版本：** 10

**替代接口：** isLocalContact(context:

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | number | 是 | ��ϵ�˶����id���ԣ�һ����ϵ�˶�Ӧһ��id�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise���󡣷���true��ʾ��ϵ��id�ڱ��ص绰���У�����false��ʾ��ϵ��id���ڱ��ص绰���С� |

**示例：**

```TypeScript
import { contact } from '@kit.ContactsKit';

// 判断id为1的联系人是否在本地电话簿中
let promise = contact.isLocalContact(1);
promise.then((data) => {
  console.info(`Succeeded in isLocalContact. data->${JSON.stringify(data)}`);
});

```


## isLocalContact

```TypeScript
function isLocalContact(context: Context, id: number): Promise<boolean>
```

�жϵ�ǰ��ϵ��id�Ƿ��ڵ绰���С�ʹ��Promise�첽�ص���

**起始版本：** 10

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | Ӧ��������Context�� |
| id | number | 是 | ��ϵ�˶����id���ԣ�һ����ϵ�˶�Ӧһ��id�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise���󡣷���true��ʾ��ϵ��id�ڱ��ص绰���У�����false��ʾ��ϵ��id���ڱ��ص绰���С� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes:<br/>1.Mandatory parameters are left unspecified. 2.Parameter verification failed. |

**示例：**

在本文档的示例中，通过this.context来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需要在界面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // 请在组件内获取context。
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let promise = contact.isLocalContact(context, 1);
  promise.then((data) => {
    console.info(`Succeeded in isLocalContact. data->${JSON.stringify(data)}`);
  });

```

