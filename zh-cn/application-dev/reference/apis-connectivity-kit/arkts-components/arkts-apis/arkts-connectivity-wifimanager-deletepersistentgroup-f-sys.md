# deletePersistentGroup（系统接口）

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## deletePersistentGroup

```TypeScript
function deletePersistentGroup(netId: number): void
```

删除指定网络ID的永久Wi-Fi组配置。该接口用于清除已保存的Wi-Fi网络配置信息，使其不再自动连接。

- 根据网络ID删除之前与P2P设备建立的永久组信息，后续与该P2P设备进行P2P连接时需要重新进行P2P协商。

**起始版本：** 9

**需要权限：** ohos.permission.SET_WIFI_INFO and ohos.permission.MANAGE_WIFI_CONNECTION

**系统能力：** SystemCapability.Communication.WiFi.P2P

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| netId | number | 是 | 组的ID。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | System API is not allowed called by Non-system application. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes: 1.Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2801000](../errorcode-wifi.md#2801000-p2p模块异常) | Operation failed. |
| [2801001](../errorcode-wifi.md#2801001-p2p功能未打开) | Wi-Fi STA disabled. |

**示例**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';

try {
  let netId = 0;
  wifiManager.deletePersistentGroup(netId);  
}catch (error) {
  console.error("failed:" + JSON.stringify(error));
}
```
