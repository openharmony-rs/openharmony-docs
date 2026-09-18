# AuthEventKey

```TypeScript
type AuthEventKey = 'result' | 'tip'
```

Defines the keyword of the authentication event type. It is used as a parameter of [on](arkts-userauthentication-userauth-authinstance-i.md#on).

It consists of the fields in **Type** in the following table.

**Since:** 9

**Deprecated since:** 11

**System capability:** SystemCapability.UserIAM.UserAuth.Core

| Type | Description |
| --- | --- |
| 'result' | If the first parameter of [on](arkts-userauthentication-userauth-authinstance-i.md#on) is **result**, the [callback](arkts-userauthentication-userauth-authevent-i.md#callback) If the first parameter of [on](arkts-userauthentication-userauth-authinstance-i.md#on) is **result**, the [callback](arkts-userauthentication-userauth-authevent-i.md#callback) If the first parameter of [on](arkts-userauthentication-userauth-authinstance-i.md#on) is **result**, the [callback](arkts-userauthentication-userauth-authevent-i.md#callback) returns the authentication result. |
| 'tip' | If the first parameter of [on](arkts-userauthentication-userauth-authinstance-i.md#on) is **tip**, the [callback](arkts-userauthentication-userauth-authevent-i.md#callback) If the first parameter of [on](arkts-userauthentication-userauth-authinstance-i.md#on) is **tip**, the [callback](arkts-userauthentication-userauth-authevent-i.md#callback) If the first parameter of [on](arkts-userauthentication-userauth-authinstance-i.md#on) is **tip**, the [callback](arkts-userauthentication-userauth-authevent-i.md#callback) returns the authentication tip information. |
