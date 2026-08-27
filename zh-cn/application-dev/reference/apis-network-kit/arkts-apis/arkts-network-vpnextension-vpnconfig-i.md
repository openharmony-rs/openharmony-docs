# VpnConfig

三方VPN配置参数。

**起始版本：** 11

**系统能力：** SystemCapability.Communication.NetManager.Vpn

## 导入模块

```TypeScript
import { vpnExtension } from '@kit.NetworkKit';
```

## addresses

```TypeScript
addresses: Array<LinkAddress>
```

VPN虚拟网卡的IP地址。API version 23之前，最多支持64个IP地址；从API version 23开始，最多支持2000个IP地址。

**类型：** Array&lt;LinkAddress&gt;

**起始版本：** 11

**系统能力：** SystemCapability.Communication.NetManager.Vpn

## blockedApplications

```TypeScript
blockedApplications?: Array<string>
```

被阻止的应用信息列表，string类型表示的包名。当配置该列表后，该列表中的应用数据不会被VPN代理，其他应用可以根据routes配置被VPN代理。API version 23前最多可配置64个被阻止的应用包名；从API version 23开始最多可配置256个被阻止的应用包名。  
**注意**：trustedApplications和blockedApplications列表不能同时配置。

**类型：** Array&lt;string&gt;

**起始版本：** 11

**系统能力：** SystemCapability.Communication.NetManager.Vpn

## dnsAddresses

```TypeScript
dnsAddresses?: Array<string>
```

DNS服务器地址信息。当配置DNS服务器地址后，VPN启动状态下被代理的应用上网时，使用配置的DNS服务器做DNS查询。

**类型：** Array&lt;string&gt;

**起始版本：** 11

**系统能力：** SystemCapability.Communication.NetManager.Vpn

## isBlocking

```TypeScript
isBlocking?: boolean
```

是否阻塞模式。true表示阻塞模式，false表示非阻塞模式, 默认值为false。

**类型：** boolean

**起始版本：** 11

**系统能力：** SystemCapability.Communication.NetManager.Vpn

## isInternal

```TypeScript
isInternal?: boolean
```

是否支持内置VPN。true表示支持，false表示不支持, 默认值为false。

**类型：** boolean

**起始版本：** 11

**系统能力：** SystemCapability.Communication.NetManager.Vpn

## isIPv4Accepted

```TypeScript
isIPv4Accepted?: boolean
```

是否支持IPv4。true表示支持，false表示不支持, 默认值为true。  
**注意**：若支持IPv4功能，需要在addresses中配置IPv4类型的IP地址。

**类型：** boolean

**起始版本：** 11

**系统能力：** SystemCapability.Communication.NetManager.Vpn

## isIPv6Accepted

```TypeScript
isIPv6Accepted?: boolean
```

是否支持IPv6。true表示支持，false表示不支持, 默认值为false。  
**注意**：若支持IPv6功能，需要在addresses中配置IPv6类型的IP地址。

**类型：** boolean

**起始版本：** 11

**系统能力：** SystemCapability.Communication.NetManager.Vpn

## mtu

```TypeScript
mtu?: number
```

最大传输单元MTU值（单位：字节）。取值范围：[576，1500]。

**类型：** number

**起始版本：** 11

**系统能力：** SystemCapability.Communication.NetManager.Vpn

## routes

```TypeScript
routes?: Array<RouteInfo>
```

VPN虚拟网卡的路由信息（API version 23前最多可配置1024条路由；从API version 23开始最多可配置10000条路由）。

**类型：** Array&lt;RouteInfo&gt;

**起始版本：** 11

**系统能力：** SystemCapability.Communication.NetManager.Vpn

## searchDomains

```TypeScript
searchDomains?: Array<string>
```

DNS的搜索域列表。

**类型：** Array&lt;string&gt;

**起始版本：** 11

**系统能力：** SystemCapability.Communication.NetManager.Vpn

## trustedApplications

```TypeScript
trustedApplications?: Array<string>
```

受信任的应用信息列表，string类型表示的包名。当配置该列表后，仅该列表中的应用数据才能根据routes被VPN代理。API version 23前最多可配置64个受信任的应用包名；从API version 23开始最多可配 置256个受信任的应用包名。  
**注意**：trustedApplications和blockedApplications列表不能同时配置。

**类型：** Array&lt;string&gt;

**起始版本：** 11

**系统能力：** SystemCapability.Communication.NetManager.Vpn

## vpnId

```TypeScript
vpnId?: string
```

VPN唯一标识。

**类型：** string

**起始版本：** 20

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**示例**

```TypeScript
import { vpnExtension} from '@kit.NetworkKit';

let vpnConfig: vpnExtension.VpnConfig = {
  addresses: [],
  vpnId: '123',
  routes: [{
    // 网卡名称配置为空时，系统默认将路由配置到VPN虚拟网卡。
    // 如填写非虚拟网卡实际名称，可能导致路由配置异常。
    interface: "vpn-tun",
    destination: {
      address: {
        address:'',
        family:1,
        port:8080
      },
      prefixLength:1
    },
    gateway: {
      // 网关地址配置为空时，系统默认将VPN虚拟网卡地址作为网关地址。
      // 如需使用非VPN虚拟网卡地址，请确保地址可达，否则可能导致路由配置失败。
      address:'',
      family:1,
      port:8080
    },
    hasGateway: true,
    isDefaultRoute: true,
  }],
  mtu: 1400,
  dnsAddresses: ["223.5.5.5", "223.6.6.6"],
  trustedApplications: [],
  blockedApplications: [],
}
let context: vpnExtension.VpnExtensionContext;

function vpnCreate(){
  let vpnConnection: vpnExtension.VpnConnection = vpnExtension.createVpnConnection(context);
  vpnConnection.create(vpnConfig).then((data) => {
    console.info("VPN create " + JSON.stringify(data));
  })
}
```
