# OsAccountSwitchEventData（系统接口）

表示系统账号前后台开始切换和结束切换事件的数据结构。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-osAccount-interface OsAccountSwitchEventData--><!--Device-osAccount-interface OsAccountSwitchEventData-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## displayId

```TypeScript
displayId?: long
```

切换事件发生的逻辑屏ID，默认值为0。

**类型：** long

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-OsAccountSwitchEventData-displayId?: long--><!--Device-OsAccountSwitchEventData-displayId?: long-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## fromAccountId

```TypeScript
fromAccountId: int
```

切换来源系统账号ID。

**类型：** int

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-OsAccountSwitchEventData-fromAccountId: int--><!--Device-OsAccountSwitchEventData-fromAccountId: int-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

## toAccountId

```TypeScript
toAccountId: int
```

切换目标系统账号ID。

**类型：** int

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-OsAccountSwitchEventData-toAccountId: int--><!--Device-OsAccountSwitchEventData-toAccountId: int-End-->

**系统能力：** SystemCapability.Account.OsAccount

**系统接口：** 此接口为系统接口。

