# AuthorizationResultCode（系统接口）

表示授权结果码的枚举。

**起始版本：** 24

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## AUTHORIZATION_SUCCESS

```TypeScript
AUTHORIZATION_SUCCESS = 0
```

表示授权成功。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## AUTHORIZATION_CANCELED

```TypeScript
AUTHORIZATION_CANCELED = 12300301
```

表示授权已取消。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## AUTHORIZATION_INTERACTION_NOT_ALLOWED

```TypeScript
AUTHORIZATION_INTERACTION_NOT_ALLOWED = 12300302
```

表示服务因不允许用户交互而拒绝授权。

可能原因：

1. 调用者位于后台；
2. isInteractionAllowed选项的值为false；
3. 指定的交互上下文无效。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## AUTHORIZATION_DENIED

```TypeScript
AUTHORIZATION_DENIED = 12300303
```

表示因不符合授权规则，如账号类型不是管理员、设备类型不支持等原因而拒绝授权。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## AUTHORIZATION_SERVICE_BUSY

```TypeScript
AUTHORIZATION_SERVICE_BUSY = 12300304
```

表示服务忙碌。

可能原因：正在处理其他授权。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

