# FlowItem

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zcdqs; @rongShao-Z; @guozejun-->
<!--Designer: @zcdqs-->
<!--Tester: @huchuyun-->
<!--Adviser: @Brilliantry_Rui-->

瀑布流组件[WaterFlow](ts-container-waterflow.md)的子组件，用来展示瀑布流具体item。


> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> * 该组件从API version 9开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
> * 仅支持作为[WaterFlow](ts-container-waterflow.md)组件的子组件使用。
> * 在滑动场景中，由于FlowItem及其子组件的频繁创建与销毁，建议将FlowItem中的组件封装为自定义组件，并使用@Reusable装饰器进行修饰，以增强组件的复用能力，从而减少ArkUI框架内部重复创建和销毁节点的开销。最佳实践请参考[优化瀑布流加载慢丢帧问题-组件复用](https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-waterflow-performance-optimization#section189041489339)。


## 子组件


支持单个子组件。


## 接口

FlowItem()

使用该接口来创建瀑布流子组件。

**原子化服务API（仅ArkTS-Dyn）：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS-Dyn起始版本：** 9

**ArkTS-Sta起始版本：** 23

## 属性

### attributeModifier<sup>23+</sup>

attributeModifier(modifier: AttributeModifier\<FlowItemAttribute> | AttributeModifier\<CommonMethod> | undefined)

动态设置FlowItem组件的属性方法。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**ArkTS模式：** 该接口仅适用于ArkTS-Sta。

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                         | 必填 | 说明                                                                                                                             |
| -------- | -------------------------------------------- | ---- | -------------------------------------------------------------------------------------------------------------------------------- |
| modifier | [AttributeModifier](./ts-universal-attributes-attribute-modifier.md#attributemodifiert)\<FlowItemAttribute> \| AttributeModifier\<CommonMethod> \| undefined | 是   | 在当前组件上，动态设置属性方法，支持使用if/else语法。<br/>CommonMethod：[通用属性](./ts-component-general-attributes.md)和[通用事件](./ts-component-general-events.md)。<br/>FlowItemAttribute：当前组件的[属性](#属性)。 |

## 示例

详见[瀑布流组件示例](ts-container-waterflow.md#示例)。