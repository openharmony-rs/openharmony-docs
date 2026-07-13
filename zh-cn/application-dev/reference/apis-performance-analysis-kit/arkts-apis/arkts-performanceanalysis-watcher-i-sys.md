# Watcher（系统接口）

系统事件订阅者对象接口。

**起始版本：** 9

**系统能力：** SystemCapability.HiviewDFX.HiSysEvent

**系统接口：** 此接口为系统接口。

## onEvent

```TypeScript
onEvent: (info: SysEventInfo) => void
```

订阅事件的回调方法(info: [SysEventInfo](arkts-performanceanalysis-syseventinfo-i-sys.md)) => void。

**类型：** (info: SysEventInfo) => void

**起始版本：** 9

**系统能力：** SystemCapability.HiviewDFX.HiSysEvent

**系统接口：** 此接口为系统接口。

## onServiceDied

```TypeScript
onServiceDied: () => void
```

系统事件服务关闭的回调方法() => void。

**类型：** () => void

**起始版本：** 9

**系统能力：** SystemCapability.HiviewDFX.HiSysEvent

**系统接口：** 此接口为系统接口。

## rules

```TypeScript
rules: WatchRule[]
```

订阅对象数组，每个订阅者对象包含多个订阅规则。

**类型：** WatchRule[]

**起始版本：** 9

**系统能力：** SystemCapability.HiviewDFX.HiSysEvent

**系统接口：** 此接口为系统接口。

