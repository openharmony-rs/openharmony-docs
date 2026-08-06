# NodeIdentity

```TypeScript
export declare type NodeIdentity = string | int
```

定义可用于标识节点的类型，string类型时为inspector id，number类型时为系统分配的唯一id。 set through .id attribute, and for the int type, it's the unique ID got from the FrameNode by getUniqueID method.

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare type NodeIdentity = string | int--><!--Device-unnamed-export declare type NodeIdentity = string | int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 类型 | 说明 |
| --- | --- |
| string |  |
| int |  |

