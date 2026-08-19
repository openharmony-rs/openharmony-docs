# TextFrameNode

定义Text类型的FrameNode。

**继承/实现关系：** TextFrameNode extends TypedFrameNode<TextAttribute>

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-typeNode-abstract class TextFrameNode--><!--Device-typeNode-abstract class TextFrameNode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## initialize

```TypeScript
abstract initialize(content?: string | Resource, value?: TextOptions): TextAttribute
```

初始化Text类型的FrameNode。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TextFrameNode-abstract initialize(content?: string | Resource, value?: TextOptions): TextAttribute--><!--Device-TextFrameNode-abstract initialize(content?: string | Resource, value?: TextOptions): TextAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| content | string \| Resource | 否 |  |
| value | TextOptions | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| TextAttribute |  |

