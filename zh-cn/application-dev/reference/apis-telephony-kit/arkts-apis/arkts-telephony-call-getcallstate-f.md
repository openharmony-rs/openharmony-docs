# getCallState

## getCallState

```TypeScript
function getCallState(callback: AsyncCallback<CallState>): void
```

获取当前通话状态。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-call-function getCallState(callback: AsyncCallback<CallState>): void--><!--Device-call-function getCallState(callback: AsyncCallback<CallState>): void-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;CallState&gt; | 是 | 回调函数，异步返回获取到的通话状态。 |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

call.getCallState((err: BusinessError, data: call.CallState) => {
    if (err) {
        console.error(`getCallState fail, err->${JSON.stringify(err)}`);
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

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-call-function getCallState(): Promise<CallState>--><!--Device-call-function getCallState(): Promise<CallState>-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;CallState&gt; | 以Promise形式异步返回获取到的通话状态。 |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

call.getCallState().then((data: call.CallState) => {
    console.info(`getCallState success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getCallState fail, promise: err->${JSON.stringify(err)}`);
});
```

