# Row

沿水平方向布局的容器。

> **说明：**

> Row未设置宽度或高度时，在主轴或交叉轴方向上自适应子组件大小。

## 子组件

可以包含子组件。

## Row

```TypeScript
Row(options?: RowOptions)
```

创建水平方向线性布局容器，可以设置子组件的间距。

> **说明：**  
>  
> 在复杂界面中使用多组件嵌套时，若布局组件的嵌套层数过深或嵌套的组件数量过多，将会产生额外开销。建议通过移除冗余节点、利用布局边界减少布局计算、合理采用渲染控制语法及布局组件方法来优化性能。最佳实践请参考  
> [布局优化指导](https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-improve-layout-performance)。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-RowInterface-(options?: RowOptions): RowAttribute--><!--Device-RowInterface-(options?: RowOptions): RowAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [RowOptions](arkts-arkui-rowoptions-i.md) | 否 | 横向布局元素间距，支持设置number或string类型。 |

## Row

```TypeScript
Row(options?: RowOptions | RowOptionsV2)
```

创建水平方向线性布局容器，可以设置子组件的间距。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-RowInterface-(options?: RowOptions | RowOptionsV2): RowAttribute--><!--Device-RowInterface-(options?: RowOptions | RowOptionsV2): RowAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [RowOptions](arkts-arkui-rowoptions-i.md) \| RowOptionsV2 | 否 | 横向布局元素间距，支持设置number、string或Resource类型。  |

## 汇总

- [RowOptions](arkts-arkui-row-rowoptions-i.md)
- [RowOptionsV2](arkts-arkui-row-rowoptionsv2-i.md)
