# @ohos.enterprise.networkManager

本模块提供设备网络管理能力，包括查询设备IP地址、MAC地址信息等。

> **说明：**
>
> 本模块接口仅可在Stage模型下使用。
>
> 本模块接口仅对设备管理应用开放，且调用接口前需激活设备管理应用，具体请参考[MDM Kit开发指南](../../../../mdm/mdm-kit-guide.md)。

**起始版本：** 10

**系统能力：** SystemCapability.Customization.EnterpriseDeviceManager

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [addApn](arkts-mdm-addapn-f.md#addapn-1) | 添加APN（Access Point Name，接入点名称）。 |
| [addDomainFilterRule](arkts-mdm-adddomainfilterrule-f.md#adddomainfilterrule-1) | 为设备添加域名过滤规则。API version 21及之前版本，仅支持IPv4。从API version 22开始，支持IPv4和IPv6。从API version 23开始，支持[LogType](arkts-mdm-logtype-e.md)。添加了[Action](arkts-mdm-action-e.md)为ALLOW规则后，将会默认添加DENY规则，不在ALLOW规则之内的域名解析数据包将会被丢弃或拦截。设备重启，将会清空域名过滤规则。 |
| [addFirewallRule](arkts-mdm-addfirewallrule-f.md#addfirewallrule-1) | 为设备添加防火墙过滤规则。API version 21及之前版本，仅支持IPv4。从API version 22开始，支持IPv4和IPv6。从API version 23开始，支持[LogType](arkts-mdm-logtype-e.md)。添加了[Action](arkts-mdm-action-e.md)为ALLOW规则后，将会默认添加DENY规则，不在ALLOW规则之内的网络数据包将会被丢弃或拦截。设备重启，将会清空防火墙过滤规则。 |
| [deleteApn](arkts-mdm-deleteapn-f.md#deleteapn-1) | 删除APN。 |
| [getAllNetworkInterfacesSync](arkts-mdm-getallnetworkinterfacessync-f.md#getallnetworkinterfacessync-1) | 获取所有激活的有线网络接口。 |
| [getDomainFilterRules](arkts-mdm-getdomainfilterrules-f.md#getdomainfilterrules-1) | 查询设备域名过滤规则。API version 21及之前版本，仅支持IPv4。从API version 22开始，支持IPv4和IPv6。从API version 23开始，支持[LogType](arkts-mdm-logtype-e.md)。 |
| [getFirewallRules](arkts-mdm-getfirewallrules-f.md#getfirewallrules-1) | 查询设备防火墙过滤规则。API version 21及之前版本，仅支持IPv4。从API version 22开始，支持IPv4和IPv6。从API version 23开始，支持[LogType](arkts-mdm-logtype-e.md)。 |
| [getGlobalProxyForAccount](arkts-mdm-getglobalproxyforaccount-f.md#getglobalproxyforaccount-1) | 获取指定用户下的网络代理。 |
| [getGlobalProxySync](arkts-mdm-getglobalproxysync-f.md#getglobalproxysync-1) | 获取网络全局代理。 |
| [getIpAddressSync](arkts-mdm-getipaddresssync-f.md#getipaddresssync-1) | 根据网络接口获取设备IP地址。 |
| [getMacSync](arkts-mdm-getmacsync-f.md#getmacsync-1) | 根据网络接口获取设备MAC地址。 |
| [isNetworkInterfaceDisabledSync](arkts-mdm-isnetworkinterfacedisabledsync-f.md#isnetworkinterfacedisabledsync-1) | 查询指定网络接口是否被禁用。 |
| [queryApn](arkts-mdm-queryapn-f.md#queryapn-1) | 查询符合特定APN信息的APN ID。 |
| [queryApn](arkts-mdm-queryapn-f.md#queryapn-2) | 查询特定APN的APN参数信息。 |
| [removeDomainFilterRule](arkts-mdm-removedomainfilterrule-f.md#removedomainfilterrule-1) | 移除设备域名过滤规则。API version 21及之前版本，仅支持IPv4。从API version 22开始，支持IPv4和IPv6。从API version 23开始，支持[LogType](arkts-mdm-logtype-e.md)。移除规则后如果不存在[Action](arkts-mdm-action-e.md)为ALLOW规则后，会将[addDomainFilterRule](arkts-mdm-adddomainfilterrule-f.md#adddomainfilterrule-1)添加的默认DENY规则清空。 |
| [removeFirewallRule](arkts-mdm-removefirewallrule-f.md#removefirewallrule-1) | 移除设备防火墙过滤规则。API version 21及之前版本，仅支持IPv4。从API version 22开始，支持IPv4和IPv6。从API version 23开始，支持[LogType](arkts-mdm-logtype-e.md)。移除规则后如果不存在[Action](arkts-mdm-action-e.md)为ALLOW规则后，会将[addFirewallRule](arkts-mdm-addfirewallrule-f.md#addfirewallrule-1)添加的默认DENY规则清空。 |
| [setEthernetConfig](arkts-mdm-setethernetconfig-f.md#setethernetconfig-1) | 设置特定以太网网络接口的IP地址。 |
| [setGlobalProxyForAccount](arkts-mdm-setglobalproxyforaccount-f.md#setglobalproxyforaccount-1) | 设置指定用户下的网络代理。 |
| [setGlobalProxySync](arkts-mdm-setglobalproxysync-f.md#setglobalproxysync-1) | 设置网络全局代理。 |
| [setNetworkInterfaceDisabledSync](arkts-mdm-setnetworkinterfacedisabledsync-f.md#setnetworkinterfacedisabledsync-1) | 禁止设备使用指定网络接口。 |
| [setPreferredApn](arkts-mdm-setpreferredapn-f.md#setpreferredapn-1) | 设置优选APN。 |
| [turnOffMobileData](arkts-mdm-turnoffmobiledata-f.md#turnoffmobiledata-1) | 关闭移动数据网络。 |
| [turnOnMobileData](arkts-mdm-turnonmobiledata-f.md#turnonmobiledata-1) | 开启移动数据网络。 |
| [updateApn](arkts-mdm-updateapn-f.md#updateapn-1) | 更新APN。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [addIptablesFilterRule](arkts-mdm-addiptablesfilterrule-f-sys.md#addiptablesfilterrule-1) | 为设备添加网络包过滤规则，仅支持IPv4。使用callback异步回调。 |
| [addIptablesFilterRule](arkts-mdm-addiptablesfilterrule-f-sys.md#addiptablesfilterrule-2) | 为设备添加网络包过滤规则，仅支持IPv4。使用Promise异步回调。 |
| [getAllNetworkInterfaces](arkts-mdm-getallnetworkinterfaces-f-sys.md#getallnetworkinterfaces-1) | 获取所有激活的有线网络接口。使用callback异步回调。 |
| [getAllNetworkInterfaces](arkts-mdm-getallnetworkinterfaces-f-sys.md#getallnetworkinterfaces-2) | 获取所有激活的有线网络接口。使用Promise异步回调。 |
| [getGlobalProxy](arkts-mdm-getglobalproxy-f-sys.md#getglobalproxy-1) | 获取网络全局代理，使用callback异步回调。 |
| [getGlobalProxy](arkts-mdm-getglobalproxy-f-sys.md#getglobalproxy-2) | 获取网络全局代理，使用Promise异步回调。 |
| [getIpAddress](arkts-mdm-getipaddress-f-sys.md#getipaddress-1) | 根据网络接口获取设备IP地址。使用callback异步回调。 |
| [getIpAddress](arkts-mdm-getipaddress-f-sys.md#getipaddress-2) | 根据网络接口获取设备IP地址。使用Promise异步回调。 |
| [getMac](arkts-mdm-getmac-f-sys.md#getmac-1) | 根据网络接口获取设备MAC地址。使用callback异步回调。 |
| [getMac](arkts-mdm-getmac-f-sys.md#getmac-2) | 根据网络接口获取设备MAC地址。使用Promise异步回调。 |
| [isNetworkInterfaceDisabled](arkts-mdm-isnetworkinterfacedisabled-f-sys.md#isnetworkinterfacedisabled-1) | 查询指定网络接口是否被禁用。使用callback异步回调。 |
| [isNetworkInterfaceDisabled](arkts-mdm-isnetworkinterfacedisabled-f-sys.md#isnetworkinterfacedisabled-2) | 查询指定网络接口是否被禁用。使用Promise异步回调。 |
| [listIptablesFilterRules](arkts-mdm-listiptablesfilterrules-f-sys.md#listiptablesfilterrules-1) | 获取网络包过滤规则，仅支持IPv4。使用callback异步回调。 |
| [listIptablesFilterRules](arkts-mdm-listiptablesfilterrules-f-sys.md#listiptablesfilterrules-2) | 获取网络包过滤规则，仅支持IPv4。使用Promise异步回调。 |
| [removeIptablesFilterRule](arkts-mdm-removeiptablesfilterrule-f-sys.md#removeiptablesfilterrule-1) | 移除网络包过滤规则，仅支持IPv4。使用callback异步回调。 |
| [removeIptablesFilterRule](arkts-mdm-removeiptablesfilterrule-f-sys.md#removeiptablesfilterrule-2) | 移除网络包过滤规则，仅支持IPv4。使用Promise异步回调。 |
| [setGlobalProxy](arkts-mdm-setglobalproxy-f-sys.md#setglobalproxy-1) | 设置网络全局代理，使用callback异步回调。 |
| [setGlobalProxy](arkts-mdm-setglobalproxy-f-sys.md#setglobalproxy-2) | 设置网络全局代理，使用Promise异步回调。 |
| [setNetworkInterfaceDisabled](arkts-mdm-setnetworkinterfacedisabled-f-sys.md#setnetworkinterfacedisabled-1) | 禁止设备使用指定网络。使用callback异步回调。 |
| [setNetworkInterfaceDisabled](arkts-mdm-setnetworkinterfacedisabled-f-sys.md#setnetworkinterfacedisabled-2) | 禁止设备使用指定网络。使用Promise异步回调。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [DomainFilterRule](arkts-mdm-domainfilterrule-i.md) | 域名过滤规则。API version 21及之前版本，仅支持IPv4。从API version 22开始，支持IPv4和IPv6。从API version 23开始，支持[LogType](arkts-mdm-logtype-e.md)。 |
| [FirewallRule](arkts-mdm-firewallrule-i.md) | 防火墙过滤规则。API version 21及之前版本，仅支持IPv4。从API version 22开始，支持IPv4和IPv6。从API version 23开始，支持[LogType](arkts-mdm-logtype-e.md)。 |
| [InterfaceConfig](arkts-mdm-interfaceconfig-i.md) | 以太网的网络接口配置。仅支持IPv4。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AddFilterRule](arkts-mdm-addfilterrule-i-sys.md) | 添加网络包过滤规则。 |
| [RemoveFilterRule](arkts-mdm-removefilterrule-i-sys.md) | 移除网络包过滤规则。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [Action](arkts-mdm-action-e.md) | 数据包的行为。 |
| [Direction](arkts-mdm-direction-e.md) | 规则链。 |
| [IpSetMode](arkts-mdm-ipsetmode-e.md) | 以太网连接模式。 |
| [LogType](arkts-mdm-logtype-e.md) | 日志类型。 |
| [Protocol](arkts-mdm-protocol-e.md) | 网络协议。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AddMethod](arkts-mdm-addmethod-e-sys.md) | 添加网络包方法。 |
<!--DelEnd-->

