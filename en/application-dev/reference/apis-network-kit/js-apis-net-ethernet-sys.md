# @ohos.net.ethernet (Ethernet Connection Management) (System API)

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->

The **ethernet** module provides wired network capabilities, which allow users to set the IP address, subnet mask, gateway, and Domain Name System (DNS) server, and HTTP proxy of a wired network.

> **NOTE**
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> The APIs provided by this module are system APIs.

## Modules to Import

```ts
import { ethernet } from '@kit.NetworkKit';
```

## ethernet.setIfaceConfig<sup>9+</sup>

setIfaceConfig(iface: string, ic: InterfaceConfiguration, callback: AsyncCallback\<void>): void

Sets the network interface configuration. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.CONNECTIVITY_INTERNAL

**System capability**: SystemCapability.Communication.NetManager.Ethernet

**Parameters**

| Name  | Type                                             | Mandatory| Description                                      |
| -------- | ------------------------------------------------- | ---- | ------------------------------------------ |
| iface    | string                                            | Yes  | Interface name.                                    |
| ic       | [InterfaceConfiguration](#interfaceconfiguration9) | Yes  | Network interface configuration to set.                  |
| callback | AsyncCallback\<void>                     | Yes  | Callback used to return the result. If the operation is successful, the return result is empty. If the operation fails, an error code is returned.|

**Error codes**

| ID| Error Message                                |
| ------- | ----------------------------------------|
| 201     | Permission denied.                      |
| 202     | Non-system applications use system APIs.                      |
| 401     | Parameter error.                        |
| 2200001 | Invalid parameter value.                |
| 2200002 | Failed to connect to the service.       |
| 2200003 | System internal error.                  |
| 2201004 | Invalid Ethernet profile.  |
| 2201005 | Device information does not exist.  |
| 2201006 | Ethernet device not connected.                    |
| 2201007 | Ethernet failed to write user configuration information.    |

**Example**

```ts
import { ethernet } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let config: ethernet.InterfaceConfiguration = {
  mode: 0,
  ipAddr: "192.168.xx.xxx",
  route: "192.168.xx.xxx",
  gateway: "192.168.xx.xxx",
  netMask: "255.255.255.0",
  dnsServers: "1.1.1.1"
};

ethernet.setIfaceConfig("eth0", config, (error: BusinessError) => {
  if (error) {
    console.error("setIfaceConfig callback error = " + JSON.stringify(error));
  } else {
    console.info("setIfaceConfig callback ok");
  }
});
```

## ethernet.setIfaceConfig<sup>9+</sup>

setIfaceConfig(iface: string, ic: InterfaceConfiguration): Promise\<void>

Sets the network interface configuration. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permissions**: ohos.permission.CONNECTIVITY_INTERNAL

**System capability**: SystemCapability.Communication.NetManager.Ethernet

**Parameters**

| Name| Type                                             | Mandatory| Description                    |
| ------ | ------------------------------------------------- | ---- | ------------------------ |
| iface  | string                                            | Yes  | Interface name.                  |
| ic     | [InterfaceConfiguration](#interfaceconfiguration9) | Yes  | Network interface configuration to set.|

**Return value**

| Type               | Description                                                       |
| ------------------- | ----------------------------------------------------------- |
| Promise\<void>       | Promise used to return the result. If the operation is successful, the return result is empty. If the operation fails, an error code is returned.|

**Error codes**

| ID| Error Message                                |
| ------- | ----------------------------------------|
| 201     | Permission denied.                      |
| 202     | Non-system applications use system APIs.                      |
| 401     | Parameter error.                        |
| 2200001 | Invalid parameter value.                |
| 2200002 |Failed to connect to the service. |
| 2200003 | System internal error.                  |
| 2201004 | Invalid Ethernet profile.  |
| 2201005 | Device information does not exist.  |
| 2201006 | Ethernet device not connected.                    |
| 2201007 | Ethernet failed to write user configuration information.    |

**Example**

```ts
import { ethernet } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let config: ethernet.InterfaceConfiguration = {
  mode: 0,
  ipAddr: "192.168.xx.xxx",
  route: "192.168.xx.xxx",
  gateway: "192.168.xx.xxx",
  netMask: "255.255.255.0",
  dnsServers: "1.1.1.1"
};

const setConfigPromise = ethernet.setIfaceConfig("eth0", config);

setConfigPromise.then(() => {
  console.info("setIfaceConfig promise ok");
}).catch((error: BusinessError)  => {
  console.error("setIfaceConfig promise error = " + JSON.stringify(error));
});
```

## ethernet.getIfaceConfig<sup>9+</sup>

getIfaceConfig(iface: string, callback: AsyncCallback\<InterfaceConfiguration>): void

Obtains the configuration of a network interface. This API uses an asynchronous callback to return the result. 

**System API**: This is a system API.

**Required permission**: ohos.permission.GET_NETWORK_INFO

**System capability**: SystemCapability.Communication.NetManager.Ethernet

**Parameters**

| Name  | Type                                           | Mandatory | Description        |
| -------- | ----------------------------------------------- | ----- | ------------ |
| iface    | string                                          | Yes   | Network interface.|
| callback | AsyncCallback\<[InterfaceConfiguration](#interfaceconfiguration9)> | Yes   | Callback used to return the result. Returns information about the specified network interface.  |

**Error codes**

| ID| Error Message                                |
| ------- | ----------------------------------------|
| 201     | Permission denied.                      |
| 202     | Non-system applications use system APIs.                      |
| 401     | Parameter error.                        |
| 2200001 | Invalid parameter value.                |
| 2200002 | Failed to connect to the service.       |
| 2200003 | System internal error.                  |
| 2201005 | Device information does not exist.  |

**Example**

```ts
import { ethernet } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

ethernet.getIfaceConfig("eth0", (error: BusinessError, value: ethernet.InterfaceConfiguration) => {
  if (error) {
    console.error("getIfaceConfig  callback error = " + JSON.stringify(error));
  } else {
    console.info("getIfaceConfig callback mode = " + JSON.stringify(value.mode));
    console.info("getIfaceConfig callback ipAddr = " + JSON.stringify(value.ipAddr));
    console.info("getIfaceConfig callback route = " + JSON.stringify(value.route));
    console.info("getIfaceConfig callback gateway = " + JSON.stringify(value.gateway));
    console.info("getIfaceConfig callback netMask = " + JSON.stringify(value.netMask));
    console.info("getIfaceConfig callback dnsServers = " + JSON.stringify(value.dnsServers));
  }
});
```

## ethernet.getIfaceConfig<sup>9+</sup>

getIfaceConfig(iface: string): Promise\<InterfaceConfiguration>

Obtains the configuration of a network interface. This API uses a promise to return the result. 

**System API**: This is a system API.

**Required permission**: ohos.permission.GET_NETWORK_INFO

**System capability**: SystemCapability.Communication.NetManager.Ethernet

**Parameters**

| Name  | Type                                   | Mandatory| Description        |
| -------- | --------------------------------------- | ---- | ------------ |
| iface    | string                                  | Yes  | Network interface.|

**Return value**

| Type                             | Description                              |
| --------------------------------- | ---------------------------------- |
| Promise\<[InterfaceConfiguration](#interfaceconfiguration9)>   | Promise used to return the result.       |

**Error codes**

| ID| Error Message                                |
| ------- | ----------------------------------------|
| 201     | Permission denied.                      |
| 202     | Non-system applications use system APIs.                      |
| 401     | Parameter error.                        |
| 2200001 | Invalid parameter value.                |
| 2200002 | Failed to connect to the service.       |
| 2200003 | System internal error.                  |
| 2201005 | Device information does not exist.  |

**Example**

```ts
import { ethernet } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

ethernet.getIfaceConfig("eth0").then((data: ethernet.InterfaceConfiguration) => {
  console.info("getIfaceConfig promise mode = " + JSON.stringify(data.mode));
  console.info("getIfaceConfig promise ipAddr = " + JSON.stringify(data.ipAddr));
  console.info("getIfaceConfig promise route = " + JSON.stringify(data.route));
  console.info("getIfaceConfig promise gateway = " + JSON.stringify(data.gateway));
  console.info("getIfaceConfig promise netMask = " + JSON.stringify(data.netMask));
  console.info("getIfaceConfig promise dnsServers = " + JSON.stringify(data.dnsServers));
}).catch((error: BusinessError) => {
  console.error("getIfaceConfig promise error = " + JSON.stringify(error));
});
```

## ethernet.isIfaceActive<sup>9+</sup>

isIfaceActive(iface: string, callback: AsyncCallback\<number>): void

Checks whether a network interface is active. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.GET_NETWORK_INFO

**System capability**: SystemCapability.Communication.NetManager.Ethernet

**Parameters**

| Name  | Type                       | Mandatory| Description                                              |
| -------- | --------------------------- | ---- | -------------------------------------------------- |
| iface    | string                      | Yes  | Interface name. If this parameter is left empty, the API checks for any active network interface.            |
| callback | AsyncCallback\<number>       | Yes  | Callback used to return the result. The value **1** means that the network interface is active, **0** means that the network interface is inactive, and any other value means that an error has occurred.|

**Error codes**

| ID| Error Message                                |
| ------- | ----------------------------------------|
| 201     | Permission denied.                      |
| 202     | Non-system applications use system APIs.                      |
| 401     | Parameter error.                        |
| 2200001 | Invalid parameter value.                |
| 2200002 | Failed to connect to the service.       |
| 2200003 | System internal error.                  |
| 2201005 | Device information does not exist.  |

**Example**

```ts
import { ethernet } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

ethernet.isIfaceActive("eth0", (error: BusinessError, value: number) => {
  if (error) {
    console.error("whether2Activate callback error = " + JSON.stringify(error));
  } else {
    console.info("whether2Activate callback = " + JSON.stringify(value));
  }
});
```

## ethernet.isIfaceActive<sup>9+</sup>

isIfaceActive(iface: string): Promise\<number>

Checks whether a network interface is active. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.GET_NETWORK_INFO

**System capability**: SystemCapability.Communication.NetManager.Ethernet

**Parameters**

| Name| Type  | Mandatory| Description                                  |
| ------ | ------ | ---- | -------------------------------------- |
| iface  | string | Yes  | Interface name. If this parameter is left empty, the API checks for any active network interface.|

**Return value**

| Type           | Description                                                              |
| ----------------| ------------------------------------------------------------------ |
| Promise\<number> | Promise used to return the result. The value **1** means that the network interface is active, **0** means that the network interface is inactive, and any other value means that an error has occurred.|

**Error codes**

| ID| Error Message                                |
| ------- | ----------------------------------------|
| 201     | Permission denied.                      |
| 202     | Non-system applications use system APIs.                      |
| 401     | Parameter error.                        |
| 2200001 | Invalid parameter value.                |
| 2200002 | Failed to connect to the service.       |
| 2200003 | System internal error.                  |
| 2201005 | Device information does not exist.  |

**Example**

```ts
import { ethernet } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

ethernet.isIfaceActive("eth0").then((data: number) => {
  console.info("isIfaceActive promise = " + JSON.stringify(data));
}).catch((error: BusinessError) => {
  console.error("isIfaceActive promise error = " + JSON.stringify(error));
});
```

## ethernet.getAllActiveIfaces<sup>9+</sup>

getAllActiveIfaces(callback: AsyncCallback\<Array\<string>>): void

Obtains the list of all active network interfaces. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.GET_NETWORK_INFO

**System capability**: SystemCapability.Communication.NetManager.Ethernet

**Parameters**

| Name  | Type                                | Mandatory| Description                          |
| -------- | ------------------------------------ | ---- | ------------------------------ |
| callback | AsyncCallback\<Array\<string>>         | Yes  | Callback used to return the result.  |

**Error codes**

| ID| Error Message                                |
| ------- | ----------------------------------------|
| 201     | Permission denied.                      |
| 202     | Non-system applications use system APIs.                      |
| 2200002 | Failed to connect to the service.       |
| 2200003 | System internal error.                  |

**Example**

```ts
import { ethernet } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

ethernet.getAllActiveIfaces((error: BusinessError, value: string[]) => {
  if (error) {
    console.error("getAllActiveIfaces callback error = " + JSON.stringify(error));
  } else {
    console.info("getAllActiveIfaces callback value.length = " + JSON.stringify(value.length));
    for (let i = 0; i < value.length; i++) {
      console.info("getAllActiveIfaces callback = " + JSON.stringify(value[i]));
    }
  }
});
```

## ethernet.getAllActiveIfaces<sup>9+</sup>

getAllActiveIfaces(): Promise\<Array\<string>>

Obtains the list of all active network interfaces. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.GET_NETWORK_INFO

**System capability**: SystemCapability.Communication.NetManager.Ethernet

**Return value**

| Type                          | Description                                           |
| ------------------------------ | ----------------------------------------------- |
| Promise\<Array\<string>>         | Promise used to return the result.  |

**Error codes**

| ID| Error Message                                |
| ------- | ----------------------------------------|
| 201     | Permission denied.                      |
| 202     | Non-system applications use system APIs.                      |
| 2200002 | Failed to connect to the service.       |
| 2200003 | System internal error.                  |

**Example**

```ts
import { ethernet } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

ethernet.getAllActiveIfaces().then((data: string[]) => {
  console.info("getAllActiveIfaces promise data.length = " + JSON.stringify(data.length));
  for (let i = 0; i < data.length; i++) {
    console.info("getAllActiveIfaces promise  = " + JSON.stringify(data[i]));
  }
}).catch((error:BusinessError) => {
  console.error("getAllActiveIfaces promise error = " + JSON.stringify(error));
});
```

## ethernet.on('interfaceStateChange')<sup>10+</sup>

on(type: 'interfaceStateChange', callback: Callback\<InterfaceStateInfo>): void

Registers an observer for NIC hot swap events. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.GET_NETWORK_INFO

**System capability**: SystemCapability.Communication.NetManager.Ethernet

**Parameters**

| Name  | Type                                   | Mandatory| Description      |
| -------- | --------------------------------------- | ---- | ---------- |
| type     | string                  | Yes  | Event type. The value is **interfaceStateChange**.|
| callback | AsyncCallback\<[InterfaceStateInfo](#interfacestateinfo11)> | Yes  | Callback used to return the result.  |

**Error codes**

| ID| Error Message                                     |
| ------- | -------------------------------------------- |
| 201     | Permission denied.                      |
| 202     | Non-system applications use system APIs.                      |
| 401     | Parameter error.                     |

**Example**

```ts
import { ethernet } from '@kit.NetworkKit';

ethernet.on('interfaceStateChange', (data: object) => {
  console.info('on interfaceSharingStateChange: ' + JSON.stringify(data));
});
```

## ethernet.off('interfaceStateChange')<sup>10+</sup>

off(type: 'interfaceStateChange', callback?: Callback\<InterfaceStateInfo\>): void

Unregisters the observer for NIC hot swap events. This API uses an asynchronous callback to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.GET_NETWORK_INFO

**System capability**: SystemCapability.Communication.NetManager.Ethernet

**Parameters**

| Name  | Type                                   | Mandatory| Description      |
| -------- | --------------------------------------- | ---- | ---------- |
| type     | string                  | Yes  | Event type. The value is **interfaceStateChange**.|
| callback | AsyncCallback\<[InterfaceStateInfo](#interfacestateinfo11)> | No  | Callback used to return the result.  |

**Error codes**

| ID| Error Message                                     |
| ------- | -------------------------------------------- |
| 201     | Permission denied.                      |
| 202     | Non-system applications use system APIs.                      |
| 401     | Parameter error.                     |

**Example**

```ts
import { ethernet } from '@kit.NetworkKit';

ethernet.off('interfaceStateChange');
```


## ethernet.getEthernetDeviceInfos<sup>20+</sup>

getEthernetDeviceInfos(): Promise\<Array\<EthernetDeviceInfos>>

Obtains Ethernet device information. This API uses a promise to return the result.

**System API**: This is a system API.

**Required permission**: ohos.permission.GET_NETWORK_INFO

**System capability**: SystemCapability.Communication.NetManager.Ethernet

**Return value**

| Type               | Description                                                       |
| ------------------- | ----------------------------------------------------------- |
| Promise\<Array\<[EthernetDeviceInfos](#ethernetdeviceinfos20)>>  | Promise used to return the result. If the operation is successful, the Ethernet device information list is returned. If the operation fails, an error code is returned.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Ethernet Connection Error Codes](errorcode-net-ethernet.md).

| ID| Error Message                               |
| ------- | ----------------------------------------|
| 201     | Permission denied.                      |
| 202     | Non-system applications use system APIs.|
| 2201005 | Device information does not exist.      |

**Example**

```ts
import { ethernet } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

ethernet.getEthernetDeviceInfos().then((data: Array<ethernet.EthernetDeviceInfos>) => {
  console.info("getEthernetDeviceInfos data.length = " + JSON.stringify(data.length));
  for (let i = 0; i < data.length; i++) {
    console.info("getEthernetDeviceInfos = " + JSON.stringify(data[i]));
  }
}).catch((err: BusinessError) => {
  console.error("getEthernetDeviceInfos err = " + err.code);
});
```

## InterfaceConfiguration<sup>9+</sup>

Defines the network configuration for the Ethernet connection.

**System API**: This is a system API.

**System capability**: SystemCapability.Communication.NetManager.Ethernet

| Name         | Type                   | Mandatory| Description                                                        |
| ------------ | ----------------------- | ---|------------------------------------------------------------ |
| mode         | [IPSetMode](#ipsetmode9) | Yes| Configuration mode of the Ethernet connection.|
| ipAddr       | string                  | Yes| Static IP address of the Ethernet connection. The value must be an IPv4 address, which is a 32-bit number displayed in dotted decimal notation and each 8-bit field ranges from 0 to 255. This parameter does not need to be configured in Dynamic Host Configuration Protocol (DHCP) mode.|
| route        | string                  | Yes| Route of the Ethernet connection. The value must be an IPv4 address, which is a 32-bit number displayed in dotted decimal notation and each 8-bit field ranges from 0 to 255. This parameter does not need to be configured in DHCP mode.|
| gateway      | string                  | Yes| Gateway of the Ethernet connection. The value must be an IPv4 address, which is a 32-bit number displayed in dotted decimal notation and each 8-bit field ranges from 0 to 255. This parameter does not need to be configured in DHCP mode.|
| netMask      | string                  | Yes| Subnet mask of the Ethernet connection. The value must be an IPv4 address, which is a 32-bit number displayed in dotted decimal notation and each 8-bit field ranges from 0 to 255. This parameter does not need to be configured in DHCP mode.|
| dnsServers   | string                  | Yes| DNS server addresses of the Ethernet connection. The value must be an IPv4 address, which is a 32-bit number displayed in dotted decimal notation and each 8-bit field ranges from 0 to 255. This parameter does not need to be configured in DHCP mode. Multiple addresses are separated by commas (,).|
| httpProxy<sup>10+</sup> | [HttpProxy](js-apis-net-connection.md#httpproxy10) | No| HTTP proxy of the Ethernet connection. By default, no proxy is configured.|

## InterfaceStateInfo<sup>11+</sup>

Listens for status changes of an Ethernet NIC.

**System API**: This is a system API.

**System capability**: SystemCapability.Communication.NetManager.Ethernet

| Name        | Type                   | Mandatory| Description                                                |
| ------------ | ----------------------- | --- | ---------------------------------------------------- |
| iface        | string                  |  Yes| Name of the Ethernet NIC.                                       |
| active       | boolean                 |  Yes| Whether the Ethernet NIC is activated. The value **true** indicates the NIC is activated, and the value **false** indicates the opposite.|

## IPSetMode<sup>9+</sup>

Defines the configuration mode of the Ethernet connection.

**System API**: This is a system API.

**System capability**: SystemCapability.Communication.NetManager.Ethernet

| Name                 | Value  | Description                       |
| --------------------- | ---- | -------------------------- |
| STATIC                | 0    | Static network configuration for an Ethernet connection.|
| DHCP                  | 1    | Dynamic network configuration for an Ethernet connection.|
| LAN_STATIC<sup>11+</sup>| 2    | Static network configuration for a LAN connection.   |
| LAN_DHCP<sup>11+</sup>  | 3    | Dynamic network configuration for a LAN connection.   |

## EthernetDeviceInfos<sup>20+</sup>

Defines Ethernet device information.

**System API**: This is a system API.

**System capability**: SystemCapability.Communication.NetManager.Ethernet

| Name          | Type                   | Read-Only| Optional| Description                                                        |
| ------------   | ----------------------- | ---| ---|------------------------------------------------------------ |
| ifaceName      | string                  | No| No| Interface name.     |
| deviceName     | string                  | No| No| Device name.   |
| connectionMode | [DeviceConnectionType](#deviceconnectiontype20)  | No| No| Device connection mode.|
| supplierName   | string                  | No| No| Vendor name.|
| supplierId     | string                  | No| No| Supplier ID.|
| productName    | string                  | No| No| Product name.|
| maximumRate    | string                  | No| No| Maximum connection rate.|

## DeviceConnectionType<sup>20+</sup>

Enumerates Ethernet device connection modes.

**System API**: This is a system API.

**System capability**: SystemCapability.Communication.NetManager.Ethernet

| Name                 | Value  | Description                       |
| --------------------- | ---- | -------------------------- |
| BUILT_IN              | 0    | Internal connection mode.|
| EXTERNAL              | 1    | External connection mode. For example, the Ethernet device is connected through a USB.|
