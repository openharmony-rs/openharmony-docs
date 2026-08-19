# getValue

## 导入模块

```TypeScript
import { deviceSettings } from '@kit.MDMKit';
```

## getValue

```TypeScript
function getValue(admin: Want, item: string): string
```

获取设备设置策略。

**起始版本：** 12

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SETTINGS

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-deviceSettings-function getValue(admin: Want, item: string): string--><!--Device-deviceSettings-function getValue(admin: Want, item: string): string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| item | string | 是 | 设备设置策略类型。<br/>- screenOff：设备息屏策略，对于PC/2in1设备，支持查询电池供电下的设备息屏策略。<br/>- powerPolicy：设备电源策略，仅对 PC/2in1设备生效，仅支持查询电池供电下的设备电源策略。<br/>- eyeComfort：从API version 23开始支持，护眼模式开关状态。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 策略类型值。<br/>当item为screenOff时，返回设备息屏时间（单位：毫秒），对于PC/2in1设备，返回设备电池供电下的息屏时间（单位：毫秒）。<br/>当item为 powerPolicy时，返回电源策略，对于PC/2in1设备，返回设备电池供电下的电源策略，格式为JSON字符串:{"powerScene":xx,"powerPolicy":{"powerPolicyAction": xx,"delayTime":xx}}。powerScene为电源策略场景；delayTime为延迟时间（单位：毫秒）；powerPolicyAction为休眠策略。<br/>电源策略场景：<br/>- 0：超时场景。&lt; br/&gt;休眠策略：<br/>- 0：不执行动作。<br/>- 1：自动进入睡眠。<br/>- 2：强制进入睡眠。<br/>- 3：进入休眠，该策略暂不生效。<br/>- 4：关机。<br/>当item为eyeComfort 时，返回的value为护眼模式开关状态的字符串。<br/>- on：全天开启护眼模式。<br/>- off：关闭护眼模式。<br/>- unknown：其他模式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |

**示例**

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

