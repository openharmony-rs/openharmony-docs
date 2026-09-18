# ProxyConfiguration

```TypeScript
export type ProxyConfiguration = 'system' | 'no-proxy' | HttpProxy
```

Represents the HTTP proxy configuration.

**Since:** 12

**System capability:** SystemCapability.Communication.NetStack

| Type | Description |
| --- | --- |
| 'system' | The default network proxy is used. |
| 'no-proxy' | No network proxy is used. |
| [HttpProxy](arkts-network-websocket-httpproxy-t.md) | The specified network proxy is used. |
