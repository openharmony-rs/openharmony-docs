# dialCall（系统接口）

## 导入模块

```TypeScript
```

## dialCall

```TypeScript
function dialCall(phoneNumber: string, options: DialCallOptions, callback: AsyncCallback<void>): void
```

拨打电话，可设置通话参数。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.PLACE_CALL

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| phoneNumber | string | 是 | 电话号码。 |
| options | [DialCallOptions](arkts-telephony-call-dialcalloptions-i-sys.md) | 是 | 通话参数，携带呼叫的其他配置信息。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 以callback形式异步返回拨打电话的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameters types; |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| 8300005 | Airplane mode is on. |
| 8300006 | Network not in service. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error code. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let dialCallOptions: call.DialCallOptions = {
    accountId: 0,
    videoState: 0,
    dialScene: 0,
    dialType: 0
}
call.dialCall("138xxxxxxxx", dialCallOptions, (err: BusinessError) => {
    if (err) {
        console.error(`dialCall fail, err->${JSON.stringify(err)}`);
    } else {
        console.info(`dialCall success.`);
    }
});
```


## dialCall

```TypeScript
function dialCall(phoneNumber: string, options?: DialCallOptions): Promise<void>
```

拨打电话，可设置通话参数。使用Promise异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.PLACE_CALL

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| phoneNumber | string | 是 | 电话号码。 |
| options | [DialCallOptions](arkts-telephony-call-dialcalloptions-i-sys.md) | 否 | 通话参数，携带呼叫的其他配置信息。不填该参数则默认使用如下配置，参考 [DialCallOptions](arkts-telephony-call-dialcalloptions-i-sys.md)。   - 帐户Id：卡槽1。    - 音视频类型：语音通话。    - 拨号场景：普通呼叫。    - 拨号类 型：运营商通话。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;void & gt; | 以Promise形式异步返回拨号结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameters types; |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| 8300005 | Airplane mode is on. |
| 8300006 | Network not in service. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error code. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let dialCallOptions: call.DialCallOptions = {
    accountId: 0,
    videoState: 0,
    dialScene: 0,
    dialType: 0
}
call.dialCall("138xxxxxxxx", dialCallOptions).then(() => {
    console.info(`dialCall success.`);
}).catch((err: BusinessError) => {
    console.error(`dialCall fail, promise: err->${JSON.stringify(err)}`);
});
```


## dialCall

```TypeScript
function dialCall(phoneNumber: string, callback: AsyncCallback<void>): void
```

拨打电话。使用callback异步回调。

**起始版本：** 9

**需要权限：** ohos.permission.PLACE_CALL

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| phoneNumber | string | 是 | 电话号码。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 以callback形式异步返回拨打电话的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameters types; |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| 8300005 | Airplane mode is on. |
| 8300006 | Network not in service. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error code. |

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

call.dialCall("138xxxxxxxx", (err: BusinessError) => {
    if (err) {
        console.error(`dialCall fail, err->${JSON.stringify(err)}`);
    } else {
        console.info(`dialCall success.`);
    }
});
```
