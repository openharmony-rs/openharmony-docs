# getSupportedFeatures（系统接口）

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## getSupportedFeatures

```TypeScript
function getSupportedFeatures(): number
```

查询设备支持的特性。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [getSupportedFeatures](arkts-connectivity-wifimanager-getsupportedfeatures-f-sys.md)

**需要权限：** ohos.permission.GET_WIFI_INFO

**系统能力：** SystemCapability.Communication.WiFi.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 支持的特性值。特性值枚举：<br>- 0x0001: 基础结构模式特性。<br>- 0x0002: 5 GHz带宽特性。<br>- 0x0004: GAS/ANQP特性。<br>- 0x0008: Wifi-Direct特性。<br>- 0x0010: Soft AP特性。<br>- 0x0040: Wi-Fi Aware组网特性。<br>- 0x8000: AP STA共存特性。<br>- 0x8000000: WPA3-Personal SAE特性。<br>- 0x10000000: WPA3-Enterprise Suite-B。<br>- 0x20000000: 增强开放特性。 |
