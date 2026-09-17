# scan

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## scan

```TypeScript
function scan(): boolean
```

启动Wi-Fi扫描。

> **说明：** 
> 
> 从API version 6开始支持，从API version 9开始废弃。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [scan](arkts-connectivity-wifimanager-scan-f.md)

**需要权限：** ohos.permission.SET_WIFI_INFO and ohos.permission.LOCATION

**系统能力：** SystemCapability.Communication.WiFi.STA

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true:扫描操作执行成功， false:扫描操作执行失败。 |

**示例**

```TypeScript
import wifi from '@ohos.wifi';

try {
  wifi.scan();
}catch(error){
  console.error("failed:" + JSON.stringify(error));
}
```
