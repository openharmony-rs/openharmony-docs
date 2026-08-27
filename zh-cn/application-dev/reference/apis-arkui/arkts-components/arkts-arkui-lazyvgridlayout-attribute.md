# LazyVGridLayout属性/事件

除支持通用属性外，还支持以下属性：除支持通用事件外，还支持以下事件：

**继承/实现关系：** LazyVGridLayoutAttribute extends LazyGridLayoutAttribute<LazyVGridLayoutAttribute>

**起始版本：** 19

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## columnsTemplate

```TypeScript
columnsTemplate(value: string)
```

设置当前网格布局列的数量、固定列宽或最小列宽值，不设置时默认1列。例如，'1fr&nbsp;1fr&nbsp;2fr'&nbsp;表示将父组件分为3列，将父组件允许的宽度分为4等份，第一列占1份，第二列占1份，第三列占2份。columnsTemplate('repeat(auto-fit, track-size)')是设置最小列宽值为track-size，自动计算列数和实际列宽。columnsTemplate('repeat(auto-fill, track-size)')是设置固定列宽值为track-size，自动计算列数。columnsTemplate('repeat(auto-stretch, track-size)')是设置固定列宽值为track-size，使用 columnsGap作为最小列间距，自动计算列数和实际列间 距。其中repeat、auto-fit、auto-fill、auto-stretch为关键字。track-size为列宽，支持的单位包括px、vp、%或有效数字，默认单位为vp，track-size至少包括一个有效列宽。auto-fit模式和auto-stretch模式只支持track-size为一个有效列宽值，并且auto-stretch模式中的track-size只支持px、vp和有效数字，不支持%。auto-fill模式支持一个或多个有效列 宽，如columnsTemplate('repeat(auto-fill, 20)')、columnsTemplate('repeat(auto-fill, 20 80px)')。使用效果可以参考[示例3](../../../reference/apis-arkui/arkui-ts/ts-container-lazyvgridlayout.md#示例3设置自适应列数)。设置为'0fr'时，该列的列宽为0，不显示子组件。设置为其他非法值时，子组件显示为固定1列。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string | 是 | 当前网格布局列的数量、固定列宽或最小列宽值。 |
