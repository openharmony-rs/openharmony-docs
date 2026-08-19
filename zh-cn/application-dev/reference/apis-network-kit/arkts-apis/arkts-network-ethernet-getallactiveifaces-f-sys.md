# getAllActiveIfaces（系统接口）

## 导入模块

```TypeScript
import { ethernet } from '@kit.NetworkKit';
```

## getAllActiveIfaces

```TypeScript
function getAllActiveIfaces(callback: AsyncCallback<Array<string>>): void
```

获取活动的网络接口，使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.GET_NETWORK_INFO

<!--Device-ethernet-function getAllActiveIfaces(callback: AsyncCallback<Array<string>>): void--><!--Device-ethernet-function getAllActiveIfaces(callback: AsyncCallback<Array<string>>): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.Ethernet

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Array&lt;string&gt;&gt; | 是 | 回调函数。返回值为对应接口名。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2200003](../errorcode-net-ethernet.md#2200003-系统内部错误) | System internal error. |
| [2200002](../errorcode-net-ethernet.md#2200002-连接服务失败) | Failed to connect to the service. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |

**示例**

```TypeScript
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


## getAllActiveIfaces

```TypeScript
function getAllActiveIfaces(): Promise<Array<string>>
```

获取活动的网络接口，使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.GET_NETWORK_INFO

<!--Device-ethernet-function getAllActiveIfaces(): Promise<Array<string>>--><!--Device-ethernet-function getAllActiveIfaces(): Promise<Array<string>>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Ethernet

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | 以Promise形式返回获取结果。返回值为对应接口名。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2200003](../errorcode-net-ethernet.md#2200003-系统内部错误) | System internal error. |
| [2200002](../errorcode-net-ethernet.md#2200002-连接服务失败) | Failed to connect to the service. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |

**示例**

```TypeScript
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

