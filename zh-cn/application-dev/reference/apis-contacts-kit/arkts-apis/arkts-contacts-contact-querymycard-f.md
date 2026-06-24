# queryMyCard

## queryMyCard

```TypeScript
function queryMyCard(callback: AsyncCallback<Contact>): void
```

��ѯ���ҵ���Ƭ����ʹ��callback�첽�ص���

**起始版本：** 7

**废弃版本：** 10

**替代接口：** queryMyCard(context:

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;Contact&gt; | 是 | �ص��������ɹ����ء��ҵ���Ƭ����Ϣ��ʧ�ܷ��ؾ���Ĵ�������Ϣ�� |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { contact } from '@kit.ContactsKit';

// 回调函数，查询“我的名片”
contact.queryMyCard((err: BusinessError, data) => {
  if (err) {
    console.error(`Failed to query My Card. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in querying My Card. data->${JSON.stringify(data)}`);
});

```


## queryMyCard

```TypeScript
function queryMyCard(context: Context, callback: AsyncCallback<Contact>): void
```

��ѯ���ҵ���Ƭ����ʹ��callback�첽�ص���

**起始版本：** 10

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | Ӧ��������Context�� |
| callback | AsyncCallback&lt;Contact&gt; | 是 | �ص��������ɹ����ء��ҵ���Ƭ����Ϣ��ʧ�ܷ��ؾ���Ĵ�������Ϣ�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: Mandatory parameters are left unspecified. |

**示例：**

在本文档的示例中，通过this.context来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需要在界面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // 请在组件内获取context。
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  contact.queryMyCard(context, (err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to query My Card. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in querying My Card. data->${JSON.stringify(data)}`);
  });

```


## queryMyCard

```TypeScript
function queryMyCard(attrs: ContactAttributes, callback: AsyncCallback<Contact>): void
```

��ѯ���ҵ���Ƭ����֧�ִ�����ϵ�˵������б�����ʹ��callback�첽�ص���

**起始版本：** 7

**废弃版本：** 10

**替代接口：** queryMyCard(context:

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| attrs | ContactAttributes | 是 | ��ϵ�˵������б������Ϊ�գ����ѯ��ϵ�˵����������ֶΣ������������绰������ȣ��� |
| callback | AsyncCallback&lt;Contact&gt; | 是 | �ص��������ɹ����ء��ҵ���Ƭ����Ϣ��ʧ�ܷ��ؾ���Ĵ�������Ϣ�� |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { contact } from '@kit.ContactsKit';

// 传入联系人的属性列表，查询“我的名片”
contact.queryMyCard({
  attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
}, (err: BusinessError, data) => {
  if (err) {
    console.error(`Failed to query My Card. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in querying My Card. data->${JSON.stringify(data)}`);
});

```


## queryMyCard

```TypeScript
function queryMyCard(context: Context, attrs: ContactAttributes, callback: AsyncCallback<Contact>): void
```

��ѯ���ҵ���Ƭ����֧�ִ�����ϵ�˵������б�����ʹ��callback�첽�ص���

**起始版本：** 10

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | Ӧ��������Context�� |
| attrs | ContactAttributes | 是 | ��ϵ�˵������б������Ϊ�գ����ѯ��ϵ�˵����������ֶΣ������������绰������ȣ��� |
| callback | AsyncCallback&lt;Contact&gt; | 是 | �ص��������ɹ����ء��ҵ���Ƭ����Ϣ��ʧ�ܷ��ؾ���Ĵ�������Ϣ�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: Mandatory parameters are left unspecified. |

**示例：**

在本文档的示例中，通过this.context来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需要在界面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
  import { BusinessError } from '@kit.BasicServicesKit';
  import { contact } from '@kit.ContactsKit';
  import { common } from '@kit.AbilityKit';

  // 请在组件内获取context。
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  contact.queryMyCard(context, {
    attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
  }, (err: BusinessError, data) => {
    if (err) {
      console.error(`Failed to query My Card. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`Succeeded in querying My Card. data->${JSON.stringify(data)}`);
  });

```


## queryMyCard

```TypeScript
function queryMyCard(attrs?: ContactAttributes): Promise<Contact>
```

��ѯ���ҵ���Ƭ����֧�ִ�����ϵ�˵������б�����ʹ��Promise�첽�ص���

**起始版本：** 7

**废弃版本：** 10

**替代接口：** queryMyCard(context:

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| attrs | ContactAttributes | 否 | ��ϵ�˵������б������Ϊ�գ����ѯ��ϵ�˵����������ֶΣ������������绰������ȣ��� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Contact&gt; | Promise���󡣷��ء��ҵ���Ƭ����ϵ�˶��� |

**示例：**

```TypeScript
import { contact } from '@kit.ContactsKit';

// 回调函数，传入联系人的属性列表，查询“我的名片”。
let promise = contact.queryMyCard({
  attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
});
promise.then((data) => {
  console.info(`Succeeded in querying My Card. data->${JSON.stringify(data)}`);
});

```


## queryMyCard

```TypeScript
function queryMyCard(context: Context, attrs?: ContactAttributes): Promise<Contact>
```

��ѯ���ҵ���Ƭ����֧�ִ�����ϵ�˵������б�����ʹ��Promise�첽�ص���

**起始版本：** 10

**需要权限：** ohos.permission.READ_CONTACTS

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | Ӧ��������Context�� |
| attrs | ContactAttributes | 否 | ��ϵ�˵������б������Ϊ�գ����ѯ��ϵ�˵����������ֶΣ������������绰������ȣ��� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Contact&gt; | Promise���󡣷��ء��ҵ���Ƭ����ϵ�˶��� |

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
  let promise = contact.queryMyCard(context, {
    attributes: [contact.Attribute.ATTR_NAME, contact.Attribute.ATTR_PHONE]
  });
  promise.then((data) => {
    console.info(`Succeeded in querying My Card. data->${JSON.stringify(data)}`);
  });

```

