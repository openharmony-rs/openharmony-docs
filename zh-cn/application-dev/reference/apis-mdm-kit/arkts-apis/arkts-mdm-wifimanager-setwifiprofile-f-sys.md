# setWifiProfile（系统接口）

## setWifiProfile

```TypeScript
function setWifiProfile(admin: Want, profile: WifiProfile, callback: AsyncCallback<void>): void
```

Ϊ��ǰ�豸����Wi-Fi��ʹ���ӵ�ָ�����硣ʹ��callback�첽�ص���

**起始版本：** 10

**废弃版本：** 26.0.0

**替代接口：** [setWifiProfileSync](arkts-mdm-wifimanager-setwifiprofilesync-f.md#setWifiProfileSync-1)

**需要权限：** ohos.permission.ENTERPRISE_SET_WIFI

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| profile | WifiProfile | 是 | Wi-Fi������Ϣ�� |
| callback | AsyncCallback&lt;void&gt; | 是 | �ص����������ӿڵ��óɹ���errΪnull������Ϊ������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { wifiManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
let profile: wifiManager.WifiProfile = {
  // 需根据实际情况进行替换
  'ssid': 'name',
  'preSharedKey': 'passwd',
  'securityType': wifiManager.WifiSecurityType.WIFI_SEC_TYPE_PSK
};

wifiManager.setWifiProfile(wantTemp, profile, (err) => {
  if (err) {
    console.error(`Failed to set wifi profile. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in setting wifi profile');
});

```


## setWifiProfile

```TypeScript
function setWifiProfile(admin: Want, profile: WifiProfile): Promise<void>
```

Ϊ��ǰ�豸����Wi-Fi��ʹ���ӵ�ָ�����硣ʹ��Promise�첽�ص���

**起始版本：** 10

**废弃版本：** 26.0.0

**替代接口：** [setWifiProfileSync](arkts-mdm-wifimanager-setwifiprofilesync-f.md#setWifiProfileSync-1)

**需要权限：** ohos.permission.ENTERPRISE_SET_WIFI

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| profile | WifiProfile | 是 | Wi-Fi������Ϣ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | �޷��ؽ����Promise���󡣵�����Wi-Fi���ӵ�ָ������ʧ��ʱ���׳�������� |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed. The application does not have the permission<br/>required to call the API. |
| [202](../../errorcode-universal.md#202-Permission) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { wifiManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
let profile: wifiManager.WifiProfile = {
  // 需根据实际情况进行替换
  'ssid': 'name',
  'preSharedKey': 'passwd',
  'securityType': wifiManager.WifiSecurityType.WIFI_SEC_TYPE_PSK
};

wifiManager.setWifiProfile(wantTemp, profile).then(() => {
  console.info('Succeeded in setting wifi profile');
}).catch((err: BusinessError) => {
  console.error(`Failed to set wifi profile. Code: ${err.code}, message: ${err.message}`);
});

```

