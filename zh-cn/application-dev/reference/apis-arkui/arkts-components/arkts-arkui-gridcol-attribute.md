# GridCol属性/事件

除支持通用属性外，还支持以下属性：支持通用事件。

**继承/实现关系：** GridColAttribute extends CommonMethod<GridColAttribute>

**起始版本：** 9

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## gridColOffset

```TypeScript
gridColOffset(value: number | GridColColumnOption)
```

设置栅格子组件相对于原本位置偏移的列数。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| [GridColColumnOption](arkts-arkui-gridcolcolumnoption-i.md) | 是 | 相对于原本位置偏移的列数。gridColOffset为0表示不偏移。 取值为非负整数，默认值为0。 非法值：按默认值处理。    **说明：** 该属性具有断点继承性，详见 [GridColOptions对象说明](../../../reference/apis-arkui/arkui-ts/ts-container-gridcol.md#gridcoloptions对象说明)。 |

## order

```TypeScript
order(value: number | GridColColumnOption)
```

设置栅格子组件的序号，根据序号从小到大对栅格子组件进行排序。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| [GridColColumnOption](arkts-arkui-gridcolcolumnoption-i.md) | 是 | 元素序号，根据栅格子组件的序号从小到大排序。 取值为非负整数，默认值为0。 非法值：按默认值处理。    **说明：** 该属性具有断点继承性，详见 [GridColOptions对象说明](../../../reference/apis-arkui/arkui-ts/ts-container-gridcol.md#gridcoloptions对象说明)。 |

## span

```TypeScript
span(value: number | GridColColumnOption)
```

设置栅格子组件占用列数。调用成功后，栅格子组件将按照设置的列数占据相应宽度的栅格区域。span为0表示该元素不参与布局计算，即不会被渲染。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| [GridColColumnOption](arkts-arkui-gridcolcolumnoption-i.md) | 是 | 占用列数。span为0表示该元素不参与布局计算，即不会被渲染。 取值为非负整数，默认值为1。 非法值：按默认值处理。    **说明：** 该属性具有断点继承性，详见 [GridColOptions对象说明](../../../reference/apis-arkui/arkui-ts/ts-container-gridcol.md#gridcoloptions对象说明)。API version 20之后，默认值继承规则有变化，详见[GridColColumnOption](arkts-arkui-gridcolcolumnoption-i.md)。 |
