# PageContent（系统接口）

屏上内容。

**起始版本：** 20

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { onScreen } from '@kit.MultimodalAwarenessKit';
```

## bundleName

```TypeScript
bundleName: string
```

获取到的屏上内容的包名。

**类型：** string

**起始版本：** 20

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## content

```TypeScript
content?: string
```

获取到的屏上内容的正文。只有在options.contentUnderstand为true时，才会获取该属性。

**类型：** string

**起始版本：** 20

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## pageLink

```TypeScript
pageLink?: string
```

获取到的屏上内容的复访链接。只有在options.pageLink为true时，才会获取该属性。

**类型：** string

**起始版本：** 20

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## paragraphs

```TypeScript
paragraphs?: Paragraph[]
```

获取到的文本段落信息。只有在options.textOnly为true时，才会获取该属性。

**类型：** Paragraph[]

**起始版本：** 20

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## scenario

```TypeScript
scenario?: Scenario
```

获取到的屏上内容的场景。仅在options.contentUnderstand为true时，才会获取该属性。

**类型：** [Scenario](arkts-multimodalawareness-onscreen-scenario-e-sys.md)

**起始版本：** 20

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## sessionId

```TypeScript
sessionId: number
```

此次调用该接口的session ID，标识当次调用动作。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## title

```TypeScript
title?: string
```

获取到的屏上内容的标题。只有在options.contentUnderstand为true时，才会获取该属性。

**类型：** string

**起始版本：** 20

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## windowId

```TypeScript
windowId: number
```

获取到的屏上内容的窗口ID

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。
