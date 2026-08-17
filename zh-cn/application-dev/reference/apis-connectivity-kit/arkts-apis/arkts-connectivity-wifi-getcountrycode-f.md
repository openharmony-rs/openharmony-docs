# getCountryCode

## getCountryCode

```TypeScript
function getCountryCode(): string
```

获取国家码信息。

**起始版本：** 7

**ArkTS模式：** 起始版本为7。

**废弃版本：** 9

**替代接口：** [getCountryCode](arkts-connectivity-wifimanager-getcountrycode-f.md#getcountrycode)

**需要权限：** ohos.permission.GET_WIFI_INFO

<!--Device-wifi-function getCountryCode(): string--><!--Device-wifi-function getCountryCode(): string-End-->

**系统能力：** SystemCapability.Communication.WiFi.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 国家码。 |

## 示例

```TypeScript
import wifi from '@ohos.wifi';

try {
  let code = wifi.getCountryCode();
  console.info("code:" + code);
}catch(error){
  console.error("failed:" + JSON.stringify(error));
}
```

