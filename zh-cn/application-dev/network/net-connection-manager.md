# 网络连接管理

## 简介

网络连接管理提供管理网络一些基础能力，包括WiFi/蜂窝/Ethernet等多网络连接优先级管理、网络质量评估、订阅默认/指定网络连接状态变化、查询网络连接信息、DNS解析等功能。

> **说明：**
>
> 为了保证应用的运行效率，大部分API调用都是异步的，对于异步调用的API，均提供了callback和Promise两种方式，以下示例均采用promise函数，更多方式可以查阅[API参考](../reference/apis-network-kit/js-apis-net-connection.md)。

## 基本概念

- 网络生产者：数据网络的提供方。例如WiFi、蜂窝、Ethernet等。
- 网络消费者：数据网络的使用方。例如应用或系统服务。
- 网络探测：检测网络有效性，避免将网络从可用网络切换到不可用网络。包括绑定网络探测、DNS探测、HTTP探测及HTTPS探测。
- 网络优选：处理多网络共存时选择最优网络。在网络状态、网络信息及评分发生变化时被触发。
- 默认网络：默认路由所在的网络。

## 场景介绍

网络连接管理的典型场景如下所示。

- 接收指定网络的状态变化通知。
- 获取所有注册的网络。
- 查询默认网络或者指定网络的连接信息。
- 使用默认网络解析域名，获取所有IP。

具体开发方式介绍如下。

## 接收指定网络的状态变化通知

