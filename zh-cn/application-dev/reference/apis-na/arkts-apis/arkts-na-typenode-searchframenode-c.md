# SearchFrameNode

定义Search类型的FrameNode。

**继承/实现关系：** SearchFrameNode extends TypedFrameNode<SearchAttribute>

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-typeNode-abstract class SearchFrameNode--><!--Device-typeNode-abstract class SearchFrameNode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## initialize

```TypeScript
abstract initialize(value?: SearchOptions): SearchAttribute
```

初始化Search类型的FrameNode。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SearchFrameNode-abstract initialize(value?: SearchOptions): SearchAttribute--><!--Device-SearchFrameNode-abstract initialize(value?: SearchOptions): SearchAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | SearchOptions | 否 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| SearchAttribute |  |

