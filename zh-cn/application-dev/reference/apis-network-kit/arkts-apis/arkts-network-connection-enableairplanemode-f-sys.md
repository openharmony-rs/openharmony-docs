# enableAirplaneMode（系统接口）

## 导入模块

```TypeScript
```

## enableAirplaneMode

```TypeScript
function enableAirplaneMode(callback: AsyncCallback<void>): void
```

开启飞行模式，使用callback异步回调。

**起始版本：** 8

**需要权限：** ohos.permission.CONNECTIVITY_INTERNAL

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。 |

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
import { connection } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

connection.enableAirplaneMode((error: BusinessError) => {
  console.error(JSON.stringify(error));
});
```


## enableAirplaneMode

```TypeScript
function enableAirplaneMode(): Promise<void>
```

开启飞行模式，使用Promise异步回调。

**起始版本：** 8

**需要权限：** ohos.permission.CONNECTIVITY_INTERNAL

**系统能力：** SystemCapability.Communication.NetManager.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | 无返回值的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Failed to connect to the service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |

**示例**

```TypeScript
import { connection } from '@kit.NetworkKit';

connection.enableAirplaneMode().then((error: void) => {
  console.error(JSON.stringify(error));
});
```
