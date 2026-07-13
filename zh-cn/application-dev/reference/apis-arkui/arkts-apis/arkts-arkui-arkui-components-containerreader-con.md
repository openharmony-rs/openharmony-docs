# 常量

## ContainerReader

```TypeScript
export declare const ContainerReader: ContainerReaderInterface
```

ContainerReader是容器断点组件，用于在动态场景下根据容器尺寸获取断点信息并进行响应式布局。该组件通过[双向绑定](../../../../ui/state-management/arkts-new-binding.md#系统组件参数双向绑定)实时返回容器的尺寸和断点，使开发者能够基于容器大小进行差异化的组件创建和布局。

> **说明：**

> - 使用ContainerReader时，ContainerReader父组件不要依赖其子组件确定自身尺寸。
>
> - 容器断点基于组件自身的实际尺寸和断点阈值数组确定高度和宽度断点值，组件尺寸和断点信息仅作用于当前组件及其子组件，同一页面中的多个容器可拥有各自独立的断点状态。
>
> - ContainerReader组件的尺寸需要由父容器和自身布局确定，不受子组件影响。在不同父容器下的布局规格：父容器为[Flex](../../../../reference/apis-arkui/arkui-ts/ts-container-flex.md)、[Column](../../../../reference/apis-arkui/arkui-ts/ts-container-column.md)、[Row](../../../../reference/apis-arkui/arkui-ts/ts-container-row.md)时撑满容器剩余空间；父容器为其他类型时撑满父容器。
>
> - ContainerReader接口的参数必须使用状态变量结合双向绑定形式([!!语法](../../../../ui/state-management/arkts-new-binding.md))，以便在后端计算尺寸变化时及时通知前端刷新UI。
>
> - 更多关于容器断点的开发指导和完整示例，可参考[容器断点 (ContainerReader)](../../../../ui/arkts-layout-development-container-reader.md)。

###### 子组件

可以包含子组件。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ContainerReaderInstance

```TypeScript
export declare const ContainerReaderInstance: ContainerReaderAttribute
```

定义ContainerReader组件实例。提供对ContainerReader组件方法的访问，用于容器尺寸分析和断点检测。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

