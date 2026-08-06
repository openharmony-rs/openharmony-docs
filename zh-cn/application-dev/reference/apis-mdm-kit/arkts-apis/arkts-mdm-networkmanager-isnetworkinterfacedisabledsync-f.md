# isNetworkInterfaceDisabledSync

## isNetworkInterfaceDisabledSync

```TypeScript
function isNetworkInterfaceDisabledSync(admin: Want, networkInterface: string): boolean
```

查询指定网络接口是否被禁用。适用于企业网络管理场景，例如检查网络接口状态、审计网络接口使用情况、验证网络策略执行效果，帮助企业确认网络接口管理策略是否生效，便于策略调整和问题排查。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_NETWORK

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-networkManager-function isNetworkInterfaceDisabledSync(admin: Want, networkInterface: string): boolean--><!--Device-networkManager-function isNetworkInterfaceDisabledSync(admin: Want, networkInterface: string): boolean-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| networkInterface | string | 是 | 指定网络接口。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回指定网络接口是否被禁用，true表示该网络接口被禁用，false表示该网络接口未被禁用。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types; 3. Parameter verification failed. |


## isNetworkInterfaceDisabledSync

```TypeScript
function isNetworkInterfaceDisabledSync(admin: Want | null, networkInterface: string): boolean
```

查询指定网络接口是否被禁用。适用于企业网络管理场景，例如检查网络接口状态、审计网络接口使用情况、验证网络策略执行效果，帮助企业确认网络接口管理策略是否生效，便于策略调整和问题排查。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_NETWORK

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-networkManager-function isNetworkInterfaceDisabledSync(admin: Want | null, networkInterface: string): boolean--><!--Device-networkManager-function isNetworkInterfaceDisabledSync(admin: Want | null, networkInterface: string): boolean-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| null | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。当设备存在多个MDM应用时，传入Want时查询对应企业设备管理应用设置的策略，传入null时查询实际生效的策略。 |
| networkInterface | string | 是 | 指定网络接口。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回指定网络接口是否被禁用，true表示该网络接口被禁用，false表示该网络接口未被禁用。 |

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
  let result: boolean = networkManager.isNetworkInterfaceDisabledSync(wantTemp, 'eth0');
  console.info(`Succeeded in querying network interface is disabled or not, result : ${result}`);
} catch (err) {
  console.error(`Failed to query network interface is disabled or not. Code: ${err.code}, message: ${err.message}`);
}
```

