# PageContent（系统接口）

屏上内容。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-onScreen-export interface PageContent--><!--Device-onScreen-export interface PageContent-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## bundleName

```TypeScript
bundleName: string
```

获取到的屏上内容的包名。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-PageContent-bundleName: string--><!--Device-PageContent-bundleName: string-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## content

```TypeScript
content?: string
```

获取到的屏上内容的正文。只有在options.contentUnderstand为true时，才会获取该属性。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-PageContent-content?: string--><!--Device-PageContent-content?: string-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## pageLink

```TypeScript
pageLink?: string
```

获取到的屏上内容的复访链接。只有在options.pageLink为true时，才会获取该属性。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-PageContent-pageLink?: string--><!--Device-PageContent-pageLink?: string-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## paragraphs

```TypeScript
paragraphs?: Paragraph[]
```

获取到的文本段落信息。只有在options.textOnly为true时，才会获取该属性。

**类型：** Paragraph[]

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-PageContent-paragraphs?: Paragraph[]--><!--Device-PageContent-paragraphs?: Paragraph[]-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## scenario

```TypeScript
scenario?: Scenario
```

获取到的屏上内容的场景。只有在options.contentUnderstand为true时，才会获取该属性。

**类型：** [Scenario](arkts-multimodalawareness-onscreen-scenario-e-sys.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-PageContent-scenario?: Scenario--><!--Device-PageContent-scenario?: Scenario-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## sessionId

```TypeScript
sessionId: long
```

此次调用该接口的session ID，标识当次调用动作。

**类型：** long

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-PageContent-sessionId: long--><!--Device-PageContent-sessionId: long-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## title

```TypeScript
title?: string
```

获取到的屏上内容的标题。只有在options.contentUnderstand为true时，才会获取该属性。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-PageContent-title?: string--><!--Device-PageContent-title?: string-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## windowId

```TypeScript
windowId: int
```

获取到的屏上内容的窗口ID

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-PageContent-windowId: int--><!--Device-PageContent-windowId: int-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

