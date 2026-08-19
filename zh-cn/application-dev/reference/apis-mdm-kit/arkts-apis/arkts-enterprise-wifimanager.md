# @ohos.enterprise.wifiManager

本模块提供企业设备Wi-Fi管理能力，包括查询Wi-Fi开启状态、配置Wi-Fi连接、管理Wi-Fi名单等。 **使用场景**： - 企业设备批量配置Wi-Fi连接，简化设备初始化流程 - 控制设备可连接的Wi-Fi网络，实现网络访问合规管理 - 管理企业设备的Wi-Fi开关，统一网络策略 **功能收益**： - 提高企业网络管理效率，减少IT运维成本 - 确保设备仅连接安全的Wi-Fi网络，降低安全风险 - 实现网络策略统一管控，满足企业合规要求 > **说明：** > > 本模块接口仅对设备管理应用开放，且调用接口前需激活设备管理应用，具体请参考[MDM Kit开发指南](../../../mdm/mdm-kit-guide.md)。 > > 全局通用限制类策略由restrictions统一提供，若要全局禁用Wi-Fi，请参考 > [@ohos.enterprise.restrictions（限制类策略）](arkts-enterprise-restrictions.md)。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-declare namespace wifiManager--><!--Device-unnamed-declare namespace wifiManager-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { wifiManager } from '@kit.MDMKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [addAllowedWifiList](arkts-mdm-wifimanager-addallowedwifilist-f.md) | 添加Wi-Fi允许名单。添加允许名单后当前设备仅允许连接该名单下的Wi-Fi。适用于企业安全管理场景，例如限制员工设备只能连接公司授权的Wi-Fi网络，防止连接不安全的外部Wi-Fi，保障企业网络安全和数据安全。 以下情况下，调用本接口会报策略冲突： 1. 已经通过[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md)接口禁用了设备Wi-Fi能力。通过[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md)解除Wi-Fi禁用后，可解除冲突。 2. 已经通过[addDisallowedWifiList](arkts-mdm-wifimanager-adddisallowedwifilist-f.md)接口添加了Wi-Fi禁用名单。通过[removeDisallowedWifiList](arkts-mdm-wifimanager-removedisallowedwifilist-f.md)移除Wi-Fi禁用名单后，可解除冲突。 |
| [addDisallowedWifiList](arkts-mdm-wifimanager-adddisallowedwifilist-f.md) | 添加Wi-Fi禁用名单。添加禁用名单后当前设备不允许连接该名单下的Wi-Fi。适用于企业安全管控场景，例如禁止设备连接不安全的公共Wi-Fi(如咖啡馆、机场Wi-Fi)、防止员工连接竞争对手或恶意网络，保障企业数据安全。 以下情况下，调用本接口会报策略冲突： 1. 已经通过[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md)接口禁用了设备Wi-Fi能力。通过[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md)解除Wi-Fi禁用后，可解除冲突。 2. 已经通过[addAllowedWifiList](arkts-mdm-wifimanager-addallowedwifilist-f.md)接口添加了Wi-Fi允许名单。通过[removeAllowedWifiList](arkts-mdm-wifimanager-removeallowedwifilist-f.md)移除Wi-Fi允许名单后，可解除冲突。 |
| [getAllowedWifiList](arkts-mdm-wifimanager-getallowedwifilist-f.md) | 获取Wi-Fi允许名单。 |
| [getAllowedWifiList](arkts-mdm-wifimanager-getallowedwifilist-f.md) | 获取Wi-Fi允许名单。 |
| [getDisallowedWifiList](arkts-mdm-wifimanager-getdisallowedwifilist-f.md) | 获取Wi-Fi禁用名单。 |
| [getDisallowedWifiList](arkts-mdm-wifimanager-getdisallowedwifilist-f.md) | 获取Wi-Fi禁用名单。 |
| [isWifiActiveSync](arkts-mdm-wifimanager-iswifiactivesync-f.md) | 查询当前设备Wi-Fi开启状态。 |
| [removeAllowedWifiList](arkts-mdm-wifimanager-removeallowedwifilist-f.md) | 移除Wi-Fi允许名单。若移除允许名单中的部分Wi-Fi，则当前设备仅允许连接剩下未移除的Wi-Fi。若移除允许名单中的所有Wi-Fi，则当前设备可以连接任意Wi-Fi。适用于企业Wi-Fi策略调整场景，例如公司更换Wi-Fi网络 时移除旧网络限制、或解除部分Wi-Fi限制以允许员工连接新的办公网络。 |
| [removeDisallowedWifiList](arkts-mdm-wifimanager-removedisallowedwifilist-f.md) | 移除Wi-Fi禁用名单。若移除禁用名单中的部分Wi-Fi，则当前设备不允许连接禁用名单内剩余的Wi-Fi。若移除禁用名单中的所有Wi-Fi，则当前设备可以连接任意的Wi-Fi。适用于企业Wi-Fi策略调整场景，例如解除对特定Wi- Fi的禁用限制、允许员工连接新批准的办公网络、或完全移除禁用策略。 |
| [setWifiProfileSync](arkts-mdm-wifimanager-setwifiprofilesync-f.md) | 为当前设备配置Wi-Fi，连接到指定网络。 |
| [turnOffWifi](arkts-mdm-wifimanager-turnoffwifi-f.md) | 关闭Wi-Fi开关。 以下情况下，通过本接口关闭Wi-Fi开关，会提示"系统功能被禁用"： ​已经通过[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md)接口禁用了Wi-Fi。需通过 [setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md)接口启用Wi-Fi，解决"系统功能被禁用"报错。 |
| [turnOnWifi](arkts-mdm-wifimanager-turnonwifi-f.md) | 打开Wi-Fi开关。适用于企业设备远程管理场景，例如管理员远程控制员工设备开启Wi-Fi或在特定策略执行时确保Wi-Fi已开启。 以下情况下，通过本接口打开Wi-Fi开关，会打开失败并提示"系统功能被禁用"： ​已经通过[setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md)接口禁用了Wi-Fi。需通过 [setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md)接口启用Wi-Fi，解决"系统功能被禁用"报错。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [isWifiActive](arkts-mdm-wifimanager-iswifiactive-f-sys.md) | 查询当前设备的Wi-Fi开启状态。使用callback异步回调。 |
| [isWifiActive](arkts-mdm-wifimanager-iswifiactive-f-sys.md) | 查询当前设备的Wi-Fi开启状态。使用Promise异步回调。 |
| [isWifiDisabled](arkts-mdm-wifimanager-iswifidisabled-f-sys.md) | 查询当前设备Wi-Fi是否被禁用。 |
| [setWifiDisabled](arkts-mdm-wifimanager-setwifidisabled-f-sys.md) | 设置禁用Wi-Fi策略。 |
| [setWifiProfile](arkts-mdm-wifimanager-setwifiprofile-f-sys.md) | 为当前设备配置Wi-Fi，使连接到指定网络。使用callback异步回调。 |
| [setWifiProfile](arkts-mdm-wifimanager-setwifiprofile-f-sys.md) | 为当前设备配置Wi-Fi，使连接到指定网络。使用Promise异步回调。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [IpProfile](arkts-mdm-wifimanager-ipprofile-i.md) | IP配置信息。 |
| [WifiAccessInfo](arkts-mdm-wifimanager-wifiaccessinfo-i.md) | Wi-Fi的SSID和BSSID信息。 |
| [WifiEapProfile](arkts-mdm-wifimanager-wifieapprofile-i.md) | 可扩展身份验证协议配置信息。 |
| [WifiProfile](arkts-mdm-wifimanager-wifiprofile-i.md) | Wi-Fi配置信息。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [EapMethod](arkts-mdm-wifimanager-eapmethod-e.md) | 表示EAP认证方式的枚举。 |
| [IpType](arkts-mdm-wifimanager-iptype-e.md) | 表示IP类型的枚举。 |
| [Phase2Method](arkts-mdm-wifimanager-phase2method-e.md) | 表示第二阶段认证方式的枚举。 |
| [WifiSecurityType](arkts-mdm-wifimanager-wifisecuritytype-e.md) | 表示加密类型的枚举。 |

