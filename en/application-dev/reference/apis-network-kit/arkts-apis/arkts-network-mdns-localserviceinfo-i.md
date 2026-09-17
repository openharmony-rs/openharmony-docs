# LocalServiceInfo

MDNS service information.

**Since:** 10

**System capability:** SystemCapability.Communication.NetManager.MDNS

## Modules to Import

```TypeScript
import { mdns } from '@kit.NetworkKit';
```

## host

```TypeScript
host?: NetAddress
```

IP address of the device that provides the MDNS service. The IP address is not effective when an MDNS service is added or removed.

**Type:** [NetAddress](arkts-network-mdns-netaddress-t.md)

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetManager.MDNS

## port

```TypeScript
port?: number
```

Service port number. The value range is [0, 65535].

**Type:** number

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetManager.MDNS

## serviceAttribute

```TypeScript
serviceAttribute?: Array<ServiceAttribute>
```

MDNS service attribute information.

**Type:** Array&lt;[ServiceAttribute](arkts-network-mdns-serviceattribute-i.md)&gt;

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetManager.MDNS

## serviceName

```TypeScript
serviceName: string
```

MDNS service name.

**Type:** string

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetManager.MDNS

## serviceType

```TypeScript
serviceType: string
```

MDNS service type. The value is in the format of **_&lt;name&gt;.&lt;_tcp/_udp&gt;**, where **name** contains a maximum of 63 characters excluding periods (.).

**Type:** string

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetManager.MDNS
