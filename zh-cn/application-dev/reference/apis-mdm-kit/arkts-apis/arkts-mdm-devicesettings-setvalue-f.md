# setValue

## 导入模块

```TypeScript
import { deviceSettings } from '@kit.MDMKit';
```

<a id="setvalue"></a>
## setValue

```TypeScript
function setValue(admin: Want, item: string, value: string): void
```

设置设备策略。

**起始版本：** 12

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_SETTINGS

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-deviceSettings-function setValue(admin: Want, item: string, value: string): void--><!--Device-deviceSettings-function setValue(admin: Want, item: string, value: string): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| item | string | 是 | 设备设置策略类型。<br/>- screenOff：设备息屏策略。对于PC/2in1设备，支持设置电池和电源供电下的设备息屏策略。<br/>- dateTime：设置系统时间。<br/>- powerPolicy：设备电源策略。该能力仅支持PC/2in1设备，策略设置之后不刷新设置—电源和电池页面，在手机平板设备设置后不生效。<br/>对于PC/2in1设备，仅支持设置电池供电下的设备电源策略。设置设备超时灭屏时睡眠延迟策略，睡眠动作需要在设置—电源和电池页面显示的睡眠时间之后等待设置的delayTime才会生效。<br/>- eyeComfort：从API version 23开始支持，设置护眼模式开关状态，仅支持全天开启和关闭护眼模式。<br/>- defaultInputMethod：从API version 23开始支持，设置默认输入法。 |
| value | string | 是 | 设备设置策略类型。<br/>- screenOff：设备息屏策略。对于PC/2in1设备，支持设置电池和电源供电下的设备息屏策略。<br/>- dateTime：设置系统时间。<br/>- powerPolicy：设备电源策略。该能力仅支持PC/2in1设备，策略设置之后不刷新设置—电源和电池页面，在手机平板设备设置后不生效。<br/>对于PC/2in1设备，仅支持设置电池供电下的设备电源策略。设置设备超时灭屏时睡眠延迟策略，睡眠动作需要在设置—电源和电池页面显示的睡眠时间之后等待设置的delayTime才会生效。<br/>- eyeComfort：从API version 23开始支持，设置护眼模式开关状态，仅支持全天开启和关闭护眼模式。<br/>- defaultInputMethod：从API version 23开始支持，设置默认输入法。 |

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
  // 需根据实际情况进行替换
  deviceSettings.setValue(wantTemp, 'screenOff', '3000');
  console.info(`Succeeded in setting screen off time.`);
} catch (err) {
  console.error(`Failed to set screen off time. Code: ${err.code}, message: ${err.message}`);
}

```

