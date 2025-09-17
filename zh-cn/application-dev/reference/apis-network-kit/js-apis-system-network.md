# @system.network (网络状态)

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->

> **说明：**
> - 本模块首批接口从API version 3开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 从API Version 8 开始，该接口不再维护，推荐使用新接口['@ohos.net.connection'](js-apis-net-connection.md)。

## 导入模块


```
import network from '@system.network';
```


## 权限列表

ohos.permission.GET_WIFI_INFO

ohos.permission.GET_NETWORK_INFO


## network.getType<sup>3+</sup>

getType(options?: {<br>
&nbsp;&nbsp;success?: (data: NetworkResponse) => void;<br>
&nbsp;&nbsp;fail?: (data: any, code: number) => void;<br>
&nbsp;&nbsp;complete?: () => void;<br>
}): void

获取当前设备的网络类型。

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| success | Function | 否 | 接口调用成功的回调函数，返回值为[NetworkResponse](#networkresponse3)。 |
| fail | Function | 否 | 接口调用失败的回调函数。 |
| complete | Function | 否 | 接口调用结束的回调函数。 |

fail返回值：

| 错误码 | 说明 |
| -------- | -------- |
| 602 | 当前权限未声明。 |

**示例：**

```
export default class Network {
  getType() {
    network.getType({
      success: (data) => {
        console.log('success get network type:' + data.type);
      }
    });
  }
}
```


## network.subscribe<sup>3+</sup>

subscribe(options?:{<br>
&nbsp;&nbsp;success?: (data: NetworkResponse) => void;<br>
&nbsp;&nbsp;fail?: (data: any, code: number) => void;<br>
  }): void

订阅当前设备的网络连接状态。如果多次调用，会覆盖前一次调用。

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| success | Function | 否 | 网络发生变化的回调函数。返回值为[NetworkResponse](#networkresponse3)。 |
| fail | Function | 否 | 接口调用失败的回调函数。 |

fail返回值：

| 错误码 | 说明 |
| -------- | -------- |
| 602 | 当前权限未声明。 |
| 200 | 订阅失败。 |

**示例：**

```
export default class Network {
  subscribe() {
    network.subscribe({
      success: (data) => {
        console.log('success get network type:' + data.type);
      }
    });
  }
}
```


## network.unsubscribe<sup>3+</sup>

unsubscribe(): void

取消订阅设备的网络连接状态。

**系统能力：** SystemCapability.Communication.NetManager.Core

**示例：**

```
import network from '@system.network';

network.unsubscribe();
```


## NetworkResponse<sup>3+</sup>

**系统能力：** SystemCapability.Communication.NetManager.Core

| 名称   | 类型                                           | 只读 | 可选 |说明                    |
| -------- | ---------------------------------------------- | ---- | --- | ---------------------- |
| metered | boolean | 否 | 是  |是否按照流量计费。true：按照流量计费；false：不按照流量计费。 |
| type | string | 否 | 否 |网络类型，可能的值有2g，3g，4g，5g，wifi，none等。 |
