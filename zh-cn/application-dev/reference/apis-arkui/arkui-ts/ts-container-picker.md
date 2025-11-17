# Picker
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @luoying_ace_admin-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @Brilliantry_Rui-->

Picker容器是用于实现用户选择操作的组件。它支持从一组有限的选项中让用户进行单选，可应用于时间选择、日期选择、地区选择、状态选择等场景。Picker容器具有立体滚轮样式，支持选项按需定制，包括文本类型、图片类型和图文组合类型。

>  **说明：**
>
> - 该组件从API version 22开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> - Picker容器的选项行高固定为40vp，最多可显示7个选项。由于显示效果为立体滚轮样式，因此除选中项外的其他选项会进行不同角度的旋转，实际的可视高度会小于40vp。
>
> - Picker容器的[height](./ts-universal-attributes-size.md#height)建议设置为200vp。当设置的高度大于等于该建议值时，可完全显示7个选项；小于该建议值时，显示范围会从上下边缘向中间裁剪，可显示的选项数量也会相应减少，始终保持选中项垂直居中。
>
> - 当Picker容器未设置[width](./ts-universal-attributes-size.md#width)时，取当前视图中可见子组件的最大宽度作为容器宽度。建议为Picker容器设置宽度，或为每个子组件设置相同宽度，以避免滑动过程中容器宽度动态发生变化，影响显示效果。
>
> - Picker容器的子组件的对齐方式固定为居中对齐，不支持通过[align](ts-universal-attributes-location.md#align)属性改变子组件的对齐方式。
>
> - Picker容器当前不支持智能手表设备。

## 子组件

- 支持多个子组件。

- 支持子组件类型：[Text](./ts-basic-components-text.md)、[Image](./ts-basic-components-image.md)、[Row](./ts-container-row.md)和[SymbolGlyph](./ts-basic-components-symbolGlyph.md)。

- 支持渲染控制类型：[if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md)和[ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md)。

>  **说明：**
>
> - 开发者在使用Row容器作为子组件时，Row容器中仅支持包含Text、Image、SymbolGlyph基础组件，包含其他容器组件可能会影响显示效果或滑动功能异常。
>
> - 统计子组件的个数时，不包含Row容器内的子组件，Row容器及其子组件共同视为1个子组件。
>
> - 子组件为Text、Image、SymbolGlyph时，[height](./ts-universal-attributes-size.md#height)属性不生效，固定为40vp。
>
> - 子组件为Row容器时，Row容器的[height](./ts-universal-attributes-size.md#height)属性不生效，固定为40vp，Row容器内的子组件[height](./ts-universal-attributes-size.md#height)属性能正常生效，最终显示效果由Row容器决定。
>
> - 图文组合类型选项需要使用Row容器包含图片和文本组件。使用图文组合类型选项时，建议将图片的[height](./ts-universal-attributes-size.md#height)设置为40vp及以下，避免图片较大时被裁剪。
>
> - Picker容器内所有文本组件（包括Row容器内的文本组件）的fontSize属性默认为20fp。用户设置将覆盖默认值，设置异常值时以文本组件[fontSize](./ts-basic-components-text.md#fontsize)处理的结果为准。建议统一设置或不设置fontSize以保证良好的显示效果。


## 接口

Picker(options?: PickerOptions)

创建Picker容器，其选中项由options参数中的selectedIndex属性值决定。

**原子化服务API：** 从API version 22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| options |  [PickerOptions](#pickeroptions对象说明)| 否 | 配置Picker容器的参数。 |

## PickerOptions对象说明

Picker容器的参数说明。

**原子化服务API：** 从API version 22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| selectedIndex | number | 否 | 是 | 选中项的索引值。</br>取值范围：[0, 子组件的个数-1]内的整数。不在取值范围内时，使用默认值；设置小数时，使用向下取整后的整数。</br>默认值：0<br/>**说明：**<br/>统计子组件的个数时，不包含Row容器内的子组件，Row容器及其子组件共同视为1个子组件。 |

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

>  **说明：**
>
>  开启触控反馈时，需要在工程的src/main/module.json5文件的"module"内配置requestPermissions字段开启振动权限，配置如下：
>  ```json
>  "requestPermissions": [
>  {
>   "name": "ohos.permission.VIBRATE",
>  }
>  ]
>  ```

**原子化服务API：** 从API version 22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型                                          | 必填  | 说明                                                                                  |
| ------ | --------------------------------------------- |-----|-------------------------------------------------------------------------------------|
| enable  | [Optional](ts-universal-attributes-custom-property.md#optionalt12)\<boolean> | 是   | 设置是否开启触控反馈。<br/>- true：开启触控反馈。<br/>- false：不开启触控反馈。<br/>默认值：true<br/>开启后，是否存在触控反馈取决于系统硬件支持情况。<br/>当enable的值为undefined时，使用默认值。|

### selectionIndicator

selectionIndicator(style: Optional\<PickerIndicatorStyle>)

设置选中项指示器的样式。

**原子化服务API：** 从API version 22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型                                                         | 必填 | 说明                                                         |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| style  | [Optional](ts-universal-attributes-custom-property.md#optionalt12)\<[PickerIndicatorStyle](ts-container-picker.md#pickerindicatorstyle对象说明)> | 是   | 设置选中项指示器的样式。|

## 事件

除支持[通用事件](ts-component-general-events.md)外，还支持以下事件：

### onChange

onChange(callback: Optional\<OnPickerCallback>)

滑动选择器选项时，若选中项发生变化，触发该事件。

>  **说明：**
> 
> 如果某个选项有一半以上的区域进入选中项区域内，则该选项成为选中项。
> 
> 选中项区域可通过设置[selectionIndicator](#selectionindicator)进行标识。如果设置选中项指示器为背景，则背景区域即为选中项区域。如果设置选中项指示器为分割线，则上下分割线的中心线内的区域为选中项区域。

**原子化服务API：** 从API version 22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型                                       | 必填 | 说明                                              |
| ------ | ------------------------------------------ | ---- | ------------------------------------------------- |
| callback  | [Optional](ts-universal-attributes-custom-property.md#optionalt12)\<[OnPickerCallback](#onpickercallback)> | 是   | 当选中项发生变化时触发的回调函数。<br/>当callback的值为undefined时，不使用回调函数。 |

### onScrollStop

onScrollStop(callback: Optional\<OnPickerCallback>)

选择器滑动停止时，触发该事件。选择器滑动停止指某次行为触发的滑动动画完全结束。如果某次滑动动画还未结束时又触发了新的滑动动画，则不属于滑动停止。

**原子化服务API：** 从API version 22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型                                       | 必填 | 说明                                              |
| ------ | ------------------------------------------ | ---- | ------------------------------------------------- |
| callback | [Optional](ts-universal-attributes-custom-property.md#optionalt12)\<[OnPickerCallback](#onpickercallback)> | 是   | 当选择器滑动停止时触发的回调函数。<br/>当callback的值为undefined时，不使用回调函数。 |

## PickerIndicatorStyle对象说明

选中项指示器样式的参数说明。

**原子化服务API：** 从API version 22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称  | 类型   | 只读 | 可选 | 说明                                       |
| ----- | ------ | ---- | ---- | ------------------------------------------ |
| type  | [PickerIndicatorType](#pickerindicatortype枚举说明) | 否   | 否   | 选中项指示器的类型。<br/>默认值：PickerIndicatorType.BACKGROUND |
| strokeWidth |  [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)      | 否   | 是   | 分割线的线宽。<br/>默认值：2.0px<br/>单位：如果未指定单位则默认为vp，也可指定为px。<br/>取值范围：最大不超过选中项高度的一半，即20vp。strokeWidth小于0时使用默认值。不支持“百分比”类型。<br/>**说明：**<br/>1. 当type为PickerIndicatorType.DIVIDER时生效。<br/>2. 通过LengthMetrics.resource方式设置时，使用非长度属性的值会按照0vp处理。  |
| dividerColor       | [ResourceColor](ts-types.md#resourcecolor) | 否   | 是   | 分割线的颜色。<br/>默认值：'sys.color.comp_divider'<br/>**说明：**<br/>当type为PickerIndicatorType.DIVIDER时生效。 |
| startMargin |  [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)       | 否   | 是   | 分割线与Picker容器侧边起始端的距离。<br/>默认值：0<br/>单位：如果未指定单位则默认为vp，也可指定为px。<br/>取值范围：startMargin与endMargin之和不得超过Picker容器的宽度。设置小于0或startMargin与endMargin之和超过Picker容器的宽度时，使用默认值。不支持“百分比”类型。<br/>**说明：**<br/>当type为PickerIndicatorType.DIVIDER时生效。 |
| endMargin   |  [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)        | 否   | 是   | 分割线与Picker容器侧边结束端的距离。<br/>默认值：0<br/>单位：如果未指定单位则默认为vp，也可指定为px。<br/>取值范围：startMargin与endMargin之和不得超过Picker容器的宽度。设置小于0或startMargin与endMargin之和超过Picker容器的宽度时，使用默认值。不支持“百分比”类型。<br/>**说明：**<br/>当type为PickerIndicatorType.DIVIDER时生效。 |
| backgroundColor  | [ResourceColor](ts-types.md#resourcecolor) | 否  | 是  | 选中项背景的颜色。<br/>默认值：'sys.color.comp_background_tertiary'<br/>**说明：**<br/>当type为PickerIndicatorType.BACKGROUND时生效。   |
| borderRadius  | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) &nbsp;\|&nbsp; [BorderRadiuses](ts-types.md#borderradiuses9) &nbsp;\|&nbsp; [LocalizedBorderRadiuses](ts-types.md#localizedborderradiuses12) | 否  | 是  | 选中项背景的边框圆角半径。<br/>默认值：{ value:12, unit:LengthUnit.vp }，即四个圆角半径均为12vp。<br/>取值范围：取选中项的宽和高之中较小的边长为x，最大不超过x的一半。当取值小于0时，使用默认值；当取值大于最大值时，使用最大值。<br/>**说明：**<br/>1. 当type为PickerIndicatorType.BACKGROUND时生效。<br/>2. [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)：统一设置四个圆角半径的大小和单位。<br/>3. [BorderRadiuses](ts-types.md#borderradiuses9)：单独设置四个圆角半径的大小（单位为vp）。<br/>4. [LocalizedBorderRadiuses](ts-types.md#localizedborderradiuses12)：单独设置四个圆角半径的大小和单位。 |

## PickerIndicatorType枚举说明

设置选中项指示器的类型。

**原子化服务API：** 从API version 22开始，该类型支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 值 | 说明 |
| -------- | - |-------- |
| BACKGROUND | 0 | 通过给选中项添加背景，标识选中项。|
| DIVIDER | 1 | 通过在选中项的上下边缘添加分割线，标识选中项。|

## OnPickerCallback

type OnPickerCallback = (selectedIndex: number) => void

定义[onChange](#onchange)和[onScrollStop](#onscrollstop)事件的回调类型。

**原子化服务API：** 从API version 22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名     | 类型                                       | 必填 | 说明                                                         |
| ---------- | ------------------------------------------ | ---- | ------------------------------------------------------------ |
| selectedIndex | number | 是   | 当前选中项的索引值。</br>取值范围：[0, 子组件的个数-1]内的整数。 |

## 示例

### 示例1（自定义月份选择器）

从API version 22开始，该示例使用Picker容器包含文本子组件的方式实现月份选择器。


```ts
// xxx.ets
@Entry
@Component
struct PickerExample {
  private fontSize: number | string | Resource = '20vp';
  private monthArray: string[] = [];

  aboutToAppear(): void {
    // 构造选项数据
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

