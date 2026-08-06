# TypedFrameNode

TypedFrameNode继承自[FrameNode]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_，用于声明具体类型的FrameNode。 > **说明：** > > [commonAttribute]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_仅在CustomFrameNode上生效，TypedFrameNode上commonAttribute行为未定义。建议使用 > \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_接口而非 > [commonAttribute]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_接口进行通用属性设置，如node.attribute.backgroundColor(Color.Pink)。

**继承/实现关系：** TypedFrameNode extends [FrameNode](framenode-framenode-c.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare abstract class TypedFrameNode<T> extends FrameNode--><!--Device-unnamed-export declare abstract class TypedFrameNode<T> extends FrameNode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## attribute

```TypeScript
get attribute(): T
```

获取FrameNode的实例属性以设置属性。 > **说明：** > > [commonAttribute]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_仅在CustomFrameNode上生效，TypedFrameNode上commonAttribute行为未定义。建议使用 > \_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_接口而非 > [commonAttribute]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_接口进行通用属性设置，如node.attribute.backgroundColor(Color.Pink)。

**类型：** T

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-TypedFrameNode-get attribute(): T--><!--Device-TypedFrameNode-get attribute(): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

