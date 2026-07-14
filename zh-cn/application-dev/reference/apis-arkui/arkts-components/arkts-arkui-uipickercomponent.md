# UIPickerComponent

UIPickerComponent容器是用于实现用户选择操作的组件。它支持从一组有限的选项中让用户进行单选，可应用于时间选择、日期选择、
地区选择、状态选择等多种场景。UIPickerComponent容器的显示效果为立体滚轮样式，支持选项按需定制，包括文本类型、图片类型
和图文组合类型。

说明：

- UIPickerComponent容器默认选项行高为40vp，默认显示7个选项。可通过
  [itemHeight]{@link UIPickerComponentAttribute#itemHeight}和
  [displayedItemCount]{@link UIPickerComponentAttribute#displayedItemCount}属性进行配置。
  由于显示效果为立体滚轮样式，因此除选中项外的其他选项会进行不同角度的旋转，实际的可视高度会小于选项行高。

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


## UIPickerComponent

```TypeScript
UIPickerComponent(options?: UIPickerComponentOptions)
```

创建UIPickerComponent容器，其选中项由options参数中的selectedIndex属性值决定。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | UIPickerComponentOptions | 否 | 配置UIPickerComponent容器的参数。参数缺省时组件占位，但内容显示为空。 |

## 汇总

- [PickerIndicatorStyle](arkts-arkui-uipickercomponent-pickerindicatorstyle-i.md)
- [UIPickerComponentOptions](arkts-arkui-uipickercomponent-uipickercomponentoptions-i.md)
- [OnUIPickerComponentCallback](arkts-arkui-uipickercomponent-onuipickercomponentcallback-t.md)
- [PickerIndicatorType](arkts-arkui-uipickercomponent-pickerindicatortype-e.md)
