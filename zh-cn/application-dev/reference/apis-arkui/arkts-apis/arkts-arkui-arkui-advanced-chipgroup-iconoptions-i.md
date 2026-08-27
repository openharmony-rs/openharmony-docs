# IconOptions

IconOptions定义图标的通用属性。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { IconOptions, LabelOptions as ChipItemLabelOptions, ChipGroupItemOptions, ChipItemStyle, ChipGroupSpaceOptions, IconItemOptions, IconGroupSuffix, ChipGroup, SuffixImageIconOptions, SymbolItemOptions } from '@kit.ArkUI';
```

## size

```TypeScript
size?: SizeOptions
```

图标大小，不支持百分比。当需要自定义图标尺寸时设置此参数。默认值：  
- ChipItemStyle.size为ChipSize.SMALL时，默认值为：{width: \$r('sys.float.chip_small_icon_size'), height: \$r('  
sys.float.chip_small_icon_size')}  
- 其他情况下，默认值为：{width: \$r('sys.float.chip_normal_icon_size'), height: \$r('sys.float.chip_normal_icon_size')}  
值为undefined时，按默认值处理。

**类型：** [SizeOptions](arkts-arkui-sizeoptions-i.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## src

```TypeScript
src: ResourceStr
```

图标图片或图片地址引用请参考Image。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
