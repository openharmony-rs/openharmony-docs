# XComponentFrameNode

定义XComponent 类型的FrameNode。

**继承/实现关系：** XComponentFrameNode extends TypedFrameNode<XComponentAttribute>

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-typeNode-abstract class XComponentFrameNode--><!--Device-typeNode-abstract class XComponentFrameNode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## initialize

```TypeScript
abstract initialize(value: XComponentParameters): XComponentAttribute
```

初始化XComponent类型的FrameNode。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-XComponentFrameNode-abstract initialize(value: XComponentParameters): XComponentAttribute--><!--Device-XComponentFrameNode-abstract initialize(value: XComponentParameters): XComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [XComponentParameters](arkts-na-xcomponent-xcomponentparameters-i.md) | 是 | xcomponent节点的选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| XComponentAttribute |  |

## initialize

```TypeScript
abstract initialize(value: XComponentOptions): XComponentAttribute
```

初始化XComponent类型的FrameNode。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-XComponentFrameNode-abstract initialize(value: XComponentOptions): XComponentAttribute--><!--Device-XComponentFrameNode-abstract initialize(value: XComponentOptions): XComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | XComponentOptions | 是 | xcomponent节点的选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| XComponentAttribute |  |

## initialize

```TypeScript
abstract initialize(params: NativeXComponentParameters): XComponentAttribute
```

初始化XComponent类型的FrameNode。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-XComponentFrameNode-abstract initialize(params: NativeXComponentParameters): XComponentAttribute--><!--Device-XComponentFrameNode-abstract initialize(params: NativeXComponentParameters): XComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| params | NativeXComponentParameters | 是 | 用于原生开发的 XComponent 的构造参数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| XComponentAttribute |  |