1. 声明接口调用所需要的权限：ohos.permission.GET_NETWORK_INFO。
此权限级别为normal，在申请权限前，请保证符合[权限使用的基本原则](../security/AccessToken/app-permission-mgmt-overview.md#权限使用的基本原则)。然后参考[访问控制-声明权限](../security/AccessToken/declare-permissions.md)声明对应权限。

2. 从@kit.NetworkKit中导入connection命名空间。

    ```ts
    // 引入包名。
    import { connection } from '@kit.NetworkKit';
    import { BusinessError } from '@kit.BasicServicesKit';
    ```

3. 调用[createNetConnection](../reference/apis-network-kit/js-apis-net-connection.md#connectioncreatenetconnection)方法，指定网络能力、网络类型和超时时间(可选，如不传入代表默认网络；创建不同于默认网络时可通过指定这些参数完成)，创建一个NetConnection对象。

    ```ts
    let netSpecifier: connection.NetSpecifier = {
      netCapabilities: {
        // 假设当前默认网络是WiFi，需要创建蜂窝网络连接，可指定网络类型为蜂窝网。
        bearerTypes: [connection.NetBearType.BEARER_CELLULAR],
        // 指定网络能力为Internet。
        networkCap: [connection.NetCap.NET_CAPABILITY_INTERNET]
      },
    };

    // 指定超时时间为10s(默认值为0)。
    let timeout = 10 * 1000;

    // 创建NetConnection对象。
    let conn = connection.createNetConnection(netSpecifier, timeout);
    ```

4. 调用该对象的[register()](../reference/apis-network-kit/js-apis-net-connection.md#register)方法，订阅指定网络状态变化的通知。当网络可用时，会收到netAvailable事件的回调；当网络不可用时，会收到netUnavailable事件的回调。

    ```ts
    // 订阅指定网络状态变化的通知。
    conn.register((err: BusinessError, data: void) => {
      console.log(JSON.stringify(err));
    });
    ```

5. 调用该对象的[on()](../reference/apis-network-kit/js-apis-net-connection.md#onnetavailable)方法，传入type和callback，订阅关心的事件。

    ```ts
    // 订阅事件，如果当前指定网络可用，通过on_netAvailable通知用户。
    conn.on('netAvailable', ((data: connection.NetHandle) => {
      console.log("net is available, netId is " + data.netId);
    }));

    // 订阅事件，如果当前指定网络不可用，通过on_netUnavailable通知用户。
    conn.on('netUnavailable', ((data: void) => {
      console.log("net is unavailable, data is " + JSON.stringify(data));
    }));
    ```
6. 当不使用该网络时，可以调用该对象的[unregister()](../reference/apis-network-kit/js-apis-net-connection.md#unregister)方法，取消订阅。

    ```ts
    // 当不使用该网络时，可以调用该对象的unregister()方法，取消订阅。
    conn.unregister((err: BusinessError, data: void) => {
    });
    ```

## 监控默认网络变化并主动重建网络连接

根据当前网络状态及网络质量情况，默认网络可能会发生变化，如下所示。
1. 在WiFi弱信号的情况下，默认网络可能会切换到蜂窝网络。
2. 在蜂窝网络状态差的情况下，默认网络可能会切换到WiFi。
3. 关闭WiFi后，默认网络可能会切换到蜂窝网络。
4. 关闭蜂窝网络后，默认网络可能会切换到WiFi。
5. 在WiFi弱信号的情况下，默认网络可能会切换到其他WiFi(存在跨网情况)。
6. 在蜂窝网络状态差的情况下，默认网络可能会切换到其他蜂窝(存在跨网情况)。

本节旨在介绍监控默认网络的变化后，应用报文能够快速迁移到新默认网络上，具体做法如下。

### 监控默认网络变化

```ts
import { connection } from '@kit.NetworkKit';

const netConnection = connection.createNetConnection();
// 监听默认网络改变。
netConnection.on('netAvailable', (data: connection.NetHandle) => {
 console.log(JSON.stringify(data));
})
```

### 默认网络变化后重新建立网络连接

<!--RP1-->

<!--RP1End-->

#### 原网络连接使用Socket模块建立连接
```ts
import { connection, socket } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 创建socket对象。
let sock: socket.TCPSocket = socket.constructTCPSocketInstance();

function useSocket() {
  let netAddress: socket.NetAddress = {
    address: '192.168.xx.xxx',
    port: 8080
  }
  let tcpConnectOptions: socket.TCPConnectOptions = {
    address: netAddress,
    timeout: 6000
  }

  // 建立socket连接。
  sock.connect(tcpConnectOptions, (err: BusinessError) => {
    if (err) {
      console.error('connect fail');
      return;
    }
    console.log('connect success');
    let tcpSendOptions: socket.TCPSendOptions = {
      data: 'Hello, server!'
    }
    socketSend(tcpSendOptions);
  })
}

// 通过socket发送数据。
function socketSend(tcpSendOptions: socket.TCPSendOptions) {
  sock.send(tcpSendOptions).then(() => {
    console.log('send success');
  }).catch((err: BusinessError) => {
    console.error('send fail');
  });
}


function socketTest() {
  const netConnection = connection.createNetConnection();
  // 网络切换会导致网络发生中断，原socket失效，故需重新建立socket。
  netConnection.on('netAvailable', (netHandle: connection.NetHandle) => {
    console.info("default network changed: " + JSON.stringify(netHandle));
    sock.close();
    sock = socket.constructTCPSocketInstance();
    // 通过socket发送数据。
    useSocket();
  });

  // 订阅指定网络状态变化的通知。
  netConnection.register((error: BusinessError) => {
    if (error) {
      console.error("register fail: " + JSON.stringify(error));
    } else {
      console.info("register success");
    }
  });
}
```

#### 原网络连接使用Socket Library建立网络连接

监控到默认网络变化后关闭原有Socket并重新建立Socket连接。

## 获取所有注册的网络

1. 声明接口调用所需要的权限：ohos.permission.GET_NETWORK_INFO。
此权限级别为normal，在申请权限前，请保证符合[权限使用的基本原则](../security/AccessToken/app-permission-mgmt-overview.md#权限使用的基本原则)。然后参考[访问控制-声明权限](../security/AccessToken/declare-permissions.md)声明对应权限。

2. 示例代码
    ```ts
    // 从@kit.NetworkKit中导入connection命名空间。
    import { connection } from '@kit.NetworkKit';
    import { BusinessError } from '@kit.BasicServicesKit';

    // 调用getAllNets方法，获取所有处于连接状态的网络列表。
    connection.getAllNets().then((data: connection.NetHandle[]) => {
      console.info("Succeeded to get data: " + JSON.stringify(data));
      if (data) {
        GlobalContext.getContext().netList = data;
      }
    });
    ```

## 查询默认网络或者指定网络的连接信息

1. 声明接口调用所需要的权限：ohos.permission.GET_NETWORK_INFO。
此权限级别为normal，在申请权限前，请保证符合[权限使用的基本原则](../security/AccessToken/app-permission-mgmt-overview.md#权限使用的基本原则)。然后参考[访问控制-声明权限](../security/AccessToken/declare-permissions.md)声明对应权限。
2. 查询默认网络或指定网络连接信息代码示例
   
   通过调用[getDefaultNet](../reference/apis-network-kit/js-apis-net-connection.md#connectiongetdefaultnet)方法，获取默认的数据网络(NetHandle)；调用[getNetCapabilities](../reference/apis-network-kit/js-apis-net-connection.md#connectiongetnetcapabilities)方法，获取该NetHandle对应网络的能力信息。能力信息包含了网络类型(蜂窝网络、Wi-Fi网络、以太网网络等)、网络具体能力等网络信息。也可以调用[getConnectionProperties](../reference/apis-network-kit/js-apis-net-connection.md#connectiongetconnectionproperties)方法，获取该NetHandle对应网络的连接信息。


    ```ts
    // 从@kit.NetworkKit中导入connection命名空间。
    import { connection } from '@kit.NetworkKit';
    import { BusinessError } from '@kit.BasicServicesKit';
    
    function getDefaultNetsInfo() {
      let netHandleInfo:connection.NetHandle|null = null;
      // 调用getDefaultNet方法，获取默认的数据网络(NetHandle)。
      connection.getDefaultNet().then((data:connection.NetHandle) => {
        if (data.netId == 0) {
          console.log("don't have defaultNet");
          // 当前无默认网络时，获取的netHandler的netid为0,属于异常情况，需要额外处理。
          return;
        }
        if (data) {
          console.info("getDefaultNet get data: " + JSON.stringify(data));
          // 获取netHandle对应网络的能力信息。能力信息包含了网络类型、网络具体能力等网络信息。
          netHandleInfo = data;
          connection.getNetCapabilities(netHandleInfo).then((data: connection.NetCapabilities) => {
            console.info("getNetCapabilities get data: " + JSON.stringify(data));
            // 获取网络类型(bearerTypes)。
            let bearerTypes: Set<number> = new Set(data.bearerTypes);
            let bearerTypesNum = Array.from(bearerTypes.values());
            for (let item of bearerTypesNum) {
              if (item == 0) {
                // 蜂窝网络。
                console.log(JSON.stringify("BEARER_CELLULAR"));
              } else if (item == 1) {
                // Wi-Fi网络。
                console.log(JSON.stringify("BEARER_WIFI"));
              } else if (item == 3) {
                // 以太网网络。
                console.log(JSON.stringify("BEARER_ETHERNET"));
              }
            }
    
            // 获取网络具体能力(networkCap)。
            let itemNumber : Set<number> = new Set(data.networkCap);
            let dataNumber = Array.from(itemNumber.values());
            for (let item of dataNumber) {
              if (item == 0) {
                // 表示网络可以访问运营商的MMSC(Multimedia Message Service，多媒体短信服务)发送和接收彩信。
                console.log(JSON.stringify("NET_CAPABILITY_MMS"));
              } else if (item == 11) {
                // 表示网络流量未被计费。
                console.log(JSON.stringify("NET_CAPABILITY_NOT_METERED"));
              } else if (item == 12) {
                // 表示该网络应具有访问Internet的能力，该能力由网络提供者设置。
                console.log(JSON.stringify("NET_CAPABILITY_INTERNET"));
              } else if (item == 15) {
                // 表示网络不使用VPN(Virtual Private Network，虚拟专用网络)。
                console.log(JSON.stringify("NET_CAPABILITY_NOT_VPN"));
              } else if (item == 16) {
                // 表示该网络访问Internet的能力被网络管理成功验证，该能力由网络管理模块设置。
                console.log(JSON.stringify("NET_CAPABILITY_VALIDATED"));
              }
            }
          })
        }
      });
    
      // 获取netHandle对应的网络的连接信息。
      connection.getConnectionProperties(netHandleInfo).then((data: connection.ConnectionProperties) => {
        console.info("getConnectionProperties get data: " + JSON.stringify(data));
      })
    }
    ```
3. 查询所有网络连接信息代码示例
   
   通过调用[getAllNets](../reference/apis-network-kit/js-apis-net-connection.md#connectiongetallnets)方法，获取所有处于连接状态的网络列表(Array\<NetHandle>)。然后遍历获取到的NetHandle数组，分别调用[getNetCapabilities](../reference/apis-network-kit/js-apis-net-connection.md#connectiongetnetcapabilities)方法，获取该NetHandle对应网络的能力信息，能力信息包含了网络类型(蜂窝网络、Wi-Fi网络、以太网网络等)、网络具体能力等网络信息。也可以调用[getConnectionProperties](../reference/apis-network-kit/js-apis-net-connection.md#connectiongetconnectionproperties)方法，获取该NetHandle对应网络的连接信息。

    ```ts
    // 从@kit.NetworkKit中导入connection命名空间。
    import { connection } from '@kit.NetworkKit';
    import { BusinessError } from '@kit.BasicServicesKit';

    function getAllNetsInfo() {
      // 调用getAllNets,获取所有处于连接状态的网络列表(Array<NetHandle>)。
      connection.getAllNets().then((data: connection.NetHandle[]) => {
        console.info("getAllNets get data: " + JSON.stringify(data));
        if (data) {
          let itemNumber : Set<connection.NetHandle> = new Set(data);
          let dataNumber = Array.from(itemNumber.values());
          for (let item of dataNumber) {
            // 循环获取网络列表每个netHandle对应网络的能力信息。
            connection.getNetCapabilities(item).then((data: connection.NetCapabilities) => {
              console.info("getNetCapabilities get data: " + JSON.stringify(data));
            })

            // 循环获取网络列表每个netHandle对应的网络的连接信息。
            connection.getConnectionProperties(item).then((data: connection.ConnectionProperties) => {
              console.info("getConnectionProperties get data: " + JSON.stringify(data));
            })
          }
        }
      })
    }
    ```

## 判断默认网络是否可以访问互联网

如果应用需要检查当前连接的网络是否可以访问互联网，可参考以下步骤进行判断：

1. 声明接口调用所需要的权限：ohos.permission.GET_NETWORK_INFO
此权限级别为normal，在申请权限前，请保证符合[权限使用的基本原则](../security/AccessToken/app-permission-mgmt-overview.md#权限使用的基本原则)。然后参考[访问控制-声明权限](../security/AccessToken/declare-permissions.md)声明对应权限。

2. 代码示例
   
   调用[getDefaultNetSync](../reference/apis-network-kit/js-apis-net-connection.md#connectiongetdefaultnetsync9)方法，获取当前默认网络的netHandle，netHandle有效的情况下，调用[getNetCapabilitiesSync](../reference/apis-network-kit/js-apis-net-connection.md#connectiongetnetcapabilitiessync10)方法，获取NetHandle对应网络的能力信息，根据获取到的能力信息，判断networkCap数组中的值判断网络是否可用。
   NET_CAPABILITY_CHECKING_CONNECTIVITY表示在进行连通性判断的过程中，当不处于连通性判断过程中，且networkCap数组中包含NET_CAPABILITY_VALIDATED表示网络连通性校验通过，可以访问互联网。

    ```ts
    // 从@kit.NetworkKit中导入connection命名空间。
    import { connection } from '@kit.NetworkKit';
    import { BusinessError } from '@kit.BasicServicesKit';

    // 获取默认激活的数据网络。
    let netHandle = connection.getDefaultNetSync();
    if (!netHandle || netHandle.netId === 0) {
      console.error("getDefaultNetSync fail");
    } else {
      console.info("default network: " + JSON.stringify(netHandle));
      // 获取netHandle对应网络的能力信息。
      let netCapabilities = connection.getNetCapabilitiesSync(netHandle);
      let cap = netCapabilities.networkCap;
      console.info("network capabilities: " + JSON.stringify(netCapabilities));
      // 判断网络是否可以访问互联网。
      if (cap?.includes(connection.NetCap.NET_CAPABILITY_CHECKING_CONNECTIVITY)) {
        // 正在验证网络连通性，请稍后重试。
        console.info("default network is checking, please try again later");
      } else {
        if (cap?.includes(connection.NetCap.NET_CAPABILITY_VALIDATED)) {
          // 网络连通性验证成功，当前默认网络可以访问互联网。
          console.info("default network is validated");
        } else {
          // 网络连通性验证失败，当前默认网络不可以访问互联网。
          console.info("default network is not validated");
        }
      }
    }
    ```

## 使用默认网络解析域名，获取所有IP

1. 声明接口调用所需要的权限：ohos.permission.GET_NETWORK_INFO
此权限级别为normal，在申请权限前，请保证符合[权限使用的基本原则](../security/AccessToken/app-permission-mgmt-overview.md#权限使用的基本原则)。然后参考[访问控制-声明权限](../security/AccessToken/declare-permissions.md)声明对应权限。

2. 代码示例
   
   调用[getAddressesByName](../reference/apis-network-kit/js-apis-net-connection.md#connectiongetaddressesbyname)方法，使用默认网络解析主机名以获取所有IP地址。
    ```ts
    // 从@kit.NetworkKit中导入connection命名空间。
    import { connection } from '@kit.NetworkKit';
    import { BusinessError } from '@kit.BasicServicesKit';
    // 使用默认网络解析主机名以获取所有IP地址。
    connection.getAddressesByName("xxxx").then((data: connection.NetAddress[]) => {
      console.info("Succeeded to get data: " + JSON.stringify(data));
    });
    ```
