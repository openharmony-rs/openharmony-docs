# getSmsMessages

## 导入模块

```TypeScript
import { telephonyManager } from '@kit.MDMKit';
```

## getSmsMessages

```TypeScript
function getSmsMessages(queryConfig: TelephonyQueryConfig): Promise<Array<SmsMessageInfo>>
```

根据指定的时间范围和电话号码查询短信消息。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.ENTERPRISE_READ_MESSAGES

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-telephonyManager-function getSmsMessages(queryConfig: TelephonyQueryConfig): Promise<Array<SmsMessageInfo>>--><!--Device-telephonyManager-function getSmsMessages(queryConfig: TelephonyQueryConfig): Promise<Array<SmsMessageInfo>>-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| queryConfig | [TelephonyQueryConfig](arkts-mdm-telephonymanager-telephonyqueryconfig-i.md) | 是 | 查询选项，包括时间范围和电话号码。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[SmsMessageInfo](arkts-mdm-telephonymanager-smsmessageinfo-i.md)&gt;&gt; | Promise对象，返回符合查询条件的短信消息列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200016](../errorcode-enterpriseDeviceManager.md#9200016-服务超时) | Service timeout. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-参数校验失败) | Parameter verification failed. |
