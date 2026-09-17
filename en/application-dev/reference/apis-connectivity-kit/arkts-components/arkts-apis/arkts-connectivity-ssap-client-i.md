# Client

Represents a SSAP client class. It provides APIs for connecting to and transmitting data with the server.

Before using the methods of this class, use the [ssap.createClient](arkts-connectivity-ssap-createclient-f.md) method to construct an instance of this class.

An app only needs to create one [Client](arkts-connectivity-ssap-client-i.md) instance for a remote device. Repeated creation will increase unnecessary resource overhead.

**Since:** 26.0.0

**System capability:** SystemCapability.Communication.NearLink.Base

## Modules to Import

```TypeScript
import { ssap } from '@kit.ConnectivityKit';
```

## close

```TypeScript
close(): void
```

Closes the client and disconnects from the remote server. To terminate the current connection while retaining the instance, use the [disconnect](#disconnect) method.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESS_NEARLINK

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [36100003](../errorcode-nearlink-service.md#36100003-nearlink-disabled) | NearLink disabled. |
| [36100099](../errorcode-nearlink-service.md#36100099-operation-failed) | Operation failed. |

## connect

```TypeScript
connect(): Promise<void>
```

Initiates a connection to the server. This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESS_NEARLINK

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [36100003](../errorcode-nearlink-service.md#36100003-nearlink-disabled) | NearLink disabled. |
| [36100099](../errorcode-nearlink-service.md#36100099-operation-failed) | Operation failed. |

## disconnect

```TypeScript
disconnect(): Promise<void>
```

Initiates a disconnection to the server, disconnecting an existing connection or terminating a connection being established. This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESS_NEARLINK

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [36100003](../errorcode-nearlink-service.md#36100003-nearlink-disabled) | NearLink disabled. |
| [36100099](../errorcode-nearlink-service.md#36100099-operation-failed) | Operation failed. |

## getServices

```TypeScript
getServices(): Promise<Service[]>
```

Obtains the list of services supported by the server. This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESS_NEARLINK

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Service](arkts-connectivity-ssap-service-i.md)[]&gt; | Promise used to return the result. The list of services supported by the server. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [36100003](../errorcode-nearlink-service.md#36100003-nearlink-disabled) | NearLink disabled. |
| [36100099](../errorcode-nearlink-service.md#36100099-operation-failed) | Operation failed. |

## offConnectionStateChange

```TypeScript
offConnectionStateChange(callback?: Callback<ConnectionChangeState>): void
```

Unsubscribes from the connection status change event. This API uses an asynchronous callback to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ConnectionChangeState](arkts-connectivity-ssap-connectionchangestate-i.md)&gt; | No | Callback used to return the connection status reporting parameters.<br>If this parameter is specified, the current callback is unregistered. If this parameter is not specified, all callbacks corresponding to the event are unregistered. |

## offMtuChange

```TypeScript
offMtuChange(callback?: Callback<number>): void
```

Unsubscribes from the MTU change event. This API uses an asynchronous callback to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | No | Callback used to return the MTU after negotiation.<br>If this parameter is specified, the current callback is unregistered. If this parameter is not specified, all callbacks corresponding to the event are unregistered. |

## offPropertyChange

```TypeScript
offPropertyChange(callback?: Callback<Property>): void
```

Unsubscribes from the property change event. This API uses an asynchronous callback to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[Property](arkts-connectivity-ssap-property-i.md)&gt; | No | Callback used to return the property from the server.<br>If this parameter is specified, the current callback is unregistered. If this parameter is not specified, all callbacks corresponding to the event are unregistered. |

## onConnectionStateChange

```TypeScript
onConnectionStateChange(callback: Callback<ConnectionChangeState>): void
```

Subscribes to the connection status change event. This API uses an asynchronous callback to return the result.

The app must have the **ohos.permission.ACCESS_NEARLINK** permission to receive this event.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ConnectionChangeState](arkts-connectivity-ssap-connectionchangestate-i.md)&gt; | Yes | Callback used to return the connection status reporting parameters. |

## onMtuChange

```TypeScript
onMtuChange(callback: Callback<number>): void
```

Subscribes to the MTU change event. This API uses an asynchronous callback to return the result.

The app must have the **ohos.permission.ACCESS_NEARLINK** permission to receive this event.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | Yes | Callback used to return the MTU after negotiation. |

## onPropertyChange

```TypeScript
onPropertyChange(callback: Callback<Property>): void
```

Subscribes to the property change event. This API uses an asynchronous callback to return the result.

The app must have the **ohos.permission.ACCESS_NEARLINK** permission to receive this event.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[Property](arkts-connectivity-ssap-property-i.md)&gt; | Yes | Callback used to return the Property of the service. |

## readProperty

```TypeScript
readProperty(property: Property): Promise<Property>
```

Reads a server attribute. This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESS_NEARLINK

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| property | [Property](arkts-connectivity-ssap-property-i.md) | Yes | Server attribute. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Property](arkts-connectivity-ssap-property-i.md)&gt; | Promise used to return the server attribute. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [36100003](../errorcode-nearlink-service.md#36100003-nearlink-disabled) | NearLink disabled. |
| [36100043](../errorcode-nearlink-service.md#36100043-invalid-uuid) | Invalid UUID in property. |
| [36100044](../errorcode-nearlink-service.md#36100044-standard-nearlink-service-uuid-not-allowed) | NearLink standard UUID not allowed. |
| [36100099](../errorcode-nearlink-service.md#36100099-operation-failed) | Operation failed. |

## requestMtuSize

```TypeScript
requestMtuSize(mtu: number): Promise<void>
```

Initiates an MTU negotiation request. This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESS_NEARLINK

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mtu | number | Yes | MTU parameter. The default value is **251**.<br>Unit: byte. Value range: [22, 1024], |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [36100003](../errorcode-nearlink-service.md#36100003-nearlink-disabled) | NearLink disabled. |
| [36100099](../errorcode-nearlink-service.md#36100099-operation-failed) | Operation failed. |

## setPropertyNotification

```TypeScript
setPropertyNotification(property: Property, enable: boolean): Promise<void>
```

Sets a [Property](arkts-connectivity-ssap-property-i.md) change notification. This method can only be used after a connection is successfully established by calling [connect](#connect).

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESS_NEARLINK

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| property | [Property](arkts-connectivity-ssap-property-i.md) | Yes | Property from the server. This property must support the **NOTIFY** operation. That is, **operation** contains **NOTIFY**. For details, see [Operation](arkts-connectivity-ssap-operation-e.md). |
| enable | boolean | Yes | Whether to enable notification. **true**: enables notification. **false**: disables notification. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. No return value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [36100003](../errorcode-nearlink-service.md#36100003-nearlink-disabled) | NearLink disabled. |
| [36100043](../errorcode-nearlink-service.md#36100043-invalid-uuid) | Invalid UUID in property. |
| [36100044](../errorcode-nearlink-service.md#36100044-standard-nearlink-service-uuid-not-allowed) | NearLink standard UUID not allowed. |
| [36100099](../errorcode-nearlink-service.md#36100099-operation-failed) | Operation failed. |

## writeProperty

```TypeScript
writeProperty(property: Property, writeType: PropertyWriteType): Promise<void>
```

Writes a property to the server. This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ACCESS_NEARLINK

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| property | [Property](arkts-connectivity-ssap-property-i.md) | Yes | Server attribute. |
| writeType | [PropertyWriteType](arkts-connectivity-ssap-propertywritetype-e.md) | Yes | Write type, which supports two modes: with and without server response. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [36100003](../errorcode-nearlink-service.md#36100003-nearlink-disabled) | NearLink disabled. |
| [36100043](../errorcode-nearlink-service.md#36100043-invalid-uuid) | Invalid UUID in property. |
| [36100044](../errorcode-nearlink-service.md#36100044-standard-nearlink-service-uuid-not-allowed) | NearLink standard UUID not allowed. |
| [36100099](../errorcode-nearlink-service.md#36100099-operation-failed) | Operation failed. |
