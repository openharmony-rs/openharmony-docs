# @ohos.secureElement(SE Management)

The **secureElement** module provides APIs for managing secure elements (SEs). SEs include the Embedded SE (eSE) and SIM on a device. The SE service mentioned in this topic is an **SEService** instance. For details, see [createService](arkts-connectivity-omapi-createservice-f.md).

**Since:** 10

**System capability:** SystemCapability.Communication.SecureElement

## Modules to Import

```TypeScript
import { omapi } from '@kit.ConnectivityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [createService](arkts-connectivity-omapi-createservice-f.md) | Creates an **SEService** instance for connecting to all available SEs in the system. The connection is time- consuming. Therefore, only asynchronous APIs are provided. This API uses a promise to return the result. |
| [newSEService](arkts-connectivity-omapi-newseservice-f.md#newseserviceservicestate) | Creates an **SEService** instance for connecting to all available SEs in the system. The connection is time- consuming. Therefore, this API supports only the asynchronous mode. This API uses an asynchronous callback to return the result. |
| [off](arkts-connectivity-omapi-off-f.md#offstatechanged) | Disables listening for service status change events. |
| [on](arkts-connectivity-omapi-on-f.md#onstatechanged) | Enables listening for service status change events. |

### Interfaces

| Name | Description |
| --- | --- |
| [Channel](arkts-connectivity-omapi-channel-i.md) | A **Channel** instance indicates a channel set up by a **Session** instance. The channel can be a basic channel or a logical channel. You can use [Session.openBasicChannel](arkts-connectivity-omapi-session-i.md#openbasicchannel) or [Session.openLogicalChannel](arkts-connectivity-omapi-session-i.md#openlogicalchannel) to obtain a channel instance. |
| [Reader](arkts-connectivity-omapi-reader-i.md) | Obtains the SE supported by the device. If eSE, SIM, and SIM2 are supported, three instances will be returned. SIM2 is supported since API version 22. You can use [SEService.getReaders](arkts-connectivity-omapi-seservice-i.md#getreaders) to obtain a **Reader** instance. |
| [SEService](arkts-connectivity-omapi-seservice-i.md) | **SEService** indicates the connection service used to connect to all available SEs in the system. You can use [createService](arkts-connectivity-omapi-createservice-f.md) to create an **SEService** instance. |
| [Session](arkts-connectivity-omapi-session-i.md) | A **Session** instance indicates a session created on an SE **Reader** instance. You can use [Reader.openSession](arkts-connectivity-omapi-reader-i.md#opensession) to obtain a **Session** instance. |

### Enums

| Name | Description |
| --- | --- |
| [ServiceState](arkts-connectivity-omapi-servicestate-e.md) | Enumerates the SE service states. |
