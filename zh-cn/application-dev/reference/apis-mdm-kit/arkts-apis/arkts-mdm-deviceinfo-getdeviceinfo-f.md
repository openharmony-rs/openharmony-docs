# getDeviceInfo

## 导入模块

```TypeScript
import { deviceInfo } from '@kit.MDMKit';
```

## getDeviceInfo

```TypeScript
function getDeviceInfo(admin: Want, label: string): string
```

获取设备信息。

**起始版本：** 12

**需要权限：** ohos.permission.ENTERPRISE_GET_DEVICE_INFO

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 企业设备管理扩展组件，用于指定具有设备管理能力的目标应用。Want对象中必须包含abilityName（扩展能力名称）和bundleName（应用包名）两个必填字段。 |
| label | string | 是 | 支持获取的设备信息标签。   - deviceName：设备名称。   - deviceSerial：设备序列号。   - simInfo：SIM卡信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Device information obtained. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200007](../errorcode-enterpriseDeviceManager.md#9200007-系统服务工作异常) | The system ability works abnormally. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

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
