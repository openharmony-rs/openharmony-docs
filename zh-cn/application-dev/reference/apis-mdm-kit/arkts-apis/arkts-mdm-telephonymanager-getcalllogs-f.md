# getCallLogs

## 导入模块

```TypeScript
import { telephonyManager } from '@kit.MDMKit';
```

## getCallLogs

```TypeScript
function getCallLogs(queryConfig: TelephonyQueryConfig): Promise<Array<CallLogInfo>>
```

根据指定的时间范围和电话号码查询通话记录。企业MDM应用可通过此接口读取设备通话记录进行审计。支持按时间范围和号码进行筛选查询。查询时间范围不能超过31天，号码采用完全匹配。通话记录最多保存5000条，超过时自动删除最早的记录。该接口使用Promise方式异步返回结果。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.ENTERPRISE_READ_CALL_LOG

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-telephonyManager-function getCallLogs(queryConfig: TelephonyQueryConfig): Promise<Array<CallLogInfo>>--><!--Device-telephonyManager-function getCallLogs(queryConfig: TelephonyQueryConfig): Promise<Array<CallLogInfo>>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| queryConfig | [TelephonyQueryConfig](arkts-mdm-telephonymanager-telephonyqueryconfig-i.md) | 是 | 查询配置，包括时间范围和电话号码。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[CallLogInfo](arkts-mdm-telephonymanager-callloginfo-i.md)&gt;&gt; | Promise对象，返回符合查询条件的通话记录列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-参数校验失败) | Parameter verification failed. |
| [9200016](../errorcode-enterpriseDeviceManager.md#9200016-服务超时) | Service timeout. |
