# getDefaultSmsSlotId

## getDefaultSmsSlotId

```TypeScript
function getDefaultSmsSlotId(callback: AsyncCallback<int>): void
```

获取发送短信的默认SIM卡槽ID。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-sms-function getDefaultSmsSlotId(callback: AsyncCallback<int>): void--><!--Device-sms-function getDefaultSmsSlotId(callback: AsyncCallback<int>): void-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;int&gt; | 是 | 获取发送短信的默认SIM卡槽ID的回调函数。&lt;br/&gt;- 0：卡槽1。&lt;br/&gt;- 1：卡槽2。 |

## 示例

```TypeScript
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

sms.getDefaultSmsSlotId((err: BusinessError, data: number) => {
    console.info(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});
```


## getDefaultSmsSlotId

```TypeScript
function getDefaultSmsSlotId(): Promise<int>
```

获取发送短信的默认SIM卡槽ID。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-sms-function getDefaultSmsSlotId(): Promise<int>--><!--Device-sms-function getDefaultSmsSlotId(): Promise<int>-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;int&gt; | 以Promise形式返回发送短信的默认SIM卡：&lt;br/&gt;- 0：卡槽1。&lt;br/&gt;- 1：卡槽2。 |

## 示例

```TypeScript
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

sms.getDefaultSmsSlotId().then((data: number) => {
    console.info(`getDefaultSmsSlotId success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getDefaultSmsSlotId failed, promise: err->${JSON.stringify(err)}`);
});
```

