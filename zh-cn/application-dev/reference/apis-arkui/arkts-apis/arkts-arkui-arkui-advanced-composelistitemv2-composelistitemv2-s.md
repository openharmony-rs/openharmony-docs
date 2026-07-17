# ComposeListItemV2

该组件用于展示一系列宽度相同的列表项，适用于展示连续、多行的同类数据组合（如图片与文本）。

该组件基于[状态管理（V2）](../../../../ui/state-management/arkts-state-management-overview.md#状态管理v2)实现，相较于[状态管理（V1）](../../../../ui/state-management/arkts-state-management-overview.md#状态管理v1)，状态管理（V2）增强了对数据对象的深度观察与管理能力，不再局限于组件层级。借助状态管理（V2），开发者可以通过该组件更灵活地控制列表项的数据和状态，实现更高效的用户界面刷新。

> **说明:**  
>  
> - 该组件仅可在Stage模型下使用。  
>  
> - 如果ComposeListItemV2设置[通用属性](./@internal/component/ets/common)和  
> [通用事件](./@internal/component/ets/common)，编译工具链会额外生成节点__Common__，并将通用属性或通用事件挂载在__Common__上，而不是直接应用到  
> ComposeListItemV2本身。这可能导致开发者设置的通用属性或通用事件不生效或不符合预期，因此，不建议ComposeListItemV2设置通用属性和通用事件。

**起始版本：** 26.0.0

<!--Device-unnamed-export declare struct ComposeListItemV2--><!--Device-unnamed-export declare struct ComposeListItemV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { OperateCheckV2Options, ComposeListItemV2, IconTypeV2, OperateIconV2, OperateCheckV2, OperateItemV2, OperateItemV2Options, OperateIconV2Options, OperateButtonV2, OperateButtonV2Options, ContentItemV2, ContentItemV2Options } from '@kit.ArkUI';
```

## contentItemV2

```TypeScript
contentItemV2?: ContentItemV2
```

定义列表项左侧以及中间元素。

**类型：** ContentItemV2

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ComposeListItemV2-contentItemV2?: ContentItemV2--><!--Device-ComposeListItemV2-contentItemV2?: ContentItemV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## operateItemV2

```TypeScript
operateItemV2?: OperateItemV2
```

定义列表项右侧元素。

**类型：** OperateItemV2

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ComposeListItemV2-operateItemV2?: OperateItemV2--><!--Device-ComposeListItemV2-operateItemV2?: OperateItemV2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

