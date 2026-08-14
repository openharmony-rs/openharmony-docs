# makeCall

## makeCall

```TypeScript
function makeCall(phoneNumber: string, callback: AsyncCallback<void>): void
```

跳转到拨号界面，并显示待拨出的号码。使用callback异步回调。只支持在UIAbility中调用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-call-function makeCall(phoneNumber: string, callback: AsyncCallback<void>): void--><!--Device-call-function makeCall(phoneNumber: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Applications.Contacts

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| phoneNumber | string | 是 | 电话号码。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 以callback形式异步返回跳转拨号界面的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameters types; |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error code. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// 从API15开始支持tel格式电话号码，如："tel:13xxxx"
call.makeCall("138xxxxxxxx", (err: BusinessError) => {
    if (err) {
        console.error(`makeCall fail, err->${JSON.stringify(err)}`);
    } else {
        console.info(`makeCall success`);
    }
});
```


## makeCall

```TypeScript
function makeCall(phoneNumber: string): Promise<void>
```

跳转到拨号界面，并显示待拨出的号码。使用Promise异步回调。只支持在UIAbility中调用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-call-function makeCall(phoneNumber: string): Promise<void>--><!--Device-call-function makeCall(phoneNumber: string): Promise<void>-End-->

**系统能力：** SystemCapability.Applications.Contacts

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| phoneNumber | string | 是 | 电话号码。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 以Promise形式异步返回拨号的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameters types; |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error code. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// 从API15开始支持tel格式电话号码，如："tel:13xxxx"
call.makeCall("138xxxxxxxx").then(() => {
    console.info(`makeCall success`);
}).catch((err: BusinessError) => {
    console.error(`makeCall fail, promise: err->${JSON.stringify(err)}`);
});
```


## makeCall

```TypeScript
function makeCall(phoneNumber: string, options?: MakeCallOptions): Promise<void>
```

跳转到拨号界面，并显示待拨出的号码。使用Promise异步回调。只支持在UIAbility中调用。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**废弃版本：** -1

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-call-function makeCall(phoneNumber: string, options?: MakeCallOptions): Promise<void>--><!--Device-call-function makeCall(phoneNumber: string, options?: MakeCallOptions): Promise<void>-End-->

**系统能力：** SystemCapability.Applications.Contacts

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| phoneNumber | string | 是 | 电话号码。 |
| options | [MakeCallOptions](arkts-telephony-call-makecalloptions-i.md) | 否 | 通话参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error code. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |

## 示例

```TypeScript
import { call } from '@kit.TelephonyKit';

// 设置通话结束后是否返回当前App
let makeOptions: call.MakeCallOptions = {
  isHideDialScreen: true
}

call.makeCall("138xxxxxxxx", makeOptions).then(() => {
    console.info(`makeCall success`);
}).catch((err: BusinessError) => {
    console.error(`makeCall fail, promise: err->${JSON.stringify(err)}`);
});
```


## makeCall

```TypeScript
function makeCall(context: Context, phoneNumber: string): Promise<void>
```

跳转到拨号界面，并显示待拨出的号码。使用Promise异步回调。后台调用需要申请ohos.permission.START_ABILITIES_FROM_BACKGROUND权限。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-call-function makeCall(context: Context, phoneNumber: string): Promise<void>--><!--Device-call-function makeCall(context: Context, phoneNumber: string): Promise<void>-End-->

**系统能力：** SystemCapability.Applications.Contacts

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | Context | 是 | 应用上下文Context。 |
| phoneNumber | string | 是 | 电话号码。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 以Promise形式异步返回拨号的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameters types; |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |

## 示例

在本文档的示例中，通过this.context来获取UIAbilityContext，其中this代表继承自UIAbility的UIAbility实例。如需要在页面中使用UIAbilityContext提供的能力，请参见[获取UIAbility的上下文信息](../../../application-models/uiability-usage.md#获取uiability的上下文信息)。

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// 获取context
let context = this.getUIContext().getHostContext() as Context;
// 从API15开始支持tel格式电话号码，如："tel:13xxxx"
call.makeCall(context, "138xxxxxxxx").then(() => {
    console.info(`makeCall success`);
}).catch((err: BusinessError) => {
    console.error(`makeCall fail, promise: err->${JSON.stringify(err)}`);
});
```

