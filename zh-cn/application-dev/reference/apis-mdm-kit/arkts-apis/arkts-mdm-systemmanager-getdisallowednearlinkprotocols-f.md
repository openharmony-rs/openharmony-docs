# getDisallowedNearLinkProtocols

## getDisallowedNearLinkProtocols

```TypeScript
function getDisallowedNearLinkProtocols(admin: Want, accountId: number): Array<NearLinkProtocol>
```

��ȡָ���û��½��õ�����Э��������

**起始版本：** 20

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| accountId | number | 是 | �û�ID��ȡֵ��Χ�����ڵ���0��<br/>accountId����ͨ��<br/>[getOsAccountLocalId](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getOsAccountLocalId-1)<br/>�Ƚӿ�����ȡ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;NearLinkProtocol&gt; | ָ���û��½��õ�����Э�������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
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
let accountId: number = 100;

try {
  let result: systemManager.NearLinkProtocol[] = systemManager.getDisallowedNearLinkProtocols(wantTemp, accountId);
  console.info(`Succeeded in querying the disabled Starlink protocol list for the specified user: ${result}`);
} catch (err) {
  console.error(`Failed to query the disabled Starlink protocol list for the specified user. Code is ${err.code}, message is ${err.message}`);
}

```

