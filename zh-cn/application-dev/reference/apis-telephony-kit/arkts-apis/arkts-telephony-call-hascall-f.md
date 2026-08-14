# hasCall

## hasCall

```TypeScript
function hasCall(callback: AsyncCallback<boolean>): void
```

判断是否存在通话。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-call-function hasCall(callback: AsyncCallback<boolean>): void--><!--Device-call-function hasCall(callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;boolean&gt; | 是 | 回调函数。返回true表示当前存在通话，false表示当前不存在通话。 |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

call.hasCall((err: BusinessError, data: boolean) => {
    if (err) {
        console.error(`hasCall fail, err->${JSON.stringify(err)}`);
    } else {
        console.info(`hasCall success, data->${JSON.stringify(data)}`);
    }
});
```


## hasCall

```TypeScript
function hasCall(): Promise<boolean>
```

判断是否存在通话。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-call-function hasCall(): Promise<boolean>--><!--Device-call-function hasCall(): Promise<boolean>-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | 以Promise形式异步返回判断是否存在通话。返回true表示当前存在通话，false表示当前不存在通话。 |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

call.hasCall().then(() => {
    console.info(`hasCall success`);
}).catch((err: BusinessError) => {
    console.error(`hasCall fail, promise: err->${JSON.stringify(err)}`);
});
```

