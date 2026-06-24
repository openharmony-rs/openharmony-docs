# getDeviceInfo

## getDeviceInfo

```TypeScript
function getDeviceInfo(admin: Want, label: string): string
```

��ȡ�豸��Ϣ��

**起始版本：** 12

**需要权限：** ohos.permission.ENTERPRISE_GET_DEVICE_INFO

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| label | string | 是 | ֧�ֻ�ȡ���豸��Ϣ��ǩ��<br/>- deviceName���豸���ơ�<br/>- deviceSerial���豸���кš�<br/>- simInfo��SIM����Ϣ�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Device information obtained.<br/><br/>If **label** is **simInfo**, the return value is the SIM card information in a JSON string. For example,<br/>[{"slotId": 0, "MEID": "", "IMSI": "", "ICCID": "", "IMEI": "", "NUMBER": ""},<br/>{"slotId": 1, "MEID": "", "IMSI": "", "ICCID": "", "IMEI": "", "NUMBER": ""}]<br/>, where **slotId:0** indicates card slot 1, and **slotId:1** indicates card slot 2. **NUMBER** indicates the<br/>phone number and is supported since API version 23. The value is in the E.164 international standard format (<br/>for example, +8612345678901) that contains the country code. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [9200007](../../errorcode-universal.md#9200007-The) | The system ability works abnormally. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { deviceInfo } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // 需根据实际情况进行替换
  let result: string = deviceInfo.getDeviceInfo(wantTemp, 'deviceName');
  console.info(`Succeeded in getting device name, result : ${result}`);
} catch (err) {
  console.error(`Failed to get device name. Code: ${err.code}, message: ${err.message}`);
}

```

