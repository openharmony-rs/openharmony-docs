# getDefaultApplicationBundleName

## 导入模块

```TypeScript
import { bundleManager } from '@kit.MDMKit';
```

## getDefaultApplicationBundleName

```TypeScript
function getDefaultApplicationBundleName(type: DefaultApplicationType, accountId: number): string
```

**起始版本：** 26.1.0

**需要权限：** ohos.permission.ENTERPRISE_INSTALL_BUNDLE

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-bundleManager-function getDefaultApplicationBundleName(type: DefaultApplicationType, accountId: number): string--><!--Device-bundleManager-function getDefaultApplicationBundleName(type: DefaultApplicationType, accountId: number): string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [DefaultApplicationType](arkts-mdm-bundlemanager-defaultapplicationtype-e.md) | 是 | Type of the default application. |
| accountId | number | 是 | User ID, which must be greater than or equal to 0. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | Returns the bundle name of the default application. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-参数校验失败) | Parameter verification failed. |
| [9200016](../errorcode-enterpriseDeviceManager.md#9200016-服务超时) | Service timeout. |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
