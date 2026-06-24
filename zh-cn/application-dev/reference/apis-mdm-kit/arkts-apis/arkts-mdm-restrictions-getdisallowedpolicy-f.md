# getDisallowedPolicy

## getDisallowedPolicy

```TypeScript
function getDisallowedPolicy(admin: Want | null, feature: string): boolean
```

��ѯĳ�����Ƿ񱻽��á�

**起始版本：** 12

**废弃版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS, ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS or ohos.permission.PERSONAL_MANAGE_RESTRICTIONS, ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS or ohos.permission.PERSONAL_MANAGE_RESTRICTIONS or ohos.permission.ENTERPRISE_MANAGE_NETWORK

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want \| null | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� [since 12 - 19] |
| feature | string | 是 | ֧�ֲ�ѯ�������嵥�ο��±�2��<br/>**˵����** ��API version 15��ʼ��Ӧ������Ȩ��<br/>ohos.permission.PERSONAL_MANAGE_RESTRICTIONS��ͨ��<br/>[startAdminProvision](arkts-mdm-adminmanager-startadminprovision-f.md#startAdminProvision-1)����Ϊ<br/>[BDA](../../../../mdm/mdm-kit-term.md#bda)������ʹ�ô˽ӿڻ�ȡ��������״̬��bluetooth��hdc��microphone��usb��wifi��tethering��camera����API�汾26.0.0��ʼ������֧��ʹ�ô˽ӿڻ�ȡmtpServer����״̬�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | admin - ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� [since 20] |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |

**示例：**

```TypeScript
import { restrictions } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // 参数需根据实际情况进行替换
  let result: boolean = restrictions.getDisallowedPolicy(wantTemp, 'printer');
  console.info(`Succeeded in querying whether the printing function is disabled. Disabled status: ${result}`);
} catch (err) {
  console.error(`Failed to get printer disabled status. Code is ${err.code}, message is ${err.message}`);
}

```


## getDisallowedPolicy

```TypeScript
function getDisallowedPolicy(admin: Want | null, feature: FeatureForDevice): boolean
```

��ѯָ���豸�����Ƿ񱻽��á�

**起始版本：** 24

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS or ohos.permission.PERSONAL_MANAGE_RESTRICTIONS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want \| null | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| feature | FeatureForDevice | 是 | ָ��Ҫ��ѯ���豸���ԡ� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | ����true��ʾfeature��Ӧ���豸���Ա����ã�false��ʾfeature��Ӧ���豸����δ�����á� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-Capability) | Capability not supported.<br/>Failed to call the API due to limited device capabilities. |

**示例：**

```TypeScript
import { restrictions } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  let result: boolean = restrictions.getDisallowedPolicy(wantTemp, restrictions.FeatureForDevice.WIFI_P2P);
  console.info(`Succeeded in querying whether Wi-Fi P2P is disabled. Disabled status: ${result}`);
} catch (err) {
  console.error(`Failed to get Wi-Fi P2P disabled status. Code is ${err.code}, message is ${err.message}`);
}

```

