# getValue

## getValue

```TypeScript
function getValue(admin: Want, item: string): string
```

��ȡ�豸���ò��ԡ�

**起始版本：** 12

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SETTINGS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | ��ҵ�豸������չ�����Want�б��������ҵ�豸������չ������abilityName������Ӧ�õ�bundleName�� |
| item | string | 是 | �豸���ò������͡�<br/>- screenOff���豸Ϣ�����ԣ�����PC/2in1�豸��֧�ֲ�ѯ��ع����µ��豸Ϣ�����ԡ�<br/>- powerPolicy���豸��Դ���ԣ�����<br/>PC/2in1�豸��Ч����֧�ֲ�ѯ��ع����µ��豸��Դ���ԡ�<br/>- eyeComfort����API version 23��ʼ֧�֣�����ģʽ����״̬�� |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Policy type value.<br/><br/>If **item** is **screenOff**, the device screen-off time (in ms) is returned. For PCs/2-in-1 devices,<br/>the device screen-off time (in ms) in battery mode is returned.<br/><br/>If **item** is **powerPolicy**, the power policy is returned. For PCs/2-in-1 devices, the power policy in<br/>battery mode is returned. The power policy a JSON string in {"powerScene":xx,"powerPolicy":{"powerPolicyAction"<br/>:xx,"delayTime":xx}} format. **powerScene** indicates the power policy scenario, **delayTime** indicates the<br/>delay time (in milliseconds), and **powerPolicyAction** indicates the sleep policy.<br/><br/>The value of **powerScene** can be:<br/><br/>- **0**: timeout.<br/><br/>The value of **powerPolicyAction** can be:<br/><br/>- **0**: No action is performed.<br/><br/>- **1**: enter sleep mode automatically.<br/><br/>- **2**: forcibly enter sleep mode.<br/><br/>- **3**: enter sleep mode. This policy does not take effect currently.<br/><br/>- **4**: power off.<br/><br/>If **item** is **eyeComfort**, **value** is a string indicating the status of the eye comfort mode.<br/><br/>- **on**: The eye comfort mode is enabled all day.<br/><br/>- **off**: The eye comfort mode is disabled.<br/><br/>- **unknown**: other modes. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../../errorcode-universal.md#9200001-The) | The application is not an administrator application of the device. |
| [9200002](../../errorcode-universal.md#9200002-The) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-Permission) | Permission verification failed.<br/>The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br/>2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { deviceSettings } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // 参数需根据实际情况进行替换
  let result: string = deviceSettings.getValue(wantTemp, 'screenOff');
  console.info(`Succeeded in getting screen off time, result : ${result}`);
} catch (err) {
  console.error(`Failed to get screen off time. Code: ${err.code}, message: ${err.message}`);
}

```

