# SimAuthenticationResponse（系统接口）

Defines the SIM card authentication response.

**起始版本：** 14

<!--Device-sim-export interface SimAuthenticationResponse--><!--Device-sim-export interface SimAuthenticationResponse-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { sim } from '@kit.TelephonyKit';
```

## response

```TypeScript
response: string
```

Indicates the response of authentication.

**类型：** string

**起始版本：** 14

<!--Device-SimAuthenticationResponse-response: string--><!--Device-SimAuthenticationResponse-response: string-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

## simStatusWord1

```TypeScript
simStatusWord1: number
```

Status word 1 of the SIM card, which is returned by the SIM card after command execution.

**类型：** number

**起始版本：** 14

<!--Device-SimAuthenticationResponse-simStatusWord1: int--><!--Device-SimAuthenticationResponse-simStatusWord1: int-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

## simStatusWord2

```TypeScript
simStatusWord2: number
```

Status word 2 of the SIM card, which is returned by the SIM card after command execution.

**类型：** number

**起始版本：** 14

<!--Device-SimAuthenticationResponse-simStatusWord2: int--><!--Device-SimAuthenticationResponse-simStatusWord2: int-End-->

**系统能力：** SystemCapability.Telephony.CoreService

**系统接口：** 此接口为系统接口。

