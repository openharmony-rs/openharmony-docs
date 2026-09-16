# Flex

Flex是以弹性方式布局子组件的容器组件，能够高效地排列、对齐子元素并分配剩余空间。

具体指南请参考[弹性布局](../../../ui/arkts-layout-development-flex-layout.md)。

> **说明：** > > - Flex组件在渲染时存在二次布局过程，因此在对性能有严格要求的场景下建议使用Column、Row代替。最佳实践请参考布局优化指导-合理使用布局组件。 > > - Flex组件主轴不设置长度时默认撑满父容器，如果包含设置position的子组件，此时Flex组件不会撑满父容器。Column、 > Row组件主轴不设置长度时默认跟随子节点大小。 > > - Flex、Column、Row组件在没有子节点且不设置宽高时，默认宽高为-1。 > > - 主轴长度可设置为auto使Flex自适应子组件布局，自适应时，Flex长度受constraintSize属性以及父容器传递的最大最小长度限制，且 > constraintSize属性优先级更高。

## 子组件

可以包含子组件。

## Flex

```TypeScript
Flex(value?: FlexOptions)
```

创建Flex布局容器，用于以弹性方式排列、对齐子组件并分配剩余空间。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [FlexOptions](arkts-arkui-flexoptions-i.md) | 否 | Flex容器的配置选项，用于设置子组件的排列方向、换行方式、对齐方式和间距。不传入时使用默认配置，各属性默认值详见[FlexOptions](arkts-arkui-flexoptions-i.md)对象说明。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [FlexOptions](arkts-arkui-flexoptions-i.md) | 设置Flex子组件的排列对齐方式。 |
| [FlexSpaceOptions](arkts-arkui-flexspaceoptions-i.md) | 设置Flex容器的子组件在主轴或交叉轴的间距。 |

## 示例

```TypeScript
### 示例1（子组件排列方向）

该示例通过设置direction实现不同的子组件排列方向效果。


```

```TypeScript
### 示例2（子组件单/多行排列）

该示例通过设置wrap实现子组件单行或多行的排列效果。


```

```TypeScript
### 示例3（子组件在主轴上的对齐格式）

该示例通过设置justifyContent实现子组件在主轴上不同的对齐效果。


```

```TypeScript
### 示例4（子组件在交叉轴上的对齐方式）

该示例通过设置alignItems实现子组件在交叉轴上的不同的对齐效果。


```

```TypeScript
### 示例5（多行内容的对齐方式）

该示例通过设置alignContent实现多行内容的不同对齐效果。


```

```TypeScript
### 示例6（子组件单/多行排列时的主/交叉轴间距）

该示例通过设置space属性，为单/多行排列的子组件设置主轴和交叉轴上的间距。


```

```TypeScript
### 示例7（宽度自适应的Flex容器）

该示例实现了Flex在宽度设置auto后可以自适应子组件布局的能力。
```
