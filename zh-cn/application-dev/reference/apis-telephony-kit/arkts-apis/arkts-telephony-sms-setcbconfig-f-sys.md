# setCBConfig（系统接口）

## setCBConfig

```TypeScript
function setCBConfig(options: CBConfigOptions, callback: AsyncCallback<void>): void
```

设置小区广播配置。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.RECEIVE_SMS

<!--Device-sms-function setCBConfig(options: CBConfigOptions, callback: AsyncCallback<void>): void--><!--Device-sms-function setCBConfig(options: CBConfigOptions, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [CBConfigOptions](arkts-telephony-sms-cbconfigoptions-i-sys.md) | 是 | 小区广播配置选项。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 设置小区广播配置的回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error code. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |

## 示例

```TypeScript
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

let cbConfigOptions: sms.CBConfigOptions = {
    slotId: 0,
    enable: true,
    startMessageId: 100,
    endMessageId: 200,
    ranType: sms.RanType.TYPE_GSM
};
sms.setCBConfig(cbConfigOptions, (err: BusinessError) => {
      console.info(`callback: err->${JSON.stringify(err)}`);
});
```


## setCBConfig

```TypeScript
function setCBConfig(options: CBConfigOptions): Promise<void>
```

设置小区广播配置。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.RECEIVE_SMS

<!--Device-sms-function setCBConfig(options: CBConfigOptions): Promise<void>--><!--Device-sms-function setCBConfig(options: CBConfigOptions): Promise<void>-End-->

**系统能力：** SystemCapability.Telephony.SmsMms

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [CBConfigOptions](arkts-telephony-sms-cbconfigoptions-i-sys.md) | 是 | 小区广播配置选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 以Promise形式返回设置的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error code. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |

## 示例

```TypeScript
import { sms } from '@kit.TelephonyKit';
import { BusinessError } from '@kit.BasicServicesKit';

let cbConfigOptions: sms.CBConfigOptions = {
    slotId: 0,
    enable: true,
    startMessageId: 100,
    endMessageId: 200,
    ranType: sms.RanType.TYPE_GSM
};
let promise = sms.setCBConfig(cbConfigOptions);
promise.then(() => {
    console.info(`setCBConfig success.`);
}).catch((err: BusinessError) => {
    console.error(`setCBConfig failed, promise: err->${JSON.stringify(err)}`);
});
```

