# @ohos.enterprise.networkManager

本模块提供设备网络管理能力，包括查询设备IP地址、MAC地址信息、管理网络接口状态、配置网络全局代理、管理防火墙规则和域名过滤规则、控制移动数据网络、管理APN配置、配置以太网网络等。适用于企业IT管理员对设备网络进行集中管理和安全管 控，帮助企业实现网络访问策略统一管理、防止网络攻击和数据泄露、降低网络管理成本。 > **说明：** > > 本模块接口仅对设备管理应用开放，且调用接口前需激活设备管理应用，具体请参考[MDM Kit开发指南](../../../mdm/mdm-kit-guide.md)。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-declare namespace networkManager--><!--Device-unnamed-declare namespace networkManager-End-->

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { networkManager } from '@kit.MDMKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [addApn](arkts-mdm-networkmanager-addapn-f.md) | 添加APN（Access Point Name，接入点名称）。 |
| [addDomainFilterRule](arkts-mdm-networkmanager-adddomainfilterrule-f.md) | 为设备添加域名过滤规则。 API version 21及之前版本，仅支持IPv4。从API version 22开始，支持IPv4和IPv6。 从API version 23开始，支持[LogType](arkts-mdm-networkmanager-logtype-e.md)。 |
| [addFirewallRule](arkts-mdm-networkmanager-addfirewallrule-f.md) | 为设备添加防火墙过滤规则。适用于企业网络安全管控场景，例如限制特定IP地址的网络访问、防止恶意网络攻击、控制应用程序的网络通信、实现网络访问的允许名单或禁用名单管理，帮助企业精细化控制 网络访问，防止网络攻击和数据泄露。 API version 21及之前版本，仅支持IPv4。从API version 22开始，支持IPv4和IPv6。 从API version 23开始，支持[LogType](arkts-mdm-networkmanager-logtype-e.md)。 |
| [deleteApn](arkts-mdm-networkmanager-deleteapn-f.md) | 删除APN。适用于企业移动网络配置管理场景，例如清理无效的APN配置、调整移动网络接入点配置、防止使用错误的APN配置，帮助企业维护正确的移动网络配置，确保设备使用正确的接入点连接移动网络。 |
| [getAllNetworkInterfacesSync](arkts-mdm-networkmanager-getallnetworkinterfacessync-f.md) | 获取所有激活的有线网络接口。适用于企业网络管理场景，例如查看当前设备可用的网络连接、审计网络接口状态、为后续网络配置操作做准备，帮助企业了解设备网络连接状态，便于集中管理网络资源和排查网络问题。 |
| [getDomainFilterRules](arkts-mdm-networkmanager-getdomainfilterrules-f.md) | 查询设备域名过滤规则。适用于企业网络安全审计场景，例如检查当前域名过滤策略配置、审计域名访问控制规则、验证域名过滤规则是否正确执行、排查域名访问问题，帮助企业审核和验证域名访问控制策略，确保网络访问控制符合安全要求。 API version 21及之前版本，仅支持IPv4。从API version 22开始，支持IPv4和IPv6。 从API version 23开始，支持[LogType](arkts-mdm-networkmanager-logtype-e.md)。 |
| [getFirewallRules](arkts-mdm-networkmanager-getfirewallrules-f.md) | 查询设备防火墙过滤规则。适用于企业网络安全审计场景，例如检查当前防火墙策略配置、审计网络访问控制规则、验证防火墙规则是否正确执行、排查网络访问问题，帮助企业审核和验证网络安全策略，确保网络访问控制符合安全要求。 API version 21及之前版本，仅支持IPv4。从API version 22开始，支持IPv4和IPv6。 从API version 23开始，支持[LogType](arkts-mdm-networkmanager-logtype-e.md)。 |
| [getGlobalProxyForAccount](arkts-mdm-networkmanager-getglobalproxyforaccount-f.md) | 获取指定用户下的网络代理。适用于企业多用户环境下的网络管理场景，例如审计用户级网络代理配置、验证用户网络访问策略、排查用户网络访问问题，帮助企业检查和验证用户级网络管理策略。 |
| [getGlobalProxySync](arkts-mdm-networkmanager-getglobalproxysync-f.md) | 获取网络全局代理。适用于企业网络管理场景，例如审计当前网络代理配置、验证代理策略是否生效、排查网络访问问题，帮助企业检查网络代理设置，确保网络访问策略正确执行。 |
| [getIpAddressSync](arkts-mdm-networkmanager-getipaddresssync-f.md) | 根据网络接口获取设备IP地址。适用于企业网络管理场景，例如网络审计、设备定位、网络连接问题排查、IP地址分配管理，帮助企业IT管理员了解设备网络配置，便于网络管理和故障诊断。 |
| [getMacSync](arkts-mdm-networkmanager-getmacsync-f.md) | 根据网络接口获取设备MAC地址。适用于企业网络管理场景，例如设备识别、网络准入控制、MAC地址审计、设备资产管理，帮助企业识别和追踪设备，实现精细化的网络访问控制。 |
| [isNetworkInterfaceDisabledSync](arkts-mdm-networkmanager-isnetworkinterfacedisabledsync-f.md) | 查询指定网络接口是否被禁用。适用于企业网络管理场景，例如检查网络接口状态、审计网络接口使用情况、验证网络策略执行效果，帮助企业确认网络接口管理策略是否生效，便于策略调整和问题排查。 |
| [isNetworkInterfaceDisabledSync](arkts-mdm-networkmanager-isnetworkinterfacedisabledsync-f.md) | 查询指定网络接口是否被禁用。适用于企业网络管理场景，例如检查网络接口状态、审计网络接口使用情况、验证网络策略执行效果，帮助企业确认网络接口管理策略是否生效，便于策略调整和问题排查。 |
| [queryApn](arkts-mdm-networkmanager-queryapn-f.md) | 查询符合特定APN信息的APN ID。适用于企业移动网络配置审计场景，例如查找特定配置的APN、验证APN配置是否存在、为APN管理操作提供APN ID参数，帮助企业查找和管理APN配置，为APN的更新和删除操作提供必要的参数信 息。 |
| [queryApn](arkts-mdm-networkmanager-queryapn-f.md) | 查询特定APN的APN参数信息。适用于企业移动网络配置审计场景，例如检查特定APN的配置参数、验证APN配置是否正确、审计移动网络接入点配置，帮助企业审核和验证APN配置，确保移动网络配置符合要求。 |
| [removeDomainFilterRule](arkts-mdm-networkmanager-removedomainfilterrule-f.md) | 移除设备域名过滤规则。适用于企业网络安全策略调整场景，例如取消某些域名访问限制、调整域名过滤策略、清理过时或无效的规则、解决误拦截问题，帮助企业灵活调整域名访问策略，确保网络访问控制策略符合实际需求。 API version 21及之前版本，仅支持IPv4。从API version 22开始，支持IPv4和IPv6。 从API version 23开始，支持[LogType](arkts-mdm-networkmanager-logtype-e.md)。 移除规则后如果不存在[Action](arkts-mdm-networkmanager-action-e.md)为ALLOW规则后，会将 [addDomainFilterRule](arkts-mdm-networkmanager-adddomainfilterrule-f.md)添加的默认DENY规则清空。 |
| [removeFirewallRule](arkts-mdm-networkmanager-removefirewallrule-f.md) | 移除设备防火墙过滤规则。适用于企业网络安全策略调整场景，例如取消某些网络访问限制、调整防火墙策略、清理过时或无效的规则，帮助企业灵活调整网络安全策略，确保网络访问控制策略与实际需求保持一致。 API version 21及之前版本，仅支持IPv4。从API version 22开始，支持IPv4和IPv6。 从API version 23开始，支持[LogType](arkts-mdm-networkmanager-logtype-e.md)。 移除规则后如果不存在[Action](arkts-mdm-networkmanager-action-e.md)为ALLOW规则后，会将[addFirewallRule](arkts-mdm-networkmanager-addfirewallrule-f.md)添 加的默认DENY规则清空。 |
| [setEthernetConfig](arkts-mdm-networkmanager-setethernetconfig-f.md) | 设置特定以太网网络接口的IP地址。适用于企业网络管理场景，例如配置设备静态IP地址、统一管理企业网络设备IP分配、设置网络参数，帮助企业集中管理网络配置，确保设备网络参数符合企业网络管理策略。 |
| [setGlobalProxyForAccount](arkts-mdm-networkmanager-setglobalproxyforaccount-f.md) | 设置指定用户下的网络代理。适用于企业多用户环境下的网络管理场景，例如为不同用户设置不同的网络代理策略、实现用户级网络访问控制、满足不同用户的网络访问需求，帮助企业实现精细化的用户级网络管理。 |
| [setGlobalProxySync](arkts-mdm-networkmanager-setglobalproxysync-f.md) | 设置网络全局代理。适用于企业网络管理场景，例如设置企业统一的网络代理、实现网络访问审计、控制网络访问路径、优化网络性能，帮助企业集中管理网络访问，实现网络访问的可审计和可控制。 |
| [setNetworkInterfaceDisabledSync](arkts-mdm-networkmanager-setnetworkinterfacedisabledsync-f.md) | 禁止设备使用指定网络接口。适用于企业网络安全管控场景，例如禁用高风险网络接口、限制设备使用特定网络连接、防止通过网络接口进行数据泄露，帮助企业降低网络安全风险，防止通过特定网络接口进行的攻击或数据外泄。 |
| [setPreferredApn](arkts-mdm-networkmanager-setpreferredapn-f.md) | 设置优选APN。 |
| [turnOffMobileData](arkts-mdm-networkmanager-turnoffmobiledata-f.md) | 关闭移动数据网络。 |
| [turnOnMobileData](arkts-mdm-networkmanager-turnonmobiledata-f.md) | 开启移动数据网络。 |
| [updateApn](arkts-mdm-networkmanager-updateapn-f.md) | 更新APN。适用于企业移动网络配置管理场景，例如修改APN配置参数、调整运营商设置、优化移动网络连接性能，帮助企业灵活调整移动网络配置，确保设备移动网络连接参数符合实际需求。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [addIptablesFilterRule](arkts-mdm-networkmanager-addiptablesfilterrule-f-sys.md) | 为设备添加网络包过滤规则，仅支持IPv4。使用callback异步回调。 |
| [addIptablesFilterRule](arkts-mdm-networkmanager-addiptablesfilterrule-f-sys.md) | 为设备添加网络包过滤规则，仅支持IPv4。使用Promise异步回调。 |
| [getAllNetworkInterfaces](arkts-mdm-networkmanager-getallnetworkinterfaces-f-sys.md) | 获取所有激活的有线网络接口。使用callback异步回调。 |
| [getAllNetworkInterfaces](arkts-mdm-networkmanager-getallnetworkinterfaces-f-sys.md) | 获取所有激活的有线网络接口。使用Promise异步回调。 |
| [getGlobalProxy](arkts-mdm-networkmanager-getglobalproxy-f-sys.md) | 获取网络全局代理，使用callback异步回调。 |
| [getGlobalProxy](arkts-mdm-networkmanager-getglobalproxy-f-sys.md) | 获取网络全局代理，使用Promise异步回调。 |
| [getIpAddress](arkts-mdm-networkmanager-getipaddress-f-sys.md) | 根据网络接口获取设备IP地址。使用callback异步回调。 |
| [getIpAddress](arkts-mdm-networkmanager-getipaddress-f-sys.md) | 根据网络接口获取设备IP地址。使用Promise异步回调。 |
| [getMac](arkts-mdm-networkmanager-getmac-f-sys.md) | 根据网络接口获取设备MAC地址。使用callback异步回调。 |
| [getMac](arkts-mdm-networkmanager-getmac-f-sys.md) | 根据网络接口获取设备MAC地址。使用Promise异步回调。 |
| [isNetworkInterfaceDisabled](arkts-mdm-networkmanager-isnetworkinterfacedisabled-f-sys.md) | 查询指定网络接口是否被禁用。使用callback异步回调。 |
| [isNetworkInterfaceDisabled](arkts-mdm-networkmanager-isnetworkinterfacedisabled-f-sys.md) | 查询指定网络接口是否被禁用。使用Promise异步回调。 |
| [listIptablesFilterRules](arkts-mdm-networkmanager-listiptablesfilterrules-f-sys.md) | 获取网络包过滤规则，仅支持IPv4。使用callback异步回调。 |
| [listIptablesFilterRules](arkts-mdm-networkmanager-listiptablesfilterrules-f-sys.md) | 获取网络包过滤规则，仅支持IPv4。使用Promise异步回调。 |
| [removeIptablesFilterRule](arkts-mdm-networkmanager-removeiptablesfilterrule-f-sys.md) | 移除网络包过滤规则，仅支持IPv4。使用callback异步回调。 |
| [removeIptablesFilterRule](arkts-mdm-networkmanager-removeiptablesfilterrule-f-sys.md) | 移除网络包过滤规则，仅支持IPv4。使用Promise异步回调。 |
| [setGlobalProxy](arkts-mdm-networkmanager-setglobalproxy-f-sys.md) | 设置网络全局代理，使用callback异步回调。 |
| [setGlobalProxy](arkts-mdm-networkmanager-setglobalproxy-f-sys.md) | 设置网络全局代理，使用Promise异步回调。 |
| [setNetworkInterfaceDisabled](arkts-mdm-networkmanager-setnetworkinterfacedisabled-f-sys.md) | 禁止设备使用指定网络。使用callback异步回调。 |
| [setNetworkInterfaceDisabled](arkts-mdm-networkmanager-setnetworkinterfacedisabled-f-sys.md) | 禁止设备使用指定网络。使用Promise异步回调。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [DomainFilterRule](arkts-mdm-networkmanager-domainfilterrule-i.md) | 域名过滤规则。 API version 21及之前版本，仅支持IPv4。从API version 22开始，支持IPv4和IPv6。 从API version 23开始，支持[LogType](arkts-mdm-networkmanager-logtype-e.md)。 |
| [FirewallRule](arkts-mdm-networkmanager-firewallrule-i.md) | 防火墙过滤规则。 API version 21及之前版本，仅支持IPv4。从API version 22开始，支持IPv4和IPv6。 从API version 23开始，支持[LogType](arkts-mdm-networkmanager-logtype-e.md)。 |
| [InterfaceConfig](arkts-mdm-networkmanager-interfaceconfig-i.md) | 以太网的网络接口配置。仅支持IPv4。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AddFilterRule](arkts-mdm-networkmanager-addfilterrule-i-sys.md) | 添加网络包过滤规则。 |
| [RemoveFilterRule](arkts-mdm-networkmanager-removefilterrule-i-sys.md) | 移除网络包过滤规则。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [Action](arkts-mdm-networkmanager-action-e.md) | 数据包的行为。 |
| [Direction](arkts-mdm-networkmanager-direction-e.md) | 规则链。 |
| [IpSetMode](arkts-mdm-networkmanager-ipsetmode-e.md) | 以太网连接模式。 |
| [LogType](arkts-mdm-networkmanager-logtype-e.md) | 日志类型。 |
| [Protocol](arkts-mdm-networkmanager-protocol-e.md) | 网络协议。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AddMethod](arkts-mdm-networkmanager-addmethod-e-sys.md) | 添加网络包方法。 |
<!--DelEnd-->

