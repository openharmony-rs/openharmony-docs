# getAllTxBytes

## 导入模块

```TypeScript
```

## getAllTxBytes

```TypeScript
function getAllTxBytes(callback: AsyncCallback<number>): void
```

获取所有网卡从最近一次开机开始至接口调用时刻的上行流量总和（单位：字节）。使用callback异步回调。

**起始版本：** 10

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NetManager.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数。当成功获取到流量数据时，error为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |
| [2103005](../errorcode-net-statistics.md#2103005-读取系统map失败) | Failed to read the system map. |
| [2103011](../errorcode-net-statistics.md#2103011-系统map创建失败) | Failed to create a system map. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { statistics } from '@kit.NetworkKit';

statistics.getAllTxBytes((error: BusinessError, stats: number) => {
  if (error) {
    console.error(JSON.stringify(error));
    return;
  }
  console.info(JSON.stringify(stats));
});
```


## getAllTxBytes

```TypeScript
function getAllTxBytes(): Promise<number>
```

获取所有网卡从最近一次开机开始至接口调用时刻的上行流量总和（单位：字节）。使用Promise异步回调。

**起始版本：** 10

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Communication.NetManager.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;number & gt; | The promise returned by the function. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |
| [2103005](../errorcode-net-statistics.md#2103005-读取系统map失败) | Failed to read the system map. |
| [2103011](../errorcode-net-statistics.md#2103011-系统map创建失败) | Failed to create a system map. |

**示例**

```TypeScript
import { statistics } from '@kit.NetworkKit';

statistics.getAllTxBytes().then((stats: number) => {
  console.info(JSON.stringify(stats));
});
```
