# @ohos.net.sharing (网络共享管理)

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->

网络共享管理模块用于将设备网络连接共享给其他连接设备。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>- 本模块首批接口从API version 9开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。


## 导入模块

```js
import { sharing } from '@kit.NetworkKit';
```

## NetHandle

type NetHandle = connection.NetHandle

数据网络的句柄。在调用NetHandle的方法之前，需要先获取NetHandle对象。

**系统能力：** SystemCapability.Communication.NetManager.Core

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

| 类型   | 说明                                                         |
| ------ | ------------------------------------------------------------ |
| [connection.NetHandle](./js-apis-net-connection.md#nethandle) | 网络链路信息。 |

## NetAddress

type NetAddress = connection.NetAddress

网络地址。

**ArkTS-Dyn起始版本：** 26.1.0

**ArkTS-Sta起始版本：** 26.1.0

**系统能力**：SystemCapability.Communication.NetManager.Core

| 类型 | 说明 |
| ---- | ---- |
| [connection.NetAddress](./js-apis-net-connection.md#netaddress) | 网络地址信息。 |

## SharingIfaceType

网络共享类型的枚举。

**ArkTS-Dyn起始版本：** 26.1.0

**ArkTS-Sta起始版本：** 26.1.0

**系统能力**：SystemCapability.Communication.NetManager.NetSharing

| 名称 | 值 | 说明 |
| ---- | -- | ---- |
| SHARING_WIFI | 0 | Wi-Fi |
| SHARING_USB | 1 | USB |
| SHARING_BLUETOOTH | 2 | 蓝牙 |

## sharing.getSharingAddress

getSharingAddress(type: SharingIfaceType): Promise\<Array\<NetAddress>>

获取指定网络共享类型的共享IP地址。使用Promise异步回调。

**ArkTS-Dyn起始版本：** 26.1.0

**ArkTS-Sta起始版本：** 26.1.0

**需要权限**：ohos.permission.GET_NETWORK_INFO

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.Communication.NetManager.NetSharing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ---- | ---- | ---- |
| type | [SharingIfaceType](#sharingifacetype) | 是 | 网络共享类型，0：Wi-Fi 1：USB 2：蓝牙。 |

**返回值：**

| 类型 | 说明 |
| ---- | ---- |
| Promise\<Array\<[NetAddress](#netaddress)>> | Promise对象，返回共享接口的IP地址列表，返回值中的port字段固定为0，无需关注。该类型共享未开启、或尚未进入已共享状态时，返回空数组。 |

**错误码：**

以下错误码的详细介绍请参见[网络共享错误码](errorcode-net-sharing.md)和[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| -------- | -------- |
| 201 | Permission verification failed.The application does not have the permission required to call the API. |
| 2200001 | Invalid parameter value. |
| 2200002 | Failed to connect to the service. |
| 2200003 | System internal error. |

**示例：**

```js
import { sharing } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 开启 Wi-Fi 热点共享后，调用本接口获取共享接口 IP，用于展示给用户或在同一网段内建连。
sharing.getSharingAddress(sharing.SharingIfaceType.SHARING_WIFI)
  .then((addresses: sharing.NetAddress[]) => {
    console.info(`getSharingAddress success, addresses: ${JSON.stringify(addresses)}`);
  })
  .catch((error: BusinessError) => {
    console.error(`getSharingAddress failed, code: ${error.code}, message: ${error.message}`);
  });
```