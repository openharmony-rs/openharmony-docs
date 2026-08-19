# getGlobalProxyForAccount

## 导入模块

```TypeScript
import { networkManager } from '@kit.MDMKit';
```

## getGlobalProxyForAccount

```TypeScript
function getGlobalProxyForAccount(admin: Want | null, accountId: number): connection.HttpProxy
```

获取指定用户下的网络代理。适用于企业多用户环境下的网络管理场景，例如审计用户级网络代理配置、验证用户网络访问策略、排查用户网络访问问题，帮助企业检查和验证用户级网络管理策略。 > **说明：** > > 本接口用于获取通过setGlobalProxyForAccount设置的、指定用户的代理配置。如果需要获取应用于所有用户的全局代理配置，建议使用 > [getGlobalProxySync](arkts-mdm-networkmanager-getglobalproxysync-f.md)接口。

**起始版本：** 15

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_NETWORK

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-networkManager-function getGlobalProxyForAccount(admin: Want | null, accountId: number): connection.HttpProxy--><!--Device-networkManager-function getGlobalProxyForAccount(admin: Want | null, accountId: number): connection.HttpProxy-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) \| null | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。<br>**起始版本：** 20 |
| accountId | number | 是 | 用户ID，取值范围：大于等于0。 <br> accountId可以通过@ohos.account.osAccount中的 [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid)等接口来获取。*@ohos.account.osAccount** to obtain the user ID. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| connection.HttpProxy | 网络代理配置信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. Failed to call the API due to limited device capabilities.<br>**适用版本：** 20+ |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |

**示例**

```TypeScript
import { networkManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';
import { connection } from '@kit.NetworkKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // 参数需根据实际情况进行替换
  let result: connection.HttpProxy = networkManager.getGlobalProxyForAccount(wantTemp, 100);
  console.info(`Succeeded in getting network global proxy, result : ${JSON.stringify(result)}`);
} catch (err) {
  console.error(`Failed to get network global proxy. Code: ${err.code}, message: ${err.message}`);
}
```

