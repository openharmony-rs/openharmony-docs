# canSetCallTransferTime（系统接口）

## canSetCallTransferTime

```TypeScript
function canSetCallTransferTime(slotId: int, callback: AsyncCallback<boolean>): void
```

检查是否可以设置呼叫转移时间。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.GET_TELEPHONY_STATE

<!--Device-call-function canSetCallTransferTime(slotId: int, callback: AsyncCallback<boolean>): void--><!--Device-call-function canSetCallTransferTime(slotId: int, callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | int | 是 | 卡槽ID。&lt;br/&gt;- 0：卡槽1。&lt;br/&gt;- 1：卡槽2。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;boolean&gt; | 是 | 回调函数。返回true表示可以设置，返回false表示不可以设置。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameters types; |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error code. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let slotId: number = 0;
call.canSetCallTransferTime(slotId, (err: BusinessError, data: boolean) => {
    if (err) {
        console.error(`canSetCallTransferTime fail, err->${JSON.stringify(err)}`);
    } else {
        console.info(`canSetCallTransferTime success, data->${JSON.stringify(data)}`);
    }
});
```


## canSetCallTransferTime

```TypeScript
function canSetCallTransferTime(slotId: int): Promise<boolean>
```

检查是否可以设置呼叫转移时间。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.GET_TELEPHONY_STATE

<!--Device-call-function canSetCallTransferTime(slotId: int): Promise<boolean>--><!--Device-call-function canSetCallTransferTime(slotId: int): Promise<boolean>-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | int | 是 | 卡槽ID。&lt;br/&gt;- 0：卡槽1。&lt;br/&gt;- 1：卡槽2。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | 以Promise形式异步返回是否可以设置呼叫转移时间。返回true表示可以设置，返回false表示不可以设置。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameters types; |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error code. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let slotId: number = 0;
call.canSetCallTransferTime(slotId).then((data: boolean) => {
    console.info(`canSetCallTransferTime success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`canSetCallTransferTime fail, promise: err->${JSON.stringify(err)}`);
});
```

