# unsubscribeSmsEvent

## 导入模块

```TypeScript
import { adminManager } from '@kit.MDMKit';
```

## unsubscribeSmsEvent

```TypeScript
function unsubscribeSmsEvent(): void
```

取消订阅监听短信事件

**起始版本：** 26.1.0

**需要权限：** ohos.permission.ENTERPRISE_RECEIVE_SMS

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-adminManager-function unsubscribeSmsEvent(): void--><!--Device-adminManager-function unsubscribeSmsEvent(): void-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. Possible causes: <br>1. The hardware does not support the capability. <br>2. The chip does not support the capability. <br>3. A dependent service feature is not supported. |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-应用没有激活成设备管理器) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-设备管理器权限不够) | The administrator application does not have permission to manage the device. |
| [9200016](../errorcode-enterpriseDeviceManager.md#9200016-服务超时) | Service timeout. |
