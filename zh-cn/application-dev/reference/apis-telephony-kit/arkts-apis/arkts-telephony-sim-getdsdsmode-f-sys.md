# getDsdsMode（系统接口）

## 导入模块

```TypeScript
import { sim } from '@kit.TelephonyKit';
```

## getDsdsMode

```TypeScript
function getDsdsMode(callback: AsyncCallback<DsdsMode>): void
```

Obtains the value of dsds mode.

**起始版本：** 11

**需要权限：** ohos.permission.GET_TELEPHONY_STATE

<!--Device-sim-function getDsdsMode(callback: AsyncCallback<DsdsMode>): void--><!--Device-sim-function getDsdsMode(callback: AsyncCallback<DsdsMode>): void-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;DsdsMode&gt; | 是 | Indicates the callback for getting one of the following dsds mode states:<ul><li>{@code DsdsMode#DSDS_MODE_V2}<li>{@code DsdsMode#DSDS_MODE_V3}<li>{@code DsdsMode#DSDS_MODE_V5_TDM}<li>{@code DsdsMode#DSDS_MODE_V5_DSDA}</ul> |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.getDsdsMode((err: BusinessError, data: sim.DsdsMode) => {
    if (err) {
        console.error(`getDsdsMode failed, callback: err->${JSON.stringify(err)}`);
    } else {
        console.info(`getDsdsMode success, callback: data->${JSON.stringify(data)}`);
    }
});

```


## getDsdsMode

```TypeScript
function getDsdsMode(): Promise<DsdsMode>
```

Obtains the value of dsds mode.

**起始版本：** 11

**需要权限：** ohos.permission.GET_TELEPHONY_STATE

<!--Device-sim-function getDsdsMode(): Promise<DsdsMode>--><!--Device-sim-function getDsdsMode(): Promise<DsdsMode>-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;DsdsMode&gt; | Returns one of the following dsds mode states:<ul><li>{@code DsdsMode#DSDS_MODE_V2}<li>{@code DsdsMode#DSDS_MODE_V3}<li>{@code DsdsMode#DSDS_MODE_V5_TDM}<li>{@code DsdsMode#DSDS_MODE_V5_DSDA}</ul> |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Operation failed. Cannot connect to service. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

let promise = sim.getDsdsMode();
promise.then((data: sim.DsdsMode) => {
    console.info(`getDsdsMode success, promise: data->${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
    console.error(`getDsdsMode failed, promise: err->${JSON.stringify(err)}`);
});

```

