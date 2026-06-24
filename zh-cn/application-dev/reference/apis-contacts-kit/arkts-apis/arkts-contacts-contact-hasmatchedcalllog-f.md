# hasMatchedCallLog

## hasMatchedCallLog

```TypeScript
function hasMatchedCallLog(context: Context, phoneNumber: string, minDuration: number): Promise<boolean>
```

����Ƿ��з���������ͨ����¼��Ĭ�ϲ�ѯ6Сʱ���ڵ�ͨ����¼���������Ӫ��ͨ����ʹ��Promise�첽�ص���

**起始版本：** 24

**需要权限：** ohos.permission.CHECK_CALL_LOG

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | Ӧ��������Context�� |
| phoneNumber | string | 是 | ��ϵ�˵ĵ绰���롣 |
| minDuration | number | 是 | ���ͨ��ʱ������λΪ�룬ȡֵ��Χ����0�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise���󣬷����Ƿ��з���������ͨ����¼��true�����з��������ģ�false����û�С� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [16700001](../../errorcode-universal.md#16700001-General) | General error. |
| [16700002](../../errorcode-universal.md#16700002-Invalid) | Invalid parameter value. |

**示例：**

在本文档的示例中，通过this.context来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需要在界面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
import { contact } from '@kit.ContactsKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context
const context = this.getUIContext().getHostContext() as common.UIAbilityContext;

const phoneNumber = '138xxxxxxxx';
const minDuration = 60;
// 调用接口查询，默认查询6小时以内的通话记录
contact.hasMatchedCallLog(context, phoneNumber, minDuration).then((hasMatch:boolean) => {
  console.info(`Has matched call log: ${hasMatch}`);
});

```


## hasMatchedCallLog

```TypeScript
function hasMatchedCallLog(context: Context, phoneNumber: string, minDuration: number, withinTime: number): Promise<boolean>
```

����Ƿ��з���������ͨ����¼���������Ӫ��ͨ����ʹ��Promise�첽�ص���

**起始版本：** 24

**需要权限：** ohos.permission.CHECK_CALL_LOG

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Applications.ContactsData

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | Ӧ��������Context�� |
| phoneNumber | string | 是 | ��ϵ�˵ĵ绰���롣 |
| minDuration | number | 是 | ���ͨ��ʱ������λΪ�룬ȡֵ��Χ����0�� |
| withinTime | number | 是 | ��ʾ�ӵ�ǰʱ�俪ʼ���㣬ͨ������ʼʱ��ͽ���ʱ��Ӧ�ڴ�ʱ�䷶Χ�ڣ���λΪ�롣��������6Сʱ������6Сʱ��Ĭ����6Сʱ��ѯ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise���󣬷����Ƿ��з���������ͨ����¼��true�����з��������ģ�false����û�С� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-Permission) | Permission denied. |
| [16700001](../../errorcode-universal.md#16700001-General) | General error. |
| [16700002](../../errorcode-universal.md#16700002-Invalid) | Invalid parameter value. |

**示例：**

在本文档的示例中，通过this.context来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需要在界面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
import { contact } from '@kit.ContactsKit';
import { common } from '@kit.AbilityKit';

// 请在组件内获取context
const context = this.getUIContext().getHostContext() as common.UIAbilityContext;

const phoneNumber = '138xxxxxxxx';
const minDuration = 60;
const withinTime = 2 * 60 *60;

// 调用接口查询
contact.hasMatchedCallLog(context, phoneNumber, minDuration, withinTime).then((hasMatch:boolean) => {
  console.info(`Has matched call log: ${hasMatch}`);
});

```

