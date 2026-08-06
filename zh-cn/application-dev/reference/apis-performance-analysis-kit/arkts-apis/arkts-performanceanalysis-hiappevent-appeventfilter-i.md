# AppEventFilter

提供设置[Watcher]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_的订阅过滤条件的参数选项。用于在事件观察者中设置事件过滤条件，确保只有满足过滤条件的事件才会被监听处理。 > **说明：** > > 不同类型应用上，系统事件的订阅规格不同，具体规格可参见\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-hiAppEvent-interface AppEventFilter--><!--Device-hiAppEvent-interface AppEventFilter-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## domain

```TypeScript
domain: string
```

需要订阅的事件领域。可以是系统事件领域（hiAppEvent.domain.OS）或开发者在使用[Write]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_接口时传入的 自定义事件信息（[AppEventInfo]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_）中的事件领域。

**类型：** string

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AppEventFilter-domain: string--><!--Device-AppEventFilter-domain: string-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## eventTypes

```TypeScript
eventTypes?: EventType[]
```

需要订阅的事件类型集合。默认不进行过滤。

**类型：** EventType[]

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AppEventFilter-eventTypes?: EventType[]--><!--Device-AppEventFilter-eventTypes?: EventType[]-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

## names

```TypeScript
names?: string[]
```

需要订阅的事件名称集合。默认不进行过滤。

**类型：** string[]

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AppEventFilter-names?: string[]--><!--Device-AppEventFilter-names?: string[]-End-->

**系统能力：** SystemCapability.HiviewDFX.HiAppEvent

