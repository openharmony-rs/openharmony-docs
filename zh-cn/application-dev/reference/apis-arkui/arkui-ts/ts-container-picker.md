# Picker
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @luoying_ace_admin-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @HelloCrease-->

Picker容器是立体滚轮样式选择器，通过子组件实现选项内容和样式的自定义，支持文本类型、图片类型和图文组合类型。

>  **说明：**
>
> - 本模块首批接口从API version 22开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - Picker容器的选择项行高固定40vp，最大显示7行。Picker容器的高度建议设置为200vp，当设置的高度大于等于该建议值时，可完全显示7个选择项；小于该建议值时，Picker容器的显示范围会从上下边缘向中间裁切，始终保持选中项在Picker容器的垂直方向上居中。
>
> - 当Picker容器未设置宽度时，取当前视图中可见子组件中最大的宽度为容器宽度。建议给Picker容器设置一个宽度，或者给每个子组件设置相同的宽度，避免滑动过程中Picker容器的宽度动态变化。
>
> - Picker容器中的子组件默认居中显示，可通过设置Picker容器的align属性改变子组件的对齐方式。

## 子组件

- 支持多个子组件。

- 支持子组件类型：[Text](./ts-basic-components-text.md)、[Image](./ts-basic-components-image.md)、[Row](./ts-container-row.md)和[SymbolGlyph](./ts-basic-components-symbolGlyph.md)。

- 支持渲染控制类型：[if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md)和[ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md)。

>  **说明：**
>
> - 建议开发者在使用Row容器作为子组件时，Row容器中只包含Text、Image、SymbolGlyph基础组件，避免包含其他容器组件。
>
> - 子组件为Text、Image、SymbolGlyph时，高度Height属性不生效，固定为40vp。子组件为Row容器时，高度Height属性不生效，固定为40vp，Row容器内的子组件高度Height属性能正常生效，最终显示效果由Row容器决定。
>
> - 图文组合类型选项需要使用Row容器包含图片和文本组件。使用图文组合类型选项时，建议将图片的高度设置为40vp及以下，避免图片较大时被裁剪。
>
> - Picker容器内所有的文本组件（包括在Row容器内的文本组件）的fontSize属性默认为20fp。若用户设置了fontSize，最终以用户设置为准。用户设置异常的fontSize时，以文本组件处理异常值的结果为准。为保证良好的显示效果，建议对文本组件统一不设置fontSize或者统一设置fontSize。


## 接口

Picker(options?: PickerOptions)

通过子组件创建Picker容器，其选中项由输入的索引值决定。

