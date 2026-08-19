# SelectFrameNode

定义Select类型的FrameNode。

**继承/实现关系：** SelectFrameNode extends TypedFrameNode<SelectAttribute>

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-typeNode-abstract class SelectFrameNode--><!--Device-typeNode-abstract class SelectFrameNode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## initialize

```TypeScript
abstract initialize(value: Array<SelectOption>): SelectAttribute
```

初始化Select类型的FrameNode。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SelectFrameNode-abstract initialize(value: Array<SelectOption>): SelectAttribute--><!--Device-SelectFrameNode-abstract initialize(value: Array<SelectOption>): SelectAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Array&lt;SelectOption&gt; | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| SelectAttribute |  |

