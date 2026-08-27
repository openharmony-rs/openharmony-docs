# getDefaultSmsSlotId

## 导入模块

```TypeScript
```

## getDefaultSmsSlotId

```TypeScript
function getDefaultSmsSlotId(callback: AsyncCallback<number>): void
```

获取发送短信的默认SIM卡槽ID。使用callback异步回调。

**起始版本：** 7

**系统能力：** SystemCapability.Telephony.SmsMms

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 获取发送短信的默认SIM卡槽ID的回调函数。   - 0：卡槽1。   - 1：卡槽2。 |

**示例**

```TypeScript
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

sms.getDefaultSmsSlotId((err: BusinessError, data: number) => {
    if (err) {
        console.error('callback: err->${JSON.stringify(err)}');
        return;
    }
    console.info('callback: data->${JSON.stringify(data)}');
});
```


## getDefaultSmsSlotId

```TypeScript
function getDefaultSmsSlotId(): Promise<number>
```

获取发送短信的默认SIM卡槽ID。使用Promise异步回调。

**起始版本：** 7

**系统能力：** SystemCapability.Telephony.SmsMms

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;number & gt; | 以Promise形式返回发送短信的默认SIM卡： |

**示例**

```TypeScript
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

sms.getDefaultSmsSlotId().then((data: number) => {
    console.info(`getDefaultSmsSlotId success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getDefaultSmsSlotId failed, promise: errCode${err.code},errMsg:${err.message}`);
});
```
