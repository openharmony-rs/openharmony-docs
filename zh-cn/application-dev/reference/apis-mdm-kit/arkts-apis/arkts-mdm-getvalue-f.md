# getValue

## getValue

```TypeScript
function getValue(admin: Want, item: string): string
```

获取设备设置策略。

**起始版本：** 12

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SETTINGS

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | Want | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| item | string | 是 | 设备设置策略类型。<br/>- screenOff：设备息屏策略，对于PC/2in1设备，支持查询电池供电下的设备息屏策略。<br/>- powerPolicy：设备电源策略，仅对PC/2in1设备生效，仅支持查询电池供电下的设备电源策略。<br/>- eyeComfort：从API version 23开始支持，护眼模式开关状态。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Policy type value.<br>If **item** is **screenOff**, the device screen-off time (in ms) is returned. For PCs/2-in-1 devices,the device screen-off time (in ms) in battery mode is returned.<br>If **item** is **powerPolicy**, the power policy is returned. For PCs/2-in-1 devices, the power policy inbattery mode is returned. The power policy a JSON string in {"powerScene":xx,"powerPolicy":{"powerPolicyAction":xx,"delayTime":xx}} format. **powerScene** indicates the power policy scenario, **delayTime** indicates thedelay time (in milliseconds), and **powerPolicyAction** indicates the sleep policy.<br>The value of **powerScene** can be:<br>- **0**: timeout.<br>The value of **powerPolicyAction** can be:<br>- **0**: No action is performed.<br>- **1**: enter sleep mode automatically.<br>- **2**: forcibly enter sleep mode.<br>- **3**: enter sleep mode. This policy does not take effect currently.<br>- **4**: power off.<br>If **item** is **eyeComfort**, **value** is a string indicating the status of the eye comfort mode.<br>- **on**: The eye comfort mode is enabled all day.<br>- **off**: The eye comfort mode is disabled.<br>- **unknown**: other modes. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed.The application does not have the permission required to call the API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

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

