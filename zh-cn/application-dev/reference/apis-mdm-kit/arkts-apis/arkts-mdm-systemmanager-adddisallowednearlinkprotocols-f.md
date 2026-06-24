# addDisallowedNearLinkProtocols

## addDisallowedNearLinkProtocols

```TypeScript
function addDisallowedNearLinkProtocols(admin: Want, protocols: Array<NearLinkProtocol>, accountId: number): void
```

Ϊָ���û����ӽ��õ�����Э��������NearLink Kit�����������ṩһ�ֵ͹��ġ������ʵĶ̾���ͨ�ŷ���֧�������豸֮������ӡ����ݽ�����<!--RP3--><!--RP3End-->���ӿڶԼ��̡���д�ʵ�ϵͳ�����ϵͳӦ��
����Ч��

**起始版本：** 20

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| protocols | Array&lt;NearLinkProtocol&gt; | 是 | ����Э���б��� |
| accountId | number | 是 | �û�ID��ȡֵ��Χ�����ڵ���0��<br/>accountId����ͨ��<br/>[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-1)<br/>�Ƚӿ�����ȡ�� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [9200012](../../errorcode-universal.md#9200012-The) | The parameter validation failed. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported. Failed to call the API due to limited device<br/>capabilities. |

**示例：**

```TypeScript
import { systemManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

// 需根据实际情况进行替换
let protocols: systemManager.NearLinkProtocol[] = [systemManager.NearLinkProtocol.SSAP,
  systemManager.NearLinkProtocol.DATA_TRANSFER];

// 需根据实际情况进行替换
let accountId: number = 100;

try {
  systemManager.addDisallowedNearLinkProtocols(wantTemp, protocols, accountId);
  console.info('Succeeded in adding the disabled Starlink protocol list for the specified user.');
} catch (err) {
  console.error(`Failed to add the disabled Starlink protocol list for the specified user. Code is ${err.code}, message is ${err.message}`);
}

```

