# AuthResult（系统接口）

表示认证结果的信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-osAccount-interface AuthResult--><!--Device-osAccount-interface AuthResult-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## accountId

```TypeScript
accountId?: int
```

指示系统账号标识，默认为undefined。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AuthResult-accountId?: int--><!--Device-AuthResult-accountId?: int-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## credentialId

```TypeScript
credentialId?: Uint8Array
```

指示凭据ID，默认为空。

**类型：** Uint8Array

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AuthResult-credentialId?: Uint8Array--><!--Device-AuthResult-credentialId?: Uint8Array-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## freezingTime

```TypeScript
freezingTime?: int
```

指示冻结时间，单位为ms，默认为-1。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AuthResult-freezingTime?: int--><!--Device-AuthResult-freezingTime?: int-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## nextPhaseFreezingTime

```TypeScript
nextPhaseFreezingTime?: int
```

指示下次冻结时间，单位为ms，默认为undefined。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AuthResult-nextPhaseFreezingTime?: int--><!--Device-AuthResult-nextPhaseFreezingTime?: int-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## pinValidityPeriod

```TypeScript
pinValidityPeriod?: long
```

指示认证有效期，单位为ms，默认为undefined。

**类型：** long

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AuthResult-pinValidityPeriod?: long--><!--Device-AuthResult-pinValidityPeriod?: long-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## remainTimes

```TypeScript
remainTimes?: int
```

指示剩余次数，默认为-1。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AuthResult-remainTimes?: int--><!--Device-AuthResult-remainTimes?: int-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## token

```TypeScript
token?: Uint8Array
```

指示认证令牌，默认为空。

**类型：** Uint8Array

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-AuthResult-token?: Uint8Array--><!--Device-AuthResult-token?: Uint8Array-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

