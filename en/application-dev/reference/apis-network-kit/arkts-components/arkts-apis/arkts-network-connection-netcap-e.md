# NetCap

Defines the network capability.

**Since:** 8

**System capability:** SystemCapability.Communication.NetManager.Core

## NET_CAPABILITY_MMS

```TypeScript
NET_CAPABILITY_MMS = 0
```

The network can connect to the carrier's Multimedia Messaging Service Center (MMSC) to send and receive multimedia messages.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetManager.Core

## NET_CAPABILITY_NOT_METERED

```TypeScript
NET_CAPABILITY_NOT_METERED = 11
```

The network traffic is not metered.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetManager.Core

## NET_CAPABILITY_INTERNET

```TypeScript
NET_CAPABILITY_INTERNET = 12
```

The network is capable of Internet access but the network connectivity is not successfully verified by the network management module. This capability is configured by the network provider. Your application can determine the network connectivity by **NET_CAPABILITY_VALIDATED** and **NET_CAPABILITY_CHECKING_CONNECTIVITY**.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetManager.Core

## NET_CAPABILITY_NOT_VPN

```TypeScript
NET_CAPABILITY_NOT_VPN = 15
```

The network does not use a virtual private network (VPN).

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetManager.Core

## NET_CAPABILITY_VALIDATED

```TypeScript
NET_CAPABILITY_VALIDATED = 16
```

The network management module successfully connects to the Huawei Cloud address through this network. This capability is configured by the network management module.

Note: If the network management module fails to connect to the Huawei Cloud address, this flag is not available in the network capability, but this does not mean a complete loss in Internet access. Note that for a newly connected network, this value may not reflect the actual verification result as network connectivity verification is in progress. Your application can use **NET_CAPABILITY_CHECKING_CONNECTIVITY**&lt;sup&gt;12+&lt;/sup&gt; to check whether network connectivity verification is in progress.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetManager.Core

## NET_CAPABILITY_PORTAL

```TypeScript
NET_CAPABILITY_PORTAL = 17
```

The network is found to have a captive portal and user login authentication is required. This capability is set by the connection management module.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NetManager.Core

## NET_CAPABILITY_CHECKING_CONNECTIVITY

```TypeScript
NET_CAPABILITY_CHECKING_CONNECTIVITY = 31
```

The network management module is verifying the network connectivity. This flag remains valid until the network connectivity check is complete. During this period, the value of **NET_CAPABILITY_VALIDATED** may be incorrect. After the network connectivity check is complete, this flag is cleared and your application can determine the network connectivity by checking **NET_CAPABILITY_VALIDATED**.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Communication.NetManager.Core
