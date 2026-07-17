# WifiProfile

Wi-Fi配置信息。

**起始版本：** 12

<!--Device-wifiManager-interface WifiProfile--><!--Device-wifiManager-interface WifiProfile-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 导入模块

```TypeScript
import { wifiManager } from '@kit.MDMKit';
```

## bssid

```TypeScript
bssid?: string
```

Wi-Fi热点的MAC地址，长度6个字节，例如：00:11:22:33:44:55。获取方式如下：打开设置应用-点击系统选项-点击开发者选项-开启WLAN详细日志记录开关，然后进入设置应用中的WLAN列表，查看显示的MAC地址。若一个Wi-Fi对应多个MAC地址，需添加所有MAC地址。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WifiProfile-bssid?: string--><!--Device-WifiProfile-bssid?: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## creatorUid

```TypeScript
creatorUid?: number
```

创建用户的ID，默认值-1。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WifiProfile-creatorUid?: number--><!--Device-WifiProfile-creatorUid?: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## disableReason

```TypeScript
disableReason?: number
```

禁用原因，默认值0。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WifiProfile-disableReason?: number--><!--Device-WifiProfile-disableReason?: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## eapProfile

```TypeScript
eapProfile?: WifiEapProfile
```

可扩展身份验证协议配置。只有securityType为WIFI_SEC_TYPE_EAP时必填。

**类型：** WifiEapProfile

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WifiProfile-eapProfile?: WifiEapProfile--><!--Device-WifiProfile-eapProfile?: WifiEapProfile-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## ipType

```TypeScript
ipType?: IpType
```

IP地址类型，默认值DHCP。

**类型：** IpType

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WifiProfile-ipType?: IpType--><!--Device-WifiProfile-ipType?: IpType-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## isHiddenSsid

```TypeScript
isHiddenSsid?: boolean
```

是否是隐藏网络。true表示是隐藏网络，false表示不是隐藏网络，默认为false。

**类型：** boolean

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WifiProfile-isHiddenSsid?: boolean--><!--Device-WifiProfile-isHiddenSsid?: boolean-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## netId

```TypeScript
netId?: number
```

分配的网络ID，默认值-1。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WifiProfile-netId?: number--><!--Device-WifiProfile-netId?: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## preSharedKey

```TypeScript
preSharedKey: string
```

热点的密钥，最大长度为64字节。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WifiProfile-preSharedKey: string--><!--Device-WifiProfile-preSharedKey: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## randomMacAddr

```TypeScript
randomMacAddr?: string
```

MAC地址。randomMacType为设备MAC类型时，该字段必填。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WifiProfile-randomMacAddr?: string--><!--Device-WifiProfile-randomMacAddr?: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## randomMacType

```TypeScript
randomMacType?: number
```

随机MAC类型。0-随机MAC地址， 1-设备MAC地址，默认值0。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WifiProfile-randomMacType?: number--><!--Device-WifiProfile-randomMacType?: number-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## securityType

```TypeScript
securityType: WifiSecurityType
```

安全类型。

**类型：** WifiSecurityType

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WifiProfile-securityType: WifiSecurityType--><!--Device-WifiProfile-securityType: WifiSecurityType-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## ssid

```TypeScript
ssid: string
```

Wi-Fi热点名称，最大长度为32字节，编码格式为UTF-8。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WifiProfile-ssid: string--><!--Device-WifiProfile-ssid: string-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## staticIp

```TypeScript
staticIp?: IpProfile
```

静态IP配置信息。ipType为STATIC时，该字段必填。

**类型：** IpProfile

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WifiProfile-staticIp?: IpProfile--><!--Device-WifiProfile-staticIp?: IpProfile-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

