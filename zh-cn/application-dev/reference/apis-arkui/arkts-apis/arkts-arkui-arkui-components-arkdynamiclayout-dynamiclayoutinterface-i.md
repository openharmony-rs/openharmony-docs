# DynamicLayoutInterface

动态布局容器组件，支持在运行时动态切换不同的布局算法，不改变子组件的状态。 > **说明：**

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

<!--Device-unnamed-export interface DynamicLayoutInterface--><!--Device-unnamed-export interface DynamicLayoutInterface-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
(algorithm: LayoutAlgorithm): DynamicLayoutAttribute
```

动态布局容器。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本24开始，该接口支持在ArkTS卡片中使用。

<!--Device-DynamicLayoutInterface-(algorithm: LayoutAlgorithm): DynamicLayoutAttribute--><!--Device-DynamicLayoutInterface-(algorithm: LayoutAlgorithm): DynamicLayoutAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| algorithm | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 指定动态布局组件的布局算法。取非法值时，按照[堆叠布局算法]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_布局子组件，子组件堆叠排列。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ |  |

