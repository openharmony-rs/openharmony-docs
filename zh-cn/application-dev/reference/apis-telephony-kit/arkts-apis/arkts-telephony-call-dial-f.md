# dial

## 导入模块

```TypeScript
```

## dial

```TypeScript
function dial(phoneNumber: string, options: DialOptions, callback: AsyncCallback<boolean>): void
```

拨打电话，可设置通话参数。使用callback异步回调。

> **说明：**
> 
> 从API version 6 开始支持，从API version 9 开始废弃。替代接口能力仅对系统应用开放。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [dialCall](arkts-telephony-call-dialcall-f-sys.md)

**需要权限：** ohos.permission.PLACE_CALL

**系统能力：** SystemCapability.Telephony.CallManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| phoneNumber | string | 是 | 电话号码。 |
| options | [DialOptions](arkts-telephony-call-dialoptions-i.md) | 是 | 通话参数，选择为语音通话还是视频通话。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数，返回true为成功，false为失败。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let dialOptions: call.DialOptions = {
    extras: false
};
call.dial("138xxxxxxxx", dialOptions, (err: BusinessError, data: boolean) => {
    console.info(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});
```


## dial

```TypeScript
function dial(phoneNumber: string, options?: DialOptions): Promise<boolean>
```

拨打电话，可设置通话参数。使用Promise异步回调。

> **说明：**
> 
> 从API version 6 开始支持，从API version 9 开始废弃。替代接口能力仅对系统应用开放。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [dialCall](arkts-telephony-call-dialcall-f-sys.md)

**需要权限：** ohos.permission.PLACE_CALL

**系统能力：** SystemCapability.Telephony.CallManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| phoneNumber | string | 是 | 电话号码。 |
| options | [DialOptions](arkts-telephony-call-dialoptions-i.md) | 否 | 通话参数，选择为语音通话还是视频通话。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;boolean & gt; | 以Promise形式返回拨打电话的结果，返回true为成功，false为失败。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let dialOptions: call.DialOptions = {
    extras: false
};
call.dial("138xxxxxxxx", dialOptions).then((data: boolean) => {
    console.info(`dial success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`dial fail, promise: err->Code${err.code}, message:${err.message}`);
});
```


## dial

```TypeScript
function dial(phoneNumber: string, callback: AsyncCallback<boolean>): void
```

拨打电话。使用callback异步回调。

> **说明：**
> 
> 从API version 6 开始支持，从API version 9 开始废弃。替代接口能力仅对系统应用开放。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [dialCall](arkts-telephony-call-dialcall-f-sys.md)

**需要权限：** ohos.permission.PLACE_CALL

**系统能力：** SystemCapability.Telephony.CallManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| phoneNumber | string | 是 | 电话号码。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数，返回true为成功，false为失败。 |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

call.dial("138xxxxxxxx", (err: BusinessError, data: boolean) => {
    console.info(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});
```
