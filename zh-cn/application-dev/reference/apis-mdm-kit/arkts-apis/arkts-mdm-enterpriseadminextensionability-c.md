# EnterpriseAdminExtensionAbility

��ģ���ṩ[��ҵ�豸������չ����](../../../../mdm/mdm-kit-term.md#��ҵ�豸������չ����)��

�豸����Ӧ����Ҫ����һ��EnterpriseAdminExtensionAbility����д��ؽӿڣ��Դ˾߱�ģ���ṩ�ĸ������������������ϵͳ���͵ĸ�Ӧ�ñ�������߽�������֪ͨ��

> **˵����**
>
> ��ģ��ӿڽ�����Stageģ����ʹ�á�

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## onAccountAdded

```TypeScript
onAccountAdded(accountId: number): void
```

ϵͳ�˺������¼��ص���ͨ���ӿ�
[adminManager.subscribeManagedEventSync](arkts-mdm-adminmanager-subscribemanagedeventsync-f.md#subscribeManagedEventSync-1)
ע��MANAGED_EVENT_ACCOUNT_ADDED�¼������յ��˻ص�����ҵ�豸���������£��豸����Ӧ�ö���ϵͳ�˺������¼���ϵͳ�˺������¼�֪ͨ�豸����Ӧ�ã��豸����Ӧ�ÿ����ڴ˻ص������н����¼��ϱ���֪ͨ��ҵ����Ա��

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accountId | number | 是 | �������û�ID�� |

**示例：**

```TypeScript
import { EnterpriseAdminExtensionAbility } from '@kit.MDMKit';

export default class EnterpriseAdminAbility extends EnterpriseAdminExtensionAbility {
  onAccountAdded(accountId: number) {
    console.info(`Succeeded in calling onAccountAdded callback, added accountId: ${accountId}`);
  }
}

```

## onAccountRemoved

```TypeScript
onAccountRemoved(accountId: number): void
```

ϵͳ�˺�ɾ���¼��ص���ͨ���ӿ�
[adminManager.subscribeManagedEventSync](arkts-mdm-adminmanager-subscribemanagedeventsync-f.md#subscribeManagedEventSync-1)
ע��MANAGED_EVENT_ACCOUNT_REMOVED�¼������յ��˻ص�����ҵ�豸���������£��豸����Ӧ�ö���ϵͳ�˺�ɾ���¼���ϵͳ�˺�ɾ���¼�֪ͨ�豸����Ӧ�ã��豸����Ӧ�ÿ����ڴ˻ص������н����¼��ϱ���֪ͨ��ҵ����Ա��

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accountId | number | 是 | ��ɾ�����û�ID�� |

**示例：**

```TypeScript
import { EnterpriseAdminExtensionAbility } from '@kit.MDMKit';

export default class EnterpriseAdminAbility extends EnterpriseAdminExtensionAbility {
  onAccountRemoved(accountId: number) {
    console.info(`Succeeded in calling onAccountRemoved callback, removed accountId: ${accountId}`);
  }
}

```

## onAccountSwitched

```TypeScript
onAccountSwitched(accountId: number): void
```

ϵͳ�˺��л��¼��ص���ͨ���ӿ�
[adminManager.subscribeManagedEventSync](arkts-mdm-adminmanager-subscribemanagedeventsync-f.md#subscribeManagedEventSync-1)
ע��MANAGED_EVENT_ACCOUNT_SWITCHED�¼������յ��˻ص�����ҵ�豸���������£��豸����Ӧ�ö���ϵͳ�˺��л��¼���ϵͳ�˺��л��¼�֪ͨ�豸����Ӧ�ã��豸����Ӧ�ÿ����ڴ˻ص������н����¼��ϱ���֪ͨ��ҵ����Ա
��

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| accountId | number | 是 | �л�����û�ID�� |

**示例：**

```TypeScript
import { EnterpriseAdminExtensionAbility } from '@kit.MDMKit';

export default class EnterpriseAdminAbility extends EnterpriseAdminExtensionAbility {
  onAccountSwitched(accountId: number) {
    console.info(`Succeeded in calling onAccountSwitched callback, switched accountId: ${accountId}`);
  }
}

```

## onAdminDisabled

```TypeScript
onAdminDisabled(): void
```

��ǰ�豸����Ӧ�ñ��������󣬴����ûص�����ҵ����Ա����Ա����������豸������ϵͳ֪ͨ�豸����Ӧ���ѽ������adminȨ�ޡ��豸����Ӧ�ÿ��ڴ˻ص�������֪ͨ��ҵ����Ա�豸���ѹܡ�����ע�ᣬ��������Ĭ�ϴ����ûص���

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**示例：**

```TypeScript
import { EnterpriseAdminExtensionAbility } from '@kit.MDMKit';

export default class EnterpriseAdminAbility extends EnterpriseAdminExtensionAbility {
  onAdminDisabled() {
  }
}

```

## onAdminEnabled

```TypeScript
onAdminEnabled(): void
```

��ǰ�豸����Ӧ�ñ�����󣬴����ûص�����ҵ����Ա����Ա�����𲢼����豸����Ӧ�ã�ϵͳ֪ͨ�豸����Ӧ���Ѽ���adminȨ�ޡ��豸����Ӧ�ÿ��ڴ˻ص������н��г�ʼ���������á�����ע�ᣬ�����Ĭ�ϴ����ûص���

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**示例：**

```TypeScript
import { EnterpriseAdminExtensionAbility } from '@kit.MDMKit';

export default class EnterpriseAdminAbility extends EnterpriseAdminExtensionAbility {
  onAdminEnabled() {
  }
}

```

## onAdminPolicyChanged

```TypeScript
onAdminPolicyChanged(event: common.PolicyChangedEvent): void
```

���Ա��ʱ�ص�

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | common.PolicyChangedEvent | 是 | ���Ա���¼� |

**示例：**

```TypeScript
import { EnterpriseAdminExtensionAbility, common } from '@kit.MDMKit';

export default class EnterpriseAdminAbility extends EnterpriseAdminExtensionAbility {
  onAdminPolicyChanged(event: common.PolicyChangedEvent) {
    // 例如当MDM应用调用setPasswordPolicy接口设置密码策略时，输出示例为: Policy changed, bundleName : com.example.test, functionName: setPasswordPolicy, parameters: {"policy":{"complexityRegex":"^(?=.*[a-zA-Z])(?=.*\\d).{8},$","validityPeriod":1808309786000,"additionalDescription":"至少8个字符，且包含数字和字母。"}}, time: 1776773305379.
    console.info(`Policy changed, bundleName : ${event.bundleName}, functionName: ${event.functionName}, parameters: ${event.parameters}, time: ${event.time}.`);
  }
}

```

## onAppStart

```TypeScript
onAppStart(bundleName: string): void
```

Ӧ�������¼��ص���ͨ���ӿ�
[adminManager.subscribeManagedEventSync](arkts-mdm-adminmanager-subscribemanagedeventsync-f.md#subscribeManagedEventSync-1)
ע��MANAGED_EVENT_APP_START�¼������յ��˻ص�����ҵ�豸���������£��豸����Ӧ�ö���Ӧ�������¼����˲�Ӧ�������¼�֪ͨ�豸����Ӧ�ã��豸����Ӧ�ÿ����ڴ˻ص������н����¼��ϱ���֪ͨ��ҵ����Ա��

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ����Ӧ�õİ����� |

**示例：**

```TypeScript
import { EnterpriseAdminExtensionAbility } from '@kit.MDMKit';

export default class EnterpriseAdminAbility extends EnterpriseAdminExtensionAbility {
  onAppStart(bundleName: string) {
    console.info(`Succeeded in calling onAppStart callback, started bundle name : ${bundleName}`);
  }
}

```

## onAppStop

```TypeScript
onAppStop(bundleName: string): void
```

Ӧ��ֹͣ�¼��ص���ͨ���ӿ�
[adminManager.subscribeManagedEventSync](arkts-mdm-adminmanager-subscribemanagedeventsync-f.md#subscribeManagedEventSync-1)
ע��MANAGED_EVENT_APP_STOP�¼������յ��˻ص�����ҵ�豸���������£��豸����Ӧ�ö���Ӧ��ֹͣ�¼����˲�Ӧ��ֹͣ�¼�֪ͨ�豸����Ӧ�ã��豸����Ӧ�ÿ����ڴ˻ص������н����¼��ϱ���֪ͨ��ҵ����Ա��

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ֹͣӦ�õİ����� |

**示例：**

```TypeScript
import { EnterpriseAdminExtensionAbility } from '@kit.MDMKit';

export default class EnterpriseAdminAbility extends EnterpriseAdminExtensionAbility {
  onAppStop(bundleName: string) {
    console.info(`Succeeded in calling onAppStop callback, stopped bundle name : ${bundleName}`);
  }
}

```

## onBundleAdded

```TypeScript
onBundleAdded(bundleName: string): void
```

Ӧ�ð�װ�¼��ص����ص��а���Ӧ�ð�����ͨ���ӿ�
[adminManager.subscribeManagedEventSync](arkts-mdm-adminmanager-subscribemanagedeventsync-f.md#subscribeManagedEventSync-1)
ע��MANAGED_EVENT_BUNDLE_ADDED�¼������յ��˻ص�����ҵ�豸���������£��豸����Ӧ�ö���Ӧ�ð�װ�¼����˲�Ӧ�ð�װ�¼�֪ͨ�豸����Ӧ�ã��豸����Ӧ�ÿ����ڴ˻ص������н����¼��ϱ���֪ͨ��ҵ����Ա��

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ����װӦ�õİ����� |

**示例：**

```TypeScript
import { EnterpriseAdminExtensionAbility } from '@kit.MDMKit';

export default class EnterpriseAdminAbility extends EnterpriseAdminExtensionAbility {
  onBundleAdded(bundleName: string) {
    console.info(`Succeeded in calling onBundleAdded callback, added bundle name : ${bundleName}`);
  }
}

```

## onBundleAdded

```TypeScript
onBundleAdded(bundleName: string, accountId: number): void
```

Ӧ�ð�װ�¼��ص����ص��а���Ӧ�ð������˺�ID��ͨ���ӿ�
[adminManager.subscribeManagedEventSync](arkts-mdm-adminmanager-subscribemanagedeventsync-f.md#subscribeManagedEventSync-1)
ע��MANAGED_EVENT_BUNDLE_ADDED�¼������յ��˻ص�����ҵ�豸���������£��豸����Ӧ�ö���Ӧ�ð�װ�¼����˲�Ӧ�ð�װ�¼�֪ͨ�豸����Ӧ�ã��豸����Ӧ�ÿ����ڴ˻ص������н����¼��ϱ���֪ͨ��ҵ����Ա��

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ����װӦ�õİ����� |
| accountId | number | 是 | ����װӦ�����ڵ��û�ID�� |

**示例：**

```TypeScript
import { EnterpriseAdminExtensionAbility } from '@kit.MDMKit';

export default class EnterpriseAdminAbility extends EnterpriseAdminExtensionAbility {
  // 由于存在同名回调方法onBundleAdded(bundleName: string)，该回调方法无accountId参数，因此在实际调用时accountId必须为可选参数，写法请参考示例代码。如果删除accountId后的问号"?"，编译会报错。
  onBundleAdded(bundleName: string, accountId?: number) {
    console.info(`Succeeded in calling onBundleAdded callback, added bundle name : ${bundleName}, accountId: ${accountId}`);
  }
}

```

## onBundleRemoved

```TypeScript
onBundleRemoved(bundleName: string): void
```

Ӧ��ж���¼��ص����ص��а���Ӧ�ð�����ͨ���ӿ�
[adminManager.subscribeManagedEventSync](arkts-mdm-adminmanager-subscribemanagedeventsync-f.md#subscribeManagedEventSync-1)
ע��MANAGED_EVENT_BUNDLE_REMOVED�¼������յ��˻ص�����ҵ�豸���������£��豸����Ӧ�ö���Ӧ��ж���¼����˲�Ӧ��ж���¼�֪ͨ�豸����Ӧ�ã��豸����Ӧ�ÿ����ڴ˻ص������н����¼��ϱ���֪ͨ��ҵ����Ա��

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ��ж��Ӧ�õİ����� |

**示例：**

```TypeScript
import { EnterpriseAdminExtensionAbility } from '@kit.MDMKit';

export default class EnterpriseAdminAbility extends EnterpriseAdminExtensionAbility {
  onBundleRemoved(bundleName: string) {
    console.info(`Succeeded in calling onBundleRemoved callback, removed bundle name : ${bundleName}`);
  }
}

```

## onBundleRemoved

```TypeScript
onBundleRemoved(bundleName: string, accountId: number): void
```

Ӧ��ж���¼��ص����ص��а���Ӧ�ð������˺�ID��ͨ���ӿ�
[adminManager.subscribeManagedEventSync](arkts-mdm-adminmanager-subscribemanagedeventsync-f.md#subscribeManagedEventSync-1)
ע��MANAGED_EVENT_BUNDLE_REMOVED�¼������յ��˻ص�����ҵ�豸���������£��豸����Ӧ�ö���Ӧ��ж���¼����˲�Ӧ��ж���¼�֪ͨ�豸����Ӧ�ã��豸����Ӧ�ÿ����ڴ˻ص������н����¼��ϱ���֪ͨ��ҵ����Ա��

**起始版本：** 14

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ��ж��Ӧ�õİ����� |
| accountId | number | 是 | ��ж��Ӧ�����ڵ��û�ID�� |

**示例：**

```TypeScript
import { EnterpriseAdminExtensionAbility } from '@kit.MDMKit';

export default class EnterpriseAdminAbility extends EnterpriseAdminExtensionAbility {
  // 由于存在同名回调方法onBundleRemoved(bundleName: string)，该回调方法无accountId参数，因此在实际调用时accountId必须为可选参数，写法请参考示例代码。如果删除accountId后的问号"?"，编译会报错。
  onBundleRemoved(bundleName: string, accountId?: number) {
    console.info(`Succeeded in calling onBundleRemoved callback, removed bundle name : ${bundleName}, accountId: ${accountId}`);
  }
}

```

## onBundleUpdated

```TypeScript
onBundleUpdated(bundleName: string, accountId: number): void
```

Ӧ�ø����¼��ص����ص��а���Ӧ�ð������û�ID��ͨ���ӿ�
[adminManager.subscribeManagedEventSync](arkts-mdm-adminmanager-subscribemanagedeventsync-f.md#subscribeManagedEventSync-1)
ע��MANAGED_EVENT_BUNDLE_UPDATED�¼������յ��˻ص�����ҵ�豸���������£��豸����Ӧ�ÿɶ��������û��µ�Ӧ�ø����¼���Ӧ�ø����¼�����ʱ��֪ͨ��ǰ�û��µ��豸����Ӧ�ã��豸����Ӧ�ÿ����ڴ˻ص������н�����
���ϱ���֪ͨ���û��µ���ҵ����Ա��

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ������Ӧ�õİ����� |
| accountId | number | 是 | ������Ӧ�����ڵ��û�ID<br/><br/>ȡֵ��ΧΪȫ�������� |

**示例：**

```TypeScript
import { EnterpriseAdminExtensionAbility } from '@kit.MDMKit';

export default class EnterpriseAdminAbility extends EnterpriseAdminExtensionAbility {
  onBundleUpdated(bundleName: string, accountId: number) {
    console.info(`Succeeded in calling onBundleUpdated callback, update bundle name : ${bundleName}, accountId: ${accountId}`);
  }
}

```

## onDeviceAdminDisabled

```TypeScript
onDeviceAdminDisabled(bundleName: string): void
```

�������豸����Ӧ������ͨ�豸����Ӧ�ñ��������ʱ�ᴥ���˻ص�����ҵ����Ա����Ա�����������ͨ�豸����Ӧ�ã�ϵͳ֪ͨ�����豸����Ӧ���ѽ������adminȨ�ޡ������豸����Ӧ�ÿ��ڴ˻ص�������֪ͨ��ҵ����Ա�豸���ѹܡ�����Ҫע�ᣬ���
�����Ĭ�ϴ����ûص���

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ���������Ӧ�õİ����� |

**示例：**

```TypeScript
import { EnterpriseAdminExtensionAbility } from '@kit.MDMKit';

export default class EnterpriseAdminAbility extends EnterpriseAdminExtensionAbility {
  onDeviceAdminDisabled(bundleName: string) {
  }
}

```

## onDeviceAdminEnabled

```TypeScript
onDeviceAdminEnabled(bundleName: string): void
```

�������豸����Ӧ������ͨ�豸����Ӧ�ñ�����ʱ�ᴥ���˻ص�����ҵ����Ա����Ա�����𲢼�����ͨ�豸����Ӧ�ã�ϵͳ֪ͨ�����豸����Ӧ���Ѽ���adminȨ�ޡ������豸����Ӧ�ÿ��ڴ˻ص������н��г�ʼ���������á�����Ҫע�ᣬ�����Ĭ�ϴ�����
�ص���

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ������Ӧ�õİ����� |

**示例：**

```TypeScript
import { EnterpriseAdminExtensionAbility } from '@kit.MDMKit';

export default class EnterpriseAdminAbility extends EnterpriseAdminExtensionAbility {
  onDeviceAdminEnabled(bundleName: string) {
  }
}

```

## onDeviceBootCompleted

```TypeScript
onDeviceBootCompleted(): void
```

�豸��������¼��ص���ͨ���ӿ�
[adminManager.subscribeManagedEventSync](arkts-mdm-adminmanager-subscribemanagedeventsync-f.md#subscribeManagedEventSync-1)
ע��MANAGED_EVENT_BOOT_COMPLETED�¼������յ��˻ص�����ҵ�豸���������£��豸����Ӧ�ö����豸��������¼����˲�ϵͳ���豸������ɺ��֪ͨ�豸����Ӧ�ã��豸����Ӧ�ÿ����ڴ˻ص������н����¼��ϱ���֪ͨ��ҵ
����Ա��

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**示例：**

```TypeScript
import { EnterpriseAdminExtensionAbility } from '@kit.MDMKit';

export default class EnterpriseAdminAbility extends EnterpriseAdminExtensionAbility {
  onDeviceBootCompleted() {
    console.info("EnterpriseAdminExtensionAbility onDeviceBootCompleted");
  }
}

```

## onKeyEvent

```TypeScript
onKeyEvent(keyEvent: systemManager.KeyEvent): void
```

�����¼�����ʱ�ص���

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyEvent | systemManager.KeyEvent | 是 | Information about the current key event. |

**示例：**

```TypeScript
import { EnterpriseAdminExtensionAbility } from '@kit.MDMKit';
import { systemManager } from '@kit.MDMKit';

export default class EnterpriseAdminAbility extends EnterpriseAdminExtensionAbility {

 /* MDM应用下发按键事件监听后，用户按键行为匹配监听策略时，将触发该事件，事件回调携带当前匹配的按键信息。
  * 
  * 例如：
  * 1.用户短按电源键时触发回调（以电源键为例）
  * 1.1 下发按键监听事件
  * 请参考systemManager.addKeyEventPolicies。
  * 下发keyCode为0，keyPolicy为1。
  * 1.2 用户短按电源键
  * 1.3 触发回调
  * 结果：按下：onKeyEvent event:{"actionTime": 1895101259, "keyCode": 0, "keyAction": 0,
  *          "keyItems": [{"pressed": true, "keyCode": 0, "downTime": 1895101259}]}
  *       抬起：onKeyEvent event:{"actionTime": 1895478977, "keyCode": 0, "keyAction": 1,
  *         "keyItems": [{"pressed": false, "keyCode": 0, "downTime": 1895101259}]}
  *
  * 2.用户长按电源键时触发回调（以电源键为例）
  * 2.1 下发按键监听事件
  * 请参考systemManager.addKeyEventPolicies。
  * 下发keyCode为0，keyPolicy为1。
  * 2.2 用户长按电源键
  * 2.3 触发回调
  * 结果：按下：onKeyEvent event:{"actionTime": 14468236859, "keyCode": 0, "keyAction": 0,
  *         "keyItems": [{"pressed": true, "keyCode": 0, "downTime": 14468236859}]}
  *      长按：onKeyEvent event:{"actionTime": 14468236859, "keyCode": 0, "keyAction": 0,
  *         "keyItems": [{"pressed": true, "keyCode": 0, "downTime": 14468236859}]}
  *          ......
  *       抬起：onKeyEvent event:{"actionTime": 14471425448, "keyCode": 0, "keyAction": 1,
  *         "keyItems": [{"pressed": false, "keyCode": 0, "downTime": 14468236859}]}
  * 
  * 组合键根据下发策略不同，分为下面多种场景：
  * 3.用户按组合键触发回调1（以电源键和音量+键为例）
  * 3.1 下发按键监听事件
  * 请参考systemManager.addKeyEventPolicies。
  * 下发keyCode为0，keyPolicy为1；keyCode为1，keyPolicy为1；
  * 3.2 用户同时按下电源键和音量+键
  * 3.3 触发回调
  * 结果：同时按下（电源键先，音量+键后）
  *      onKeyEvent event:{"actionTime": 20991450446, "keyCode": 1, "keyAction": 0,
  *   "keyItems": [{"pressed": true, "keyCode": 0, "downTime": 20991432293}，
  *   {"pressed": true, "keyCode": 1, "downTime": 20991450446}]}
  *      同时抬起 （音量+键先，电源键后）
  *      onKeyEvent event:{"actionTime": 20590590293, "keyCode": 1, "keyAction": 1,
  *   "keyItems": [{"pressed": true, "keyCode": 0, "downTime": 28588682984}，
  *   {"pressed": false, "keyCode": 1, "downTime": 21588900860}]}
  * 
  * 4.用户按组合键触发回调2（以电源键和音量+键为例）
  * 4.1 下发按键监听事件
  * 请参考systemManager.addKeyEventPolicies。
  * 下发keyCode为0，keyPolicy为1；keyCode为1，keyPolicy为0；
  * 4.2 用户同时按下电源键和音量+键
  * 4.3 触发回调
  * 结果：同时按下（音量+键先，电源键后）
  *      onKeyEvent event:{"actionTime": 28991115400, "keyCode": 0, "keyAction": 0,
  *   "keyItems": [{"pressed": true, "keyCode": 1, "downTime": 28990731985}，
  *   {"pressed": true, "keyCode": 0, "downTime": 20991115400}]}
  *      同时抬起 （音量+键先，电源键后）
  *      onKeyEvent event:{"actionTime": 28992721560, "keyCode": 0, "keyAction": 1,
  *   "keyItems": [{"pressed": false, "keyCode": 0, "downTime": 28991115400}]}
  * 
  * 5.用户按组合键触发回调3（以电源键和音量+键为例）
  * 5.1 下发按键监听事件
  * 请参考systemManager.addKeyEventPolicies。
  * 下发keyCode为0，keyPolicy为1；
  * 5.2 用户同时按下电源键和音量+键
  * 5.3 触发回调
  * 结果：同时按下（音量+键先，电源键后）
  *      onKeyEvent event:{"actionTime": 29979014190, "keyCode": 0, "keyAction": 0,
  *   "keyItems": [{"pressed": true, "keyCode": 1, "downTime": 29978420634}，
  *   {"pressed": true, "keyCode": 0, "downTime": 29979014190}]}
  *      同时抬起 （电源键先，音量+键后）
  *      onKeyEvent event:{"actionTime": 29982420773, "keyCode": 0, "keyAction": 1,
  *   "keyItems": [{"pressed": true, "keyCode": 1, "downTime": 29978420634}，
  *   {"pressed": false, "keyCode": 0, "downTime": 29979014190}]}
  * 
  * 6.用户按组合键触发回调4（以电源键和导航键-最近打开为例）
  * 6.1 下发按键监听事件
  * 请参考systemManager.addKeyEventPolicies。
  * 下发keyCode为0，keyPolicy为1；keyCode为5，keyPolicy为1；
  * 6.2 用户同时按下电源键和导航键-最近打开
  * 6.3 触发回调
  * 结果：同时按下（各自执行回调，互不影响）
  *      onKeyEvent event:{"actionTime": 34073626894, "keyCode": 0, "keyAction": 0,
  *   "keyItems": [{"pressed": true, "keyCode": 0, "downTime": 34073626894}]}
  *      onKeyEvent event:{"actionTime": 34075144844, "keyCode": 5, "keyAction": 0,
  *   "keyItems": [{"pressed": true, "keyCode": 5, "downTime": 0}]}
  */
  onKeyEvent(keyEvent: systemManager.KeyEvent): void {
    console.info(`Succeeded in calling onKeyEvent callback, key event:${JSON.stringify(keyEvent)}`);
  }
}

```

## onKioskModeEntering

```TypeScript
onKioskModeEntering(bundleName: string, accountId: number): void
```

Ӧ�ý���Kioskģʽ�ص����ص��а���Ӧ�ð������û�ID��

KioskģʽΪϵͳ�����ṩ��һ��Ӧ������ģʽ����ģʽ�»Ὣ�豸�����ڵ���Ӧ�û���һ��Ӧ�����У�ͬʱ������״̬��״̬�������Ʋ����͹ؼ����ܽ��п��ƣ���ֹ�û����豸����������Ӧ�û�ִ������������

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | ����KioskģʽӦ�õİ����� |
| accountId | number | 是 | ����KioskģʽӦ�����ڵ��û�ID�� |

**示例：**

```TypeScript
import { EnterpriseAdminExtensionAbility } from '@kit.MDMKit';

export default class EnterpriseAdminAbility extends EnterpriseAdminExtensionAbility {
  onKioskModeEntering(bundleName: string, accountId: number): void {
    console.info(`Succeeded in calling onKioskModeEntering callback, bundleName:${bundleName}, accountId:${accountId}`);
  }
}

```

## onKioskModeExiting

```TypeScript
onKioskModeExiting(bundleName: string, accountId: number): void
```

Ӧ���˳�Kioskģʽ�ص����ص��а���Ӧ�ð������û�ID��

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | �˳�KioskģʽӦ�õİ����� |
| accountId | number | 是 | �˳�KioskģʽӦ�����ڵ��û�ID�� |

**示例：**

```TypeScript
import { EnterpriseAdminExtensionAbility } from '@kit.MDMKit';

export default class EnterpriseAdminAbility extends EnterpriseAdminExtensionAbility {
  onKioskModeExiting(bundleName: string, accountId: number): void {
    console.info(`Succeeded in calling onKioskModeExiting callback, bundleName:${bundleName}, accountId:${accountId}`);
  }
}

```

## onLogCollected

```TypeScript
onLogCollected(result: common.Result): void
```

��־�ռ���ɻص�

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| result | common.Result | 是 | Log collection result. |

**示例：**

```TypeScript
import { Want } from '@kit.AbilityKit';
import { EnterpriseAdminExtensionAbility, common, systemManager } from '@kit.MDMKit';
import { fileIo as fs } from '@kit.CoreFileKit';

export default class EnterpriseAdminAbility extends EnterpriseAdminExtensionAbility {
  /**
   * MDM应用调用systemManager.startCollectLog接口启动日志收集任务后，将触发该回调函数，回调携带日志收集结果。
   * 若result为common.Result.SUCCESS，表示日志收集成功。请取走日志，并调用systemManager.finishLogCollected删除已收集到的日志。
   * 若result为common.Result.FAIL，表示日志收集失败。
   */
  onLogCollected(result: common.Result): void {
    console.info(`Succeeded in calling onLogCollected callback, result:${result}`);
    if (result === common.Result.SUCCESS) {
      let filesDir = '/data/edm/log';
      // 应用沙箱路径，需根据实际情况进行替换
      let targetPath = this.context.tempDir;
      try {
        let files: string[] = fs.listFileSync(filesDir);
        // 从/data/edm/log沙箱目录取走日志
        files.forEach(value => {
          fs.copyFileSync(filesDir + '/' + value, targetPath + '/' + value);
        });
        let wantTemp: Want = {
          // 需根据实际情况进行替换
          bundleName: 'com.example.myapplication',
          abilityName: 'EnterpriseAdminAbility'
        };
        systemManager.finishLogCollected(wantTemp);
      } catch (error) {
        console.info("onLogCollected", "error: " + JSON.stringify(error))
      }
    }
    if (result === common.Result.FAIL) {
      console.error("onLogCollected", "Failed to collect log.")
    }
  }
}

```

## onMarketAppInstallResult

```TypeScript
onMarketAppInstallResult(bundleName: string, result: common.InstallationResult): void
```

��װӦ���г�Ӧ�ýӿ�[bundleManager.installMarketApps](arkts-mdm-bundlemanager-installmarketapps-f.md#installMarketApps-1)��װ
����ص����ص��а���Ӧ�ð����Ͱ�װ�����

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | Ӧ���г�Ӧ�ð����� |
| result | common.InstallationResult | 是 | ��װ����� |

**示例：**

```TypeScript
import { EnterpriseAdminExtensionAbility, common } from '@kit.MDMKit';

export default class EnterpriseAdminAbility extends EnterpriseAdminExtensionAbility {
  onMarketAppInstallResult(bundleName: string, result: common.InstallationResult): void {
    console.info(`Succeeded in calling onMarketAppInstallResult callback, bundleName:${bundleName}, result:${result}`);
  }
}

```

## onStart

```TypeScript
onStart(): void
```

EnterpriseAdminExtensionAbility�����¼��ص���

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**示例：**

```TypeScript
import { EnterpriseAdminExtensionAbility } from '@kit.MDMKit';

export default class EnterpriseAdminAbility extends EnterpriseAdminExtensionAbility {
  onStart() {
    console.info(`Succeeded in calling onStart callback.`);
  }
}

```

## onStartupGuideCompleted

```TypeScript
onStartupGuideCompleted(scene: common.StartupScene): void
```

����������¼��ص���ͨ���ӿ�
[adminManager.subscribeManagedEventSync](arkts-mdm-adminmanager-subscribemanagedeventsync-f.md#subscribeManagedEventSync-1)
ע��MANAGED_EVENT_STARTUP_GUIDE_COMPLETED�¼������յ��˻ص�����ҵ�豸���������£��豸����Ӧ�ö��Ŀ���������¼����˲�ϵͳ���״��л����û���ɣ�����PC����OTA������ɡ��״ο�����ɿ�����
ʱ��֪ͨ�豸����Ӧ�ã��豸����Ӧ�ÿ����ڴ˻ص������н����¼��ϱ���֪ͨ��ҵ����Ա��

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scene | common.StartupScene | 是 | ��������ɳ����� |

**示例：**

```TypeScript
import { EnterpriseAdminExtensionAbility, common } from '@kit.MDMKit';

export default class EnterpriseAdminAbility extends EnterpriseAdminExtensionAbility {
  onStartupGuideCompleted(scene: common.StartupScene) {
    if (scene === common.StartupScene.USER_SETUP) {
      console.info('onStartupGuideCompleted scene is USER_SETUP');
    } else if (scene === common.StartupScene.OTA) {
      console.info('onStartupGuideCompleted scene is OTA');
    } else if (scene === common.StartupScene.DEVICE_PROVISION) {
      console.info('onStartupGuideCompleted scene is DEVICE_PROVISION');
    }
  }
}

```

## onSystemUpdate

```TypeScript
onSystemUpdate(systemUpdateInfo: systemManager.SystemUpdateInfo): void
```

ϵͳ�����¼��ص���ͨ���ӿ�
[adminManager.subscribeManagedEventSync](arkts-mdm-adminmanager-subscribemanagedeventsync-f.md#subscribeManagedEventSync-1)
ע��MANAGED_EVENT_SYSTEM_UPDATE�¼������յ��˻ص�����ҵ�豸���������£��豸����Ӧ�ö���ϵͳ�����¼����˲�ϵͳ�����¼�֪ͨ�豸����Ӧ�ã��豸����Ӧ�ÿ����ڴ˻ص������н����¼��ϱ���֪ͨ��ҵ����Ա��

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| systemUpdateInfo | systemManager.SystemUpdateInfo | 是 | ϵͳ���µİ汾��Ϣ�� |

**示例：**

```TypeScript
import { EnterpriseAdminExtensionAbility } from '@kit.MDMKit';
import { systemManager } from '@kit.MDMKit';

export default class EnterpriseAdminAbility extends EnterpriseAdminExtensionAbility {
  onSystemUpdate(systemUpdateInfo: systemManager.SystemUpdateInfo) {
    console.info(`Succeeded in calling onSystemUpdate callback, version name  : ${systemUpdateInfo.versionName}`);
  }
}

```

## context

```TypeScript
context: EnterpriseAdminExtensionContext
```

EnterpriseAdminExtensionAbility�������ġ��̳���[ExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-extensioncontext-c.md#ExtensionContext)��

**类型：** EnterpriseAdminExtensionContext

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

