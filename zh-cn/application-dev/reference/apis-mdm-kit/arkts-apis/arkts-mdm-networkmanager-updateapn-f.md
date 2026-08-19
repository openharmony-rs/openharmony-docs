# updateApn

## 导入模块

```TypeScript
import { networkManager } from '@kit.MDMKit';
```

## updateApn

```TypeScript
function updateApn(admin: Want, apnInfo: Record<string, string>, apnId: string): void
```

更新APN。适用于企业移动网络配置管理场景，例如修改APN配置参数、调整运营商设置、优化移动网络连接性能，帮助企业灵活调整移动网络配置，确保设备移动网络连接参数符合实际需求。

**起始版本：** 20

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APN

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-networkManager-function updateApn(admin: Want, apnInfo: Record<string, string>, apnId: string): void--><!--Device-networkManager-function updateApn(admin: Want, apnInfo: Record<string, string>, apnId: string): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| apnInfo | Record&lt;string, string&gt; | 是 | 需要更新的APN参数信息。设置后系统将使用更新后的参数修改对应APN配置，影响网络连接方式和数据传输路径。<br/>- apnName：APN 配置的名称标识符，可选。<br/>- mcc：3位数字的移动国家代码，可选。<br/>- mnc：2-3位数字的移动网络代码，可选。<br/>- APN：接入点名称，可选。<br/>- type：APN的服务类型，可选。&lt; br/&gt;- user：APN身份验证的用户名，可选。<br/>- password：APN身份验证的密码，可选。<br/>- proxy：普通数据连接的代理服务器地址，可选。<br/>- mmsproxy：彩信服务的专用代 理地址，可选。<br/>- authType：APN的认证协议类型，可选。 |
| apnId | string | 是 | 需要更新的APN ID。可以通过[networkManager.queryApn](arkts-mdm-networkmanager-queryapn-f.md)获取设备APN信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |

**示例**

```TypeScript
import { Want } from '@kit.AbilityKit';
import { networkManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
let apnInfo: Record<string, string> = {
  // 需根据实际情况进行替换
  "apnName": "CTNET",
  "apn": "CTNET",
  "mnc": "11",
  "mcc": "460"
};
let apnId: string = "1"; // 需根据实际情况进行替换
try {
  networkManager.updateApn(wantTemp, apnInfo, apnId);
  console.info(`Succeeded in updating apn.`);
} catch (err) {
  console.error(`Failed to update apn. Code: ${err.code}, message: ${err.message}`);
}
```

