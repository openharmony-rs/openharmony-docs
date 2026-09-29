# @ohos.net.vpn (VPN Management) (System API)

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=162967c12d854d79d44ff47f88b93df57a9bf51b translatedAt=2026-09-23T02:30:08.228Z pushedAt=2026-09-24T06:00:14.212Z -->

The VPN management module supports starting and stopping VPN connections.

This module is the built-in VPN function provided by the OS. It allows users to set up VPN connections through the network settings of the OS. Generally, this module provides only limited functions and is subject to strict restrictions.

> **NOTE**
>
> The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> The APIs provided by this module are system APIs.

## Modules to Import

```js
import { vpn } from '@kit.NetworkKit';
```

## vpn.createVpnConnection

createVpnConnection(context: AbilityContext): VpnConnection

Creates a VPN connection.

**System API**: This is a system API.

**System capability**: SystemCapability.Communication.NetManager.Vpn

**Parameters**

| Name | Type                                                                            | Mandatory| Description        |
| ------- | -------------------------------------------------------------------------------- | ---- | ------------ |
| context | [AbilityContext](../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md) | Yes  | Specified context.|

**Return value**

| Type                           | Description                   |
| :------------------------------ | :---------------------- |
| [VpnConnection](#vpnconnection) | VPN connection object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message         |
| --------- | ---------------- |
| 202       | Non-system applications use system APIs.         |
| 401       | Parameter error.                                 |

**Example**

> **NOTE**
>
> In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use the capabilities provided by **UIAbilityContext** on a page, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

Stage model:

```ts
import { vpn } from '@kit.NetworkKit';
import { common } from '@kit.AbilityKit';

@Entry
@Component
struct Index {
  private context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
  private VpnConnection: vpn.VpnConnection = vpn.createVpnConnection(this.context);
  functiontest(): void {
    console.info("vpn createVpnConnection: " + JSON.stringify(this.VpnConnection));
  }
  build() {  }
}
```

## VpnConnection

VPN connection object. Before calling the methods of **VpnConnection**, you must create a VPN connection object through [vpn.createVpnConnection](#vpncreatevpnconnection).

### setUp

setUp(config: VpnConfig, callback: AsyncCallback\<number\>): void

Creates a VPN network based on the specified configuration. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MANAGE_VPN

**System capability**: SystemCapability.Communication.NetManager.Vpn

**Parameters**

| Name  | Type                   | Mandatory| Description                                                                                              |
| -------- | ----------------------- | ---- | -------------------------------------------------------------------------------------------------- |
| config   | [VpnConfig](#vpnconfig) | Yes  | VPN configuration.                                                                         |
| callback | AsyncCallback\<number\> | Yes | Callback function. When the VPN network is started successfully, returns the file descriptor (fd) of the virtual network interface, and error is undefined; otherwise, returns an error object. |

**Error codes**

For details about the error codes, see [VPN Error Codes](errorcode-net-vpn.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                         |
| --------- | ------------------------------------------------ |
| 201       | Permission denied.                               |
| 202       | Non-system applications use system APIs.         |
| 401       | Parameter error.                                 |
| 2200001   | Invalid parameter value.                         |
| 2200002   | Operation failed. Cannot connect to service.     |
| 2200003   | System internal error.                           |
| 2203001   | VPN creation denied. Check the user type.        |
| 2203002   | VPN already exists.                              |

**Example**

> **NOTE**
>
> In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use the capabilities provided by **UIAbilityContext** on a page, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```ts
import { vpn } from '@kit.NetworkKit';
import { common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  private context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
  private VpnConnection: vpn.VpnConnection = vpn.createVpnConnection(this.context);
  SetUp(): void {
    let config: vpn.VpnConfig = {
      addresses: [{
        address: {
          address: "10.0.0.5",
          family: 1
        },
        prefixLength: 24
      }],
      mtu: 1400,
      dnsAddresses: ["114.114.114.114"]
    }
    this.VpnConnection.setUp(config, (error: BusinessError, data: number) => {
      if (error) {
        console.error(JSON.stringify(error));
        return;
      };
      console.info("tunfd: " + JSON.stringify(data));
    });
  }
  build() { }
}
```

### setUp

setUp(config: VpnConfig): Promise\<number\>

Creates a VPN based on the specified configuration. This API uses a promise to return the result.

> **NOTE**
>
> Only one VPN connection is allowed for the same user at the same time. If a VPN connection already exists, error code 2203002 is returned. The VPN network persists and must be destroyed by calling **destroy**.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MANAGE_VPN

**System capability**: SystemCapability.Communication.NetManager.Vpn

**Parameters**

| Name| Type                   | Mandatory| Description                     |
| ------ | ----------------------- | ---- | ------------------------- |
| config | [VpnConfig](#vpnconfig) | Yes  | VPN configuration.|

**Return value**

| Type             | Description                                                          |
| ----------------- | -------------------------------------------------------------- |
| Promise\<number\> | Promise object that returns the file descriptor (fd) of the specified virtual network interface. |

**Error codes**

For details about the error codes, see [VPN Error Codes](errorcode-net-vpn.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                         |
| --------- | ------------------------------------------------ |
| 201       | Permission denied.                               |
| 202       | Non-system applications use system APIs.         |
| 401       | Parameter error.                                 |
| 2200001   | Invalid parameter value.                         |
| 2200002   | Operation failed. Cannot connect to service.     |
| 2200003   | System internal error.                           |
| 2203001   | VPN creation denied. Check the user type.        |
| 2203002   | VPN already exists.                              |

**Example**

> **NOTE**
>
> In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use the capabilities provided by **UIAbilityContext** on a page, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```ts
import { vpn } from '@kit.NetworkKit';
import { common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  private context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
  private VpnConnection: vpn.VpnConnection = vpn.createVpnConnection(this.context);
  SetUp(): void {
    let config: vpn.VpnConfig = {
      addresses: [{
        address: {
          address: "10.0.0.5",
          family: 1
        },
        prefixLength: 24
      }],
      mtu: 1400,
      dnsAddresses: ["114.114.114.114"]
    }
    this.VpnConnection.setUp(config).then((data: number) => {
      console.info("setUp success, tunfd: " + JSON.stringify(data));
    }).catch((err: BusinessError) => {
      console.error("setUp fail" + JSON.stringify(err));
    });
  }
  build() { }
}
```

### protect

protect(socketFd: number, callback: AsyncCallback\<void\>): void

Protects the specified sockets so that their data traffic bypasses the VPN network and is sent and received directly over the physical network. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MANAGE_VPN

**System capability**: SystemCapability.Communication.NetManager.Vpn

**Parameters**

| Name  | Type                 | Mandatory| Description                                                                                     |
| -------- | --------------------- | ---- | ----------------------------------------------------------------------------------------- |
| socketFd | number | Yes | Socket file descriptor (socketfd) to be protected. The file descriptor is obtained through [getSocketFd](js-apis-socket.md#getsocketfd10). |
| callback | AsyncCallback\<void\> | Yes | Callback function. If the operation is successful, error is undefined. Returns an error code and error message on failure. |

**Error codes**

For details about the error codes, see [VPN Error Codes](errorcode-net-vpn.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                     |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 401       | Parameter error.                             |
| 2200001   | Invalid parameter value.                     |
| 2200002   | Operation failed. Cannot connect to service. |
| 2200003   | System internal error.                       |
| 2203004   | Invalid socket file descriptor.              |

**Example**

> **NOTE**
>
> In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use the capabilities provided by **UIAbilityContext** on a page, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```ts
import { socket, vpn } from '@kit.NetworkKit';
import { common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  private context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
  private VpnConnection: vpn.VpnConnection = vpn.createVpnConnection(this.context);

  Protect(): void {
    let tcp: socket.TCPSocket = socket.constructTCPSocketInstance();
    let ipAddress: socket.NetAddress = {
      address: "0.0.0.0"
    }
    tcp.bind(ipAddress);
    let netAddress: socket.NetAddress = {
      address: "192.168.1.11",
      port: 8888
    }
    let addressConnect: socket.TCPConnectOptions = {
      address: netAddress,
      timeout: 6000
    }
    tcp.connect(addressConnect);
    tcp.getSocketFd().then((tunnelFd: number) => {
      console.info("tunnelFd: " + tunnelFd);
      this.VpnConnection.protect(tunnelFd, (error: BusinessError) => {
        console.error(JSON.stringify(error));
      });
    });
  }
  build() { }
}
```

### protect

protect(socketFd: number): Promise\<void\>

Protects the specified socket so that its data traffic bypasses the VPN and is sent and received directly over the physical network. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MANAGE_VPN

**System capability**: SystemCapability.Communication.NetManager.Vpn

**Parameters**

| Name  | Type  | Mandatory| Description                                                                                       |
| -------- | ------ | ---- | ------------------------------------------------------------------------------------------- |
| socketFd | number | Yes | Socket file descriptor. It can be obtained through [getSocketFd](js-apis-socket.md#getsocketfd10-1). |

**Return value**

| Type           | Description                                                 |
| --------------- | ----------------------------------------------------- |
| Promise\<void\> | Promise object that returns no value. Returns the error code and error message on failure. |

**Error codes**

For details about the error codes, see [VPN Error Codes](errorcode-net-vpn.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                     |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 401       | Parameter error.                             |
| 2200001   | Invalid parameter value.                     |
| 2200002   | Operation failed. Cannot connect to service. |
| 2200003   | System internal error.                       |
| 2203004   | Invalid socket file descriptor.              |

**Example**

> **NOTE**
>
>In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use the capabilities provided by **UIAbilityContext** in a page, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```ts
import { socket, vpn } from '@kit.NetworkKit';
import { common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  private context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
  private VpnConnection: vpn.VpnConnection = vpn.createVpnConnection(this.context);

  Protect(): void {
    let tcp: socket.TCPSocket = socket.constructTCPSocketInstance();
    let ipAddress: socket.NetAddress = {
      address: "0.0.0.0"
    }
    tcp.bind(ipAddress);
    let netAddress: socket.NetAddress = {
      address: "192.168.1.11",
      port: 8888
    }
    let addressConnect: socket.TCPConnectOptions = {
      address: netAddress,
      timeout: 6000
    }
    tcp.connect(addressConnect);
    tcp.getSocketFd().then((tunnelFd: number) => {
      console.info("tunnelFd: " + tunnelFd);
      this.VpnConnection.protect(tunnelFd).then(() => {
        console.info("protect success.");
      }).catch((err: BusinessError) => {
        console.error("protect fail" + JSON.stringify(err));
      });
    });
  }
  build() { }
}
```

### destroy

destroy(callback: AsyncCallback\<void\>): void

Destroys the started VPN. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MANAGE_VPN

**System capability**: SystemCapability.Communication.NetManager.Vpn

**Parameters**

| Name  | Type                 | Mandatory| Description                                                          |
| -------- | --------------------- | ---- | -------------------------------------------------------------- |
| callback | AsyncCallback\<void\> | Yes | Callback function. On success, error is undefined; on failure, returns the error code and error message. |

**Error codes**

For details about the error codes, see [VPN Error Codes](errorcode-net-vpn.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                     |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 401       | Parameter error.                             |
| 2200002   | Operation failed. Cannot connect to service. |
| 2200003   | System internal error.                       |

**Example**

> **NOTE**
>
>In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use the capabilities provided by **UIAbilityContext** in a page, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```ts
import { vpn } from '@kit.NetworkKit';
import { common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  private context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
  private VpnConnection: vpn.VpnConnection = vpn.createVpnConnection(this.context);
  Destroy(): void {
    this.VpnConnection.destroy((error: BusinessError) => {
      console.error(JSON.stringify(error));
    });
  }
  build() { }
}
```

### destroy

destroy(): Promise\<void\>

Destroys a VPN. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.MANAGE_VPN

**System capability**: SystemCapability.Communication.NetManager.Vpn

**Return value**

| Type           | Description                                                 |
| --------------- | ----------------------------------------------------- |
| Promise\<void\> | Promise object, no return value. Returns the error code and error message on failure. |

**Error codes**

For details about the error codes, see [VPN Error Codes](errorcode-net-vpn.md) and [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message                                     |
| --------- | -------------------------------------------- |
| 201       | Permission denied.                           |
| 202       | Non-system applications use system APIs.     |
| 401       | Parameter error.                                 |
| 2200002   | Operation failed. Cannot connect to service. |
| 2200003   | System internal error.                       |

**Example**

> **NOTE**
>
>In the sample code provided in this topic, **this.context** is used to obtain **UIAbilityContext**, where **this** indicates a UIAbility instance inherited from **UIAbility**. To use the capabilities provided by **UIAbilityContext** in a page, see [Obtaining the Context of UIAbility](../../application-models/uiability-usage.md#obtaining-the-context-of-uiability).

```ts
import { vpn } from '@kit.NetworkKit';
import { common } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  private context: common.UIAbilityContext = this.getUIContext().getHostContext() as common.UIAbilityContext;
  private VpnConnection: vpn.VpnConnection = vpn.createVpnConnection(this.context);
  Destroy(): void {
    this.VpnConnection.destroy().then(() => {
      console.info("destroy success.");
    }).catch((err: BusinessError) => {
      console.error("destroy fail" + JSON.stringify(err));
    });
  }
  build() { }
}
```

## VpnConfig

Defines the VPN configuration.

**System API**: This is a system API.

**System capability**: SystemCapability.Communication.NetManager.Vpn

| Name               | Type                                                          | Read-Only|Optional| Description                               |
| ------------------- | -------------------------------------------------------------- | ---- | ---|----------------------------------- |
| vpnId<sup>20+</sup>           | string | No   |Yes| Unique identifier of the VPN. The value is empty by default if this parameter is not set.            |
| addresses           | Array\<[LinkAddress](js-apis-net-connection.md#linkaddress)\> | No  |No| IP address of the vNIC.           |
| routes              | Array\<[RouteInfo](js-apis-net-connection.md#routeinfo)\>     | No   |Yes | Route information of the VPN virtual network interface. The value is empty by default if this parameter is not set.            |
| dnsAddresses        | Array\<string\>                                                | No   |Yes | DNS server address information. The value is empty by default if this parameter is not set.                |
| searchDomains       | Array\<string\>                                                | No   | Yes| List of DNS search domains. The value is empty by default if this parameter is not set.                  |
| mtu                 | number                                                         | No   |Yes |Maximum transmission unit (MTU) value, in bytes. The system default MTU value is used if this parameter is not set.     |
| isIPv4Accepted      | boolean                                                        | No  | Yes| Whether IPv4 is supported. The value **true** indicates that IPv4 is supported, and the value **false** indicates the opposite. Default value: **true**.     |
| isIPv6Accepted      | boolean                                                        | No  |Yes|Whether IPv6 is supported. The value **true** indicates that IPv6 is supported, and the value **false** indicates the opposite. The default value is **false**.    |
| isLegacy            | boolean                                                        | No  |Yes|Whether the built-in VPN is supported. The value **true** indicates that the built-in VPN is supported, and the value **false** indicates the opposite. The default value is **false**.  |
| isBlocking          | boolean                                                        | No  |Yes|Whether the blocking mode is used. The value **true** indicates that the blocking mode is used, and the value **false** indicates the opposite. The default value is **false**.      |
| trustedApplications | Array\<string\>                                                | No   |Yes | Bundle names, represented by strings, that can access the VPN network. The value is empty by default if this parameter is not set.  |
| blockedApplications | Array\<string\>                                                | No   |Yes | Bundle names, represented by strings, that cannot access the VPN network. The value is empty by default if this parameter is not set.  |