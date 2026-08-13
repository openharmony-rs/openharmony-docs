# getActiveSimAccountInfoList

## getActiveSimAccountInfoList

```TypeScript
function getActiveSimAccountInfoList(callback: AsyncCallback<Array<IccAccountInfo>>): void
```

Get the list of active SIM card account information.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.GET_TELEPHONY_STATE

<!--Device-sim-function getActiveSimAccountInfoList(callback: AsyncCallback<Array<IccAccountInfo>>): void--><!--Device-sim-function getActiveSimAccountInfoList(callback: AsyncCallback<Array<IccAccountInfo>>): void-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Array&lt;[IccAccountInfo](arkts-telephony-sim-iccaccountinfo-i.md)&gt;&gt; | 是 | The callback is used to return the array of [IccAccountInfo](arkts-telephony-sim-iccaccountinfo-i.md#IccAccountInfo). The ICCID and phone number will be null if has no ohos.permission.GET_TELEPHONY_STATE. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error. |
| [8300004](../errorcode-telephony.md#8300004-未识别sim卡) | No SIM card found. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.getActiveSimAccountInfoList((err: BusinessError, data: Array<sim.IccAccountInfo>) => {
    console.info(`callback: err->${JSON.stringify(err)}, data->${JSON.stringify(data)}`);
});
```


## getActiveSimAccountInfoList

```TypeScript
function getActiveSimAccountInfoList(): Promise<Array<IccAccountInfo>>
```

Get the list of active SIM card account information.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.GET_TELEPHONY_STATE

<!--Device-sim-function getActiveSimAccountInfoList(): Promise<Array<IccAccountInfo>>--><!--Device-sim-function getActiveSimAccountInfoList(): Promise<Array<IccAccountInfo>>-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[IccAccountInfo](arkts-telephony-sim-iccaccountinfo-i.md)&gt;&gt; | Returns the array of { |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error. |
| [8300004](../errorcode-telephony.md#8300004-未识别sim卡) | No SIM card found. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.getActiveSimAccountInfoList().then((data: Array<sim.IccAccountInfo>) => {
    console.info(`getActiveSimAccountInfoList success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getActiveSimAccountInfoList failed, promise: err->${JSON.stringify(err)}`);
});
```

