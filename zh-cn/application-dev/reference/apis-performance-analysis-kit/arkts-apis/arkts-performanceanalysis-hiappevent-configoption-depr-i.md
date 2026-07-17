# ConfigOption

此接口提供了应用打点的配置选项。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** ConfigOption

<!--Device-hiAppEvent-interface ConfigOption--><!--Device-hiAppEvent-interface ConfigOption-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## disable

```TypeScript
disable?: boolean
```

应用打点功能开关。配置值为true表示关闭打点功能，false表示不关闭打点功能。

**类型：** boolean

**起始版本：** 7

**废弃版本：** 9

**替代接口：** disable

<!--Device-ConfigOption-disable?: boolean--><!--Device-ConfigOption-disable?: boolean-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## maxStorage

```TypeScript
maxStorage?: string
```

打点数据本地存储文件所在目录的配额大小，默认限额为“10M”。所在目录大小超出限额后会对目录进行清理操作，会按从旧到新的顺序逐个删除打点数据文件，直到目录大小不超出限额时停止。

**类型：** string

**起始版本：** 7

**废弃版本：** 9

**替代接口：** maxStorage

<!--Device-ConfigOption-maxStorage?: string--><!--Device-ConfigOption-maxStorage?: string-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

