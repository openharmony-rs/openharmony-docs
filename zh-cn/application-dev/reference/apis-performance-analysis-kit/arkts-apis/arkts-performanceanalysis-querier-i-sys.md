# Querier（系统接口）

系统事件查询者对象接口。

**起始版本：** 9

**系统能力：** SystemCapability.HiviewDFX.HiSysEvent

**系统接口：** 此接口为系统接口。

## onComplete

```TypeScript
onComplete: (reason: number, total: number) => void
```

查询结果统计的回调方法(reason: int, total: int) => void。

**类型：** (reason: number, total: number) => void

**起始版本：** 9

**系统能力：** SystemCapability.HiviewDFX.HiSysEvent

**系统接口：** 此接口为系统接口。

## onQuery

```TypeScript
onQuery: (infos: SysEventInfo[]) => void
```

返回查询到的系统事件的回调方法(infos: [SysEventInfo](arkts-performanceanalysis-syseventinfo-i-sys.md)[]) => void。

**类型：** (infos: SysEventInfo[]) => void

**起始版本：** 9

**系统能力：** SystemCapability.HiviewDFX.HiSysEvent

**系统接口：** 此接口为系统接口。

