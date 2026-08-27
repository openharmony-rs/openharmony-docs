# NetCap

网络具体能力。

**起始版本：** 8

**系统能力：** SystemCapability.Communication.NetManager.Core

## NET_CAPABILITY_MMS

```TypeScript
NET_CAPABILITY_MMS = 0
```

表示网络可以访问运营商的MMSC（Multimedia Message Service，多媒体短信服务）发送和接收彩信。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NetManager.Core

## NET_CAPABILITY_NOT_METERED

```TypeScript
NET_CAPABILITY_NOT_METERED = 11
```

表示网络流量未被计费。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NetManager.Core

## NET_CAPABILITY_INTERNET

```TypeScript
NET_CAPABILITY_INTERNET = 12
```

表示该网络应具有访问Internet的能力，此能力由网络提供者设置，但该网络访问Internet的连通性并未被网络管理成功验证。网络连通性可以通过NET_CAPABILITY_VALIDATED和 NET_CAPABILITY_CHECKING_CONNECTIVITY判断。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NetManager.Core

## NET_CAPABILITY_NOT_VPN

```TypeScript
NET_CAPABILITY_NOT_VPN = 15
```

表示网络不使用VPN（Virtual Private Network，虚拟专用网络）。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NetManager.Core

## NET_CAPABILITY_VALIDATED

```TypeScript
NET_CAPABILITY_VALIDATED = 16
```

表示网络管理通过该网络与华为云地址成功建立连接，此能力由网络管理模块设置。  
**注意：** 网络管理可能会与华为云地址建立连接失败，导致网络能力不具备此标记位，但不完全代表该网络无法访问互联网。另外，对于新完成连接的网络，由于网络正在进行连通性验证，此值可能无法反映真实的验证结果。对此，应用可以通过 NET_CAPABILITY_CHECKING_CONNECTIVITY&lt;sup&gt;12+&lt;/sup&gt;检查网络是否正在检测连通性。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NetManager.Core

## NET_CAPABILITY_PORTAL

```TypeScript
NET_CAPABILITY_PORTAL = 17
```

表示系统发现该网络存在强制网络门户，需要用户登陆认证，该能力由网络管理模块设置。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NetManager.Core

## NET_CAPABILITY_CHECKING_CONNECTIVITY

```TypeScript
NET_CAPABILITY_CHECKING_CONNECTIVITY = 31
```

表示网络管理正在检验当前网络的连通性，此值会在网络连接时设置。当此值存在时，NET_CAPABILITY_VALIDATED的值不准确，连通性检测结束后不再设置，此时可以通过判断NetCap是否包含 NET_CAPABILITY_VALIDATED判断连通性。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NetManager.Core
