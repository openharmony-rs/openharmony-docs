# ResultCode（系统接口）

表示身份验证结果码。

**起始版本：** 8

<!--Device-osAccount-enum ResultCode--><!--Device-osAccount-enum ResultCode-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## SUCCESS

```TypeScript
SUCCESS = 0
```

表示身份验证成功或支持此功能。

**起始版本：** 8

<!--Device-ResultCode-SUCCESS = 0--><!--Device-ResultCode-SUCCESS = 0-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## FAIL

```TypeScript
FAIL = 1
```

表示验证器无法识别用户。

**起始版本：** 8

<!--Device-ResultCode-FAIL = 1--><!--Device-ResultCode-FAIL = 1-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## GENERAL_ERROR

```TypeScript
GENERAL_ERROR = 2
```

表示其他错误。

**起始版本：** 8

<!--Device-ResultCode-GENERAL_ERROR = 2--><!--Device-ResultCode-GENERAL_ERROR = 2-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## CANCELED

```TypeScript
CANCELED = 3
```

表示身份验证已取消。

**起始版本：** 8

<!--Device-ResultCode-CANCELED = 3--><!--Device-ResultCode-CANCELED = 3-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## TIMEOUT

```TypeScript
TIMEOUT = 4
```

表示身份验证已超时。

**起始版本：** 8

<!--Device-ResultCode-TIMEOUT = 4--><!--Device-ResultCode-TIMEOUT = 4-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## TYPE_NOT_SUPPORT

```TypeScript
TYPE_NOT_SUPPORT = 5
```

表示不支持此身份验证类型。

**起始版本：** 8

<!--Device-ResultCode-TYPE_NOT_SUPPORT = 5--><!--Device-ResultCode-TYPE_NOT_SUPPORT = 5-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## TRUST_LEVEL_NOT_SUPPORT

```TypeScript
TRUST_LEVEL_NOT_SUPPORT = 6
```

表示不支持身份验证信任级别。

**起始版本：** 8

<!--Device-ResultCode-TRUST_LEVEL_NOT_SUPPORT = 6--><!--Device-ResultCode-TRUST_LEVEL_NOT_SUPPORT = 6-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## BUSY

```TypeScript
BUSY = 7
```

表示身份验证任务正忙。等待几秒钟，然后重试。

**起始版本：** 8

<!--Device-ResultCode-BUSY = 7--><!--Device-ResultCode-BUSY = 7-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## INVALID_PARAMETERS

```TypeScript
INVALID_PARAMETERS = 8
```

表示参数不正确。

**起始版本：** 8

<!--Device-ResultCode-INVALID_PARAMETERS = 8--><!--Device-ResultCode-INVALID_PARAMETERS = 8-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## LOCKED

```TypeScript
LOCKED = 9
```

指示身份验证器已锁定。

**起始版本：** 8

<!--Device-ResultCode-LOCKED = 9--><!--Device-ResultCode-LOCKED = 9-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## NOT_ENROLLED

```TypeScript
NOT_ENROLLED = 10
```

表示用户尚未注册验证器。

**起始版本：** 8

<!--Device-ResultCode-NOT_ENROLLED = 10--><!--Device-ResultCode-NOT_ENROLLED = 10-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

