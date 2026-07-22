# addApn

## 导入模块

```TypeScript
import { networkManager } from '@kit.MDMKit';
```

## addApn

```TypeScript
function addApn(admin: Want, apnInfo: Record<string, string>): void
```

添加APN（Access Point Name，接入点名称）。

**起始版本：** 20

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APN

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-networkManager-function addApn(admin: Want, apnInfo: Record<string, string>): void--><!--Device-networkManager-function addApn(admin: Want, apnInfo: Record<string, string>): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-arkui/arkts-apis/arkts-arkui-want-t-sys.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| apnInfo | Record&lt;string, string&gt; | 是 | 需要添加的APN参数信息。<br/>- apnName：APN配置的名称标识符，必选。<br/>- mcc：3位数字的移动国家代码，必选。<br/>- mnc：2-3位数字的移动网络代码，必选。<br/>- apn：接入点名称，必选。<br/>- type：APN的服务类型，可选。<br/>- user：APN身份验证的用户名，可选。<br/>-password：APN身份验证的密码，可选。<br/>- proxy：普通数据连接的代理服务器地址，可选。<br/>- mmsproxy：彩信服务的专用代理地址，可选。<br/>- authType：APN的认证协议类型，可选。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |

**示例：**

```TypeScript
import { Want } from '@kit.AbilityKit';
import { networkManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility',
};
let apnInfo: Record<string, string> = {
  // 需根据实际情况进行替换
  "apnName": "CTNET",
  "apn": "CTNET",
  "mnc": "11",
  "mcc": "460",
};
try {
  networkManager.addApn(wantTemp, apnInfo);
  console.info(`Succeeded in adding apn.`);
} catch (err) {
  console.error(`Failed to add apn. Code: ${err.code}, message: ${err.message}`);
}

```

