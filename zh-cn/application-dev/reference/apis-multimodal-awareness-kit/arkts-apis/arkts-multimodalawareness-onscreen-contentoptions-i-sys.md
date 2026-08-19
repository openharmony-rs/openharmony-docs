# ContentOptions（系统接口）

屏上内容的获取选项。

**起始版本：** 23

<!--Device-onScreen-export interface ContentOptions--><!--Device-onScreen-export interface ContentOptions-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { onScreen } from '@kit.MultimodalAwarenessKit';
```

## contentUnderstand

```TypeScript
contentUnderstand?: boolean
```

是否需要进行内容理解，true表示需要，false表示不需要，默认为false。

**类型：** boolean

**起始版本：** 23

<!--Device-ContentOptions-contentUnderstand?: boolean--><!--Device-ContentOptions-contentUnderstand?: boolean-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## pageLink

```TypeScript
pageLink?: boolean
```

是否获取复访链接，true表示获取，false表示不获取，默认为false。

**类型：** boolean

**起始版本：** 23

<!--Device-ContentOptions-pageLink?: boolean--><!--Device-ContentOptions-pageLink?: boolean-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## textOnly

```TypeScript
textOnly?: boolean
```

是否只获取文本并划分段落，true表示是，false表示否，默认为false。

**类型：** boolean

**起始版本：** 23

<!--Device-ContentOptions-textOnly?: boolean--><!--Device-ContentOptions-textOnly?: boolean-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

## windowId

```TypeScript
windowId?: int
```

需要获取内容的窗口ID，不赋值或赋值undefined则默认获取全屏窗口。

**类型：** int

**起始版本：** 23

<!--Device-ContentOptions-windowId?: int--><!--Device-ContentOptions-windowId?: int-End-->

**系统能力：** SystemCapability.MultimodalAwareness.OnScreenAwareness

**系统接口：** 此接口为系统接口。

