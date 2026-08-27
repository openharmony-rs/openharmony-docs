# $$语法：系统组件双向同步
<!--Kit: ArkUI--> 
<!--Subsystem: ArkUI--> 
<!--Owner: @Cuecuexiaoyu--> 
<!--Designer: @VictorS67--> 
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->

`$$`运算符为系统组件提供TS变量的引用，使得TS变量和系统组件的内部状态保持同步。


内部状态的具体含义取决于组件。例如，TextInput组件的text参数。


## 使用规则

- 当前`$$`支持基础类型变量，当该变量使用\@State、\@Link、\@Prop、\@Provide等状态管理V1装饰器装饰，或者\@Local等状态管理V2装饰器装饰时，变量值的变化会触发UI刷新。

- 当前`$$`支持的组件：

  | 组件                                                         | 支持的参数/属性 | 起始API版本 |
  | ------------------------------------------------------------ | --------------- | ----------- |
  | Checkbox | select          | 10          |
  | CheckboxGroup | selectAll       | 10          |
  | DatePicker | selected        | 10          |
  | TimePicker | selected        | 10          |
  | MenuItem | selected        | 10          |
  | Panel         | mode            | 10          |
  | Radio  | checked         | 10          |
  | Rating | rating          | 10          |
  | Search | value           | 10          |
  | SideBarContainer | showSideBar     | 10          |
  | Slider | value           | 10          |
  | Stepper | index           | 10          |
  | Swiper       | index       | 10          |
  | Tabs           | index           | 10          |
  | TextArea | text            | 10          |
  | TextInput | text            | 10          |
  | TextPicker | selected、value | 10          |
  | Toggle | isOn            | 10          |
  | AlphabetIndexer | selected        | 10          |
  | Select | selected、value | 10          |
  | BindSheet | isShow | 10          |
  | BindContentCover | isShow | 10          |
  | Refresh | refreshing | 8 |
  | GridItem | selected | 10 |
  | ListItem | selected | 10 |


## 使用示例

以TextInput组件的text参数为例：
<!-- @[sync_state_manager_$$](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkUISample/ParadigmStateManagement/entry/src/main/ets/pages/syncStateManager/SyncUsageExample.ets) -->

``` TypeScript
@Entry
@Component
struct TextInputExample {
  @State text: string = '';
  controller: TextInputController = new TextInputController();

  build() {
    Column({ space: 20 }) {
      Text(this.text)
        .fontSize(20)
        .margin(10)
      // $$运算符为系统组件提供TS变量的引用，使得TS变量和系统组件的内部状态保持同步
      TextInput({ text: $$this.text, placeholder: 'input your word...', controller: this.controller })
        .placeholderColor(Color.Grey)
        .placeholderFont({ size: 14, weight: 400 })
        .caretColor(Color.Blue)
        .width(300)
    }
    .width('100%')
    .height('100%')
    .justifyContent(FlexAlign.Center)
  }
}
```

![TextInputDouble](figures/TextInputDouble.gif)
