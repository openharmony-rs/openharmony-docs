# DiscoveryService

```TypeScript
export interface DiscoveryService
```

Defines a **DiscoveryService** object for discovering MDNS services of the specified type.

**Since:** 10

**System capability:** SystemCapability.Communication.NetManager.MDNS

## Modules to Import

```TypeScript
import { mdns } from '@kit.NetworkKit';
```

## off('discoveryStart')

```TypeScript
off(type: 'discoveryStart', callback?: Callback<DiscoveryEventInfo>): void
```

Disables listening for **discoveryStart** events.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetManager.MDNS

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'discoveryStart' | Yes | Event type. This field has a fixed value of **discoveryStart**.<br>**discoveryStart**: event of starting discovery of MDNS services on the LAN. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[DiscoveryEventInfo](arkts-network-mdns-discoveryeventinfo-i.md)&gt; | No | Callback used to return the MDNS service and error information. You can pass the callback of the **on** function if you want to cancel listening for a certain type of events. If you do not pass the callback, you will cancel listening for all events.<br>**Since:** 11 |

**Examples**

> NOTE
> 
> In the sample code provided in this topic, this.context is used to obtain UIAbilityContext, where this indicates a UIAbility instance inherited from UIAbility. To use UIAbilityContext APIs on pages, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```TypeScript
import { mdns } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// See mdns.createDiscoveryService.
let context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
let serviceType = "_print._tcp";
let discoveryService = mdns.createDiscoveryService(context, serviceType);
discoveryService.startSearchingMDNS();

discoveryService.on('discoveryStart', (data: mdns.DiscoveryEventInfo) => {
  console.info(JSON.stringify(data));
});

discoveryService.stopSearchingMDNS();

discoveryService.off('discoveryStart', (data: mdns.DiscoveryEventInfo) => {
  console.info(JSON.stringify(data));
});
```

## off('discoveryStop')

```TypeScript
off(type: 'discoveryStop', callback?: Callback<DiscoveryEventInfo>): void
```

Disables listening for **discoveryStop** events.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetManager.MDNS

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'discoveryStop' | Yes | Event type. This field has a fixed value of **discoveryStop**.<br>**discoveryStop**: event of stopping discovery of MDNS services on the LAN. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[DiscoveryEventInfo](arkts-network-mdns-discoveryeventinfo-i.md)&gt; | No | Callback used to return the MDNS service and error information. You can pass the callback of the **on** function if you want to cancel listening for a certain type of events. If you do not pass the callback, you will cancel listening for all events.<br>**Since:** 11 |

## off('serviceFound')

```TypeScript
off(type: 'serviceFound', callback?: Callback<LocalServiceInfo>): void
```

Disables listening for **serviceFound** events.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetManager.MDNS

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'serviceFound' | Yes | Event type. This field has a fixed value of **serviceFound**.<br>**serviceFound**: event indicating an MDNS service is found. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[LocalServiceInfo](arkts-network-mdns-localserviceinfo-i.md)&gt; | No | MDNS service information. You can pass the callback of the **on** function if you want to cancel listening for a certain type of events. If you do not pass the callback, you will cancel listening for all events.<br>**Since:** 11 |

**Examples**

> NOTE
> 
> In the sample code provided in this topic, this.context is used to obtain UIAbilityContext, where this indicates a UIAbility instance inherited from UIAbility. To use UIAbilityContext APIs on pages, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```TypeScript
import { mdns } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// See mdns.createDiscoveryService.
let context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
let serviceType = "_print._tcp";
let discoveryService = mdns.createDiscoveryService(context, serviceType);
discoveryService.startSearchingMDNS();

discoveryService.on('serviceFound', (data: mdns.LocalServiceInfo) => {
  console.info('serviceFound', JSON.stringify(data));
  mdns.resolveLocalService(context, data, (error: BusinessError, resolveData: mdns.LocalServiceInfo) =>  {
    console.info('serviceFound', JSON.stringify(resolveData));
  });
});

discoveryService.stopSearchingMDNS();

discoveryService.off('serviceFound', (data: mdns.LocalServiceInfo) => {
  console.info(JSON.stringify(data));
});
```

