# Watcher（系统接口）

系统事件订阅者对象接口。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-hiSysEvent-interface Watcher--><!--Device-hiSysEvent-interface Watcher-End-->

**系统能力：** SystemCapability.HiviewDFX.HiSysEvent

**系统接口：** 此接口为系统接口。

## onEvent

```TypeScript
onEvent: (info: SysEventInfo) => void
```

订阅事件的回调方法(info: [SysEventInfo](arkts-performanceanalysis-hisysevent-syseventinfo-i-sys.md#SysEventInfo（系统接口）)) => void。

**类型：** (info: SysEventInfo) =&gt; void

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Watcher-onEvent: (info: SysEventInfo) => void--><!--Device-Watcher-onEvent: (info: SysEventInfo) => void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiSysEvent

**系统接口：** 此接口为系统接口。

## onServiceDied

```TypeScript
onServiceDied: () => void
```

系统事件服务关闭的回调方法() => void。

**类型：** () =&gt; void

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Watcher-onServiceDied: () => void--><!--Device-Watcher-onServiceDied: () => void-End-->

**系统能力：** SystemCapability.HiviewDFX.HiSysEvent

**系统接口：** 此接口为系统接口。

## rules

```TypeScript
rules: WatchRule[]
```

订阅对象数组，每个订阅者对象包含多个订阅规则。

**类型：** [WatchRule](arkts-performanceanalysis-hisysevent-watchrule-i-sys.md)[]

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-Watcher-rules: WatchRule[]--><!--Device-Watcher-rules: WatchRule[]-End-->

**系统能力：** SystemCapability.HiviewDFX.HiSysEvent

**系统接口：** 此接口为系统接口。

