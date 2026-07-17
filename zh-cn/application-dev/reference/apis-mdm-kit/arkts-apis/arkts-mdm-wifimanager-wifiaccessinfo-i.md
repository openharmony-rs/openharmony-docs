# WifiAccessInfo

Wi-Fi的SSID和BSSID信息。

**起始版本：** 19

<!--Device-wifiManager-interface WifiAccessInfo--><!--Device-wifiManager-interface WifiAccessInfo-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 导入模块

```TypeScript
import { wifiManager } from '@kit.MDMKit';
```

## bssid

```TypeScript
bssid?: string
```

Wi-Fi热点的MAC地址，例如：00:11:22:33:44:55。获取方式如下：打开设置应用-点击系统选项-点击开发者选项-开启WLAN详细日志记录开关，然后进入设置应用中的WLAN列表，查看显示的MAC地址。若一个Wi-Fi对应多个MAC地址，需添加所有MAC地址。

作为[addDisallowedWifiList](arkts-mdm-wifimanager-adddisallowedwifilist-f.md#adddisallowedwifilist-1)和[removeDisallowedWifiList](arkts-mdm-wifimanager-removedisallowedwifilist-f.md#removedisallowedwifilist-1)接口的入参时，该属性可选，默认值为空字符串。

作为[addAllowedWifiList](arkts-mdm-wifimanager-addallowedwifilist-f.md#addallowedwifilist-1)和[removeAllowedWifiList](arkts-mdm-wifimanager-removeallowedwifilist-f.md#removeallowedwifilist-1)接口入参时，从API version 21开始，该属性可选，默认值为空字符串。API version 20及之前的版本，该属性必填。

**类型：** string

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WifiAccessInfo-bssid?: string--><!--Device-WifiAccessInfo-bssid?: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## ssid

```TypeScript
ssid: string
```

Wi-Fi热点名称，编码格式为UTF-8，最大长度为32字节（中文字符占3位，英文字符占1位）。

**类型：** string

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WifiAccessInfo-ssid: string--><!--Device-WifiAccessInfo-ssid: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

