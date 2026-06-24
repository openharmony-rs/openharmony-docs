# @ohos.arkui.advanced.ChipGroup

## 汇总

### 结构体

| 名称 | 说明 |
| --- | --- |
| [ChipGroup](arkts-arkui-chipgroup-s.md) | &gt; **说明：**<br/>&gt;<br/>&gt; 1. 针对`selectedIndexes`和`multiple`接口，当`multiple`等于`false`时，如果没有传入`selectedIndexes`，默认是第一个Chip被选中，如果传入的<br/>&gt; `selectedIndexes`有一个以上的元素时，默认第一个索引的Chip被选中。<br/>&gt;<br/>&gt; 2. 使用suffix接口时，需引入IconGroupSuffix接口，若不传入，suffix将为空。<br/>&gt;<br/>&gt; 3. 图标填充色（`fillColor`和`activedFillColor`）的设置应与字体颜色（`fontColor`）保持一致。如果需要设置不同的颜色，可以在传入<br/>&gt; `[ChipGroupSpaceOptions](#chipgroupspaceoptions)`时使用`prefixSymbol`。<br/> |
| [IconGroupSuffix](arkts-arkui-icongroupsuffix-s.md) | &gt; **说明：**<br/>&gt;<br/>&gt; 传参SymbolGlyphModifier时，不支持使用symbolEffect修改动效类型和[effectStrategy](SymbolGlyphAttribute#effectStrategy)设置动效。<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ChipGroupItemOptions](arkts-arkui-chipgroupitemoptions-i.md) | ChipGroupItemOptions定义每个Chip的非通用属性。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 当传入`suffixIcon`参数时，`allowClose`不生效；未传入`suffixIcon`参数时，`allowClose`决定是否显示移除图标。<br/> |
| [ChipGroupPaddingOptions](arkts-arkui-chipgrouppaddingoptions-i.md) | ChipGroupPaddingOptions定义了ChipGroup的上下内边距，用于控制其整体高度。<br/> |
| [ChipGroupSpaceOptions](arkts-arkui-chipgroupspaceoptions-i.md) | ChipGroupSpaceOptions 定义了ChipGroup左右内边距，以及Chip与Chip之间的间距。<br/> |
| [ChipItemStyle](arkts-arkui-chipitemstyle-i.md) | ChipItemStyle定义了Chip的共通属性。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 1. 操作块的大小有两种类型，一种是ChipSize，提供NORMAL和SMALL两种尺寸供选择；另一种是SizeOptions。<br/>&gt;<br/>&gt; 2. backgroundColor、selectedBackgroundColor传入undefined时，显示默认背景颜色，传入非法值时，背景色透明。<br/> |
| [IconItemOptions](arkts-arkui-iconitemoptions-i.md) | 定义了尾部builder接口，针对背板大小及颜色设置限制。<br/> |
| [IconOptions](arkts-arkui-iconoptions-i.md) | IconOptions定义图标的共通属性。<br/> |
| [LabelOptions](arkts-arkui-labeloptions-i.md) | Label定义图标属性。<br/> |
| [SuffixImageIconOptions](arkts-arkui-suffiximageiconoptions-i.md) | 后缀图标选项的类型。<br/><br/>继承自[IconOptions](arkts-arkui-iconoptions-i.md#IconOptions)。<br/> |
| [SymbolItemOptions](arkts-arkui-symbolitemoptions-i.md) | ChipGroup的尾部图标选项类型。<br/> |

