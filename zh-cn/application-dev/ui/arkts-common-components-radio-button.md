# 单选框 (Radio)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @houguobiao-->
<!--Designer: @houguobiao-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->


Radio是单选框组件，通常用于提供相应的用户交互选择项，同一组的Radio中只有一个可以被选中。具体用法请参考[Radio](../reference/apis-arkui/arkui-ts/ts-basic-components-radio.md)。


## 创建单选框

Radio通过调用[RadioOptions](../reference/apis-arkui/arkui-ts/ts-basic-components-radio.md#radiooptions对象说明)来创建，以RadioOptions中的value和group为例：

```ts
Radio(options: {value: string, group: string})
```

其中，value是单选框的名称，group是单选框的所属群组名称。checked属性可以设置单选框的状态，状态分别为false和true，设置为true时表示单选框被选中。

Radio支持设置选中状态和非选中状态的样式。

<!-- @[click_radio_to_show_function](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ChooseComponent/entry/src/main/ets/pages/radio/RadioButton.ets) -->


![zh-cn_image_0000001562820821](figures/zh-cn_image_0000001562820821.png)

## 添加事件

除支持[通用事件](../reference/apis-arkui/arkui-ts/ts-component-general-events.md)外，Radio还用于选中后触发某些操作，可以绑定onChange事件来响应选中操作后的自定义行为。

<!-- @[click_radio_event_function](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ChooseComponent/entry/src/main/ets/pages/radio/RadioButton.ets) -->


## 场景示例

通过点击Radio切换声音模式。

<!-- @[click_radio_to_change_function](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ChooseComponent/entry/src/main/ets/pages/radio/RadioSample.ets) -->


![zh-cn_image_0000001562700457](figures/zh-cn_image_0000001562700457.gif)
