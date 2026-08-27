# getDefaultVoiceSlotId

## 导入模块

```TypeScript
```

## getDefaultVoiceSlotId

```TypeScript
function getDefaultVoiceSlotId(callback: AsyncCallback<number>): void
```

获取默认语音业务的卡槽ID。使用callback异步回调。

**起始版本：** 7

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数。   - 0：卡槽1。   - 1：卡槽2。   - -1：未设置或服务不可用。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.getDefaultVoiceSlotId((err: BusinessError, data: number) => {
    console.info(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});
```


## getDefaultVoiceSlotId

```TypeScript
function getDefaultVoiceSlotId(): Promise<number>
```

获取默认语音业务的卡槽ID。使用Promise异步回调。

**起始版本：** 7

**系统能力：** SystemCapability.Telephony.CoreService

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;number & gt; | 以Promise形式返回默认语音业务的卡槽ID。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.getDefaultVoiceSlotId().then((data: number) => {
    console.info(`getDefaultVoiceSlotId success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getDefaultVoiceSlotId failed, promise: err->${JSON.stringify(err)}`);
});
```
