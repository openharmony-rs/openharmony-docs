# getAllowedBluetoothDevices

## 导入模块

```TypeScript
import { bluetoothManager } from '@kit.MDMKit';
```

## getAllowedBluetoothDevices

```TypeScript
function getAllowedBluetoothDevices(admin: Want): Array<string>
```

获取蓝牙设备可用名单。

**起始版本：** 12

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-bluetoothManager-function getAllowedBluetoothDevices(admin: Want): Array<string>--><!--Device-bluetoothManager-function getAllowedBluetoothDevices(admin: Want): Array<string>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | 可用名单中蓝牙设备MAC地址的数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |

**示例**

```TypeScript
import { bluetoothManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

// 创建企业设备管理扩展组件
let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
try {
  // 获取蓝牙设备允许名单
  let result: Array<string> = bluetoothManager.getAllowedBluetoothDevices(wantTemp);
  console.info(`Succeeded in getting allowed bluetooth devices. Result: ${JSON.stringify(result)}`);
} catch (err) {
  console.error(`Failed to get allowed bluetooth devices. Code: ${err.code}, message: ${err.message}`);
}
```


## getAllowedBluetoothDevices

```TypeScript
function getAllowedBluetoothDevices(admin: Want | null): Array<string>
```

获取蓝牙设备可用名单。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_BLUETOOTH

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-bluetoothManager-function getAllowedBluetoothDevices(admin: Want | null): Array<string>--><!--Device-bluetoothManager-function getAllowedBluetoothDevices(admin: Want | null): Array<string>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) \| null | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 当设备存在多个MDM应用时，传入Want时查询对应企业设备管理应用设置的策略，传入null时查询实际生效的策略。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | 可用名单中蓝牙设备MAC地址的数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |

**示例**

```TypeScript
import { bluetoothManager } from '@kit.MDMKit';

// 创建企业设备管理扩展组件
try {
  // 获取蓝牙设备允许名单
  // 参数需根据实际情况进行替换
  let result: Array<string> = bluetoothManager.getAllowedBluetoothDevices(null);
  console.info(`Succeeded in getting allowed bluetooth devices. Result: ${JSON.stringify(result)}`);
} catch(err) {
  console.error(`Failed to get allowed bluetooth devices. Code: ${err.code}, message: ${err.message}`);
}
```

