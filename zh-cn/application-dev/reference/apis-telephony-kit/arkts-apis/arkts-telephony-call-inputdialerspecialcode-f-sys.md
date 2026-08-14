# inputDialerSpecialCode（系统接口）

## inputDialerSpecialCode

```TypeScript
function inputDialerSpecialCode(inputCode: string, callback: AsyncCallback<void>): void
```

暗码广播。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.PLACE_CALL

<!--Device-call-function inputDialerSpecialCode(inputCode: string, callback: AsyncCallback<void>): void--><!--Device-call-function inputDialerSpecialCode(inputCode: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| inputCode | string | 是 | 暗码。支持暗码字段, 如：*#*#2846579#*#*(工程菜单)。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 以回调函数的方式返回暗码广播的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameters types; |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

call.inputDialerSpecialCode('*#*#2846579#*#*', (err: BusinessError) => {
    if (err) {
        console.error(`inputDialerSpecialCode fail, err->${JSON.stringify(err)}`);
    } else {
        console.info(`inputDialerSpecialCode success`);
    }
});
```


## inputDialerSpecialCode

```TypeScript
function inputDialerSpecialCode(inputCode: string): Promise<void>
```

暗码广播。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.PLACE_CALL

<!--Device-call-function inputDialerSpecialCode(inputCode: string): Promise<void>--><!--Device-call-function inputDialerSpecialCode(inputCode: string): Promise<void>-End-->

**系统能力：** SystemCapability.Telephony.CallManager

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| inputCode | string | 是 | 暗码。支持暗码字段, 如：*#*#2846579#*#*(工程菜单)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 以Promise形式异步返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2. Incorrect parameters types; |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    call.inputDialerSpecialCode('*#*#2846579#*#*');
    console.info(`inputDialerSpecialCode success`);
} catch (error) {
    console.error(`inputDialerSpecialCode fail, promise: err->${JSON.stringify(error)}`);
}
```

