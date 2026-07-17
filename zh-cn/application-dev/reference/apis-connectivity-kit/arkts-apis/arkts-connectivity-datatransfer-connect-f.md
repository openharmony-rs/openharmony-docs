# connect

## 导入模块

```TypeScript
import { dataTransfer } from '@kit.ConnectivityKit';
```

## connect

```TypeScript
function connect(params: ConnectionParams): Promise<void>
```

连接服务端。如果连接成功，则可以向服务端发送数据。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-dataTransfer-function connect(params: ConnectionParams): Promise<void>--><!--Device-dataTransfer-function connect(params: ConnectionParams): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [ConnectionParams](arkts-connectivity-datatransfer-connectionparams-i.md) | 是 | 连接参数 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | 返回promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported because the chip does not support it. |
| 36100003 | NearLink disabled. |
| 36100041 | Invalid address. |
| 36100043 | Invalid UUID. |
| 36100044 | NearLink standard UUID not allowed. |
| 36100099 | Operation failed. |

