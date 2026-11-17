# addOptimizationBatteryExclusionApps

## 导入模块

```TypeScript
import { applicationManager } from '@kit.MDMKit';
```

## addOptimizationBatteryExclusionApps

```TypeScript
function addOptimizationBatteryExclusionApps(appIdentifiers: Array<string>, accountId: number): void
```

添加应用至电池优化排除列表。使用异步回调返回结果。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-applicationManager-function addOptimizationBatteryExclusionApps(appIdentifiers: Array<string>, accountId: number): void--><!--Device-applicationManager-function addOptimizationBatteryExclusionApps(appIdentifiers: Array<string>, accountId: number): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appIdentifiers | Array&lt;string&gt; | 是 | 待添加应用的唯一标识符。 |
| accountId | number | 是 | 用户账号ID。<br>取值应≥0。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200006](../errorcode-enterpriseDeviceManager.md#9200006-指定的用户id非法) | The specified account ID is invalid. |
| [9200016](../errorcode-enterpriseDeviceManager.md#9200016-服务超时) | Service timeout. |
| [9200019](../errorcode-enterpriseDeviceManager.md#9200019-策略列表超限) | The policy list has exceeded the limit. |
| [9201015](../errorcode-enterpriseDeviceManager.md#9201015-指定应用未安装) | The application is not installed. |
