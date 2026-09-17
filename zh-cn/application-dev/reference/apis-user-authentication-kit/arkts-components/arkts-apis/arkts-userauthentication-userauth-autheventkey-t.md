# AuthEventKey

```TypeScript
type AuthEventKey = 'result' | 'tip'
```

表示认证事件类型的关键字，作为[on](arkts-userauthentication-userauth-authinstance-i.md#on)接口的参数。

该类型为下表类型取值中的联合类型。

**起始版本：** 9

**废弃版本：** 11

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

| 类型 | 说明 |
| --- | --- |
| 'result' | If the first parameter of [on](arkts-userauthentication-userauth-authinstance-i.md#on) is **result**, the [callback](arkts-userauthentication-userauth-authevent-i.md#callback) If the first parameter of [on](arkts-userauthentication-userauth-authinstance-i.md#on) is **result**, the [callback](arkts-userauthentication-userauth-authevent-i.md#callback) [on](arkts-userauthentication-userauth-authinstance-i.md#on)接口第一个参数为"result"时，[callback](arkts-userauthentication-userauth-authevent-i.md#callback)回调返回认证的结果信息。 |
| 'tip' | If the first parameter of [on](arkts-userauthentication-userauth-authinstance-i.md#on) is **tip**, the [callback](arkts-userauthentication-userauth-authevent-i.md#callback) If the first parameter of [on](arkts-userauthentication-userauth-authinstance-i.md#on) is **tip**, the [callback](arkts-userauthentication-userauth-authevent-i.md#callback) [on](arkts-userauthentication-userauth-authinstance-i.md#on)接口第一个参数为"tip"时，[callback](arkts-userauthentication-userauth-authevent-i.md#callback)回调返回认证操作中的提示信息。 |
