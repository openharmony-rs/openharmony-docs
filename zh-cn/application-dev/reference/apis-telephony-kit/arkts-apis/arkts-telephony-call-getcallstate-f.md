# getCallState

## 导入模块

```TypeScript
```

## getCallState

```TypeScript
function getCallState(callback: AsyncCallback<CallState>): void
```

获取当前通话状态。使用callback异步回调。

**起始版本：** 6

**系统能力：** SystemCapability.Telephony.CallManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;CallState&gt; | 是 | 回调函数，异步返回获取到的通话状态。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

call.getCallState((err: BusinessError, data: call.CallState) => {
    if (err) {
        console.error(`getCallState fail, err->Code${err.code}, message:${err.message}`);
    } else {
        console.info(`getCallState success, data->${JSON.stringify(data)}`);
    }
});
```


## getCallState

```TypeScript
function getCallState(): Promise<CallState>
```

获取当前通话状态。使用Promise异步回调。

**起始版本：** 6

**系统能力：** SystemCapability.Telephony.CallManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;CallState & gt; | 以Promise形式异步返回获取到的通话状态。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

call.getCallState().then((data: call.CallState) => {
    console.info(`getCallState success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getCallState fail, promise: err->Code${err.code}, message:${err.message}`);
});
```
