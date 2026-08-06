# CommonEventData

表示公共事件的数据。CommonEventData用于在公共事件订阅场景中承载 订阅者接收到的公共事件数据，包含事件名称、发布者包名、code数据、 data数据及附加参数等信息，适用于应用订阅并处理公共事件、 解析事件携带数据的场景。

**起始版本：** 7

**ArkTS模式：** ArkTS-Dyn起始版本为7；ArkTS-Sta起始版本为23。

<!--Device-unnamed-export interface CommonEventData--><!--Device-unnamed-export interface CommonEventData-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## bundleName

```TypeScript
bundleName?: string
```

表示发布公共事件的应用包名，默认为空字符串。

**类型：** string

**起始版本：** 7

**ArkTS模式：** ArkTS-Dyn起始版本为7；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventData-bundleName?: string--><!--Device-CommonEventData-bundleName?: string-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## code

```TypeScript
code?: int
```

表示订阅者接收到的公共事件数据。该字段取值与发布者使用 [commonEventManager.publish]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_ 发布公共事件时，通过[CommonEventPublishData]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_中的\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_字段传递的数据一致。取值范围[-2147483648, 2147483647]，默认值为0。

**类型：** int

**默认值：** 0

**起始版本：** 7

**ArkTS模式：** ArkTS-Dyn起始版本为7；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventData-code?: int--><!--Device-CommonEventData-code?: int-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## data

```TypeScript
data?: string
```

表示订阅者接收到的公共事件数据，数据大小不超过64KB。该字段取值与发布者使用 [commonEventManager.publish]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_ 发布公共事件时，通过[CommonEventPublishData]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_中的\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_字段传递的数据一致。

**类型：** string

**起始版本：** 7

**ArkTS模式：** ArkTS-Dyn起始版本为7；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventData-data?: string--><!--Device-CommonEventData-data?: string-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## event

```TypeScript
event: string
```

表示当前接收的公共事件名称。

**类型：** string

**起始版本：** 7

**ArkTS模式：** ArkTS-Dyn起始版本为7；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventData-event: string--><!--Device-CommonEventData-event: string-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

## parameters

```TypeScript
parameters?: { [key: string]: any }
```

表示订阅者接收到的公共事件的附加信息。该字段取值与发布者使用 [commonEventManager.publish]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_ 发布公共事件时，通过[CommonEventPublishData]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_中的\_\_\_INLINE\_CODE\_DESC\_USD\_0\_\_\_字段传递的数据一致。

**类型：** { [key: string]: any }

**起始版本：** 7

**ArkTS模式：** ArkTS-Dyn起始版本为7；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-CommonEventData-parameters?: { [key: string]: any }--><!--Device-CommonEventData-parameters?: { [key: string]: any }-End-->

**系统能力：** SystemCapability.Notification.CommonEvent

