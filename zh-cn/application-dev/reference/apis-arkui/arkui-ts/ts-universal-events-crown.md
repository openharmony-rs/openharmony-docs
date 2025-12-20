# 表冠事件
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
   指扭动表冠时触发的事件，事件的分发依赖于应用焦点，开发者可以通过[焦点事件](ts-universal-focus-event.md)自定义事件处理。

>  **说明：**
>
> - 本模块首批接口从API version 18开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
>  - 手动旋转表冠以触发其存在默认的交互逻辑，例如旋转手表的表冠后，滚动条会根据旋转表冠的旋转方向进行滚动。
>
> - 组件收到表冠事件的前提是该组件获焦，焦点控制可以通过[focusable](ts-universal-attributes-focus.md#focusable)、[defaultFocus](ts-universal-attributes-focus.md#defaultfocus9)、[focusOnTouch](ts-universal-attributes-focus.md#focusontouch9)进行管理。
>
> - 仅穿戴设备支持该事件。
>
> - 默认支持表冠事件的组件: [Slider](ts-basic-components-slider.md)、[DatePicker](ts-basic-components-datepicker.md)、[TextPicker](ts-basic-components-textpicker.md)、 [TimePicker](ts-basic-components-timepicker.md)、[Scroll](ts-container-scroll.md)、[List](ts-container-list.md)、[Grid](ts-container-grid.md)、[WaterFlow](ts-container-waterflow.md)、[ArcList](ts-container-arclist.md)、[Refresh](ts-container-refresh.md)和[ArcSwiper](ts-container-arcswiper.md)。

## onDigitalCrown

onDigitalCrown(handler: Optional&lt;Callback&lt;CrownEvent&gt;&gt;): T

组件获焦以后扭动表冠时触发该回调。

> **说明：**
>
> 该接口不支持在[attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier)中调用。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full


**参数：** 
| 参数名      | 类型                             | 必填     | 说明                                      |
| ---------- | -------------------------------- | ------- | ----------------------------------------- |
| handler      | Optional&lt;Callback&lt;[CrownEvent](#crownevent对象说明)&gt;&gt; | 是       | 获得[CrownEvent](#crownevent对象说明)对象。   |


**返回值：**
| 类型      | 说明           |
| --------- | ---------------|
| T         | 返回当前组件。   |

## CrownEvent对象说明

组件接收表冠事件的数据结构。内容包括时间戳、旋转角速度、旋转角度、表冠动作和阻止事件冒泡。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称                   | 类型       | 只读    |  可选   |  说明                                                       |
| --------------------- | ------------- | ---------- |------------ |-------------------------------------- |
| timestamp         | number   |  否     | 否    |时间戳。                                  |
| angularVelocity | number   |  否     | 否    |旋转角速度，每秒转的角度(°/s)。                   |
| degree          | number   |  否     | 否    |相对旋转角度。<br>单位：度。<br>取值范围:[-360, 360]。     |
| action          | [CrownAction](ts-appendix-enums.md#crownaction18)   |  否     | 否    |表冠动作。  |
| stopPropagation | Callback\<void>    |  否      | 否    |阻止[事件冒泡](../../../ui/arkts-interaction-basic-principles.md#事件冒泡)。                         |

## 示例
该示例实现了组件注册表冠事件，接收表冠事件数据上报内容。
```ts
// xxx.ets
@Entry
@Component
struct CityList {
  @State message: string = "onDigitalCrown";

  build() {
    Column() {
      Row() {
        Stack() {
          Text(this.message)
            .fontSize(20)
            .fontColor(Color.White)
            .backgroundColor("#262626")
            .textAlign(TextAlign.Center)
            .focusable(true)
            .focusOnTouch(true)
            .defaultFocus(true)
            .borderWidth(2)
            .width(223)
            .height(223)
            .borderRadius(110)
            .onDigitalCrown((event: CrownEvent) => {
              event.stopPropagation();
              this.message = "CrownEvent\n\n" + JSON.stringify(event);
              console.info(`action: ${event.action}, angularVelocity: ${event.angularVelocity}, degree: ${event.degree}, timestamp: ${event.timestamp}`);
            })
        }.width("100%").height("100%")
      }.width("100%").height("100%")
    }
  }
}
```

![crown.gif](figures/crown.gif)
