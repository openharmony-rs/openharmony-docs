# getCountryCode

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## getCountryCode

```TypeScript
function getCountryCode(): string
```

获取国家码信息。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [getCountryCode](arkts-connectivity-wifimanager-getcountrycode-f.md)

**需要权限：** ohos.permission.GET_WIFI_INFO

**系统能力：** SystemCapability.Communication.WiFi.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 国家码。 |

**示例**

```TypeScript
import wifi from '@ohos.wifi';

try {
  let code = wifi.getCountryCode();
  console.info("code:" + code);
}catch(error){
  console.error("failed:" + JSON.stringify(error));
}
```
