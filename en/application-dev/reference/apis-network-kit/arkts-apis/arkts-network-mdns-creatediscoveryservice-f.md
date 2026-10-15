# createDiscoveryService

## Modules to Import

```TypeScript
import { mdns } from '@kit.NetworkKit';
```

## createDiscoveryService

```TypeScript
function createDiscoveryService(context: Context, serviceType: string): DiscoveryService
```

Creates a **DiscoveryService** object, which is used to discover MDNS services of the specified type.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-mdns-function createDiscoveryService(context: Context, serviceType: string): DiscoveryService--><!--Device-mdns-function createDiscoveryService(context: Context, serviceType: string): DiscoveryService-End-->

**System capability:** SystemCapability.Communication.NetManager.MDNS

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | Yes | Application context. <br>For details about the application context of the FA model, see [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context.md). <br>For details about the application context of the stage model, see [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md). |
| serviceType | string | Yes | MDNS service type. |

**Return value:**

| Type | Description |
| --- | --- |
| [DiscoveryService](arkts-network-mdns-discoveryservice-i.md) | **DiscoveryService** object obtained based on the specified **serviceType** and **context**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |

**Examples**

> NOTE
> 
> In the examples in this document, this.context is used to obtain the UIAbilityContext, where this represents the UIAbility instance inherited from UIAbility. To use the capabilities provided by UIAbilityContext on a page, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

Stage model:

```TypeScript
import { mdns } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

// Obtain the application context.
let context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;

let serviceType = "_print._tcp";
let discoveryService : Object = mdns.createDiscoveryService(context, serviceType);
```
