# isNetworkInterfaceDisabledSync

## 导入模块

```TypeScript
import { networkManager } from '@kit.MDMKit';
```

## isNetworkInterfaceDisabledSync

```TypeScript
function isNetworkInterfaceDisabledSync(admin: Want, networkInterface: string): boolean
```

查询指定网络接口是否被禁用。

**起始版本：** 12

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_NETWORK

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-networkManager-function isNetworkInterfaceDisabledSync(admin: Want, networkInterface: string): boolean--><!--Device-networkManager-function isNetworkInterfaceDisabledSync(admin: Want, networkInterface: string): boolean-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
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

