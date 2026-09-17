# isFeatureSupported

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## isFeatureSupported

```TypeScript
function isFeatureSupported(featureId: number): boolean
```

判断设备是否支持指定的Wi-Fi特性。

**起始版本：** 9

**需要权限：** ohos.permission.GET_WIFI_INFO

**系统能力：** SystemCapability.Communication.WiFi.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| featureId | number | 是 | 特性ID值。枚举值如下：<br>- 0x0001: 基础结构模式特性。<br>- 0x0002: 5 GHz带宽特性。<br>- 0x0004: GAS/ANQP特性。<br>- 0x0008: Wifi-Direct特性。<br>- 0x0010: Soft AP特性。<br>- 0x0040: Wi-Fi AWare组网特性。<br>- 0x8000: AP STA共存特性。<br>- 0x8000000: WPA3-Personal SAE特性。<br>- 0x10000000: WPA3-Enterprise Suite-B。<br>- 0x20000000: 增强开放特性。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true:支持， false:不支持。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2401000](../errorcode-wifi.md#2401000-sta内部异常) | Operation failed. |

**示例**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';

  try {
    let featureId = 0;
    let ret = wifiManager.isFeatureSupported(featureId);
    console.info("isFeatureSupported:" + ret);
  }catch(error){
    console.error("failed:" + JSON.stringify(error));
  }
```
