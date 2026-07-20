# Flex

Flex是以弹性方式布局子组件的容器组件，能够高效地排列、对齐子元素并分配剩余空间。

具体指南请参考[弹性布局](docroot://ui/arkts-layout-development-flex-layout.md)。

> **说明：**

> - Flex组件在渲染时存在二次布局过程，因此在对性能有严格要求的场景下建议使用[Column]{@link column}、[Row]{@link row}代替。最佳实践请参考
> [布局优化指导-合理使用布局组件](https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-improve-layout-performance#section12745188175420)。
>
> - Flex组件主轴不设置长度时默认撑满父容器，如果包含设置[position]{@link CommonMethod#position}的子组件，此时Flex组件不会撑满父容器。[Column]{@link column}、
> [Row]{@link row}组件主轴不设置长度时默认跟随子节点大小。
>
> - Flex、Column、Row组件在没有子节点且不设置宽高时，默认宽高为-1。
>
> - 主轴长度可设置为auto使Flex自适应子组件布局，自适应时，Flex长度受[constraintSize]{@link CommonMethod#constraintSize}属性以及父容器传递的最大最小长度限制，且
> constraintSize属性优先级更高。

## 子组件

可以包含子组件。

## Flex

```TypeScript
Flex(value?: FlexOptions)
```

Flex布局容器。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-FlexInterface-(value?: FlexOptions): FlexAttribute--><!--Device-FlexInterface-(value?: FlexOptions): FlexAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [FlexOptions](arkts-arkui-flexoptions-i.md) | 否 | 弹性布局子组件参数。  |

## 汇总

- [FlexOptions](arkts-arkui-flex-flexoptions-i.md)
- [FlexSpaceOptions](arkts-arkui-flex-flexspaceoptions-i.md)
