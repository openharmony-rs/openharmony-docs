# createClient

## 导入模块

```TypeScript
import { ssap } from '@kit.ConnectivityKit';
```

## createClient

```TypeScript
function createClient(address: string): Client
```

创建SSAP客户端实例。调用此接口前，您可以调用[isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md)查询设备是否支持星闪。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-ssap-function createClient(address: string): Client--><!--Device-ssap-function createClient(address: string): Client-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| address | string | 是 | 远端服务端设备地址。地址格式参考：11:22:33:AA:BB:FF。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Client](arkts-connectivity-ssap-client-i.md) | SSAP客户端实例。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. Possible causes:         1. The hardware does not support the capability;         2. The chip does not support the capability;         3. A dependent service feature is not supported. |
| [36100003](../errorcode-nearlink-service.md#36100003-星闪关闭) | NearLink disabled. |
| [36100041](../errorcode-nearlink-service.md#36100041-无效地址) | Invalid address. |
| [36100099](../errorcode-nearlink-service.md#36100099-操作失败) | Operation failed. |
