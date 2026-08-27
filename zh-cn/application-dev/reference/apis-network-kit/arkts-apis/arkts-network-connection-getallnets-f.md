# getAllNets

## 导入模块

```TypeScript
```

## getAllNets

```TypeScript
function getAllNets(callback: AsyncCallback<Array<NetHandle>>): void
```

获取所有处于连接状态的网络列表，使用callback异步回调。

**起始版本：** 8

**需要权限：** ohos.permission.GET_NETWORK_INFO

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;NetHandle&gt;&gt; | 是 | 回调函数。当成功获取所有处于连接状态的网络列表时，error为undefined，data为处于激活状态的网络列表；否则为 错误对象。    **说明：** 在Wi-Fi和蜂窝数据开关均开启的情况下，若无应用指定使用蜂窝网络，则仅激活Wi-Fi网络，因此仅返回Wi-Fi的NetHandle。除非有特定应用启动蜂窝网络，才能同时获取Wi-Fi和蜂窝数据的 NetHandle。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |

**示例**

```TypeScript
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.getAllNets((error: BusinessError, data: connection.NetHandle[]) => {
  if (error) {
    console.error(`Failed to get all nets. Code:${error.code}, message:${error.message}`);
    return;
  }
  console.info("Succeeded to get data: " + JSON.stringify(data));
});
```


## getAllNets

```TypeScript
function getAllNets(): Promise<Array<NetHandle>>
```

获取所有处于连接状态的网络列表。使用Promise异步回调。

**起始版本：** 8

**需要权限：** ohos.permission.GET_NETWORK_INFO

**系统能力：** SystemCapability.Communication.NetManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;Array & lt;NetHandle & gt; & gt; | Promise对象，返回处于激活状态的网络列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |

**示例**

```TypeScript
import { connection } from '@kit.NetworkKit';

connection.getAllNets().then((data: connection.NetHandle[]) => {
  console.info("Succeeded to get data: " + JSON.stringify(data));
});
```
