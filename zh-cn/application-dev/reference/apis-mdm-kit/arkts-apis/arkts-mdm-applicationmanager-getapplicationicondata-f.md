# getApplicationIconData

## 导入模块

```TypeScript
import { applicationManager } from '@kit.MDMKit';
```

## getApplicationIconData

```TypeScript
function getApplicationIconData(bundleName: string): string
```

获取应用的图标数据。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-applicationManager-function getApplicationIconData(bundleName: string): string--><!--Device-applicationManager-function getApplicationIconData(bundleName: string): string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bundleName | string | 是 | 应用的Bundle名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 应用的Base64编码的图标数据。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200016](../errorcode-enterpriseDeviceManager.md#9200016-服务超时) | Service timeout. |
| [9201015](../errorcode-enterpriseDeviceManager.md#9201015-指定应用未安装) | The application is not installed. |
