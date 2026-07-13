# OsAccountSwitchEventData（系统接口）

表示系统账号前后台开始切换和结束切换事件的数据结构。

**起始版本：** 12

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## displayId

```TypeScript
displayId?: number
```

切换事件发生的逻辑屏ID，默认值为0。

**类型：** number

**起始版本：** 23

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## fromAccountId

```TypeScript
fromAccountId: number
```

切换来源系统账号ID。

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## toAccountId

```TypeScript
toAccountId: number
```

切换目标系统账号ID。

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

