# GridFrameNode

定义Grid类型的FrameNode。

**继承/实现关系：** GridFrameNode extends TypedFrameNode<GridAttribute>

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-typeNode-abstract class GridFrameNode--><!--Device-typeNode-abstract class GridFrameNode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## initialize

```TypeScript
abstract initialize(scroller?: Scroller, layoutOptions?: GridLayoutOptions): GridAttribute
```

初始化Grid类型的FrameNode。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GridFrameNode-abstract initialize(scroller?: Scroller, layoutOptions?: GridLayoutOptions): GridAttribute--><!--Device-GridFrameNode-abstract initialize(scroller?: Scroller, layoutOptions?: GridLayoutOptions): GridAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scroller | Scroller | 否 | grid的控制器。 |
| layoutOptions | GridLayoutOptions | 否 | Grid布局选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| GridAttribute |  |