**原子化服务API：** 从API version 22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| options |  [PickerOptions](#pickeroptions对象说明)| 否 | Picker容器的参数。 |

## PickerOptions对象说明

Picker容器支持的参数。

**原子化服务API：** 从API version 22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| selectedIndex | number | 否 | 是 | 选中项的索引值。</br>取值范围：[0, 子组件的个数-1]。不在取值范围内时，使用默认值；设置小数时，使用向下取整后的整数。</br>默认值：0<br/>**说明：**统计子组件的个数时不包含Row容器内的子组件，Row容器及其子组件共同视为1个子组件。 |

## 属性

除支持[通用属性](ts-component-general-attributes.md)外，还支持以下属性：

### canLoop

canLoop(isLoop: Optional\<boolean>)

设置选项列是否可循环滚动。

**原子化服务API：** 从API version 22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型    | 必填 | 说明                                                         |
| ------ | ------- | ---- | ------------------------------------------------------------ |
| isLoop  | [Optional](ts-universal-attributes-custom-property.md#optionalt12)\<boolean> | 是   | 是否可循环滚动。<br/>- true：可循环。<br/>- false：不可循环。<br/>默认值：true<br/>当isLoop的值为undefined时，使用默认值。 |

### enableHapticFeedback

enableHapticFeedback(enable: Optional\<boolean>)

设置是否开启触控反馈。

**原子化服务API：** 从API version 22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型                                          | 必填  | 说明                                                                                  |
| ------ | --------------------------------------------- |-----|-------------------------------------------------------------------------------------|
| enable  | [Optional](ts-universal-attributes-custom-property.md#optionalt12)\<boolean> | 是   | 设置是否开启触控反馈。<br/>- true：开启触控反馈。<br/>- false：不开启触控反馈。<br/>默认值：true<br/>开启后，是否存在触控反馈取决于系统硬件支持情况。<br/>当enable的值为undefined时，使用默认值。|

>  **说明：**
>
>  开启触控反馈需在工程src/main/module.json5文件配置requestPermissions字段，开启振动权限，配置如下：
>  ```json
>  "requestPermissions": [
>  {
>   "name": "ohos.permission.VIBRATE",
>  }
>  ]
>  ```

### selectionIndicator

selectionIndicator(style: Optional\<PickerIndicatorStyle>)

该接口用于设置选中项指示器的样式。

**原子化服务API：** 从API version 22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型                                                         | 必填 | 说明                                                         |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| style  | [Optional](ts-universal-attributes-custom-property.md#optionalt12)\<[PickerIndicatorStyle](ts-container-picker.md#pickerindicatorstyle)> | 是   | 设置选中项指示器的样式。|

## 事件

除支持[通用事件](ts-component-general-events.md)外，还支持以下事件：

### onChange

onChange(callback: Optional\<OnPickerCallback>)

滑动选择器选项时，当选项有超过一半的区域进入分割线区域内（即该选项在分割线区域内的高度超过选中项高度的一半）时，触发该回调。

**原子化服务API：** 从API version 22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型                                       | 必填 | 说明                                              |
| ------ | ------------------------------------------ | ---- | ------------------------------------------------- |
| callback  | [Optional](ts-universal-attributes-custom-property.md#optionalt12)\<[OnPickerCallback](#onpickercallback)> | 是   | 当选中项发生变化时触发的回调函数。<br/>当callback的值为undefined时，不使用回调函数。 |

### onScrollStop

onScrollStop(callback: Optional\<OnPickerCallback>)

选择器滑动停止时触发该事件。

**原子化服务API：** 从API version 22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型                                       | 必填 | 说明                                              |
| ------ | ------------------------------------------ | ---- | ------------------------------------------------- |
| callback | [Optional](ts-universal-attributes-custom-property.md#optionalt12)\<[OnPickerCallback](#onpickercallback)> | 是   | 当选择器滑动停止时触发的回调函数。<br/>当callback的值为undefined时，不使用回调函数。 |

## PickerIndicatorType枚举说明

设置选中项指示器的类型。

**原子化服务API：** 从API version 22开始，该类型支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 值 | 说明 |
| -------- | - |-------- |
| BACKGROUND | 0 | 通过添加背景色，标识选中项。|
| DIVIDER | 1 | 通过上下分割线，标识选中项。|

## PickerIndicatorStyle

选中项指示器的配置样式。

**原子化服务API：** 从API version 22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称  | 类型   | 只读 | 可选 | 说明                                       |
| ----- | ------ | ---- | ---- | ------------------------------------------ |
| type  | [PickerIndicatorType](#pickerindicatortype枚举说明) | 否   | 否   | 选中项指示器的类型。<br/>默认值：PickerIndicatorType.BACKGROUND |
| strokeWidth |  [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)      | 否   | 是   | 分割线的粗细。<br/>默认值：2.0px<br/>单位：默认为vp，也可指定单位为px。<br/>取值范围：[0, +∞)，strokeWidth小于0时使用默认值。不支持“百分比”类型。<br/>**说明：**<br/>当type为PickerIndicatorType.DIVIDER时生效。 |
| dividerColor       | [ResourceColor](ts-types.md#resourcecolor) | 否   | 是   | 分割线的颜色。<br/>默认值：'sys.color.comp_divider'<br/>**说明：**<br/>当type为PickerIndicatorType.DIVIDER时生效。 |
| startMargin |  [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)       | 否   | 是   | 分割线与Picker容器侧边起始端的距离。<br/>默认值：0<br/>单位：默认为vp，也可指定单位为px。<br/>取值范围：startMargin与endMargin之和不得超过Picker容器的宽度。设置小于0或startMargin与endMargin之和超过Picker容器的宽度时，使用默认值。不支持“百分比”类型。<br/>**说明：**<br/>当type为PickerIndicatorType.DIVIDER时生效。 |
| endMargin   |  [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)        | 否   | 是   | 分割线与Picker容器侧边结束端的距离。<br/>默认值：0<br/>单位：默认为vp，也可指定单位为px。<br/>取值范围：startMargin与endMargin之和不得超过Picker容器的宽度。设置小于0或startMargin与endMargin之和超过Picker容器的宽度时，使用默认值。不支持“百分比”类型。<br/>**说明：**<br/>当type为PickerIndicatorType.DIVIDER时生效。 |
| backgroundColor  | [ResourceColor](ts-types.md#resourcecolor) | 否  | 是  | 选中项的背景颜色。<br/>默认值：'sys.color.comp_background_tertiary'<br/>**说明：**<br/>当type为PickerIndicatorType.BACKGROUND时生效。   |
| borderRadius  | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) &nbsp;\|&nbsp; [BorderRadiuses](ts-types.md#borderradiuses9) &nbsp;\|&nbsp; [LocalizedBorderRadiuses](ts-types.md#localizedborderradiuses12) | 否  | 是  | 选中项的边框圆角半径。<br/>默认值：LengthMetrics{ value:12, unit:LengthUnit.vp }，即四个圆角半径均为12vp。<br/>取值范围：取选中项的宽和高之中较小的边长为x（单位：vp），取值范围为[0, x/2]（单位：vp）。当取值小于0时，使用默认值；当取值大于最大值时，使用最大值。<br/>**说明：**<br/>1. 当type为PickerIndicatorType.BACKGROUND时生效。<br/>2. [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)类型的value参数同时作用于四个圆角半径大小，unit参数用于设置单位。<br/>3. [BorderRadiuses](ts-types.md#borderradiuses9)类型可以设置四个不同值的圆角半径，所有单位固定为vp。<br/>4. [LocalizedBorderRadiuses](ts-types.md#localizedborderradiuses12)类型可以设置四个不同值的圆角半径，并且可以单独设置每个圆角的单位。 |

## OnPickerCallback

type OnPickerCallback = (selectedIndex: number) => void

定义触发[onChange](#onchange)事件、[onScrollStop](#onscrollstop)事件的回调类型。

**原子化服务API：** 从API version 22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名     | 类型                                       | 必填 | 说明                                                         |
| ---------- | ------------------------------------------ | ---- | ------------------------------------------------------------ |
| selectedIndex | number | 是   | 当前选中项的索引值。</br>取值范围：[0, 子组件的个数-1]内的整数。 |

## 示例

### 示例1（自定义月份选择器）

从API version 22开始，该示例通过Picker容器包含文本子组件实现月份选择器。


```ts
// xxx.ets
@Entry
@Component
struct PickerExample {
  private fontSize: number | string | Resource = '20vp';
  private monthArray: string[] = [];

  aboutToAppear(): void {
    // 构造选择项数据
    for (let i = 1; i <= 12; i++) {
      this.monthArray.push(i + '月')
    }
  }

  build() {
    Row() {
      Picker() {
        ForEach(this.monthArray, (item: string) => {
          Text(item)
            .fontSize(this.fontSize)
            .textAlign(TextAlign.Center)
            .fontColor(Color.Black)
        })
      }
      // 配置选项列表循环
      .canLoop(true)
      // 配置触控音振反馈为关闭
      .enableHapticFeedback(false)
      // 配置选中项的指示器标识为分割线
      .selectionIndicator({ type: PickerIndicatorType.DIVIDER })
      // 订阅选中项改变事件
      .onChange((idx: number) => {
        console.info('Picker item changed:' + this.monthArray[idx])
      })
      // 订阅滑动停止事件
      .onScrollStop((idx: number) => {
        console.info('Picker scroll stopped: ' + this.monthArray[idx])
      })
    }.width('70%')
  }
}
```

