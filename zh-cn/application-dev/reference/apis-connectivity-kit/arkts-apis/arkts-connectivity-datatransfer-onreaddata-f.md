# onReadData

## 导入模块

```TypeScript
import { dataTransfer } from '@kit.ConnectivityKit';
```

## onReadData

```TypeScript
function onReadData(callback: Callback<DataParams>): void
```

订阅端口通道数据接收事件。使用callback异步回调。

应用需具备ohos.permission.ACCESS_NEARLINK权限，方可接收此事件上报。调用此接口前，您可以调用[isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md)查询设备是否支持星闪。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-dataTransfer-function onReadData(callback: Callback<DataParams>): void--><!--Device-dataTransfer-function onReadData(callback: Callback<DataParams>): void-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**参见：** [offReadData](arkts-connectivity-datatransfer-offreaddata-f.md#offreaddata-1) 取消订阅端口通道数据接收事件。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[DataParams](arkts-connectivity-datatransfer-dataparams-i.md)&gt; | 是 | 回调函数，返回端口通道接收到的数据参数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. Possible causes:         1. The hardware does not support the capability;         2. The chip does not support the capability;         3. A dependent service feature is not supported. |
| [36100099](../errorcode-nearlink-service.md#36100099-操作失败) | Operation failed. |
