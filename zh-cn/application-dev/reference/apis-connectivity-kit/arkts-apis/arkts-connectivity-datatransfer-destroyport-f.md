# destroyPort

## 导入模块

```TypeScript
import { dataTransfer } from '@kit.ConnectivityKit';
```

## destroyPort

```TypeScript
function destroyPort(uuid: string): void
```

销毁端口通道。调用此接口前，您可以调用[isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md)查询设备是否支持星闪。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.1.0开始，该接口支持在原子化服务中使用。

<!--Device-dataTransfer-function destroyPort(uuid: string): void--><!--Device-dataTransfer-function destroyPort(uuid: string): void-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**参见：** [createPort](arkts-connectivity-datatransfer-createport-f.md#createport-1) 注册端口通道。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uuid | string | 是 | 星闪服务UUID，长度必须为36个字符，由32个十六进制数字和4个连字符（-）组成，例如： FFFFFFFF-1234-5678-ABCD-000000001234，表示一个128位标识符。 不允许使用星闪标准UUID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. Possible causes:         1. The hardware does not support the capability;         2. The chip does not support the capability;         3. A dependent service feature is not supported. |
| [36100003](../errorcode-nearlink-service.md#36100003-星闪关闭) | NearLink disabled. |
| [36100022](../errorcode-nearlink-service.md#36100022-端口未注册) | The UUID is not registered. |
| [36100043](../errorcode-nearlink-service.md#36100043-无效uuid) | Invalid UUID. |
| [36100044](../errorcode-nearlink-service.md#36100044-禁止使用星闪标准服务uuid) | NearLink standard UUID not allowed. |
| [36100099](../errorcode-nearlink-service.md#36100099-操作失败) | Operation failed. |
