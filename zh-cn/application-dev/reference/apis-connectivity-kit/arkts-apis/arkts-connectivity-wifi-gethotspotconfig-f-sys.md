# getHotspotConfig（系统接口）

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## getHotspotConfig

```TypeScript
function getHotspotConfig(): HotspotConfig
```

获取热点配置信息。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [getHotspotConfig](arkts-connectivity-wifimanager-gethotspotconfig-f-sys.md)

**需要权限：** ohos.permission.GET_WIFI_INFO and ohos.permission.GET_WIFI_CONFIG

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| HotspotConfig | 热点的配置信息。 |

**示例**

```TypeScript
import wifi from '@ohos.wifi';

try {
    let config = wifi.getHotspotConfig();
    console.info("result:" + JSON.stringify(config));        
}catch(error){
    console.error("failed:" + JSON.stringify(error));
}
```
