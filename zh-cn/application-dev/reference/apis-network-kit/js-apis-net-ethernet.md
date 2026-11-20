# @ohos.net.ethernet (以太网连接管理)

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->

本模块提供以太网连接管理能力，包括有线网络能力、获取有线网络的IP地址等信息。

> **说明：**
> 本模块首批接口从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```ts
import { ethernet } from '@kit.NetworkKit';
```

## HttpProxy<sup>10+</sup>

type HttpProxy = connection.HttpProxy

网络代理配置信息。

**系统能力**：SystemCapability.Communication.NetManager.Ethernet

| 类型 | 说明                                       |
| ------- | ----------------------------------------|
| connection.HttpProxy     | 网络代理配置信息。      |


## ethernet.getIfaceConfig

getIfaceConfig(iface: string, callback: AsyncCallback\<InterfaceConfiguration>): void

获取指定网络接口的配置信息。使用callback异步回调。

**起始版本**：26.1.0

**需要权限**：ohos.permission.GET_NETWORK_INFO

**系统能力**：SystemCapability.Communication.NetManager.Ethernet

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| iface | string | 是 | 指定网络接口。 |
| callback | AsyncCallback\<[InterfaceConfiguration](js-apis-net-ethernet-sys.md#interfaceconfiguration)> | 是 | 回调函数。返回指定网络接口的配置信息。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[以太网连接错误码](errorcode-net-ethernet.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission denied. |
| 202 | Non-system applications use system APIs.<br>适用版本：9-26.0.1 |
| 401 | Parameter error. |
| 2200001 | Invalid parameter value. |
| 2200002 | Failed to connect to the service. |
| 2200003 | System internal error. |
| 2201005 | Device information does not exist. |

**示例：**

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

## ethernet.getIfaceConfig

getIfaceConfig(iface: string): Promise\<InterfaceConfiguration>

获取指定网络接口的配置信息。使用Promise异步回调。

**起始版本**：26.1.0

**需要权限**：ohos.permission.GET_NETWORK_INFO

**系统能力**：SystemCapability.Communication.NetManager.Ethernet

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| iface | string | 是 | 指定网络接口。 |

**返回值：**

| 类型 | 说明 |
| -------- | -------- |
| Promise\<[InterfaceConfiguration](js-apis-net-ethernet-sys.md#interfaceconfiguration)> | Promise对象，返回指定网络接口的配置信息。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[以太网连接错误码](errorcode-net-ethernet.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission denied. |
| 202 | Non-system applications use system APIs.<br>适用版本：9-26.0.1 |
| 401 | Parameter error. |
| 2200001 | Invalid parameter value. |
| 2200002 | Failed to connect to the service. |
| 2200003 | System internal error. |
| 2201005 | Device information does not exist. |

**示例：**

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

## ethernet.getMacAddress<sup>14+</sup>

getMacAddress(): Promise\<Array\<MacAddressInfo>>

获取所有以太网网卡名称及对应网卡的MAC地址信息，使用Promise异步回调。

**需要权限**：ohos.permission.GET_ETHERNET_LOCAL_MAC

**系统能力**：SystemCapability.Communication.NetManager.Ethernet

**返回值：**

| 类型                                                    | 说明                               |
|-------------------------------------------------------| ---------------------------------- |
| Promise\<Array\<[MacAddressInfo](#macaddressinfo14)\>\> | Promise对象，返回所有以太网网卡名称及对应网卡的MAC地址信息。        |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[以太网连接错误码](errorcode-net-ethernet.md)。

| 错误码ID | 错误信息                                 |
| ------- | ----------------------------------------|
| 201     | Permission denied.                      |
| 2200002 | Operation failed. Cannot connect to service.       |
| 2201005 | Device information does not exist.  |

**示例：**

```ts
import { ethernet } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

ethernet.getMacAddress().then((data: Array<ethernet.MacAddressInfo>) => {
  console.info(`getMacAddress promise data = ${JSON.stringify(data)}`);
}).catch((error: BusinessError) => {
  console.error(`getMacAddress promise error = ${JSON.stringify(error)}`);
});
```

## MacAddressInfo<sup>14+</sup>
以太网网卡名称及MAC地址信息。

**系统能力**：SystemCapability.Communication.NetManager.Ethernet

| 名称   | 类型                                           | 只读 | 可选 |说明                    |
| -------- | ---------------------------------------------- | ---- | --- | ---------------------- |
| iface        | string                  |  否   | 否 | 以太网网卡名称，如"eth0"。可通过[getMacAddress](#ethernetgetmacaddress14)获取。                                        |
| macAddress       | string                |  否   | 否 | 以太网网卡MAC地址信息，格式为"XX:XX:XX:XX:XX:XX"。 |
