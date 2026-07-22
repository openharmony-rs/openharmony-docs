# ChipGroupV2Padding

ChipGroupV2Padding定义了ChipGroupV2的上下内边距，用于控制其整体高度。

**起始版本：** 26.0.0

**装饰器类型：** @ObservedV2

<!--Device-unnamed-export declare class ChipGroupV2Padding--><!--Device-unnamed-export declare class ChipGroupV2Padding-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { ChipGroupV2ItemConfig, ChipGroupV2ItemStyleConfig, ChipGroupV2SpaceConfig, ChipGroupV2IconGroupSuffix, ChipGroupV2Items, ChipGroupV2Padding, ChipGroupV2Item, ChipGroupV2ItemStyle, ChipGroupV2, ChipGroupV2PaddingConfig, ChipGroupV2IconItemConfig, ChipGroupV2SymbolItemConfig, ChipGroupV2Space } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(config: ChipGroupV2PaddingConfig)
```

ChipGroupV2Padding的构造函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroupV2Padding-constructor(config: ChipGroupV2PaddingConfig)--><!--Device-ChipGroupV2Padding-constructor(config: ChipGroupV2PaddingConfig)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [ChipGroupV2PaddingConfig](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2paddingconfig-i.md) | 是 | 芯片组内边距配置。 |

## bottom

```TypeScript
public bottom: Length
```

ChipGroupV2的下方内边距（不支持百分比）。

默认值：14

单位：vp

值为undefined时，按默认值处理。

**类型：** Length

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroupV2Padding-public bottom: Length--><!--Device-ChipGroupV2Padding-public bottom: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## top

```TypeScript
public top: Length
```

ChipGroupV2的上方内边距（不支持百分比）。

默认值：14

单位：vp

值为undefined时，按默认值处理。

**类型：** Length

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroupV2Padding-public top: Length--><!--Device-ChipGroupV2Padding-public top: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

