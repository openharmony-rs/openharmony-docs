# setDisallowedPolicy

## setDisallowedPolicy

```TypeScript
function setDisallowedPolicy(admin: Want, feature: string, disallow: boolean): void
```

���ý���/����ĳ���ԡ�

**起始版本：** 12

**废弃版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS, ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS or ohos.permission.PERSONAL_MANAGE_RESTRICTIONS, ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS or ohos.permission.PERSONAL_MANAGE_RESTRICTIONS or ohos.permission.ENTERPRISE_MANAGE_NETWORK

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| feature | string | 是 | ֧�����õ������嵥�ο���1��<br/>**˵����** ��API version 15��ʼ��Ӧ������Ȩ��<br/>ohos.permission.PERSONAL_MANAGE_RESTRICTIONS��ͨ��<br/>[startAdminProvision](arkts-mdm-adminmanager-startadminprovision-f.md#startAdminProvision-1)����Ϊ<br/>[BDA](../../../../mdm/mdm-kit-term.md#bda)������ʹ�ô˽ӿ������������ԣ�bluetooth��hdc��microphone��usb��wifi��tethering��camera����API�汾26.0.0��ʼ������֧��ʹ�ô˽ӿ�����mtpServer���ԡ� |
| disallow | boolean | 是 | true��ʾ��ֹʹ�ã�false��ʾ����ʹ�á� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |
| [9200013](../../errorcode-universal.md#9200013-The) | The enterprise management policy has been successfully set,<br/>but the function has not taken effect in real time.&lt;br&gt;**适用版本：** 21+ |

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
  restrictions.setDisallowedPolicy(wantTemp, 'printer', true);
  console.info('Succeeded in setting printer disabled');
} catch (err) {
  console.error(`Failed to set printer disabled. Code is ${err.code}, message is ${err.message}`);
}

```


## setDisallowedPolicy

```TypeScript
function setDisallowedPolicy(admin: Want, feature: FeatureForDevice, disallow: boolean): void
```

���ý���/����ָ���豸���ԣ����ú�����豸�����޷���ʹ�á�

**起始版本：** 24

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS or ohos.permission.PERSONAL_MANAGE_RESTRICTIONS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| feature | FeatureForDevice | 是 | ָ��Ҫ���û��������豸���ԡ�<br/>**˵����** Ӧ������Ȩ��<br/>ohos.permission.PERSONAL_MANAGE_RESTRICTIONS��ͨ��<br/>[startAdminProvision](arkts-mdm-adminmanager-startadminprovision-f.md#startAdminProvision-1)����Ϊ<br/>[BDA](../../../../mdm/mdm-kit-term.md#bda)������ʹ�ô˽ӿ������������ԣ�<br/>[FeatureForDevice.WIFI_P2P](arkts-mdm-restrictions-featurefordevice-e.md#FeatureForDevice)�� |
| disallow | boolean | 是 | true��ʾ��ֹʹ�ã�false��ʾ����ʹ�á� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [9200010](../../errorcode-universal.md#9200010-A) | A conflict policy has been configured. |
| [9200013](../../errorcode-universal.md#9200013-The) | The enterprise management policy has been successfully set,<br/>but the function has not taken effect in real time. |
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
  restrictions.setDisallowedPolicy(wantTemp, restrictions.FeatureForDevice.WIFI_P2P, true);
  console.info('Succeeded in setting Wi-Fi P2P disabled');
} catch (err) {
  console.error(`Failed to set Wi-Fi P2P disabled. Code is ${err.code}, message is ${err.message}`);
}

```