## off('serviceLost')

```TypeScript
off(type: 'serviceLost', callback?: Callback<LocalServiceInfo>): void
```

Disables listening for **serviceLost** events.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetManager.MDNS

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'serviceLost' | Yes | Event type. This field has a fixed value of **serviceLost**.<br>**serviceLost**: event indicating that an MDNS service is removed. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[LocalServiceInfo](arkts-network-mdns-localserviceinfo-i.md)&gt; | No | MDNS service information. You can pass the callback of the **on** function if you want to cancel listening for a certain type of events. If you do not pass the callback, you will cancel listening for all events. |

**Examples**

> NOTE
> 
> In the sample code provided in this topic, this.context is used to obtain UIAbilityContext, where this indicates a UIAbility instance inherited from UIAbility. To use UIAbilityContext APIs on pages, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```TypeScript
import { mdns } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// See mdns.createDiscoveryService.
let context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
let serviceType = "_print._tcp";
let discoveryService = mdns.createDiscoveryService(context, serviceType);
discoveryService.startSearchingMDNS();

discoveryService.on('serviceLost', (data: mdns.LocalServiceInfo) => {
  console.info(JSON.stringify(data));
});

discoveryService.stopSearchingMDNS();

discoveryService.off('serviceLost', (data: mdns.LocalServiceInfo) => {
  console.info(JSON.stringify(data));
});
```

## on('discoveryStart')

```TypeScript
on(type: 'discoveryStart', callback: Callback<DiscoveryEventInfo>): void
```

Enables listening for **discoveryStart** events.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetManager.MDNS

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'discoveryStart' | Yes | Event type. This field has a fixed value of **discoveryStart**.<br>**discoveryStart**: event of starting discovery of MDNS services on the LAN. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[DiscoveryEventInfo](arkts-network-mdns-discoveryeventinfo-i.md)&gt; | Yes | Callback used to return the MDNS service and error information.<br>**Since:** 11 |

**Examples**

> NOTE
> 
> In the sample code provided in this topic, this.context is used to obtain UIAbilityContext, where this indicates a UIAbility instance inherited from UIAbility. To use UIAbilityContext APIs on pages, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```TypeScript
import { mdns } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// See mdns.createDiscoveryService.
let context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
let serviceType = "_print._tcp";
let discoveryService = mdns.createDiscoveryService(context, serviceType);
discoveryService.startSearchingMDNS();

discoveryService.on('discoveryStart', (data: mdns.DiscoveryEventInfo) => {
  console.info(JSON.stringify(data));
});

discoveryService.stopSearchingMDNS();
```

## on('discoveryStop')

```TypeScript
on(type: 'discoveryStop', callback: Callback<DiscoveryEventInfo>): void
```

Enables listening for **discoveryStop** events.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetManager.MDNS

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'discoveryStop' | Yes | Event type. This field has a fixed value of **discoveryStop**.<br>**discoveryStop**: event of stopping discovery of MDNS services on the LAN. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[DiscoveryEventInfo](arkts-network-mdns-discoveryeventinfo-i.md)&gt; | Yes | Callback used to return the MDNS service and error information.<br>**Since:** 11 |

**Examples**

> NOTE
> 
> In the sample code provided in this topic, this.context is used to obtain UIAbilityContext, where this indicates a UIAbility instance inherited from UIAbility. To use UIAbilityContext APIs on pages, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```TypeScript
import { mdns } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// See mdns.createDiscoveryService.
let context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
let serviceType = "_print._tcp";
let discoveryService = mdns.createDiscoveryService(context, serviceType);
discoveryService.startSearchingMDNS();

discoveryService.on('discoveryStop', (data: mdns.DiscoveryEventInfo) => {
  console.info(JSON.stringify(data));
});

discoveryService.stopSearchingMDNS();
```

