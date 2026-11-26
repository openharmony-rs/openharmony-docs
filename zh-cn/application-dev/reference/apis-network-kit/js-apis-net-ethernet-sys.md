# @ohos.net.ethernet (以太网连接管理)（系统接口）

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->

以太网连接管理主要提供有线网络能力，提供设置有线网络的IP地址，子网掩码，网关，DNS，代理等信息。

> **说明：**
>
> 本模块首批接口从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
> 本模块为系统接口。

## 导入模块

```ts
import { ethernet } from '@kit.NetworkKit';
```

## ethernet.setIfaceConfig

setIfaceConfig(iface: string, ic: InterfaceConfiguration, callback: AsyncCallback\<void>): void

设置网络接口配置信息。使用callback异步回调。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.CONNECTIVITY_INTERNAL

**系统能力**：SystemCapability.Communication.NetManager.Ethernet

**参数：**

| 参数名   | 类型                                              | 必填 | 说明                                       |
| -------- | ------------------------------------------------- | ---- | ------------------------------------------ |
| iface    | string                                            | 是   | 网络接口名。                                     |
| ic       | [InterfaceConfiguration](js-apis-net-ethernet.md#interfaceconfiguration) | 是   | 要设置的网络接口配置信息。                   |
| callback | AsyncCallback\<void>                     | 是   | 回调函数。成功无返回，失败返回对应错误码。 |

**错误码：**

| 错误码ID | 错误信息                                 |
| ------- | ----------------------------------------|
| 201     | Permission denied.                      |
| 202     | Non-system applications use system APIs.                      |
| 401     | Parameter error.                        |
| 2100001 | Invalid parameter value.                |
| 2200002 | Failed to connect to the service.       |
| 2200003 | System internal error.                  |
| 2201004 | Invalid Ethernet profile.  |
| 2201005 | Device information does not exist.  |
| 2201006 | Ethernet device not connected.                    |
| 2201007 | Ethernet failed to write user configuration information.    |

**示例：**

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

## ethernet.setIfaceConfig

setIfaceConfig(iface: string, ic: InterfaceConfiguration): Promise\<void>

设置网络接口配置信息。使用Promise异步回调。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.CONNECTIVITY_INTERNAL

**系统能力**：SystemCapability.Communication.NetManager.Ethernet

**参数：**

| 参数名 | 类型                                              | 必填 | 说明                     |
| ------ | ------------------------------------------------- | ---- | ------------------------ |
| iface  | string                                            | 是   | 接口名。                   |
| ic     | [InterfaceConfiguration](js-apis-net-ethernet.md#interfaceconfiguration) | 是   | 要设置的网络接口配置信息。 |

**返回值：**

| 类型                | 说明                                                        |
| ------------------- | ----------------------------------------------------------- |
| Promise\<void>       | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息                                 |
| ------- | ----------------------------------------|
| 201     | Permission denied.                      |
| 202     | Non-system applications use system APIs.                      |
| 401     | Parameter error.                        |
| 2100001 | Invalid parameter value.                |
| 2200002 |Failed to connect to the service. |
| 2200003 | System internal error.                  |
| 2201004 | Invalid Ethernet profile.  |
| 2201005 | Device information does not exist.  |
| 2201006 | Ethernet device not connected.                    |
| 2201007 | Ethernet failed to write user configuration information.    |

**示例：**

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

## ethernet.isIfaceActive

isIfaceActive(iface: string, callback: AsyncCallback\<number>): void

判断接口是否已激活。使用callback异步回调。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.GET_NETWORK_INFO

**系统能力**：SystemCapability.Communication.NetManager.Ethernet

**参数：**

| 参数名   | 类型                        | 必填 | 说明                                               |
| -------- | --------------------------- | ---- | -------------------------------------------------- |
| iface    | string                      | 是   | 接口名。为空时代表查询是否存在激活接口。             |
| callback | AsyncCallback\<number>       | 是   | 回调函数。 <br>- 1：已激活<br>- 0：未激活<br>- 其他值:表示获取失败的错误码。 |

**错误码：**

| 错误码ID | 错误信息                                 |
| ------- | ----------------------------------------|
| 201     | Permission denied.                      |
| 202     | Non-system applications use system APIs.                      |
| 401     | Parameter error.                        |
| 2200001 | Invalid parameter value.                |
| 2200002 | Failed to connect to the service.       |
| 2200003 | System internal error.                  |
| 2201005 | Device information does not exist.  |

**示例：**

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

## ethernet.isIfaceActive

isIfaceActive(iface: string): Promise\<number>

判断接口是否已激活。使用Promise异步回调。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.GET_NETWORK_INFO

**系统能力**：SystemCapability.Communication.NetManager.Ethernet

**参数：**

| 参数名 | 类型   | 必填 | 说明                                   |
| ------ | ------ | ---- | -------------------------------------- |
| iface  | string | 是   | 接口名。为空时代表查询是否存在激活接口。 |

**返回值：**

| 类型            | 说明                                                               |
| ----------------| ------------------------------------------------------------------ |
| Promise\<number> | Promise对象，返回获取结果。已激活：1，未激活：0，其他为获取失败错误码。|

**错误码：**

| 错误码ID | 错误信息                                 |
| ------- | ----------------------------------------|
| 201     | Permission denied.                      |
| 202     | Non-system applications use system APIs.                      |
| 401     | Parameter error.                        |
| 2200001 | Invalid parameter value.                |
| 2200002 | Failed to connect to the service.       |
| 2200003 | System internal error.                  |
| 2201005 | Device information does not exist.  |

**示例：**

```ts
import { ethernet } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

ethernet.isIfaceActive("eth0").then((data: number) => {
  console.info("isIfaceActive promise = " + JSON.stringify(data));
}).catch((error: BusinessError) => {
  console.error("isIfaceActive promise error = " + JSON.stringify(error));
});
```

## ethernet.getAllActiveIfaces

getAllActiveIfaces(callback: AsyncCallback\<Array\<string>>): void

获取活动的网络接口。使用callback异步回调。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.GET_NETWORK_INFO

**系统能力**：SystemCapability.Communication.NetManager.Ethernet

**参数：**

| 参数名   | 类型                                 | 必填 | 说明                           |
| -------- | ------------------------------------ | ---- | ------------------------------ |
| callback | AsyncCallback\<Array\<string>>         | 是   | 回调函数。返回值为对应接口名。 |

**错误码：**

| 错误码ID | 错误信息                                 |
| ------- | ----------------------------------------|
| 201     | Permission denied.                      |
| 202     | Non-system applications use system APIs.                      |
| 2200002 | Failed to connect to the service.       |
| 2200003 | System internal error.                  |

**示例：**

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

## ethernet.getAllActiveIfaces

getAllActiveIfaces(): Promise\<Array\<string>>

获取活动的网络接口。使用Promise异步回调。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.GET_NETWORK_INFO

**系统能力**：SystemCapability.Communication.NetManager.Ethernet

**返回值：**

| 类型                           | 说明                                            |
| ------------------------------ | ----------------------------------------------- |
| Promise\<Array\<string>>         | Promise对象，返回获取结果。返回值为对应接口名。 |

**错误码：**

| 错误码ID | 错误信息                                 |
| ------- | ----------------------------------------|
| 201     | Permission denied.                      |
| 202     | Non-system applications use system APIs.                      |
| 2200002 | Failed to connect to the service.       |
| 2200003 | System internal error.                  |

**示例：**

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

注册网卡热插拔事件。使用callback异步回调。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.GET_NETWORK_INFO

**系统能力**：SystemCapability.Communication.NetManager.Ethernet

**参数：**

| 参数名   | 类型                                    | 必填 | 说明       |
| -------- | --------------------------------------- | ---- | ---------- |
| type     | string                  | 是   | 订阅的事件类型，'interfaceStateChange'。 |
| callback | Callback\<[InterfaceStateInfo](#interfacestateinfo11)> | 是   | 回调函数，返回以太网卡状态信息。 |

**错误码：**

| 错误码ID | 错误信息                                      |
| ------- | -------------------------------------------- |
| 201     | Permission denied.                      |
| 202     | Non-system applications use system APIs.                      |
| 401     | Parameter error.                     |

**示例：**

```ts
import { ethernet } from '@kit.NetworkKit';

ethernet.on('interfaceStateChange', (data: object) => {
  console.info('on interfaceSharingStateChange：' + JSON.stringify(data));
});
```

## ethernet.off('interfaceStateChange')<sup>10+</sup>

off(type: 'interfaceStateChange', callback?: Callback\<InterfaceStateInfo\>): void

注销网卡热插拔事件。使用callback异步回调。

**系统接口**：此接口为系统接口。

**需要权限**：ohos.permission.GET_NETWORK_INFO

**系统能力**：SystemCapability.Communication.NetManager.Ethernet

**参数：**

| 参数名   | 类型                                    | 必填 | 说明       |
| -------- | --------------------------------------- | ---- | ---------- |
| type     | string                  | 是   | 订阅的事件类型，'interfaceStateChange'。 |
| callback | Callback\<[InterfaceStateInfo](#interfacestateinfo11)> | 否   | 回调函数，返回以太网卡状态信息。 |

**错误码：**

| 错误码ID | 错误信息                                      |
| ------- | -------------------------------------------- |
| 201     | Permission denied.                      |
| 202     | Non-system applications use system APIs.                      |
| 401     | Parameter error.                     |

**示例：**

```ts
import { ethernet } from '@kit.NetworkKit';

ethernet.off('interfaceStateChange');
```


## InterfaceStateInfo<sup>11+</sup>

监听以太网卡状态变化。

**系统接口**：此接口为系统接口。

**系统能力**：SystemCapability.Communication.NetManager.Ethernet

| 名称         | 类型                    | 只读 |可选| 说明                                                 |
| ------------ | ----------------------- | --- | ---|------------------------------------------------- |
| iface        | string                  |  否 |否 |以太网卡名称。                                        |
| active       | boolean                 |  否 |否 |以太网卡是否处于激活状态。true表示激活，false表示未激活。 |

