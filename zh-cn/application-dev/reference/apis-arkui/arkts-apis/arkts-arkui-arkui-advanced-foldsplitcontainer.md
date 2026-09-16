# @ohos.arkui.advanced.FoldSplitContainer(Defines FoldSplitContainer component.)

## 导入模块

```TypeScript
import { ExtraRegionPosition, ExpandedRegionLayoutOptions, HoverModeRegionLayoutOptions, FoldedRegionLayoutOptions, PresetSplitRatio, FoldSplitContainer, HoverModeStatus, OnHoverStatusChangeHandler, } from '@kit.ArkUI';
```

## 汇总

### 结构体

| 名称 | 说明 |
| --- | --- |
| [FoldSplitContainer](arkts-arkui-arkui-advanced-foldsplitcontainer-foldsplitcontainer-s.md) | FoldSplitContainer分栏布局，实现折叠屏二分栏、三分栏在展开态（设备完全展开状态）、悬停态（设备半折叠状态）以及折叠态（设备完全折叠状态）的区域控制。适用于折叠屏应用的响应式布局适配场景，可帮助开发者实现多屏状态下的智能分栏布局，提升用户体验。折叠状态详情可参考[display.FoldStatus](arkts-arkui-display-foldstatus-e.md)。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ExpandedRegionLayoutOptions](arkts-arkui-arkui-advanced-foldsplitcontainer-expandedregionlayoutoptions-i.md) | 展开态布局信息。 |
| [FoldedRegionLayoutOptions](arkts-arkui-arkui-advanced-foldsplitcontainer-foldedregionlayoutoptions-i.md) | 折叠态布局信息。 |
| [HoverModeRegionLayoutOptions](arkts-arkui-arkui-advanced-foldsplitcontainer-hovermoderegionlayoutoptions-i.md) | 悬停态布局信息。 |
| [HoverModeStatus](arkts-arkui-arkui-advanced-foldsplitcontainer-hovermodestatus-i.md) | 设备或应用的折叠、悬停、旋转、窗口状态信息。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ExtraRegionPosition](arkts-arkui-arkui-advanced-foldsplitcontainer-extraregionposition-e.md) | 扩展区域位置信息。 |
| [PresetSplitRatio](arkts-arkui-arkui-advanced-foldsplitcontainer-presetsplitratio-e.md) | 区域比例。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [OnHoverStatusChangeHandler](arkts-arkui-onhoverstatuschangehandler-t.md) | 悬停状态变化事件处理器。 |

## 示例

```TypeScript
### 示例1（设置二分栏）

该示例实现了折叠屏二分栏在展开态、悬停态以及折叠态的区域控制。
```

```TypeScript
### 示例2（设置三分栏）

该示例实现了折叠屏三分栏在展开态、悬停态以及折叠态的区域控制。
```

```TypeScript
### 示例3（展示FoldSplitContainer折叠态、悬停态、展开态下的配置行为）

该示例通过[ExpandedRegionLayoutOptions](arkts-arkui-arkui-advanced-foldsplitcontainer-expandedregionlayoutoptions-i.md)、[HoverModeRegionLayoutOptions](arkts-arkui-arkui-advanced-foldsplitcontainer-hovermoderegionlayoutoptions-i.md)和[FoldedRegionLayoutOptions](arkts-arkui-arkui-advanced-foldsplitcontainer-foldedregionlayoutoptions-i.md)分别配置折叠屏的展开态、悬停态和折叠态布局信息。示例提供交互式配置界面，用户可在各区域实时调整布局参数：主要区域（MajorRegion）用于配置折叠态参数，次要区域（MinorRegion）用于配置悬停态参数，扩展区域（ExtraRegion）用于配置展开态参数。这些区域使用封装的区域组件Region实现，其中RadioOptions为封装的切换单选框组件，SwitchOption为封装的切换开关组件。示意图展示了不同参数配置下的多种布局效果。
```
