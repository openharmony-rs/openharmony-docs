# HuksExceptionErrCode

表示错误码的枚举以及对应的错误信息，错误码表示错误类型，错误信息展示错误详情。

关于错误码的具体信息，可在[通用错误码](../../../reference/errorcode-universal.md)和[HUKS错误码](../../../reference/apis-universal-keystore-kit/errorcode-huks.md)中查看。

**起始版本：** 9

<!--Device-huks-export enum HuksExceptionErrCode--><!--Device-huks-export enum HuksExceptionErrCode-End-->

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_ERR_CODE_PERMISSION_FAIL

```TypeScript
HUKS_ERR_CODE_PERMISSION_FAIL = 201
```

权限错误导致失败。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_PERMISSION_FAIL = 201--><!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_PERMISSION_FAIL = 201-End-->

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_ERR_CODE_NOT_SYSTEM_APP

```TypeScript
HUKS_ERR_CODE_NOT_SYSTEM_APP = 202
```

非系统应用不可以调用系统API。

**起始版本：** 12

<!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_NOT_SYSTEM_APP = 202--><!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_NOT_SYSTEM_APP = 202-End-->

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_ERR_CODE_ILLEGAL_ARGUMENT

```TypeScript
HUKS_ERR_CODE_ILLEGAL_ARGUMENT = 401
```

参数错误导致失败。可能原因：1. 必选参数未指定。2. 参数类型不正确。3. 参数校验失败。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_ILLEGAL_ARGUMENT = 401--><!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_ILLEGAL_ARGUMENT = 401-End-->

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_ERR_CODE_NOT_SUPPORTED_API

```TypeScript
HUKS_ERR_CODE_NOT_SUPPORTED_API = 801
```

不支持的API。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_NOT_SUPPORTED_API = 801--><!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_NOT_SUPPORTED_API = 801-End-->

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_ERR_CODE_FEATURE_NOT_SUPPORTED

```TypeScript
HUKS_ERR_CODE_FEATURE_NOT_SUPPORTED = 12000001
```

不支持的功能/特性。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_FEATURE_NOT_SUPPORTED = 12000001--><!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_FEATURE_NOT_SUPPORTED = 12000001-End-->

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_ERR_CODE_MISSING_CRYPTO_ALG_ARGUMENT

```TypeScript
HUKS_ERR_CODE_MISSING_CRYPTO_ALG_ARGUMENT = 12000002
```

缺少密钥算法参数。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_MISSING_CRYPTO_ALG_ARGUMENT = 12000002--><!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_MISSING_CRYPTO_ALG_ARGUMENT = 12000002-End-->

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_ERR_CODE_INVALID_CRYPTO_ALG_ARGUMENT

```TypeScript
HUKS_ERR_CODE_INVALID_CRYPTO_ALG_ARGUMENT = 12000003
```

无效密钥算法参数。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_INVALID_CRYPTO_ALG_ARGUMENT = 12000003--><!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_INVALID_CRYPTO_ALG_ARGUMENT = 12000003-End-->

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_ERR_CODE_FILE_OPERATION_FAIL

```TypeScript
HUKS_ERR_CODE_FILE_OPERATION_FAIL = 12000004
```

文件操作失败。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_FILE_OPERATION_FAIL = 12000004--><!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_FILE_OPERATION_FAIL = 12000004-End-->

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_ERR_CODE_COMMUNICATION_FAIL

```TypeScript
HUKS_ERR_CODE_COMMUNICATION_FAIL = 12000005
```

通信失败。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_COMMUNICATION_FAIL = 12000005--><!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_COMMUNICATION_FAIL = 12000005-End-->

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_ERR_CODE_CRYPTO_FAIL

```TypeScript
HUKS_ERR_CODE_CRYPTO_FAIL = 12000006
```

算法库操作失败。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_CRYPTO_FAIL = 12000006--><!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_CRYPTO_FAIL = 12000006-End-->

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_ERR_CODE_KEY_AUTH_PERMANENTLY_INVALIDATED

```TypeScript
HUKS_ERR_CODE_KEY_AUTH_PERMANENTLY_INVALIDATED = 12000007
```

密钥访问失败-密钥访问失效。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_KEY_AUTH_PERMANENTLY_INVALIDATED = 12000007--><!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_KEY_AUTH_PERMANENTLY_INVALIDATED = 12000007-End-->

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_ERR_CODE_KEY_AUTH_VERIFY_FAILED

```TypeScript
HUKS_ERR_CODE_KEY_AUTH_VERIFY_FAILED = 12000008
```

密钥访问失败-密钥认证失败。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_KEY_AUTH_VERIFY_FAILED = 12000008--><!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_KEY_AUTH_VERIFY_FAILED = 12000008-End-->

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_ERR_CODE_KEY_AUTH_TIME_OUT

```TypeScript
HUKS_ERR_CODE_KEY_AUTH_TIME_OUT = 12000009
```

密钥访问失败-密钥访问超时。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_KEY_AUTH_TIME_OUT = 12000009--><!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_KEY_AUTH_TIME_OUT = 12000009-End-->

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_ERR_CODE_SESSION_LIMIT

```TypeScript
HUKS_ERR_CODE_SESSION_LIMIT = 12000010
```

密钥操作会话数已达上限。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_SESSION_LIMIT = 12000010--><!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_SESSION_LIMIT = 12000010-End-->

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_ERR_CODE_ITEM_NOT_EXIST

