# enableEthernetInterface（系统接口）

## 导入模块

```TypeScript
import { ethernet } from '@kit.NetworkKit';
```

## enableEthernetInterface

```TypeScript
function enableEthernetInterface(): Promise<void>
```

启用以太网接口。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.CONNECTIVITY_INTERNAL

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ethernet-function enableEthernetInterface(): Promise<void>--><!--Device-ethernet-function enableEthernetInterface(): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Ethernet

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 启用以太网接口成功返回的Promise。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2200003](../errorcode-net-ethernet.md#2200003-系统内部错误) | System internal error. |
| [2200002](../errorcode-net-ethernet.md#2200002-连接服务失败) | Failed to connect to the service. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |

