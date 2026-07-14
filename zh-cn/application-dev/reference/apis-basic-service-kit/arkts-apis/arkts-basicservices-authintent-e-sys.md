# AuthIntent（系统接口）

表示认证意图的枚举。

**起始版本：** 12

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## UNLOCK

```TypeScript
UNLOCK = 1
```

解锁意图。

**起始版本：** 12

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## SILENT_AUTH

```TypeScript
SILENT_AUTH = 2
```

静默认证意图。

**起始版本：** 14

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## QUESTION_AUTH

```TypeScript
QUESTION_AUTH = 3
```

密保问题认证意图。

**起始版本：** 14

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## ABANDONED_PIN_AUTH

```TypeScript
ABANDONED_PIN_AUTH = 4
```

废弃PIN码认证意图。用户修改锁屏密码后，旧的PIN码被废弃。废弃PIN存在期间，用户如果忘记密码可以通过废弃PIN认证通过后重置锁屏密码。

**起始版本：** 20

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

