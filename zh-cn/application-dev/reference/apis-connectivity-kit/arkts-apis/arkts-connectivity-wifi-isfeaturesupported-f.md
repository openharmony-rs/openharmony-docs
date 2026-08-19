# isFeatureSupported

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
import { wifiext } from '@kit.ConnectivityKit';
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## isFeatureSupported

```TypeScript
function isFeatureSupported(featureId: number): boolean
```

判断设备是否支持相关WLAN特性。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [isFeatureSupported](arkts-connectivity-wifimanager-isfeaturesupported-f.md)

**需要权限：** ohos.permission.GET_WIFI_INFO

<!--Device-wifi-function isFeatureSupported(featureId: number): boolean--><!--Device-wifi-function isFeatureSupported(featureId: number): boolean-End-->

**系统能力：** SystemCapability.Communication.WiFi.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| featureId | number | 是 | 特性ID值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true:支持，false:不支持。 |

**示例**

```TypeScript
import wifi from '@ohos.wifi';

try {
  let featureId = 0;
  let ret = wifi.isFeatureSupported(featureId);
  console.info("isFeatureSupported:" + ret);
}catch(error){
  console.error("failed:" + JSON.stringify(error));
}
```

