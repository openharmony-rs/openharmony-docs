# AuthInstance

执行用户认证的对象。

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [UserAuthInstance](arkts-userauthentication-userauthinstance-i.md)

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## cancel

```TypeScript
cancel: () => void
```

取消认证。

> **说明：**
>
> 使用获取到的[AuthInstance](arkts-userauthentication-authinstance-i.md)对象调用该接口进行取消认证，此[AuthInstance](arkts-userauthentication-authinstance-i.md)需要是正
> 在进行认证的对象。

**类型：** () => void

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [cancel](arkts-userauthentication-userauthinstance-i.md#cancel-1)

**需要权限：** ohos.permission.ACCESS_BIOMETRIC

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## off

```TypeScript
off: (name: AuthEventKey) => void
```

取消订阅特定类型的认证事件。

- **name**: 表示认证事件类型，取值为"result"时，取消订阅认证结果；取值为"tip"时，取消订阅认证过程中的提示信息，类型为
[AuthEventKey](arkts-userauthentication-autheventkey-t.md)。

> **说明：**
>
> 需要使用已经成功订阅事件的[AuthInstance](arkts-userauthentication-authinstance-i.md)对象调用该接口进行取消订阅。

**类型：** (name: AuthEventKey) => void

**起始版本：** 9

**废弃版本：** 10

**替代接口：** off

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## on

```TypeScript
on: (name: AuthEventKey, callback: AuthEvent) => void
```

订阅指定类型的用户认证事件。

- **name**: 表示认证事件类型，取值为"result"时，回调函数返回认证结果；取值为"tip"时，回调函数返回认证过程中的提示信息，类型为
[AuthEventKey](arkts-userauthentication-autheventkey-t.md)。
- **callback**: 认证接口的回调函数，用于返回认证结果或认证过程中的提示信息，类型为[AuthEvent](arkts-userauthentication-authevent-i.md)。

> **说明：**
>
> 使用获取到的[AuthInstance](arkts-userauthentication-authinstance-i.md)对象调用该接口进行订阅。

**类型：** (name: AuthEventKey, callback: AuthEvent) => void

**起始版本：** 9

**废弃版本：** 10

**替代接口：** on

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## start

```TypeScript
start: () => void
```

开始认证。

> **说明：**
>
> 使用获取到的[AuthInstance](arkts-userauthentication-authinstance-i.md)对象调用该接口进行认证。

**类型：** () => void

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [start](arkts-userauthentication-userauthinstance-i.md#start-1)

**需要权限：** ohos.permission.ACCESS_BIOMETRIC

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

