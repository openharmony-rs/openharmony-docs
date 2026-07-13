# @ohos.enterprise.wifiManager

本模块提供企业设备Wi-Fi管理能力，包括查询Wi-Fi开启状态等。

> **说明：**
>
> 本模块接口仅可在Stage模型下使用。
>
> 本模块接口仅对设备管理应用开放，且调用接口前需激活设备管理应用，具体请参考[MDM Kit开发指南](../../../../mdm/mdm-kit-guide.md)。
>
> 全局通用限制类策略由restrictions统一提供，若要全局禁用Wi-Fi，请参考
> [@ohos.enterprise.restrictions（限制类策略）](arkts-enterprise-restrictions.md)。

**起始版本：** 10

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [addAllowedWifiList](arkts-mdm-addallowedwifilist-f.md#addallowedwifilist-1) | 添加Wi-Fi允许名单。添加允许名单后当前设备仅允许连接该名单下的Wi-Fi。以下情况下，调用本接口会报策略冲突：1. 已经通过[setDisallowedPolicy](arkts-mdm-setdisallowedpolicy-f.md#setdisallowedpolicy-1)接口禁用了设备Wi-Fi能力。通过[setDisallowedPolicy](arkts-mdm-setdisallowedpolicy-f.md#setdisallowedpolicy-1)解除Wi-Fi禁用后，可解除冲突。2. 已经通过[addDisallowedWifiList](arkts-mdm-adddisallowedwifilist-f.md#adddisallowedwifilist-1)接口添加了Wi-Fi禁用名单。通过[removeDisallowedWifiList](arkts-mdm-removedisallowedwifilist-f.md#removedisallowedwifilist-1)移除Wi-Fi禁用名单后，可解除冲突。 |
| [addDisallowedWifiList](arkts-mdm-adddisallowedwifilist-f.md#adddisallowedwifilist-1) | 添加Wi-Fi禁用名单。添加禁用名单后当前设备不允许连接该名单下的Wi-Fi。以下情况下，调用本接口会报策略冲突：1. 已经通过[setDisallowedPolicy](arkts-mdm-setdisallowedpolicy-f.md#setdisallowedpolicy-1)接口禁用了设备Wi-Fi能力。通过[setDisallowedPolicy](arkts-mdm-setdisallowedpolicy-f.md#setdisallowedpolicy-1)解除Wi-Fi禁用后，可解除冲突。2. 已经通过[addAllowedWifiList](arkts-mdm-addallowedwifilist-f.md#addallowedwifilist-1)接口添加了Wi-Fi允许名单。通过[removeAllowedWifiList](arkts-mdm-removeallowedwifilist-f.md#removeallowedwifilist-1)移除Wi-Fi允许名单后，可解除冲突。 |
| [getAllowedWifiList](arkts-mdm-getallowedwifilist-f.md#getallowedwifilist-1) | 获取Wi-Fi允许名单。 |
| [getDisallowedWifiList](arkts-mdm-getdisallowedwifilist-f.md#getdisallowedwifilist-1) | 获取Wi-Fi禁用名单。 |
| [isWifiActiveSync](arkts-mdm-iswifiactivesync-f.md#iswifiactivesync-1) | 查询当前设备Wi-Fi开启状态。 |
| [removeAllowedWifiList](arkts-mdm-removeallowedwifilist-f.md#removeallowedwifilist-1) | 移除Wi-Fi允许名单。若移除允许名单中的部分Wi-Fi，则当前设备仅允许连接剩下未移除的Wi-Fi。若移除允许名单中的所有Wi-Fi，则当前设备可以连接任意Wi-Fi。 |
| [removeDisallowedWifiList](arkts-mdm-removedisallowedwifilist-f.md#removedisallowedwifilist-1) | 移除Wi-Fi禁用名单。若移除禁用名单中的部分Wi-Fi，则当前设备不允许连接禁用名单内剩余的Wi-Fi。若移除禁用名单中的所有Wi-Fi，则当前设备可以连接任意的Wi-Fi。 |
| [setWifiProfileSync](arkts-mdm-setwifiprofilesync-f.md#setwifiprofilesync-1) | 为当前设备配置Wi-Fi，连接到指定网络。 |
| [turnOffWifi](arkts-mdm-turnoffwifi-f.md#turnoffwifi-1) | 关闭Wi-Fi开关。以下情况下，通过本接口关闭Wi-Fi开关，会提示"系统功能被禁用"：?已经通过[setDisallowedPolicy](arkts-mdm-setdisallowedpolicy-f.md#setdisallowedpolicy-1)接口禁用了Wi-Fi。需通过[setDisallowedPolicy](arkts-mdm-setdisallowedpolicy-f.md#setdisallowedpolicy-1)接口启用Wi-Fi，解决"系统功能被禁用"报错。 |
| [turnOnWifi](arkts-mdm-turnonwifi-f.md#turnonwifi-1) | 打开Wi-Fi开关。以下情况下，通过本接口打开Wi-Fi开关，会打开失败并提示"系统功能被禁用"：?已经通过[setDisallowedPolicy](arkts-mdm-setdisallowedpolicy-f.md#setdisallowedpolicy-1)接口禁用了Wi-Fi。需通过[setDisallowedPolicy](arkts-mdm-setdisallowedpolicy-f.md#setdisallowedpolicy-1)接口启用Wi-Fi，解决"系统功能被禁用"报错。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [isWifiActive](arkts-mdm-iswifiactive-f-sys.md#iswifiactive-1) | 查询当前设备的Wi-Fi开启状态。使用callback异步回调。 |
| [isWifiActive](arkts-mdm-iswifiactive-f-sys.md#iswifiactive-2) | 查询当前设备的Wi-Fi开启状态。使用Promise异步回调。 |
| [isWifiDisabled](arkts-mdm-iswifidisabled-f-sys.md#iswifidisabled-1) | 查询当前设备Wi-Fi是否被禁用。 |
| [setWifiDisabled](arkts-mdm-setwifidisabled-f-sys.md#setwifidisabled-1) | 设置禁用Wi-Fi策略。 |
| [setWifiProfile](arkts-mdm-setwifiprofile-f-sys.md#setwifiprofile-1) | 为当前设备配置Wi-Fi，使连接到指定网络。使用callback异步回调。 |
| [setWifiProfile](arkts-mdm-setwifiprofile-f-sys.md#setwifiprofile-2) | 为当前设备配置Wi-Fi，使连接到指定网络。使用Promise异步回调。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [IpProfile](arkts-mdm-ipprofile-i.md) | IP配置信息。 |
| [WifiAccessInfo](arkts-mdm-wifiaccessinfo-i.md) | Wi-Fi的SSID和BSSID信息。 |
| [WifiEapProfile](arkts-mdm-wifieapprofile-i.md) | 可扩展身份验证协议配置信息。 |
| [WifiProfile](arkts-mdm-wifiprofile-i.md) | Wi-Fi配置信息。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [EapMethod](arkts-mdm-eapmethod-e.md) | 表示EAP认证方式的枚举。&gt; **说明**：&gt;&gt; 当前仅支持使用EAP_PEAP、EAP_TLS两种认证方式，其他暂不支持。 |
| [IpType](arkts-mdm-iptype-e.md) | 表示IP类型的枚举。 |
| [Phase2Method](arkts-mdm-phase2method-e.md) | 表示第二阶段认证方式的枚举。 |
| [WifiSecurityType](arkts-mdm-wifisecuritytype-e.md) | 表示加密类型的枚举。 |

