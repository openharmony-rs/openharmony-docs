# StackFrameNode

定义Stack类型的FrameNode。

**继承/实现关系：** StackFrameNode extends TypedFrameNode<StackAttribute>

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-typeNode-abstract class StackFrameNode--><!--Device-typeNode-abstract class StackFrameNode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## initialize

```TypeScript
abstract initialize(options?: StackOptions): StackAttribute
```

初始化Stack类型的FrameNode。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-StackFrameNode-abstract initialize(options?: StackOptions): StackAttribute--><!--Device-StackFrameNode-abstract initialize(options?: StackOptions): StackAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | StackOptions | 否 | Stack节点的选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| StackAttribute |  |

