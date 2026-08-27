# on（系统接口）

## 导入模块

```TypeScript
```

## on('netStatsChange')

```TypeScript
function on(type: 'netStatsChange', callback: Callback<NetStatsChangeInfo>): void
```

订阅流量改变事件通知。使用callback异步回调。

**起始版本：** 10

**需要权限：** ohos.permission.GET_NETWORK_STATS

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'netStatsChange' | 是 | 订阅事件，固定为'netStatsChange'。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[NetStatsChangeInfo](arkts-network-statistics-netstatschangeinfo-i-sys.md)&gt; | 是 | 当流量有改变时触发回调函数。<br>**起始版本：** 11 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |

**示例**

```TypeScript
import { statistics } from '@kit.NetworkKit';

class IFace {
  iface: string = ""
  uid?: number = 0
}
statistics.on('netStatsChange', (data: IFace) => {
  console.info('on netStatsChange' + JSON.stringify(data));
});
```
