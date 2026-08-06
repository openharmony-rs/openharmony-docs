# Querier（系统接口）

系统事件查询者对象接口。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-hiSysEvent-interface Querier--><!--Device-hiSysEvent-interface Querier-End-->

**系统能力：** SystemCapability.HiviewDFX.HiSysEvent

**系统接口：** 此接口为系统接口。

## onComplete

```TypeScript
onComplete: (reason: int, total: int) => void
```

查询结果统计的回调方法(reason: int, total: int) => void。

**类型：** (reason: int, total: int) =&gt; void

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-Querier-onComplete: (reason: int, total: int) => void--><!--Device-Querier-onComplete: (reason: int, total: int) => void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiSysEvent

**系统接口：** 此接口为系统接口。

## onQuery

```TypeScript
onQuery: (infos: SysEventInfo[]) => void
```

返回查询到的系统事件的回调方法(infos: [SysEventInfo]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_[]) => void。

**类型：** (infos: SysEventInfo[]) =&gt; void

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-Querier-onQuery: (infos: SysEventInfo[]) => void--><!--Device-Querier-onQuery: (infos: SysEventInfo[]) => void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiSysEvent

**系统接口：** 此接口为系统接口。

