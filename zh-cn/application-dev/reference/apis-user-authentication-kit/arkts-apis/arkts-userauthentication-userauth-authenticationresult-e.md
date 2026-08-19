# AuthenticationResult

表示认证结果的枚举。

**起始版本：** 6

**废弃版本：** 8

**替代接口：** [UserAuthResultCode](arkts-userauthentication-userauth-userauthresultcode-e.md)

<!--Device-userAuth-export enum AuthenticationResult--><!--Device-userAuth-export enum AuthenticationResult-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## NO_SUPPORT

```TypeScript
NO_SUPPORT = -1
```

设备不支持当前的认证方式。

**起始版本：** 6

**废弃版本：** 8

**替代接口：** [TYPE_NOT_SUPPORT](arkts-userauthentication-userauth-resultcode-e.md#type_not_support)

<!--Device-AuthenticationResult-NO_SUPPORT = -1--><!--Device-AuthenticationResult-NO_SUPPORT = -1-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## SUCCESS

```TypeScript
SUCCESS = 0
```

认证成功。

**起始版本：** 6

**废弃版本：** 8

**替代接口：** [SUCCESS](arkts-userauthentication-userauth-resultcode-e.md#success)

<!--Device-AuthenticationResult-SUCCESS = 0--><!--Device-AuthenticationResult-SUCCESS = 0-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## COMPARE_FAILURE

```TypeScript
COMPARE_FAILURE = 1
```

比对失败。

**起始版本：** 6

**废弃版本：** 8

**替代接口：** [FAIL](arkts-userauthentication-userauth-resultcode-e.md#fail)

<!--Device-AuthenticationResult-COMPARE_FAILURE = 1--><!--Device-AuthenticationResult-COMPARE_FAILURE = 1-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## CANCELED

```TypeScript
CANCELED = 2
```

用户取消认证。

**起始版本：** 6

**废弃版本：** 8

**替代接口：** [CANCELED](arkts-userauthentication-userauth-resultcode-e.md#canceled)

<!--Device-AuthenticationResult-CANCELED = 2--><!--Device-AuthenticationResult-CANCELED = 2-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## TIMEOUT

```TypeScript
TIMEOUT = 3
```

认证超时。

**起始版本：** 6

**废弃版本：** 8

**替代接口：** [TIMEOUT](arkts-userauthentication-userauth-resultcode-e.md#timeout)

<!--Device-AuthenticationResult-TIMEOUT = 3--><!--Device-AuthenticationResult-TIMEOUT = 3-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## CAMERA_FAIL

```TypeScript
CAMERA_FAIL = 4
```

开启相机失败。

**起始版本：** 6

**废弃版本：** 8

<!--Device-AuthenticationResult-CAMERA_FAIL = 4--><!--Device-AuthenticationResult-CAMERA_FAIL = 4-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## BUSY

```TypeScript
BUSY = 5
```

认证服务忙，请稍后重试。

**起始版本：** 6

**废弃版本：** 8

**替代接口：** [BUSY](arkts-userauthentication-userauth-resultcode-e.md#busy)

<!--Device-AuthenticationResult-BUSY = 5--><!--Device-AuthenticationResult-BUSY = 5-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## INVALID_PARAMETERS

```TypeScript
INVALID_PARAMETERS = 6
```

认证参数无效。

**起始版本：** 6

**废弃版本：** 8

**替代接口：** [INVALID_PARAMETERS](arkts-userauthentication-userauth-resultcode-e.md#invalid_parameters)

<!--Device-AuthenticationResult-INVALID_PARAMETERS = 6--><!--Device-AuthenticationResult-INVALID_PARAMETERS = 6-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## LOCKED

```TypeScript
LOCKED = 7
```

认证失败次数过多，已锁定。

**起始版本：** 6

**废弃版本：** 8

**替代接口：** [LOCKED](arkts-userauthentication-userauth-resultcode-e.md#locked)

<!--Device-AuthenticationResult-LOCKED = 7--><!--Device-AuthenticationResult-LOCKED = 7-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## NOT_ENROLLED

```TypeScript
NOT_ENROLLED = 8
```

未录入认证凭据。

**起始版本：** 6

**废弃版本：** 8

**替代接口：** [NOT_ENROLLED](arkts-userauthentication-userauth-resultcode-e.md#not_enrolled)

<!--Device-AuthenticationResult-NOT_ENROLLED = 8--><!--Device-AuthenticationResult-NOT_ENROLLED = 8-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## GENERAL_ERROR

```TypeScript
GENERAL_ERROR = 100
```

其他错误。

**起始版本：** 6

**废弃版本：** 8

**替代接口：** [GENERAL_ERROR](arkts-userauthentication-userauth-resultcode-e.md#general_error)

<!--Device-AuthenticationResult-GENERAL_ERROR = 100--><!--Device-AuthenticationResult-GENERAL_ERROR = 100-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

