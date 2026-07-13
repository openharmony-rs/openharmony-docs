# AuthenticationResult

表示认证结果的枚举。

**起始版本：** 6

**废弃版本：** 8

**替代接口：** [UserAuthResultCode](arkts-userauthentication-userauthresultcode-e.md)

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## NO_SUPPORT

```TypeScript
NO_SUPPORT = -1
```

设备不支持当前的认证方式。

**起始版本：** 6

**废弃版本：** 8

**替代接口：** [TYPE_NOT_SUPPORT](arkts-userauthentication-resultcode-e.md#type_not_support)

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## SUCCESS

```TypeScript
SUCCESS = 0
```

认证成功。

**起始版本：** 6

**废弃版本：** 8

**替代接口：** [SUCCESS](arkts-userauthentication-resultcode-e.md#success)

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## COMPARE_FAILURE

```TypeScript
COMPARE_FAILURE = 1
```

比对失败。

**起始版本：** 6

**废弃版本：** 8

**替代接口：** [FAIL](arkts-userauthentication-resultcode-e.md#fail)

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## CANCELED

```TypeScript
CANCELED = 2
```

用户取消认证。

**起始版本：** 6

**废弃版本：** 8

**替代接口：** [CANCELED](arkts-userauthentication-resultcode-e.md#canceled)

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## TIMEOUT

```TypeScript
TIMEOUT = 3
```

认证超时。

**起始版本：** 6

**废弃版本：** 8

**替代接口：** [TIMEOUT](arkts-userauthentication-resultcode-e.md#timeout)

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## CAMERA_FAIL

```TypeScript
CAMERA_FAIL = 4
```

开启相机失败。

**起始版本：** 6

**废弃版本：** 8

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## BUSY

```TypeScript
BUSY = 5
```

认证服务忙，请稍后重试。

**起始版本：** 6

**废弃版本：** 8

**替代接口：** [BUSY](arkts-userauthentication-resultcode-e.md#busy)

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## INVALID_PARAMETERS

```TypeScript
INVALID_PARAMETERS = 6
```

认证参数无效。

**起始版本：** 6

**废弃版本：** 8

**替代接口：** [INVALID_PARAMETERS](arkts-userauthentication-resultcode-e.md#invalid_parameters)

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## LOCKED

```TypeScript
LOCKED = 7
```

认证失败次数过多，已锁定。

**起始版本：** 6

**废弃版本：** 8

**替代接口：** [LOCKED](arkts-userauthentication-resultcode-e.md#locked)

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## NOT_ENROLLED

```TypeScript
NOT_ENROLLED = 8
```

未录入认证凭据。

**起始版本：** 6

**废弃版本：** 8

**替代接口：** [NOT_ENROLLED](arkts-userauthentication-resultcode-e.md#not_enrolled)

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## GENERAL_ERROR

```TypeScript
GENERAL_ERROR = 100
```

其他错误。

**起始版本：** 6

**废弃版本：** 8

**替代接口：** [GENERAL_ERROR](arkts-userauthentication-resultcode-e.md#general_error)

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

