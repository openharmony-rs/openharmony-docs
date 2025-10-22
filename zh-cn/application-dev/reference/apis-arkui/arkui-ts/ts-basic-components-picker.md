# Picker
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @luoying_ace_admin-->
<!--Designer: @weixin_52725220-->
<!--Tester: @xiong0104-->
<!--Adviser: @HelloCrease-->

Picker容器是立体滚轮样式选择器，通过子组件实现选项内容和样式的自定义，支持文本类型和图文组合类型，图文组合类型选项需要Row容器包含图片和文本组件。

>  **说明：**
>
> - 本模块首批接口从API version 22开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 开发者在子组件Row容器中通常应包含Text、Image、SymbolGlyph基础组件，避免继续包含其他容器。
>
> - Picker容器的选择项行高固定40vp，最大显示7行。容器高度建议设置为200vp，当设置的高度大于等于该建议值时，全部显示；小于该建议值时，选择项行数会从容器的上下边缘向中间减少。
>
> - 当Picker容器设置宽度时子组件的宽度会被覆盖；未设置宽度时，取当前视图中可见子组件中最大的宽度为容器宽度。建议选项行宽度设置相同，避免滑动过程动态变化。

## 子组件

支持多个子组件。

>  **说明：**
>
>  支持子组件类型：[Text](./ts-basic-components-text.md)、[Image](./ts-basic-components-image.md)、[Row](./ts-container-row.md)和[SymbolGlyph](./ts-basic-components-symbolGlyph.md)。
>
>  支持渲染控制类型：[if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md)和[ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md)。


## 接口

Picker(options?: PickerOptions)

通过子组件创建Picker容器，其选中项由输入的索引值决定。

**原子化服务API：** 从API version 22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| options |  [PickerOptions](#pickeroptions对象说明)| 否 | Picker容器的参数，包括选中项的索引值。</br>默认索引值：0 |

## PickerOptions对象说明

Picker容器支持的参数。

**原子化服务API：** 从API version 22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| selectedIndex | number | 否 | 否 | 选中项的索引值，取值为大于等于0的整数。</br>默认值：0 |

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
| isLoop  | [Optional](ts-universal-attributes-custom-property.md#optionalt12)\<boolean> | 是   | 是否可循环滚动。<br/>- true：可循环。<br/>- false：不可循环。当isLoop的值为undefined时，使用默认值：true。 |

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
| style  | [Optional](ts-universal-attributes-custom-property.md#optionalt12)\<[PickerIndicatorStyle](ts-basic-components-picker.md#pickerindicatorstyle)> | 是   | 设置选中项指示器的样式。|

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
| callback  | [Optional](ts-universal-attributes-custom-property.md#optionalt12)\<[OnPickerCallback](#onpickercallback)> | 是   | 当选中项发生变化时触发的回调。<br/>当callback的值为undefined时，不使用回调函数。 |

### onScrollStop

onScrollStop(callback: Optional\<OnPickerCallback>)

选择器选项列滑动停止时触发该事件。

**原子化服务API：** 从API version 22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型                                       | 必填 | 说明                                              |
| ------ | ------------------------------------------ | ---- | ------------------------------------------------- |
| callback | [Optional](ts-universal-attributes-custom-property.md#optionalt12)\<[OnPickerCallback](#onpickercallback)> | 是   | 当选择器选项列滑动停止时触发的回调。<br/>当callback的值为undefined时，不使用回调函数。 |

## PickerIndicatorType枚举说明

设置选中项指示器的类型。

**原子化服务API：** 从API version 22开始，该类型支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 值 | 说明 |
| -------- | - |-------- |
| DIVIDER | 0 | 通过上下分割线，标识选中项。|
| BACKGROUND | 1 | 通过添加背景色，标识选中项。|

## PickerIndicatorStyle

选中项指示器的配置样式。

**原子化服务API：** 从API version 22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称  | 类型   | 只读 | 可选 | 说明                                       |
| ----- | ------ | ---- | ---- | ------------------------------------------ |
| type  | [PickerIndicatorType](#pickerindicatortype枚举说明) | 否   | 否   | 选中项指示器的类型。                             |
| dividerWidth |  [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)      | 否   | 是   | 分割线的线宽。<br/>默认值：2.0px<br/>单位：默认为vp，也可指定单位为px。<br/>取值范围：dividerWidth小于0取默认值，最大不得超过列高的一半。不支持“百分比”类型。 |
| dividerColor       | [ResourceColor](ts-types.md#resourcecolor) | 否   | 是   | 分割线的颜色。<br/>默认值：'#33000000'                       |
| startMargin |  [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)       | 否   | 是   | 分割线与Picker侧边起始端的距离。<br/>默认值：0<br/>单位：默认为vp，也可指定单位为px。<br/>取值范围：startMargin小于0时无效，最大值不得超过Picker容器列宽。不支持“百分比”类型。 |
| endMargin   |  [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)        | 否   | 是   | 分割线与Picker侧边结束端的距离。<br/>默认值：0<br/>单位：默认为vp，也可指定单位为px。<br/>取值范围：endMargin小于0时无效，最大值不得超过Picker容器列宽。不支持“百分比”类型。 |
| backgroundColor  | [ResourceColor](ts-types.md#resourcecolor) | 否  | 是  | 选中项的背景颜色。<br/>默认值：'sys.color.comp_background_tertiary'   |
| borderRadius  | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) &nbsp;\|&nbsp; [BorderRadiuses](ts-types.md#borderradiuses9) &nbsp;\|&nbsp; [LocalizedBorderRadiuses](ts-types.md#localizedborderradiuses12) | 否  | 是  | 选中项的边框圆角半径。<br/>默认值：{ value:24, unit:LengthUnit.vp }，即四个圆角半径均为24vp。<br/>**说明：**<br/>1. [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12)类型的value参数同时作用于四个圆角半径大小，unit参数用于设置单位。<br/>2. [BorderRadiuses](ts-types.md#borderradiuses9)类型可以设置四个不同值的圆角半径，所有单位固定为vp。<br/>3. [LocalizedBorderRadiuses](ts-types.md#localizedborderradiuses12)类型可以设置四个不同值的圆角半径，并且可以单独设置每个圆角的单位。 |

## OnPickerCallback

type OnPickerCallback = (selectedIndex: number) => void

定义当用户选择项变化时触发onChange事件、当滚动停止时触发onScrollStop事件的回调类型。

**原子化服务API：** 从API version 22开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名     | 类型                                       | 必填 | 说明                                                         |
| ---------- | ------------------------------------------ | ---- | ------------------------------------------------------------ |
| selectedIndex | number | 是   | 当前选中项的索引值，索引从0开始。 |

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
    for (let i = 1; i < 13; i++) {
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
      // 订阅选中项事件
      .onChange((idx: number) => {
        console.info('Picker item changed:' + this.monthArray[idx])
      })
      // 订阅滑动停止事件
      .onScrollStop((idx: number) => {
        console.info('Picker item stoped: ' + this.monthArray[idx])
      })
    }.width('70%')
  }
}
```

