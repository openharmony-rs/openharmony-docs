# Http_Proxy

```c
typedef struct Http_Proxy {...} Http_Proxy
```

## Overview

Defines the proxy configuration structure.

<!--Device-struct Http_Proxy {...}--><!--Device-struct Http_Proxy {...}-End-->

**System capability**: SystemCapability.Communication.NetStack

**Since**: 20

**Related module**: [netstack](capi-network-kit-netstack.md)

**Header file**: [net_http_type.h](capi-net-http-type-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [Http_ProxyType](capi-net-http-type-h.md#http_proxytype) proxyType | Proxy configuration type. For details, see [Http_ProxyType](capi-net-http-type-h.md#http_proxytype).<br><!--Device-Http_ProxyType proxyType--><!--Device-Http_ProxyType proxyType-End--> |
| [Http_CustomProxy](capi-netstack-http-customproxy.md) customProxy | Custom proxy configuration. For details, see [Http_CustomProxy](capi-netstack-http-customproxy.md).<br><!--Device-Http_CustomProxy customProxy--><!--Device-Http_CustomProxy customProxy-End--> |


