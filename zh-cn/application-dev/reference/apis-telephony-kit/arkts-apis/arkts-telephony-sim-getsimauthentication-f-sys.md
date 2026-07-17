# getSimAuthentication（系统接口）

## 导入模块

```TypeScript
import { sim } from '@kit.TelephonyKit';
```

## getSimAuthentication

```TypeScript
function getSimAuthentication(slotId: number, authType: AuthType, authData: string): Promise<SimAuthenticationResponse>
```

Performs SIM card authentication.

**起始版本：** 14

**需要权限：** ohos.permission.GET_TELEPHONY_STATE

<!--Device-sim-function getSimAuthentication(slotId: int, authType: AuthType, authData: string): Promise<SimAuthenticationResponse>--><!--Device-sim-function getSimAuthentication(slotId: int, authType: AuthType, authData: string): Promise<SimAuthenticationResponse>-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| slotId | number | 是 | Sim slot id. |
| authType | [AuthType](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-osaccount-authtype-e-sys.md) | 是 | The authentication type. |
| authData | string | 是 | Ser password or other authentication information. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<SimAuthenticationResponse> | A string the response of authentication.This value will be null in the following cases: Authentication error, incorrect MAC Authentication error, security context not supported Key freshness failure Authentication error, no memory space available Authentication error, no memory space available in EFMUK. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Non-system applications use system APIs. |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified.2. Incorrect parameter types. |
| [8300001](../errorcode-telephony.md#8300001-输入参数不在处理范围内) | Invalid parameter value. |
| [8300002](../errorcode-telephony.md#8300002-服务连接失败) | Service connection failed. |
| [8300003](../errorcode-telephony.md#8300003-系统内部错误) | System internal error. |
| [8300004](../errorcode-telephony.md#8300004-未识别sim卡) | No SIM card. |
| [8300999](../errorcode-telephony.md#8300999-内部错误) | Unknown error. |
| [8301002](../errorcode-telephony.md#8301002-sim卡读取数据或者更新数据失败) | An error occurred when operating the SIM card. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sim } from '@kit.TelephonyKit';

sim.getSimAuthentication(0, sim.AuthType.SIM_AUTH_EAP_SIM_TYPE, "test").then(() => {
    console.info(`getSimAuthentication success.`);
}).catch((err: BusinessError) => {
    console.error(`getSimAuthentication failed, promise: err->${JSON.stringify(err)}`);
});

```

