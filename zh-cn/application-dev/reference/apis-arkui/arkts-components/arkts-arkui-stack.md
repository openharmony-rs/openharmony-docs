# Stack

堆叠容器，子组件按照顺序依次入栈，后一个子组件覆盖前一个子组件。

> **说明：**

> - 通用属性[align]{@link CommonMethod#align(value: Alignment)}在该组件上支持镜像能力。


## Stack

```TypeScript
Stack(options?: StackOptions)
```

堆叠容器，子组件按照顺序依次入栈，后一个子组件覆盖前一个子组件。

> **说明：**
>
> 过多的组件嵌套会导致性能劣化。在部分场景中，直接使用组件属性或借助系统API的能力可以替代层叠容器的效果，减少了嵌套组件数进而优化性能。最佳实践请参考
> [组件嵌套优化-优先使用组件属性代替嵌套组件](https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-component-nesting-optimization#section78181114123811)。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | StackOptions | 否 | 设置子组件在容器内的对齐方式。 |

## 汇总

- [StackOptions](arkts-arkui-stack-stackoptions-i.md)
