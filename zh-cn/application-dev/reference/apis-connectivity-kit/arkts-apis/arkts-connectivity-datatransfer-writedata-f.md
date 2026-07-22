# writeData

## 导入模块

```TypeScript
import { dataTransfer } from '@kit.ConnectivityKit';
```

## writeData

```TypeScript
function writeData(params: DataParams): Promise<void>
```

根据地址和UUID写入数据。

**起始版本：** 26.0.0

**需要权限：** ohos.permission.ACCESS_NEARLINK

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-dataTransfer-function writeData(params: DataParams): Promise<void>--><!--Device-dataTransfer-function writeData(params: DataParams): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NearLink.Base

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | [DataParams](arkts-connectivity-datatransfer-dataparams-i.md) | 是 | 发送数据的参数 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 返回promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported because the chip does not support it. |
| [36100003](../errorcode-nearlink.md#36100003--星闪关闭) | NearLink disabled. |
| [36100023](../errorcode-nearlink.md#36100023-数据传输拥塞) | Write data congestion. |
| [36100041](../errorcode-nearlink.md#36100041-无效地址) | Invalid address. |
| [36100043](../errorcode-nearlink.md#36100043-无效uuid) | Invalid UUID. |
| [36100044](../errorcode-nearlink.md#36100044-禁止使用星闪标准服务uuid) | NearLink standard UUID not allowed. |
| [36100099](../errorcode-nearlink.md#36100099-操作失败) | Operation failed. |

