# PopupV2

## 导入模块

```TypeScript
import { PopupV2Button, PopupV2, PopupV2InitInfo } from '@kit.ArkUI';
```

## PopupV2

```TypeScript
export declare function PopupV2(options: PopupV2InitInfo): void
```

PopupV2用于显示特定样式的气泡。

该组件基于[状态管理（V2）](../../../ui/state-management/arkts-state-management-overview.md#状态管理v2)实现，相较于[状态管理（V1）](../../../ui/state-management/arkts-state-management-overview.md#状态管理v1)，状态管理（V2）增强了对数据对象的深度观察与管理能力，不再局限于组件层级。借助状态管理（V2），开发者可以通过该组件更灵活地控制显示特定样式的气泡，实现更高效的用户界面刷新。

**起始版本：** 26.0.0

**装饰器类型：** @Builder

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-export declare function PopupV2(options: PopupV2InitInfo): void--><!--Device-unnamed-export declare function PopupV2(options: PopupV2InitInfo): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [PopupV2InitInfo](arkts-arkui-arkui-advanced-popupv2-popupv2initinfo-i.md) | 是 | 定义PopupV2组件的配置参数。 |

