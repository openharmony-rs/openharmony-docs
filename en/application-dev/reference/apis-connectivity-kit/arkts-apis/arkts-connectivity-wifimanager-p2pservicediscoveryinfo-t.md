# P2pServiceDiscoveryInfo

```TypeScript
type P2pServiceDiscoveryInfo = P2pDnsSdInfo | P2pDnsSdTxtInfo | P2pUpnpInfo | P2pGenericInfo
```

Represents the P2P service discovery response information received from a peer device. The specific type is determined by the service protocol type of the response.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-wifiManager-type P2pServiceDiscoveryInfo = P2pDnsSdInfo | P2pDnsSdTxtInfo | P2pUpnpInfo | P2pGenericInfo--><!--Device-wifiManager-type P2pServiceDiscoveryInfo = P2pDnsSdInfo | P2pDnsSdTxtInfo | P2pUpnpInfo | P2pGenericInfo-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

| Type | Description |
| --- | --- |
| [P2pDnsSdInfo](arkts-connectivity-wifimanager-p2pdnssdinfo-i.md) | DNS-SD service response information received from a peer device. |
| [P2pDnsSdTxtInfo](arkts-connectivity-wifimanager-p2pdnssdtxtinfo-i.md) | DNS-SD TXT record information received from a peer device. |
| [P2pUpnpInfo](arkts-connectivity-wifimanager-p2pupnpinfo-i.md) | UPnP service response information received from a peer device. |
| [P2pGenericInfo](arkts-connectivity-wifimanager-p2pgenericinfo-i.md) | Generic service response information received from a peer device. |
