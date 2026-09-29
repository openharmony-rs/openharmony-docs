# ExecutorProperty (System API)

```TypeScript
interface ExecutorProperty
```

Defines the executor property.

**Since:** 8

<!--Device-osAccount-interface ExecutorProperty--><!--Device-osAccount-interface ExecutorProperty-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

## authSubType

```TypeScript
authSubType: AuthSubType
```

Authentication credential subtype.

**Type:** [AuthSubType](arkts-basicservices-osaccount-authsubtype-e-sys.md)

**Since:** 8

<!--Device-ExecutorProperty-authSubType: AuthSubType--><!--Device-ExecutorProperty-authSubType: AuthSubType-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## credentialLength

```TypeScript
credentialLength?: number
```

Credential length, which is **undefined** by default. When credentials with indefinite-length attributes such as biometric information are queried, **undefined** is returned.

**Type:** number

**Since:** 20

<!--Device-ExecutorProperty-credentialLength?: int--><!--Device-ExecutorProperty-credentialLength?: int-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## enrollmentProgress

```TypeScript
enrollmentProgress?: string
```

Enrollment progress, which is left blank by default.

**Type:** string

**Since:** 10

<!--Device-ExecutorProperty-enrollmentProgress?: string--><!--Device-ExecutorProperty-enrollmentProgress?: string-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## freezingTime

```TypeScript
freezingTime?: number
```

Freezing time, in milliseconds. The default value is **-1**.

**Type:** number

**Since:** 8

<!--Device-ExecutorProperty-freezingTime?: int--><!--Device-ExecutorProperty-freezingTime?: int-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## nextPhaseFreezingTime

```TypeScript
nextPhaseFreezingTime?: number
```

Next freezing time, in milliseconds. The default value is **undefined**.

**Type:** number

**Since:** 12

<!--Device-ExecutorProperty-nextPhaseFreezingTime?: int--><!--Device-ExecutorProperty-nextPhaseFreezingTime?: int-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## remainTimes

```TypeScript
remainTimes?: number
```

Number of remaining authentication times, which is **-1** by default.

**Type:** number

**Since:** 8

<!--Device-ExecutorProperty-remainTimes?: int--><!--Device-ExecutorProperty-remainTimes?: int-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## result

```TypeScript
result: number
```

Result.

**Type:** number

**Since:** 8

<!--Device-ExecutorProperty-result: int--><!--Device-ExecutorProperty-result: int-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.

## sensorInfo

```TypeScript
sensorInfo?: string
```

Sensor information, which is left blank by default.

**Type:** string

**Since:** 10

<!--Device-ExecutorProperty-sensorInfo?: string--><!--Device-ExecutorProperty-sensorInfo?: string-End-->

**System capability:** SystemCapability.Account.OsAccount

**System API:** This is a system API.
