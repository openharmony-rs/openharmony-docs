# ChipGroupV2Items

ChipGroupV2Items定义了芯片组项的数组类，继承自Array<[ChipGroupV2Item](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2item-c.md)>。

**继承/实现关系：** ChipGroupV2Items extends [Array<ChipGroupV2Item>](Array<ChipGroupV2Item>)

**起始版本：** 26.0.0

<!--Device-unnamed-export declare class ChipGroupV2Items extends Array<ChipGroupV2Item>--><!--Device-unnamed-export declare class ChipGroupV2Items extends Array<ChipGroupV2Item>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { ChipGroupV2ItemConfig, ChipGroupV2ItemStyleConfig, ChipGroupV2SpaceConfig, ChipGroupV2IconGroupSuffix, ChipGroupV2Items, ChipGroupV2Padding, ChipGroupV2Item, ChipGroupV2ItemStyle, ChipGroupV2, ChipGroupV2PaddingConfig, ChipGroupV2IconItemConfig, ChipGroupV2SymbolItemConfig, ChipGroupV2Space } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(items: ChipGroupV2ItemConfig[])
```

ChipGroupV2Items的构造函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipGroupV2Items-constructor(items: ChipGroupV2ItemConfig[])--><!--Device-ChipGroupV2Items-constructor(items: ChipGroupV2ItemConfig[])-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| items | [ChipGroupV2ItemConfig](arkts-arkui-arkui-advanced-chipgroupv2-chipgroupv2itemconfig-i.md)[] | 是 | 芯片组项配置数组。 |

