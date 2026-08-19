# getSockfdTxBytes

## 导入模块

```TypeScript
import { statistics } from '@kit.NetworkKit';
```

## getSockfdTxBytes

```TypeScript
function getSockfdTxBytes(sockfd: int, callback: AsyncCallback<long>): void
```

获取指定Socket的上行流量（单位：字节）。使用callback异步回调。 > **说明：** > > 推荐在Socket连接时使用，否则Socket已经关闭后无法查询到对应流量数据。

**起始版本：** 23

<!--Device-statistics-function getSockfdTxBytes(sockfd: int, callback: AsyncCallback<long>): void--><!--Device-statistics-function getSockfdTxBytes(sockfd: int, callback: AsyncCallback<long>): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sockfd | int | 是 | 指定查询的Socket的FD(file description)。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;long&gt; | 是 | 回调函数。当成功获取Socket的上行流量时，error为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2100001](../errorcode-net-connection.md#2100001-非法参数值) | Invalid parameter value |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { statistics } from '@kit.NetworkKit';

let sockfd = 50; // 实际开发中需要先根据自己创建的socket获取到。
statistics.getSockfdTxBytes(sockfd, (error: BusinessError, stats: number) => {
  console.error(JSON.stringify(error));
  console.info(JSON.stringify(stats));
});
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { statistics } from '@kit.NetworkKit';

let sockfd = 50; // 实际开发中需要先根据自己创建的socket获取到。
statistics.getSockfdTxBytes(sockfd, (error: BusinessError|null, stats: long|undefined) => {
  console.error(JSON.stringify(error));
  console.info(JSON.stringify(stats));
});
```


## getSockfdTxBytes

```TypeScript
function getSockfdTxBytes(sockfd: int): Promise<long>
```

获取指定Socket的上行流量（单位：字节）。使用Promise异步回调。 > **说明：** > > 推荐在Socket连接时使用，否则Socket已经关闭后无法查询到对应流量数据。

**起始版本：** 23

<!--Device-statistics-function getSockfdTxBytes(sockfd: int): Promise<long>--><!--Device-statistics-function getSockfdTxBytes(sockfd: int): Promise<long>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sockfd | int | 是 | 指定查询的Socket的FD(file description)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;long&gt; | Promise对象。返回该Socket的上行流量（单位：字节）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2100001](../errorcode-net-connection.md#2100001-非法参数值) | Invalid parameter value |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { statistics } from '@kit.NetworkKit';

let sockfd = 50; // 实际开发中需要先根据自己创建的socket获取到。
statistics.getSockfdTxBytes(sockfd).then((stats: number) => {
  console.info(JSON.stringify(stats));
}).catch((err: BusinessError) => {
  console.error(JSON.stringify(err));
});
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { statistics } from '@kit.NetworkKit';

let sockfd = 50; // 实际开发中需要先根据自己创建的socket获取到。
statistics.getSockfdTxBytes(sockfd).then((stats: long) => {
  console.info(JSON.stringify(stats));
}).catch((err: Error) => {
  let businessError = err as BusinessError;
  console.error(JSON.stringify(err));
});
```

