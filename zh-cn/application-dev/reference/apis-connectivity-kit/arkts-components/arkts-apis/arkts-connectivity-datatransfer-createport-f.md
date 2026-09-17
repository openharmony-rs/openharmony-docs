# createPort

## 导入模块

```TypeScript
import { dataTransfer } from '@kit.ConnectivityKit';
```

## createPort

```TypeScript
function createPort(uuid: string): void
```

注册端口通道。端口通道注册后方可用于连接远端设备，不再使用时需通过[dataTransfer.destroyPort](arkts-connectivity-datatransfer-destroyport-f.md)销毁。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uuid | string | 是 | 星闪服务UUID，长度必须为36个字符，由32个十六进制数字和4个连字符（-）组成，例如： FFFFFFFF-1234-5678-ABCD-000000001234，表示一个128位标识符。 不允许使用星闪标准UUID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported because the chip does not support it. |
| [36100003](../errorcode-nearlink-service.md#36100003-星闪关闭) | NearLink disabled. |
| [36100020](../errorcode-nearlink-service.md#36100020-端口重复注册) | The UUID is already registered. |
| [36100021](../errorcode-nearlink-service.md#36100021-端口注册数量超出上限) | Port exceeds the upper limit. |
| [36100043](../errorcode-nearlink-service.md#36100043-无效uuid) | Invalid UUID. |
| [36100044](../errorcode-nearlink-service.md#36100044-禁止使用星闪标准服务uuid) | NearLink standard UUID not allowed. |
| [36100099](../errorcode-nearlink-service.md#36100099-操作失败) | Operation failed. |
