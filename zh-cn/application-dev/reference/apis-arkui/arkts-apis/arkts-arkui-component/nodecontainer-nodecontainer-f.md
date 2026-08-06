# NodeContainer

## NodeContainer

```TypeScript
export declare function NodeContainer(
    controller: NodeController
): NodeContainerAttribute
```

创建NodeContainer组件。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare function NodeContainer(    controller: NodeController): NodeContainerAttribute--><!--Device-unnamed-export declare function NodeContainer(    controller: NodeController): NodeContainerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| controller | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 一个NodeController对象，其用于控制NodeContainer中的节点的上树和下树，反映NodeContainer容器的生命周期。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ |  |


## NodeContainer

```TypeScript
export declare function NodeContainer(
    style: CustomBuilderT<NodeContainerAttribute>
): NodeContainerAttribute
```

定义NodeContainer组件。需要在组件属性设置开始时调用setNodeContainerOptions，并在组件属性设置结束时调用applyAttributeFinish。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**装饰器类型：** @Builder

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export declare function NodeContainer(    style: CustomBuilderT<NodeContainerAttribute>): NodeContainerAttribute--><!--Device-unnamed-export declare function NodeContainer(    style: CustomBuilderT<NodeContainerAttribute>): NodeContainerAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;\_\_\_MD\_LINK\_USD\_1\_\_\_&gt; | 是 | 用于设置NodeContainer属性的回调。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | NodeContainer属性实例。 |

