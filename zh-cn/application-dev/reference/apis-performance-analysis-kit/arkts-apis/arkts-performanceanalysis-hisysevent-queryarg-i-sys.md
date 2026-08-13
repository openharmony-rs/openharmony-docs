# QueryArg（系统接口）

系统事件查询参数对象接口。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-hiSysEvent-interface QueryArg--><!--Device-hiSysEvent-interface QueryArg-End-->

**系统能力：** SystemCapability.HiviewDFX.HiSysEvent

**系统接口：** 此接口为系统接口。

## beginTime

```TypeScript
beginTime: long
```

查询的系统事件起始时间（13位时间戳），表示距1970年1月1日0时0分0秒0毫秒的毫秒数。

**类型：** long

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-QueryArg-beginTime: long--><!--Device-QueryArg-beginTime: long-End-->

**系统能力：** SystemCapability.HiviewDFX.HiSysEvent

**系统接口：** 此接口为系统接口。

## endTime

```TypeScript
endTime: long
```

查询的系统事件结束时间（13位时间戳），表示距1970年1月1日0时0分0秒0毫秒的毫秒数。

**类型：** long

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-QueryArg-endTime: long--><!--Device-QueryArg-endTime: long-End-->

**系统能力：** SystemCapability.HiviewDFX.HiSysEvent

**系统接口：** 此接口为系统接口。

## fromSeq

```TypeScript
fromSeq?: long | null | undefined
```

查询的系统事件起始序列号，默认值为-1。

**类型：** long \| null \| undefined

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-QueryArg-fromSeq?: long | null | undefined--><!--Device-QueryArg-fromSeq?: long | null | undefined-End-->

**系统能力：** SystemCapability.HiviewDFX.HiSysEvent

**系统接口：** 此接口为系统接口。

## maxEvents

```TypeScript
maxEvents: long
```

查询的系统事件最多条数。

**类型：** long

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-QueryArg-maxEvents: long--><!--Device-QueryArg-maxEvents: long-End-->

**系统能力：** SystemCapability.HiviewDFX.HiSysEvent

**系统接口：** 此接口为系统接口。

## toSeq

```TypeScript
toSeq?: long | null | undefined
```

查询的系统事件结束序列号，默认值为-1。

**类型：** long \| null \| undefined

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-QueryArg-toSeq?: long | null | undefined--><!--Device-QueryArg-toSeq?: long | null | undefined-End-->

**系统能力：** SystemCapability.HiviewDFX.HiSysEvent

**系统接口：** 此接口为系统接口。

