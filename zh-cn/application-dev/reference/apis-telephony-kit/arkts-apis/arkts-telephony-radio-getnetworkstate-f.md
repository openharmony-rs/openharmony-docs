# getNetworkState

## 导入模块

```TypeScript
```

## getNetworkState

```TypeScript
function getNetworkState(slotId: number, callback: AsyncCallback<NetworkState>): void
```

获取网络状态。使用callback异步回调。

**起始版本：** 6

**需要权限：** ohos.permission.GET_NETWORK_INFO

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | 卡槽ID。   - 0：卡槽1。   - 1：卡槽2。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;NetworkState&gt; | 是 | 回调函数。返回当前网络状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let slotId: number = 0;
radio.getNetworkState(slotId, (err: BusinessError, data: radio.NetworkState) => {
    if (err) {
        console.error(`getNetworkState failed, callback: err->${JSON.stringify(err)}`);
        return;
    }
    console.info(`getNetworkState success, callback: data->${JSON.stringify(data)}`);
});
```


## getNetworkState

```TypeScript
function getNetworkState(slotId?: number): Promise<NetworkState>
```

获取网络状态。使用Promise异步回调。

**起始版本：** 6

**需要权限：** ohos.permission.GET_NETWORK_INFO

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 否 | 卡槽ID。   - 0：卡槽1。   - 1：卡槽2。    未指定卡槽时，默认为卡槽1。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;NetworkState & gt; | Promise对象，返回网络状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let slotId: number = 0;
radio.getNetworkState(slotId).then((data: radio.NetworkState) => {
    console.info(`getNetworkState success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getNetworkState failed, promise: err->${JSON.stringify(err)}`);
});
```


## getNetworkState

```TypeScript
function getNetworkState(callback: AsyncCallback<NetworkState>): void
```

获取网络状态。使用callback异步回调。

**起始版本：** 6

**需要权限：** ohos.permission.GET_NETWORK_INFO

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;NetworkState&gt; | 是 | 回调函数。返回当前网络状态。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

radio.getNetworkState((err: BusinessError, data: radio.NetworkState) => {
    if (err) {
        console.error(`getNetworkState failed, callback: err->${JSON.stringify(err)}`);
        return;
    }
    console.info(`getNetworkState success, callback: data->${JSON.stringify(data)}`);
});
```
