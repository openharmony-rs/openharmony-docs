# VpnConnection (System API)

Defines a VPN connection object. Before calling **VpnConnection** APIs, you need to create a VPN connection object by calling [vpn.createVpnConnection](arkts-network-vpn-createvpnconnection-f-sys.md).

**Since:** 10

**System capability:** SystemCapability.Communication.NetManager.Vpn

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { vpn } from '@kit.NetworkKit';
```

## destroy

```TypeScript
destroy(callback: AsyncCallback<void>): void
```

Destroys a VPN. This API uses an asynchronous callback to return the result.

**Since:** 10

**Required permissions:** ohos.permission.MANAGE_VPN

**System capability:** SystemCapability.Communication.NetManager.Vpn

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **error** is **undefined**. If the operation fails, an error message is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [2200002](../errorcode-net-ethernet.md#2200002-service-connection-failure) | Operation failed. Cannot connect to service. |
| [2200003](../errorcode-net-ethernet.md#2200003-system-internal-error) | System internal error. |

**Examples**

```TypeScript
> NOTE
> 
> In the sample code provided in this topic, this.context is used to obtain UIAbilityContext, where this indicates a UIAbility instance inherited from UIAbility. To use UIAbilityContext APIs on pages, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).
```

## destroy

```TypeScript
destroy(): Promise<void>
```

Destroys a VPN. This API uses a promise to return the result.

**Since:** 10

**Required permissions:** ohos.permission.MANAGE_VPN

**System capability:** SystemCapability.Communication.NetManager.Vpn

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. If the operation is successful, the operation result is returned. If the operation fails, an error message is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [2200002](../errorcode-net-ethernet.md#2200002-service-connection-failure) | Operation failed. Cannot connect to service. |
| [2200003](../errorcode-net-ethernet.md#2200003-system-internal-error) | System internal error. |

**Examples**

See [destroy](#destroy)

## protect

```TypeScript
protect(socketFd: number, callback: AsyncCallback<void>): void
```

Protects sockets against a VPN connection. The data sent through sockets is directly transmitted over the physical network and therefore the traffic does not traverse through the VPN. This API uses an asynchronous callback to return the result.

**Since:** 10

**Required permissions:** ohos.permission.MANAGE_VPN

**System capability:** SystemCapability.Communication.NetManager.Vpn

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| socketFd | number | Yes | Socket file descriptor. It can be obtained through [getSocketFd](arkts-network-socket-tcpsocket-i.md#getsocketfd). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **error** is **undefined**. If the operation fails, an error message is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [2200001](../errorcode-net-ethernet.md#2200001-invalid-parameter-value) | Invalid parameter value. |
| [2200002](../errorcode-net-ethernet.md#2200002-service-connection-failure) | Operation failed. Cannot connect to service. |
| [2200003](../errorcode-net-ethernet.md#2200003-system-internal-error) | System internal error. |
| [2203004](../errorcode-net-vpn.md#2203004-invalid-descriptor) | Invalid socket file descriptor. |

**Examples**

```TypeScript
> NOTE
> 
> In the sample code provided in this topic, this.context is used to obtain UIAbilityContext, where this indicates a UIAbility instance inherited from UIAbility. To use UIAbilityContext APIs on pages, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).
```

## protect

```TypeScript
protect(socketFd: number): Promise<void>
```

Protects sockets against a VPN connection. The data sent through sockets is directly transmitted over the physical network and therefore the traffic does not traverse through the VPN. This API uses a promise to return the result.

**Since:** 10

**Required permissions:** ohos.permission.MANAGE_VPN

**System capability:** SystemCapability.Communication.NetManager.Vpn

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| socketFd | number | Yes | Socket file descriptor. It can be obtained through [getSocketFd](arkts-network-socket-tcpsocket-i.md#getsocketfd). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. If the operation is successful, the operation result is returned. If the operation fails, an error message is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [2200001](../errorcode-net-ethernet.md#2200001-invalid-parameter-value) | Invalid parameter value. |
| [2200002](../errorcode-net-ethernet.md#2200002-service-connection-failure) | Operation failed. Cannot connect to service. |
| [2200003](../errorcode-net-ethernet.md#2200003-system-internal-error) | System internal error. |
| [2203004](../errorcode-net-vpn.md#2203004-invalid-descriptor) | Invalid socket file descriptor. |

**Examples**

See [protect](#protect)

## setUp

```TypeScript
setUp(config: VpnConfig, callback: AsyncCallback<number>): void
```

Creates a VPN based on the specified configuration. This API uses an asynchronous callback to return the result.

**Since:** 10

**Required permissions:** ohos.permission.MANAGE_VPN

**System capability:** SystemCapability.Communication.NetManager.Vpn

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [VpnConfig](arkts-network-vpnextension-vpnconfig-i.md) | Yes | VPN configuration. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the result. If a VPN is created successfully, **error** is **undefined** and **data** is the file descriptor of the vNIC. Otherwise, **error** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [2200001](../errorcode-net-ethernet.md#2200001-invalid-parameter-value) | Invalid parameter value. |
| [2200002](../errorcode-net-ethernet.md#2200002-service-connection-failure) | Operation failed. Cannot connect to service. |
| [2200003](../errorcode-net-ethernet.md#2200003-system-internal-error) | System internal error. |
| [2203001](../errorcode-net-vpn.md#2203001-failed-to-create-a-vpn) | VPN creation denied. Check the user type. |
| [2203002](../errorcode-net-vpn.md#2203002-vpn-already-exists) | VPN already exists. |

**Examples**

```TypeScript
> NOTE
> 
> In the sample code provided in this topic, this.context is used to obtain UIAbilityContext, where this indicates a UIAbility instance inherited from UIAbility. To use UIAbilityContext APIs on pages, see [Obtaining the Context of UIAbility](../../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).
```

## setUp

```TypeScript
setUp(config: VpnConfig): Promise<number>
```

Creates a VPN based on the specified configuration. This API uses a promise to return the result.

**Since:** 10

**Required permissions:** ohos.permission.MANAGE_VPN

**System capability:** SystemCapability.Communication.NetManager.Vpn

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [VpnConfig](arkts-network-vpnextension-vpnconfig-i.md) | Yes | VPN configuration. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the result, which is the file descriptor of the vNIC. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [2200001](../errorcode-net-ethernet.md#2200001-invalid-parameter-value) | Invalid parameter value. |
| [2200002](../errorcode-net-ethernet.md#2200002-service-connection-failure) | Operation failed. Cannot connect to service. |
| [2200003](../errorcode-net-ethernet.md#2200003-system-internal-error) | System internal error. |
| [2203001](../errorcode-net-vpn.md#2203001-failed-to-create-a-vpn) | VPN creation denied. Check the user type. |
| [2203002](../errorcode-net-vpn.md#2203002-vpn-already-exists) | VPN already exists. |

**Examples**

See [setUp](#setup)
