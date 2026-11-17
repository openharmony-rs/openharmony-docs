# P2pServiceDiscoveryInfo

```TypeScript
type P2pServiceDiscoveryInfo = P2pDnsSdInfo | P2pDnsSdTxtInfo | P2pUpnpInfo | P2pGenericInfo
```

表示从对端设备收到的P2P服务发现响应信息。具体类型由响应的服务协议类型决定。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-wifiManager-type P2pServiceDiscoveryInfo = P2pDnsSdInfo | P2pDnsSdTxtInfo | P2pUpnpInfo | P2pGenericInfo--><!--Device-wifiManager-type P2pServiceDiscoveryInfo = P2pDnsSdInfo | P2pDnsSdTxtInfo | P2pUpnpInfo | P2pGenericInfo-End-->

**系统能力：** SystemCapability.Communication.WiFi.P2P

| 类型 | 说明 |
| --- | --- |
| [P2pDnsSdInfo](arkts-connectivity-wifimanager-p2pdnssdinfo-i.md) | 从对端设备收到的DNS-SD服务响应信息。 |
| [P2pDnsSdTxtInfo](arkts-connectivity-wifimanager-p2pdnssdtxtinfo-i.md) | 从对端设备收到的DNS-SD TXT记录信息。 |
| [P2pUpnpInfo](arkts-connectivity-wifimanager-p2pupnpinfo-i.md) | 从对端设备收到的UPnP服务响应信息。 |
| [P2pGenericInfo](arkts-connectivity-wifimanager-p2pgenericinfo-i.md) | 从对端设备收到的通用服务响应信息。 |
