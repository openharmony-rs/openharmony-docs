# EventInfo

```TypeScript
type EventInfo = AuthResultInfo | TipInfo
```

表示认证过程中事件信息的类型。

该类型为下表类型取值中的联合类型。

**起始版本：** 9

**废弃版本：** 11

**替代接口：** [UserAuthResult](arkts-userauthentication-userauth-userauthresult-i.md)

<!--Device-userAuth-type EventInfo = AuthResultInfo | TipInfo--><!--Device-userAuth-type EventInfo = AuthResultInfo | TipInfo-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

| 类型 | 说明 |
| --- | --- |
| AuthResultInfo | 获取到的认证结果信息。 |
| TipInfo | 认证过程中的提示信息。 |

