# removeLocalService

## Modules to Import

```TypeScript
import { mdns } from '@kit.NetworkKit';
```

## removeLocalService

```TypeScript
function removeLocalService(context: Context, serviceInfo: LocalServiceInfo,
                              callback: AsyncCallback<LocalServiceInfo>): void
```

Removes an MDNS service. This API uses an asynchronous callback to return the result.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetManager.MDNS

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | Yes | Application context. <br>For details about the application context of the FA model, see Context. <br>For details about the application context of the stage model, see [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md). |
| serviceInfo | [LocalServiceInfo](arkts-network-mdns-localserviceinfo-i.md) | Yes | MDNS service information. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[LocalServiceInfo](arkts-network-mdns-localserviceinfo-i.md)&gt; | Yes | Callback used to return the result. If the operation is successful, **error** is **undefined** and **data** is the MDNS service information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [2100002](../errorcode-net-connection.md#2100002-service-connection-failure) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-system-internal-error) | System internal error. |
| [2204002](../errorcode-net-mdns.md#2204002-target-service-not-found) | Callback not found. |
| [2204008](../errorcode-net-mdns.md#2204008-service-deletion-failure) | Failed to delete the service instance. |
| [2204010](../errorcode-net-mdns.md#2204010-message-sending-failure) | Failed to send the message. |

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

let localServiceInfo: mdns.LocalServiceInfo = {
  serviceType: "_print._tcp",
  serviceName: "servicename",
  port: 5555,
  host: {
  address: "10.14.**.***",
  },
  serviceAttribute: [{key: "111", value: [1]}]
}

mdns.removeLocalService(context, localServiceInfo, (error: BusinessError, data: mdns.LocalServiceInfo) =>  {
  console.error(JSON.stringify(error));
  console.info(JSON.stringify(data));
});
```


<a id="removelocalservice-1"></a>

## removeLocalService

```TypeScript
function removeLocalService(context: Context, serviceInfo: LocalServiceInfo): Promise<LocalServiceInfo>
```

Removes an MDNS service. This API uses a promise to return the result.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Communication.NetManager.MDNS

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) | Yes | Application context. <br>For details about the application context of the FA model, see Context. <br>For details about the application context of the stage model, see [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md). |
| serviceInfo | [LocalServiceInfo](arkts-network-mdns-localserviceinfo-i.md) | Yes | MDNS service information. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[LocalServiceInfo](arkts-network-mdns-localserviceinfo-i.md)&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [2100002](../errorcode-net-connection.md#2100002-service-connection-failure) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-system-internal-error) | System internal error. |
| [2204002](../errorcode-net-mdns.md#2204002-target-service-not-found) | Callback not found. |
| [2204008](../errorcode-net-mdns.md#2204008-service-deletion-failure) | Failed to delete the service instance. |
| [2204010](../errorcode-net-mdns.md#2204010-message-sending-failure) | Failed to send the message. |

**Examples**

> NOTE
> 
> In the sample code provided in this topic, this.context is used to obtain UIAbilityContext, where this indicates a UIAbility instance inherited from UIAbility. To use UIAbilityContext APIs on pages, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

Stage model:

```TypeScript
import { mdns } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { common } from '@kit.AbilityKit';

let context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;

let localServiceInfo: mdns.LocalServiceInfo = {
  serviceType: "_print._tcp",
  serviceName: "servicename",
  port: 5555,
  host: {
  address: "10.14.**.***",
  },
  serviceAttribute: [{key: "111", value: [1]}]
}

mdns.removeLocalService(context, localServiceInfo).then((data: mdns.LocalServiceInfo) => {
  console.info(JSON.stringify(data));
});
```
