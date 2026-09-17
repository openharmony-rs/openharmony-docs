# getSupportedFeatures（系统接口）

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## getSupportedFeatures

```TypeScript
function getSupportedFeatures(): number
```

查询设备支持的特性。

**起始版本：** 9

**需要权限：** ohos.permission.GET_WIFI_INFO

**系统能力：** SystemCapability.Communication.WiFi.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 支持的特性值。枚举值如下：<br>- 0x0001: 基础结构模式特性。<br>- 0x0002: 5 GHz带宽特性。<br>- 0x0004: GAS/ANQP特性。<br>- 0x 0008: WiFi-Direct特性。<br>- 0x0010: Soft AP特性。<br>- 0x0040: Wi-Fi Aware组网特性。<br>- 0x8000: AP STA共存特性。<br>- 0x 8000000: WPA3-Personal SAE特性。<br>- 0x10000000: WPA3-Enterprise Suite-B。<br>- 0x20000000: 增强开放特性。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | System API is not allowed called by Non-system application. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2401000](../errorcode-wifi.md#2401000-sta内部异常) | Operation failed. |

**示例**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';

try {
    let ret = wifiManager.getSupportedFeatures();
    console.info("supportedFeatures:" + ret);
} catch (error) {
    console.error("failed:" + JSON.stringify(error));
}
```
