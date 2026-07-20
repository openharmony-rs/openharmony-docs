# getIpAddressSync

## 导入模块

```TypeScript
import { networkManager } from '@kit.MDMKit';
```

<a id="getipaddresssync"></a>
## getIpAddressSync

```TypeScript
function getIpAddressSync(admin: Want, networkInterface: string): string
```

根据网络接口获取设备IP地址。

**起始版本：** 12

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_NETWORK

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-networkManager-function getIpAddressSync(admin: Want, networkInterface: string): string--><!--Device-networkManager-function getIpAddressSync(admin: Want, networkInterface: string): string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| networkInterface | string | 是 | 指定网络接口。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回设备指定网络接口的IP地址。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |

**示例：**

```TypeScript
import { networkManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // 参数需根据实际情况进行替换
  let result: string = networkManager.getIpAddressSync(wantTemp, 'eth0');
  console.info(`Succeeded in getting ip address, result : ${result}`);
} catch (err) {
  console.error(`Failed to get ip address. Code: ${err.code}, message: ${err.message}`);
}

```

