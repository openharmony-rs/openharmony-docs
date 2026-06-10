# 统计网络流量消耗
<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->

## 简介

流量管理提供了基于物理网络的数据流量统计能力，支持基于网卡/UID的流量统计。

流量管理主要实现功能有：

- 支持基于网卡的流量统计。
- 支持基于应用UID流量统计。
<br>
> **说明：**
>
> - 为了保证应用的运行效率，大部分API调用都是异步的，对于异步调用的API均提供了callback和Promise两种方式，以下示例均采用Promise函数，更多方式可以查阅[@ohos.net.statistics (流量管理)](../reference/apis-network-kit/js-apis-net-statistics.md)。
> - 上行流量是指由终端设备向网络侧发送的数据量，下行流量是指由网络侧向终端设备发起传输的数据量。

以下分别介绍具体开发方式。

## 开发步骤

1. 导入[statistics](../reference/apis-network-kit/js-apis-net-statistics.md)、[socket](../reference/apis-network-kit/js-apis-socket.md)以及错误码模块。

   <!-- @[flow_management_case_module_import](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/FlowManagement_case/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   import { socket, statistics } from '@kit.NetworkKit';
   import { BusinessError } from '@kit.BasicServicesKit';
   import { hilog } from '@kit.PerformanceAnalysisKit';
   ```
2. 获取指定网卡流量数据。

   分别调用[getIfaceRxBytes](../reference/apis-network-kit/js-apis-net-statistics.md#statisticsgetifacerxbytes-1)和[getIfaceTxBytes](../reference/apis-network-kit/js-apis-net-statistics.md#statisticsgetifacetxbytes-1)接口传入网卡名获取指定网卡从最近一次开机至今的下行和上行流量数据。

   <!-- @[flow_management_getIfaceRxBytes_and_getIfaceTxBytes](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/FlowManagement_case/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
     // wlan0为主WiFi网卡名，获取主WiFi实时下行流量数据。
     statistics.getIfaceRxBytes('wlan0').then((stats: number) => {
       hilog.info(0x0000, 'testTag', JSON.stringify(stats));
       // ...
     })
     .catch((err: BusinessError) => {
       hilog.error(0x0000, 'testTag', JSON.stringify(err));
       // ...
     });
     // ...
     // wlan0为主WiFi网卡名，获取主WiFi实时上行流量数据。
     statistics.getIfaceTxBytes('wlan0').then((stats: number) => {
       hilog.info(0x0000, 'testTag', JSON.stringify(stats));
       // ...
     })
     .catch((err: BusinessError) => {
       hilog.error(0x0000, 'testTag', JSON.stringify(err));
       // ...
     });
   // ...
   ```
3. 获取蜂窝流量数据。

    分别调用[getCellularRxBytes](../reference/apis-network-kit/js-apis-net-statistics.md#statisticsgetcellularrxbytes-1)和[getCellularTxBytes](../reference/apis-network-kit/js-apis-net-statistics.md#statisticsgetcellulartxbytes-1)接口获取从最近一次开机至今的蜂窝下行和上行流量数据。

   <!-- @[flow_management_getCellularRxBytes_and_getCellularTxBytes](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/FlowManagement_case/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   // 获取蜂窝实时下行流量数据。
   statistics.getCellularRxBytes().then((stats: number) => {
     hilog.info(0x0000, 'testTag', JSON.stringify(stats));
     // ...
   })
   // ...
   // 获取蜂窝实时上行流量数据。
   statistics.getCellularTxBytes().then((stats: number) => {
     hilog.info(0x0000, 'testTag', JSON.stringify(stats));
     // ...
   })
   // ...
   ```
4. 获取所有网卡流量数据。

    分别调用[getAllRxBytes](../reference/apis-network-kit/js-apis-net-statistics.md#statisticsgetallrxbytes-1)和[getAllTxBytes](../reference/apis-network-kit/js-apis-net-statistics.md#statisticsgetalltxbytes-1)接口获取所有网卡从最近一次开机到现在的下行和上行流量数据。

   <!-- @[flow_management_getAllRxBytes_and_getAllTxBytes](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/FlowManagement_case/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   // 获取所有网卡实时下行流量数据。
   statistics.getAllRxBytes().then((stats: number) => {
     hilog.info(0x0000, 'testTag', JSON.stringify(stats));
     // ...
   })
   // ...
   // 获取所有网卡实时上行流量数据。
   statistics.getAllTxBytes().then((stats: number) => {
     hilog.info(0x0000, 'testTag', JSON.stringify(stats));
     // ...
   })
   // ...
   ```
5. 获取指定应用流量数据。

    分别调用[getUidRxBytes](../reference/apis-network-kit/js-apis-net-statistics.md#statisticsgetuidrxbytes-1)和[getUidTxBytes](../reference/apis-network-kit/js-apis-net-statistics.md#statisticsgetuidtxbytes-1)接口，传入UID获取指定应用从最近一次开机至今的下行和上行流量数据。<br>
    此处仅以应用UID为20010038为例，实际调用时需修改为真实UID。
   ```ts
    let UID = 20010038;
   ```
   <!-- @[flow_management_getUidRxBytes_and_getUidTxBytes](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/FlowManagement_case/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   // 获取指定应用实时下行流量数据。
   // ...
   statistics.getUidRxBytes(UID).then((stats: number) => {
     hilog.info(0x0000, 'testTag', JSON.stringify(stats));
     // ...
   })
   // ...
   // 获取指定应用实时上行流量数据。
   // ...
   statistics.getUidTxBytes(UID).then((stats: number) => {
     hilog.info(0x0000, 'testTag', JSON.stringify(stats));
     // ...
   })
   // ...
   ```
6. 获取指定socket流量数据。

    分别调用[getSockfdRxBytes](../reference/apis-network-kit/js-apis-net-statistics.md#statisticsgetsockfdrxbytes11-1)接口和[getSockfdTxBytes](../reference/apis-network-kit/js-apis-net-statistics.md#statisticsgetsockfdtxbytes11-1)，传入socket fd获取指定socket的下行和上行流量数据。

   <!-- @[flow_management_getSockfdRxBytes_and_getSockfdTxBytes](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/FlowManagement_case/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   // 获取指定socket实时下行流量数据。
   let tcp: socket.TCPSocket = socket.constructTCPSocketInstance();
   // ...
   tcp.getSocketFd().then((sockfd: number) => {
     statistics.getSockfdRxBytes(sockfd).then((stats: number) => {
       hilog.info(0x0000, 'testTag', JSON.stringify(stats));
       // ...
     }).catch((err: BusinessError) => {
       hilog.error(0x0000, 'testTag', JSON.stringify(err));
       // ...
     });
   })
   // ...
   // 获取指定socket实时上行流量数据。
   tcp.getSocketFd().then((sockfd: number) => {
     statistics.getSockfdTxBytes(sockfd).then((stats: number) => {
       hilog.info(0x0000, 'testTag', JSON.stringify(stats));
       // ...
     }).catch((err: BusinessError) => {
       hilog.error(0x0000, 'testTag', JSON.stringify(err));
       // ...
     });
   })
   // ...
   ```
<!--Del-->
## 获取网卡/应用UID的历史流量统计数据

1. 获取指定网卡历史流量信息。
2. 获取指定应用历史流量信息。

      ```ts
      import { statistics } from '@kit.NetworkKit';

      class IfaceInfo {
        iface: string = "wlan0",
        startTime: number = 1685948465,
        endTime: number = 16859485670
      }
      // 获取指定网卡历史流量信息。
      statistics.getTrafficStatsByIface(new IfaceInfo()).then((statsInfo: statistics.NetStatsInfo) => {
        console.info(
          "getTrafficStatsByIface bytes of received = " +
          JSON.stringify(statsInfo.rxBytes)
        );
        console.info(
          "getTrafficStatsByIface bytes of sent = " +
          JSON.stringify(statsInfo.txBytes)
        );
        console.info(
          "getTrafficStatsByIface packets of received = " +
          JSON.stringify(statsInfo.rxPackets)
        );
        console.info(
          "getTrafficStatsByIface packets of sent = " +
          JSON.stringify(statsInfo.txPackets)
        );
      });

      class UidInfo {
        uid: number = 20010037
        ifaceInfo: IfaceInfo = new IfaceInfo()
      }

      let uidInfo = new UidInfo()

      // 获取指定应用历史流量信息。
      statistics.getTrafficStatsByUid(uidInfo).then((statsInfo: statistics.NetStatsInfo) => {
        console.info("getTrafficStatsByUid bytes of received = " + JSON.stringify(statsInfo.rxBytes));
        console.info("getTrafficStatsByUid bytes of sent = " + JSON.stringify(statsInfo.txBytes));
        console.info("getTrafficStatsByUid packets of received = " + JSON.stringify(statsInfo.rxPackets));
        console.info("getTrafficStatsByUid packets of sent = " + JSON.stringify(statsInfo.txPackets));
      })
      ```

## 订阅流量变化事件

1. 订阅流量改变事件通知。
2. 取消订阅流量改变事件通知。

      ```ts
      import { statistics } from '@kit.NetworkKit';

      class Data {
        iface: string = ""
        uid?: number = 0
      }

      let callback = (data: Data) => {
        console.info('on netStatsChange, data:' + JSON.stringify(data));
      };
      // 订阅流量改变事件通知。
      statistics.on('netStatsChange', callback);

      // 取消订阅流量改变事件通知。可以指定传入on中的callback取消一个订阅，也可以不指定callback清空所有订阅。
      statistics.off('netStatsChange', callback);
      statistics.off('netStatsChange');
      ```
      <!--DelEnd-->

## 相关实例

针对流量管理的开发，有以下相关实例可供参考：

- [流量管理](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/NetWork_Kit/NetWorkKit_NetManager/FlowManagement_case)
