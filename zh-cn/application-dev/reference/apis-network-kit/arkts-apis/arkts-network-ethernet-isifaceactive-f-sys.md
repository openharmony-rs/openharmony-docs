# isIfaceActive（系统接口）

## 导入模块

```TypeScript
import { ethernet } from '@kit.NetworkKit';
```

## isIfaceActive

```TypeScript
function isIfaceActive(iface: string, callback: AsyncCallback<int>): void
```

判断接口是否已激活，使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.GET_NETWORK_INFO

<!--Device-ethernet-function isIfaceActive(iface: string, callback: AsyncCallback<int>): void--><!--Device-ethernet-function isIfaceActive(iface: string, callback: AsyncCallback<int>): void-End-->

**系统能力：** SystemCapability.Communication.NetManager.Ethernet

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| iface | string | 是 | 接口名。为空时代表查询是否存在激活接口。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;int&gt; | 是 | 回调函数。已激活：1，未激活：0，其他为获取失败错误码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2200001](../errorcode-net-ethernet.md#2200001-非法参数值) | Invalid parameter value. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2200003](../errorcode-net-ethernet.md#2200003-系统内部错误) | System internal error. |
| [2200002](../errorcode-net-ethernet.md#2200002-连接服务失败) | Failed to connect to the service. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [2201005](../errorcode-net-ethernet.md#2201005-设备信息不存在) | Device information does not exist. |

**示例**

```TypeScript
import { ethernet } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

ethernet.isIfaceActive("eth0", (error: BusinessError, value: number) => {
  if (error) {
    console.error("whether2Activate callback error = " + JSON.stringify(error));
  } else {
    console.info("whether2Activate callback = " + JSON.stringify(value));
  }
});
```


## isIfaceActive

```TypeScript
function isIfaceActive(iface: string): Promise<int>
```

判断接口是否已激活，使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.GET_NETWORK_INFO

<!--Device-ethernet-function isIfaceActive(iface: string): Promise<int>--><!--Device-ethernet-function isIfaceActive(iface: string): Promise<int>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Ethernet

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| iface | string | 是 | 接口名。为空时代表查询是否存在激活接口。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;int&gt; | 以Promise形式返回获取结果。已激活：1，未激活：0，其他为获取失败错误码。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [2200001](../errorcode-net-ethernet.md#2200001-非法参数值) | Invalid parameter value. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2200003](../errorcode-net-ethernet.md#2200003-系统内部错误) | System internal error. |
| [2200002](../errorcode-net-ethernet.md#2200002-连接服务失败) | Failed to connect to the service. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [2201005](../errorcode-net-ethernet.md#2201005-设备信息不存在) | Device information does not exist. |

**示例**

```TypeScript
import { ethernet } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

ethernet.isIfaceActive("eth0").then((data: number) => {
  console.info("isIfaceActive promise = " + JSON.stringify(data));
}).catch((error: BusinessError) => {
  console.error("isIfaceActive promise error = " + JSON.stringify(error));
});
```