```TypeScript
HUKS_ERR_CODE_ITEM_NOT_EXIST = 12000011
```

目标对象不存在。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_ITEM_NOT_EXIST = 12000011--><!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_ITEM_NOT_EXIST = 12000011-End-->

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_ERR_CODE_EXTERNAL_ERROR

```TypeScript
HUKS_ERR_CODE_EXTERNAL_ERROR = 12000012
```

外部错误。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_EXTERNAL_ERROR = 12000012--><!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_EXTERNAL_ERROR = 12000012-End-->

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_ERR_CODE_CREDENTIAL_NOT_EXIST

```TypeScript
HUKS_ERR_CODE_CREDENTIAL_NOT_EXIST = 12000013
```

缺失所需凭据。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_CREDENTIAL_NOT_EXIST = 12000013--><!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_CREDENTIAL_NOT_EXIST = 12000013-End-->

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_ERR_CODE_INSUFFICIENT_MEMORY

```TypeScript
HUKS_ERR_CODE_INSUFFICIENT_MEMORY = 12000014
```

内存不足。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_INSUFFICIENT_MEMORY = 12000014--><!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_INSUFFICIENT_MEMORY = 12000014-End-->

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_ERR_CODE_CALL_SERVICE_FAILED

```TypeScript
HUKS_ERR_CODE_CALL_SERVICE_FAILED = 12000015
```

调用其他系统服务失败。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_CALL_SERVICE_FAILED = 12000015--><!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_CALL_SERVICE_FAILED = 12000015-End-->

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_ERR_CODE_DEVICE_PASSWORD_UNSET

```TypeScript
HUKS_ERR_CODE_DEVICE_PASSWORD_UNSET = 12000016
```

需要锁屏密码但未设置。

**起始版本：** 11

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_DEVICE_PASSWORD_UNSET = 12000016--><!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_DEVICE_PASSWORD_UNSET = 12000016-End-->

**系统能力：** SystemCapability.Security.Huks.Extension

## HUKS_ERR_CODE_KEY_ALREADY_EXIST

```TypeScript
HUKS_ERR_CODE_KEY_ALREADY_EXIST = 12000017
```

同名密钥已存在。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_KEY_ALREADY_EXIST = 12000017--><!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_KEY_ALREADY_EXIST = 12000017-End-->

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_ERR_CODE_INVALID_ARGUMENT

```TypeScript
HUKS_ERR_CODE_INVALID_ARGUMENT = 12000018
```

输入参数非法。

**起始版本：** 20

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_INVALID_ARGUMENT = 12000018--><!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_INVALID_ARGUMENT = 12000018-End-->

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_ERR_CODE_ITEM_EXISTS

```TypeScript
HUKS_ERR_CODE_ITEM_EXISTS = 12000019
```

同名provider已注册。

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_ITEM_EXISTS = 12000019--><!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_ITEM_EXISTS = 12000019-End-->

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_ERR_CODE_EXTERNAL_MODULE

```TypeScript
HUKS_ERR_CODE_EXTERNAL_MODULE = 12000020
```

依赖的外部模块返回错误。

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_EXTERNAL_MODULE = 12000020--><!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_EXTERNAL_MODULE = 12000020-End-->

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_ERR_CODE_PIN_LOCKED

```TypeScript
HUKS_ERR_CODE_PIN_LOCKED = 12000021
```

Ukey PIN码被锁。

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_PIN_LOCKED = 12000021--><!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_PIN_LOCKED = 12000021-End-->

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

## HUKS_ERR_CODE_PIN_INCORRECT

```TypeScript
HUKS_ERR_CODE_PIN_INCORRECT = 12000022
```

Ukey PIN码错误。

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_PIN_INCORRECT = 12000022--><!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_PIN_INCORRECT = 12000022-End-->

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

## HUKS_ERR_CODE_PIN_NO_AUTH

```TypeScript
HUKS_ERR_CODE_PIN_NO_AUTH = 12000023
```

Ukey PIN码未认证。

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_PIN_NO_AUTH = 12000023--><!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_PIN_NO_AUTH = 12000023-End-->

**系统能力：** SystemCapability.Security.Huks.CryptoExtension

## HUKS_ERR_CODE_BUSY

```TypeScript
HUKS_ERR_CODE_BUSY = 12000024
```

设备或资源繁忙。

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_BUSY = 12000024--><!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_BUSY = 12000024-End-->

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_ERR_CODE_EXCEED_LIMIT

```TypeScript
HUKS_ERR_CODE_EXCEED_LIMIT = 12000025
```

资源超过限制。

**起始版本：** 22

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_EXCEED_LIMIT = 12000025--><!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_EXCEED_LIMIT = 12000025-End-->

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_ERR_CODE_SE_FAULT

```TypeScript
HUKS_ERR_CODE_SE_FAULT = 12000026
```

安全元件故障。

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_SE_FAULT = 12000026--><!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_SE_FAULT = 12000026-End-->

**系统能力：** SystemCapability.Security.Huks.Core

## HUKS_ERR_CODE_NETWORK_UNAVAILABLE

```TypeScript
HUKS_ERR_CODE_NETWORK_UNAVAILABLE = 12000027
```

网络不可用。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_NETWORK_UNAVAILABLE = 12000027--><!--Device-HuksExceptionErrCode-HUKS_ERR_CODE_NETWORK_UNAVAILABLE = 12000027-End-->

**系统能力：** SystemCapability.Security.Huks.Extension

