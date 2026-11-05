# disconnectFromCandidateConfig

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## disconnectFromCandidateConfig

```TypeScript
function disconnectFromCandidateConfig(networkId: number, blockDuration: number): void
```

断开networkId标识的候选网络一段时间。断开的候选网络在阻塞持续时间内不会重新关联。您只能断开由主叫方添加的候选网络。

**起始版本：** 26.1.0

**需要权限：** ohos.permission.SET_WIFI_INFO

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-wifiManager-function disconnectFromCandidateConfig(networkId: int, blockDuration: int): void--><!--Device-wifiManager-function disconnectFromCandidateConfig(networkId: int, blockDuration: int): void-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| networkId | number | 是 | 标识要断开的候选网络。取值必须为大于等于 0 的整数。<br>单位为：秒。取值限定为整数。<br>不合法的值区间: 取值必须为大于等于 0 的整数。<br>单位为：秒。取值限定为整数。 |
| blockDuration | number | 是 | 网络被禁止重新关联的时长，单位为秒。取值必须为整数。如果取值为 -1，则该候选网络被永久禁止重新关联。<br>取值限定为整数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-api权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-api功能在部分设备不支持) | Capability not supported. |
| [2501000](../errorcode-wifi.md#2501000-sta内部异常) | Operation failed, possibly causes: <br>The network identified by networkId does not exist. <br>The candidate network was not added by the caller. <br>The caller is not running in the foreground. |
| [2501001](../errorcode-wifi.md#2501001-sta功能未打开) | Wi-Fi STA disabled. |
