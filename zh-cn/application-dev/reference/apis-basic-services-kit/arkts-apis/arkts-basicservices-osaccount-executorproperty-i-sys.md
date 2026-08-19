# ExecutorProperty（系统接口）

提供执行器的属性。

**起始版本：** 23

<!--Device-osAccount-interface ExecutorProperty--><!--Device-osAccount-interface ExecutorProperty-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

## authSubType

```TypeScript
authSubType: AuthSubType
```

指示认证凭据子类型。

**类型：** [AuthSubType](arkts-basicservices-osaccount-authsubtype-e-sys.md)

**起始版本：** 23

<!--Device-ExecutorProperty-authSubType: AuthSubType--><!--Device-ExecutorProperty-authSubType: AuthSubType-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## credentialLength

```TypeScript
credentialLength?: int
```

指示凭据长度，默认为undefined。查询生物信息等无定长属性的凭据时返回undefined。

**类型：** int

**起始版本：** 23

<!--Device-ExecutorProperty-credentialLength?: int--><!--Device-ExecutorProperty-credentialLength?: int-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## enrollmentProgress

```TypeScript
enrollmentProgress?: string
```

指示录入进度，默认为空。

**类型：** string

**起始版本：** 23

<!--Device-ExecutorProperty-enrollmentProgress?: string--><!--Device-ExecutorProperty-enrollmentProgress?: string-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## freezingTime

```TypeScript
freezingTime?: int
```

指示冻结时间，单位为ms，默认为-1。

**类型：** int

**起始版本：** 23

<!--Device-ExecutorProperty-freezingTime?: int--><!--Device-ExecutorProperty-freezingTime?: int-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## nextPhaseFreezingTime

```TypeScript
nextPhaseFreezingTime?: int
```

指示下次冻结时间，单位为ms，默认为undefined。

**类型：** int

**起始版本：** 23

<!--Device-ExecutorProperty-nextPhaseFreezingTime?: int--><!--Device-ExecutorProperty-nextPhaseFreezingTime?: int-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## remainTimes

```TypeScript
remainTimes?: int
```

指示剩余次数，默认为-1。

**类型：** int

**起始版本：** 23

<!--Device-ExecutorProperty-remainTimes?: int--><!--Device-ExecutorProperty-remainTimes?: int-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## result

```TypeScript
result: int
```

指示结果。

**类型：** int

**起始版本：** 23

<!--Device-ExecutorProperty-result: int--><!--Device-ExecutorProperty-result: int-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## sensorInfo

```TypeScript
sensorInfo?: string
```

指示传感器信息，默认为空。

**类型：** string

**起始版本：** 23

<!--Device-ExecutorProperty-sensorInfo?: string--><!--Device-ExecutorProperty-sensorInfo?: string-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