## on('serviceFound')

```TypeScript
on(type: 'serviceFound', callback: Callback<LocalServiceInfo>): void
```

Enables listening for **serviceFound** events.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetManager.MDNS

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'serviceFound' | Yes | Event type. This field has a fixed value of **serviceFound**.<br>**serviceFound**: event indicating an MDNS service is found. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[LocalServiceInfo](arkts-network-mdns-localserviceinfo-i.md)&gt; | Yes | Callback used to return the MDNS service information. You need to call **resolveLocalService** to parse the information. |

**Examples**

> NOTE
> 
> In the sample code provided in this topic, this.context is used to obtain UIAbilityContext, where this indicates a UIAbility instance inherited from UIAbility. To use UIAbilityContext APIs on pages, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```TypeScript
import { mdns } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// See mdns.createDiscoveryService.
let context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
let serviceType = "_print._tcp";
let discoveryService = mdns.createDiscoveryService(context, serviceType);
discoveryService.startSearchingMDNS();

discoveryService.on('serviceFound', (data: mdns.LocalServiceInfo) => {
  console.info('serviceFound', JSON.stringify(data));
  mdns.resolveLocalService(context, data, (error: BusinessError, resolveData: mdns.LocalServiceInfo) =>  {
    console.info('serviceFound', JSON.stringify(resolveData));
  });
});

discoveryService.stopSearchingMDNS();
```

## on('serviceLost')

```TypeScript
on(type: 'serviceLost', callback: Callback<LocalServiceInfo>): void
```

Enables listening for **serviceLost** events.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetManager.MDNS

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'serviceLost' | Yes | Event type. This field has a fixed value of **serviceLost**.<br>**serviceLost**: event indicating that an MDNS service is removed. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[LocalServiceInfo](arkts-network-mdns-localserviceinfo-i.md)&gt; | Yes | MDNS service information. |

**Examples**

> NOTE
> 
> In the sample code provided in this topic, this.context is used to obtain UIAbilityContext, where this indicates a UIAbility instance inherited from UIAbility. To use UIAbilityContext APIs on pages, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```TypeScript
import { mdns } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// See mdns.createDiscoveryService.
let context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
let serviceType = "_print._tcp";
let discoveryService = mdns.createDiscoveryService(context, serviceType);
discoveryService.startSearchingMDNS();

discoveryService.on('serviceLost', (data: mdns.LocalServiceInfo) => {
  console.info(JSON.stringify(data));
});

discoveryService.stopSearchingMDNS();
```

## startSearchingMDNS

```TypeScript
startSearchingMDNS(): void
```

Searches for MDNS services on the LAN.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetManager.MDNS

**Examples**

> NOTE
> 
> In the sample code provided in this topic, this.context is used to obtain UIAbilityContext, where this indicates a UIAbility instance inherited from UIAbility. To use UIAbilityContext APIs on pages, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

Stage model:

```TypeScript
import { mdns } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Obtain the application context.
let context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
let serviceType = "_print._tcp";
let discoveryService = mdns.createDiscoveryService(context, serviceType);
discoveryService.startSearchingMDNS();
```

## stopSearchingMDNS

```TypeScript
stopSearchingMDNS(): void
```

Stops searching for MDNS services on the LAN.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetManager.MDNS

**Examples**

> NOTE
> 
> In the sample code provided in this topic, this.context is used to obtain UIAbilityContext, where this indicates a UIAbility instance inherited from UIAbility. To use UIAbilityContext APIs on pages, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

Stage model:

```TypeScript
import { mdns } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Obtain the application context.
let context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
let serviceType = "_print._tcp";
let discoveryService = mdns.createDiscoveryService(context, serviceType);
discoveryService.stopSearchingMDNS();
```
