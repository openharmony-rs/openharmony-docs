# AuthResult（系统接口）

表示认证结果的信息。

**起始版本：** 8

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## accountId

```TypeScript
accountId?: number
```

指示系统账号标识，默认为undefined。

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## credentialId

```TypeScript
credentialId?: Uint8Array
```

指示凭据ID，默认为空。

**类型：** Uint8Array

**起始版本：** 12

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## freezingTime

```TypeScript
freezingTime?: number
```

指示冻结时间，单位为ms，默认为-1。

**类型：** number

**起始版本：** 8

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## nextPhaseFreezingTime

```TypeScript
nextPhaseFreezingTime?: number
```

指示下次冻结时间，单位为ms，默认为undefined。

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## pinValidityPeriod

```TypeScript
pinValidityPeriod?: number
```

指示认证有效期，单位为ms，默认为undefined。

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## remainTimes

```TypeScript
remainTimes?: number
```

指示剩余次数，默认为-1。

**类型：** number

**起始版本：** 8

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## token

```TypeScript
token?: Uint8Array
```

指示认证令牌，默认为空。

**类型：** Uint8Array

**起始版本：** 8

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

