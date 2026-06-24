# subscribeManagedEvent（系统接口）

## subscribeManagedEvent

```TypeScript
function subscribeManagedEvent(admin: Want, managedEvents: Array<ManagedEvent>, callback: AsyncCallback<void>): void
```

����ϵͳ�����¼���ʹ��callback�첽�ص���

**起始版本：** 9

**废弃版本：** 26.0.0

**替代接口：** [subscribeManagedEventSync](arkts-mdm-adminmanager-subscribemanagedeventsync-f.md#subscribeManagedEventSync-1)

**需要权限：** ohos.permission.ENTERPRISE_SUBSCRIBE_MANAGED_EVENT

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| managedEvents | Array&lt;ManagedEvent&gt; | 是 | �����¼����顣 |
| callback | AsyncCallback&lt;void&gt; | 是 | �ص����������ӿڵ��óɹ���errΪnull������Ϊ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200008](../../errorcode-universal.md#9200008-The) | The specified system event is invalid. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { adminManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
let events: Array<adminManager.ManagedEvent> = [adminManager.ManagedEvent.MANAGED_EVENT_BUNDLE_ADDED, adminManager.ManagedEvent.MANAGED_EVENT_BUNDLE_REMOVED];

adminManager.subscribeManagedEvent(wantTemp, events, (err) => {
  if (err) {
    console.error(`Failed to subscribe managed event. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in subscribing managed event');
});

```


## subscribeManagedEvent

```TypeScript
function subscribeManagedEvent(admin: Want, managedEvents: Array<ManagedEvent>): Promise<void>
```

����ϵͳ�����¼���ʹ��Promise�첽�ص���

**起始版本：** 9

**废弃版本：** 26.0.0

**替代接口：** [subscribeManagedEventSync](arkts-mdm-adminmanager-subscribemanagedeventsync-f.md#subscribeManagedEventSync-1)

**需要权限：** ohos.permission.ENTERPRISE_SUBSCRIBE_MANAGED_EVENT

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| managedEvents | Array&lt;ManagedEvent&gt; | 是 | �����¼����顣 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | �޷��ؽ����Promise���󡣵�����ϵͳ�¼�ʧ��ʱ�����׳�������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200008](../../errorcode-universal.md#9200008-The) | The specified system event is invalid. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { adminManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
let events: Array<adminManager.ManagedEvent> = [adminManager.ManagedEvent.MANAGED_EVENT_BUNDLE_ADDED, adminManager.ManagedEvent.MANAGED_EVENT_BUNDLE_REMOVED];

adminManager.subscribeManagedEvent(wantTemp, events).then(() => {
}).catch((err: BusinessError) => {
  console.error(`Failed to subscribe managed event. Code: ${err.code}, message: ${err.message}`);
})

```

