# @ohos.net.vpn(VPN管理)

本模块是操作系统提供的内置VPN功能，允许用户通过系统的网络设置进行VPN连接，通常提供的功能较少，而且有比较严格的限制。

> **说明：**
> 
> 本模块首批接口从 API version 10 开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.NetManager.Vpn

## 导入模块

```TypeScript
import { vpn } from '@kit.NetworkKit';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [addSysVpnConfig(VPN管理)](arkts-network-vpn-addsysvpnconfig-f-sys.md) | 添加系统VPN网络配置。 |
| [createVpnConnection(VPN管理)](arkts-network-vpn-createvpnconnection-f-sys.md) | 创建一个 VPN 连接对象。 |
| [deleteSysVpnConfig(VPN管理)](arkts-network-vpn-deletesysvpnconfig-f-sys.md) | 删除指定vpnId的系统VPN网络配置。 |
| [getConnectedSysVpnConfig(VPN管理)](arkts-network-vpn-getconnectedsysvpnconfig-f-sys.md) | 获取已连接的VPN网络配置。 |
| [getConnectedVpnAppInfo(VPN管理)](arkts-network-vpn-getconnectedvpnappinfo-f-sys.md) | 获取已连接的VPN应用信息。 |
| [getSysVpnConfig(VPN管理)](arkts-network-vpn-getsysvpnconfig-f-sys.md) | 获取指定vpnId的系统VPN网络配置。 |
| [getSysVpnConfigList(VPN管理)](arkts-network-vpn-getsysvpnconfiglist-f-sys.md) | 获取所有系统VPN网络配置。 |
| off(VPN管理) | 取消订阅VPN连接状态变化事件。 |
| off(VPN管理) | 取消订阅VPN连接状态变化事件。 |
| on(VPN管理) | 订阅VPN连接状态变化事件。 |
| on(VPN管理) | 订阅VPN连接状态变化事件。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [IpsecVpnConfig(VPN管理)](arkts-network-vpn-ipsecvpnconfig-i-sys.md) | 定义IPSec VPN网络的配置。 |
| [L2tpVpnConfig(VPN管理)](arkts-network-vpn-l2tpvpnconfig-i-sys.md) | 定义L2TP VPN网络的配置。 |
| [OpenVpnConfig(VPN管理)](arkts-network-vpn-openvpnconfig-i-sys.md) | 定义开放VPN网络的配置。 |
| [SysVpnConfig(VPN管理)](arkts-network-vpn-sysvpnconfig-i-sys.md) | 定义系统VPN网络的配置。 |
| [VpnConfig(VPN管理)](arkts-network-vpn-vpnconfig-i-sys.md) | VPN 配置参数。 |
| [VpnConnection(VPN管理)](arkts-network-vpn-vpnconnection-i-sys.md) | VPN 连接对象。在调用 VpnConnection 的方法前，需要先通过[vpn.createVpnConnection](arkts-network-vpn-createvpnconnection-f-sys.md)创建 VPN 连接对象。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [SysVpnType(VPN管理)](arkts-network-vpn-sysvpntype-e-sys.md) | 定义VPN网络的类型。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [AbilityContext(VPN管理)](arkts-network-vpn-abilitycontext-t.md) |  |
| [LinkAddress(VPN管理)](arkts-network-vpn-linkaddress-t.md) | 获取网络链接信息。 |
| [RouteInfo(VPN管理)](arkts-network-vpn-routeinfo-t.md) | 获取网络路由信息。 |
