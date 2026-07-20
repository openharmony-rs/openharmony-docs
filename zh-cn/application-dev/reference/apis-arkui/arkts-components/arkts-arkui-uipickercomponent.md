# UIPickerComponent

UIPickerComponent容器是用于实现用户选择操作的组件。它支持从一组有限的选项中让用户进行单选，可应用于时间选择、日期选择、地区选
择、状态选择等多种场景。UIPickerComponent容器的显示效果为立体滚轮样式，支持选项按需定制，包括文本类型、图片类型和图文组合类型。

说明：

- UIPickerComponent容器默认选项行高为40vp，默认显示7个选项。可通过
  [itemHeight]{@link UIPickerComponentAttribute#itemHeight}和
  [displayedItemCount]{@link UIPickerComponentAttribute#displayedItemCount}属性进行配置。由于显示效果为立体滚轮样式，
  因此除选中项外的其他选项会进行不同角度的旋转，实际的可视高度会小于选项行高。

- UIPickerComponent容器的[height]{@link CommonMethod#height(value: Length)}建议设置为200vp。当设置的高度大于等于
  该建议值时，可完整显示默认的7个选项；若通过[displayedItemCount]{@link UIPickerComponentAttribute#displayedItemCount}或
  [itemHeight]{@link UIPickerComponentAttribute#itemHeight}配置了更多可见项或更大选项高度，建议相应增大组件高度。
  设置高度小于建议值时，显示范围会从上下边缘向中间裁剪，可显示的选项数量也会相应减少，始终保持选中项垂直居中。

- 当UIPickerComponent容器未设置[width]{@link CommonMethod#width(value: Length)}时，取当前视图中可见子组件的最大宽度作为容
  器宽度。建议为UIPickerComponent容器设置宽度，或为每个子组件设置相同宽度，以避免滑动过程中容器宽度动态发生变化，影响显示效果。

- UIPickerComponent容器的子组件的对齐方式固定为居中对齐，不支持通过[align]{@link CommonMethod#align(value: Alignment)}属性
  改变子组件的对齐方式。

- UIPickerComponent容器当前不支持智能手表设备。

- 该组件从API版本26.0.0开始支持[WithTheme]{@link with_theme}。

组件

- 支持多个子组件。
- 支持子组件类型：[Text]{@link text}、[Image]{@link image}、[Row]{@link row}和[SymbolGlyph]{@link symbolglyph}。
- 支持渲染控制类型：[if/else](docroot://ui/rendering-control/arkts-rendering-control-ifelse.md)和
[ForEach](docroot://ui/rendering-control/arkts-rendering-control-foreach.md)。

说明：

- 开发者在使用Row容器作为子组件时，Row容器中仅支持包含Text、Image、SymbolGlyph基础组件，包含其他容器组件可能会影响显示效果
  或滑动功能异常。

- 统计子组件的个数时，不包含Row容器内的子组件，Row容器及其子组件共同视为1个子组件。

- 子组件为Text、Image、SymbolGlyph时，[height]{@link CommonMethod#height(value: Length)}属性不生效，固定为40vp。

- 子组件为Row容器时，Row容器的[height]{@link CommonMethod#height(value: Length)}属性不生效，固定为40vp，Row容器内的子组件
 [height]{@link CommonMethod#height(value: Length)}属性能正常生效，最终显示效果由Row容器决定。

- 图文组合类型选项需要使用Row容器包含图片和文本组件。使用图文组合类型选项时，
  建议将图片的[height]{@link CommonMethod#height(value: Length)}设置为40vp及以下，避免图片较大时被裁剪。

- UIPickerComponent容器内所有文本组件（包括Row容器内的文本组件）的fontSize属性默认为20fp。用户设置将覆盖默认值，设置异常值时
  以文本组件[fontSize]{@link TextAttribute#fontSize}处理的结果为准。建议统一设置或不设置fontSize以保证良好的显示效果。


## UIPickerComponent

```TypeScript
UIPickerComponent(options?: UIPickerComponentOptions)
```

创建UIPickerComponent容器，其选中项由options参数中的selectedIndex属性值决定。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-UIPickerComponentInterface-(options?: UIPickerComponentOptions): UIPickerComponentAttribute--><!--Device-UIPickerComponentInterface-(options?: UIPickerComponentOptions): UIPickerComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [UIPickerComponentOptions](arkts-arkui-uipickercomponentoptions-i.md) | 否 | 配置UIPickerComponent容器的参数。参数缺省时组件占位，但内容显示为空。  |

## 汇总

- [PickerIndicatorStyle](arkts-arkui-uipickercomponent-pickerindicatorstyle-i.md)
- [UIPickerComponentOptions](arkts-arkui-uipickercomponent-uipickercomponentoptions-i.md)
- [OnUIPickerComponentCallback](arkts-arkui-uipickercomponent-onuipickercomponentcallback-t.md)
- [PickerIndicatorType](arkts-arkui-uipickercomponent-pickerindicatortype-e.md)
