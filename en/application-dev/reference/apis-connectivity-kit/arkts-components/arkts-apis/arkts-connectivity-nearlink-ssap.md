# @ohos.nearlink.ssap(NearLink SSAP Connection Capability)

This module provides the SparkLink Service Access Protocol (SSAP) connection capability, including creating and connecting to a client, calling server methods, reading and writing descriptors, and subscribing to event notifications.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

## Modules to Import

```TypeScript
import { ssap } from '@kit.ConnectivityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [createClient](arkts-connectivity-ssap-createclient-f.md) | Creates an SSAP client instance. |
| [createServer](arkts-connectivity-ssap-createserver-f.md) | Creates an SSAP server instance. |

### Interfaces

| Name | Description |
| --- | --- |
| [Client](arkts-connectivity-ssap-client-i.md) | Represents a SSAP client class. It provides APIs for connecting to and transmitting data with the server. |
| [ConnectionChangeState](arkts-connectivity-ssap-connectionchangestate-i.md) | Defines the connection status reporting parameters. |
| [Property](arkts-connectivity-ssap-property-i.md) | Represents a service Property. |
| [PropertyDescriptor](arkts-connectivity-ssap-propertydescriptor-i.md) | Defines the descriptor of a property. |
| [PropertyReadRequest](arkts-connectivity-ssap-propertyreadrequest-i.md) | Represents the Property read request parameter of the client. |
| [PropertyWriteRequest](arkts-connectivity-ssap-propertywriterequest-i.md) | Define a client property write request. |
| [Server](arkts-connectivity-ssap-server-i.md) | Represents a SSAP server class, which provides APIs for connecting to and exchanging data with the client. |
| [ServerResponse](arkts-connectivity-ssap-serverresponse-i.md) | Defines a response to a client request. |
| [Service](arkts-connectivity-ssap-service-i.md) | Represents the NearLink service. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [Client](arkts-connectivity-ssap-client-i-sys.md) | Represents a SSAP client class. It provides APIs for connecting to and transmitting data with the server. |
| [Event](arkts-connectivity-ssap-event-i-sys.md) | Represents a service event. |
| [Method](arkts-connectivity-ssap-method-i-sys.md) | Represents a method of the service. |
| [Service](arkts-connectivity-ssap-service-i-sys.md) | Represents the NearLink service. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [Operation](arkts-connectivity-ssap-operation-e.md) | Enumerates the operation types supported by a property. |
| [PropertyDescriptorType](arkts-connectivity-ssap-propertydescriptortype-e.md) | Enumerates the property descriptor types. |
| [PropertyWriteType](arkts-connectivity-ssap-propertywritetype-e.md) | Enumerates the write types supported by a property. |

### Types

| Name | Description |
| --- | --- |
| [ConnectionState](arkts-connectivity-ssap-connectionstate-t.md) | Enumerates the connection states with a remote device. |
