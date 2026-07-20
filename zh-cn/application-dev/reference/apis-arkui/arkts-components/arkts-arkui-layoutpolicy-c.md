# LayoutPolicy

用于组件宽度和高度的布局策略。  
> **说明：**  
>  
> -LayoutPolicy支持设置三种布局策略：matchParent（自适应父组件布局）、wrapContent（根据内容自适应但不超过父组件尺寸的布局）和fixAtIdealSize（根据内容自适应，可能超过父组件尺寸的布局）。具体示例代码参见[设置布局策略](./ts-universal-attributes-size.md#示例5设置布局策略)。  
>  
> - wrapContent和fixAtIdealSize场景，组件无法通过内容确定大小时，如果组件大小有默认值，则按照默认值进行测算；如果没有默认值，则按照宽高(0,0)进行测算。  
>  
> -容器设置wrapContent，并且有子组件设置matchParent时（包括仅一边设置matchParent），容器先由确定大小的子组件撑大，设置matchParent的子组件再匹配容器大小；如果没有确定大小的子组件，容器和子组件大小均为0。  
>  
> - LayoutPolicy优先级低于constraintSize。  
>  
> - 从API version 15开始，仅Row和Column组件的width和height属性支持设置LayoutPolicy类型参数，其他组件设置LayoutPolicy类型参数后与不设置宽度或高度表现一致；从API version 20开始，所有基础组件均支持设置LayoutPolicy类型参数。  
>  
> -当Row、Column、Flex组件主轴尺寸自适应子组件，且子组件A仅交叉轴设置matchParent时，API版本26.0.0之前，子组件A不参与Row、Column、Flex组件的主轴尺寸测量过程，此时Row、Column、Fle x组件主轴方向不自适应子组件A的尺寸；从API版本26.0.0开始，子组件A会参与Row、Column、Flex组件的主轴尺寸测量过程，此时Row、Column、Flex组件主轴方向会自适应子组件A的尺寸。交叉轴方向同理。

**起始版本：** 15

<!--Device-unnamed-declare class LayoutPolicy--><!--Device-unnamed-declare class LayoutPolicy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fixAtIdealSize

```TypeScript
static readonly fixAtIdealSize: LayoutPolicy
```

当前组件自适应子组件（内容）时，其大小与子组件（内容）相等，并且其大小不受父组件内容区大小约束。

**类型：** LayoutPolicy

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本20开始，该接口支持在ArkTS卡片中使用。

<!--Device-LayoutPolicy-static readonly fixAtIdealSize: LayoutPolicy--><!--Device-LayoutPolicy-static readonly fixAtIdealSize: LayoutPolicy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## matchParent

```TypeScript
static readonly matchParent: LayoutPolicy
```

当前组件自适应父组件布局时，其大小与父组件内容区相等，不包括padding，border和safeAreaPadding。

**类型：** LayoutPolicy

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本15开始，该接口支持在ArkTS卡片中使用。

<!--Device-LayoutPolicy-static readonly matchParent: LayoutPolicy--><!--Device-LayoutPolicy-static readonly matchParent: LayoutPolicy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## wrapContent

```TypeScript
static readonly wrapContent: LayoutPolicy
```

当前组件自适应子组件（内容）时，其大小与子组件（内容）相等，并且其大小受父组件内容区大小约束。

**类型：** LayoutPolicy

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本20开始，该接口支持在ArkTS卡片中使用。

<!--Device-LayoutPolicy-static readonly wrapContent: LayoutPolicy--><!--Device-LayoutPolicy-static readonly wrapContent: LayoutPolicy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

