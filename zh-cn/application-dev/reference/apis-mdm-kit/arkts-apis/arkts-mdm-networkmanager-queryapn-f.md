# queryApn

## queryApn

```TypeScript
function queryApn(admin: Want, apnInfo: Record<string, string>): Array<string>
```

查询符合特定APN信息的APN ID。适用于企业移动网络配置审计场景，例如查找特定配置的APN、验证APN配置是否存在、为APN管理操作提供APN ID参数，帮助企业查找和管理APN配置，为APN的更新和删除操作提供必要的参数信 息。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** -1

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APN

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-networkManager-function queryApn(admin: Want, apnInfo: Record<string, string>): Array<string>--><!--Device-networkManager-function queryApn(admin: Want, apnInfo: Record<string, string>): Array<string>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| apnInfo | Record&lt;string, string&gt; | 是 | APN的查询条件。设置后系统将根据这些条件筛选匹配的APN配置，返回符合条件的APN ID列表。&lt;br/&gt;- apnName：APN配置的名称 标识符，可选。&lt;br/&gt;- mcc：3位数字的移动国家代码，可选。&lt;br/&gt;- mnc：2-3位数字的移动网络代码，可选。&lt;br/&gt;- apn：接入点名称，可选。&lt;br/&gt;- type：APN的服务类型，可选。&lt;br/&gt;- user：APN身份验证的用户名，可选。&lt;br/&gt;- proxy：普通数据连接的代理服务器地址，可选。&lt;br/&gt;- mmsproxy：彩信服务的专用代理地址，可选。&lt;br/&gt;- authType：APN的认证协议类型，可 选。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | 满足要求的APN ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |

## 示例

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
  let queryResult: Array<string> = networkManager.queryApn(wantTemp, apnInfo);
  console.info(`Succeeded in querying apn, result : ${JSON.stringify(queryResult)}`);
} catch (err) {
  console.error(`Failed to query apn. Code: ${err.code}, message: ${err.message}`);
}
```


## queryApn

```TypeScript
function queryApn(admin: Want, apnId: string): Record<string, string>
```

查询特定APN的APN参数信息。适用于企业移动网络配置审计场景，例如检查特定APN的配置参数、验证APN配置是否正确、审计移动网络接入点配置，帮助企业审核和验证APN配置，确保移动网络配置符合要求。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** -1

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APN

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-networkManager-function queryApn(admin: Want, apnId: string): Record<string, string>--><!--Device-networkManager-function queryApn(admin: Want, apnId: string): Record<string, string>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | 是 | 企业设备管理扩展组件。Want中必须包含企业设备管理扩展能力的abilityName和所在应用的bundleName。 |
| apnId | string | 是 | 指定的APN ID。设置后将查询该APN ID对应的详细参数配置信息。可以通过 [networkManager.queryApn](#queryApn)获取设备信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Record&lt;string, string&gt; | 指定APN ID的APN参数信息。&lt;br/&gt;- apnName：APN配置的名称标识符。&lt;br/&gt;- mcc：3位数字的移动国家代码。&lt;br/&gt;- mnc：2 -3位数字的移动网络代码。&lt;br/&gt;- apn：接入点名称。&lt;br/&gt;- type：APN的服务类型。&lt;br/&gt;- user：APN身份验证的用户名。&lt;br/&gt;- proxy：普通数据连接的代理服务器地址。&lt;br/&gt;- mmsproxy：彩信服务的专用代理地址。&lt;br/&gt;- authType：APN的认证协议类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |

## 示例

```TypeScript
import { Want } from '@kit.AbilityKit';
import { networkManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // 需根据实际情况进行替换
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility',
};
let apnId: string = "1"; // 需根据实际情况进行替换
try {
  let queryResult: Record<string, string> = networkManager.queryApn(wantTemp, apnId);
  console.info(`Succeeded in querying apn, result : ${JSON.stringify(queryResult)}`);
} catch (err) {
  console.error(`Failed to query apn. Code: ${err.code}, message: ${err.message}`);
}
```

