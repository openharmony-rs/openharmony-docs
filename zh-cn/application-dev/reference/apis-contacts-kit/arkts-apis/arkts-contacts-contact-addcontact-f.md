# addContact

## addContact

```TypeScript
function addContact(contact: Contact, callback: AsyncCallback<number>): void
```

������ϵ�ˡ�ʹ��callback�첽�ص���

**起始版本：** 7

**废弃版本：** 10

**替代接口：** addContact(context:

**需要权限：** ohos.permission.WRITE_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| contact | Contact | 是 | ��ϵ����Ϣ�� |
| callback | AsyncCallback&lt;number&gt; | 是 | �ص��������ɹ��������ӵ���ϵ��id��ʧ�ܷ��ؾ���Ĵ�������Ϣ�� |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';
import { contact } from '@kit.ContactsKit';

// 请在组件内获取context。
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
contact.addContact(context, {
  name: {
    fullName: 'xxx'
  },
  phoneNumbers: [{
    phoneNumber: '138xxxxxxxx'
  }]
}, (err: BusinessError, data) => {
  if (err) {
    console.error(`Failed to add Contact. Code:${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in adding Contact. data: ${JSON.stringify(data)}`);
});

```


## addContact

```TypeScript
function addContact(context: Context, contact: Contact, callback: AsyncCallback<number>): void
```

������ϵ�ˡ�ʹ��callback�첽�ص���

**起始版本：** 10

**需要权限：** ohos.permission.WRITE_CONTACTS

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | Ӧ��������Context�� |
| contact | Contact | 是 | ��ϵ����Ϣ�� |
| callback | AsyncCallback&lt;number&gt; | 是 | �ص��������ɹ��������ӵ���ϵ��id��ʧ�ܷ��ؾ���Ĵ�������Ϣ�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: Mandatory parameters are left unspecified. |

**示例：**

在本文档的示例中，通过this.context来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需要在界面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';
  import { contact } from '@kit.ContactsKit';

  // 请在组件内获取context。
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  contact.addContact(context, {
    name: {
      fullName: 'xxx'
    },
    phoneNumbers: [{
      phoneNumber: '138xxxxxxxx'
    }]
  }, (err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to add Contact. Code:${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in adding Contact. data: ${JSON.stringify(data)}`);
  });

```


## addContact

```TypeScript
function addContact(contact: Contact): Promise<number>
```

������ϵ�ˡ�ʹ��Promise�첽�ص���

**起始版本：** 7

**废弃版本：** 10

**替代接口：** addContact(context:

**需要权限：** ohos.permission.WRITE_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| contact | Contact | 是 | ��ϵ����Ϣ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise���󣬷������ӵ���ϵ��id�� |

**示例：**

```TypeScript
import { contact } from '@kit.ContactsKit';

// Promise 成功时返回添加成功后的数据。
let promise = contact.addContact({
  name: {
    fullName: 'xxx'
  },
  phoneNumbers: [{
    phoneNumber: '138xxxxxxxx'
  }]
});
// 成功回调：Promise resolve 时执行
promise.then((data) => {
  console.info(`Succeeded in adding Contact. data: ${JSON.stringify(data)}`);
});

```


## addContact

```TypeScript
function addContact(context: Context, contact: Contact): Promise<number>
```

������ϵ�ˡ�ʹ��Promise�첽�ص���

**起始版本：** 10

**需要权限：** ohos.permission.WRITE_CONTACTS

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | Ӧ��������Context�� |
| contact | Contact | 是 | ��ϵ����Ϣ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise���󣬷������ӵ���ϵ��id�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: Mandatory parameters are left unspecified. |

**示例：**

在本文档的示例中，通过this.context来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需要在界面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // 请在组件内获取context。
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let promise = contact.addContact(context, {
    name: {
      fullName: 'xxx'
    },
    phoneNumbers: [{
      phoneNumber: '138xxxxxxxx'
    }]
  });
  promise.then((data) => {
    console.info(`Succeeded in adding Contact. data: ${JSON.stringify(data)}`);
  });

```

