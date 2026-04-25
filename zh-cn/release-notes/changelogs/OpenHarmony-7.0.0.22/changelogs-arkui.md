# ArkUI子系统Changelog

## cl.arkui.1 WithTheme相关组件行为变更

**访问级别**

公开接口

**变更原因**

为提升主题功能的一致性与完整性，对下述场景下的组件行为进行优化适配。

1. 当前已支持[WithTheme](../../../application-dev/reference/apis-arkui/arkui-ts/ts-container-with-theme.md)的组件，在特定场景下部分组件未能正确应用[WithTheme](../../../application-dev/reference/apis-arkui/arkui-ts/ts-container-with-theme.md)所设置的主题样式，与预期设计效果不符。
   - 弹窗类组件不跟随宿主节点的局部主题或深浅色样式。
   - 部分组件（组件范围见**场景二**）动态添加至[WithTheme](../../../application-dev/reference/apis-arkui/arkui-ts/ts-container-with-theme.md)中后，不会跟随局部主题或深浅色变化而变化（例如通过ForEach+ListItem，将组件添加到WithTheme组件下）。

2. 对于暂不支持[WithTheme](../../../application-dev/reference/apis-arkui/arkui-ts/ts-container-with-theme.md)的组件，其样式不会响应WithTheme或默认主题[setDefaultTheme](../../../application-dev/reference/apis-arkui/js-apis-arkui-theme.md#setdefaulttheme)设置的主题样式。

**变更影响**

此变更涉及应用适配。

**场景一：弹窗类组件跟随宿主节点的WithTheme样式**

变更前：宿主节点的[bindMenu](../../../application-dev/reference/apis-arkui/arkui-ts/ts-universal-attributes-menu.md#bindmenu11)、[bindPopup](../../../application-dev/reference/apis-arkui/arkui-ts/ts-universal-attributes-popup.md#bindpopup)、[bindSheet](../../../application-dev/reference/apis-arkui/arkui-ts/ts-universal-attributes-sheet-transition.md#bindsheet)、[CalendarPicker](../../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-calendarpicker.md)弹窗类组件弹出时，不跟随宿主节点的局部主题或深浅色样式。

变更后：宿主节点的[bindMenu](../../../application-dev/reference/apis-arkui/arkui-ts/ts-universal-attributes-menu.md#bindmenu11)、[bindPopup](../../../application-dev/reference/apis-arkui/arkui-ts/ts-universal-attributes-popup.md#bindpopup)、[bindSheet](../../../application-dev/reference/apis-arkui/arkui-ts/ts-universal-attributes-sheet-transition.md#bindsheet)、[CalendarPicker](../../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-calendarpicker.md)弹窗类组件弹出时，会跟随宿主节点的局部主题或深浅色样式。


**场景二：动态添加到WithTheme的组件响应主题变化**

变更前：当WithTheme的主题样式或深浅色发生动态变化时，后续动态添加到WithTheme中的组件不会同步响应这些变化。

变更后：当WithTheme的主题样式或深浅色发生动态变化时，后续动态添加到WithTheme中的组件会同步响应这些变化。

| 涉及场景 | 涉及组件 |
| --- | --- |
| 动态添加场景 | [Button](../../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-button.md)、[Menu](../../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-menu.md)、[DatePicker](../../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-datepicker.md)、[TextPicker](../../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-textpicker.md)、[TimePicker](../../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-timepicker.md)、[Counter](../../../application-dev/reference/apis-arkui/arkui-ts/ts-container-counter.md)、[Progress](../../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-progress.md)、[TextClock](../../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-textclock.md)、[LoadingProgress](../../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-loadingprogress.md)、[Scroll](../../../application-dev/reference/apis-arkui/arkui-ts/ts-container-scroll.md)、[AlphabetIndexer](../../../application-dev/reference/apis-arkui/arkui-ts/ts-container-alphabet-indexer.md)、[Tabs](../../../application-dev/reference/apis-arkui/arkui-ts/ts-container-tabs.md)、[TabContent](../../../application-dev/reference/apis-arkui/arkui-ts/ts-container-tabcontent.md)、[Swiper](../../../application-dev/reference/apis-arkui/arkui-ts/ts-container-swiper.md)、[Indicator](../../../application-dev/reference/apis-arkui/arkui-ts/ts-swiper-components-indicator.md)。 |

**场景三：组件新增WithTheme支持能力**

变更前：组件不受WithTheme或setDefaultTheme设置的样式影响，显示为系统默认样式。

变更后：组件会响应WithTheme或setDefaultTheme设置的样式，并优先显示对应的主题效果。

| 涉及场景 | 涉及组件 |
| --- | --- |
| 组件新增WithTheme支持能力 | [TextArea](../../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-textarea.md)、[Search](../../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-search.md)、[RichEditor](../../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-richeditor.md)、[Image](../../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-image.md)、[ImageAnimator](../../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-imageanimator.md)、[PatternLock](../../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-patternlock.md)、[QRCode](../../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-qrcode.md)、[DataPanel](../../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-datapanel.md)、[文本选择菜单](../../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-text.md)、[Badge](../../../application-dev/reference/apis-arkui/arkui-ts/ts-container-badge.md)、[styleString](../../../application-dev/reference/apis-arkui/arkui-ts/ts-universal-styled-string.md)、[LocalBuilder](../../../application-dev/ui/state-management/arkts-localBuilder.md)、[Tabs](../../../application-dev/reference/apis-arkui/arkui-ts/ts-container-tabs.md)、[TabContent](../../../application-dev/reference/apis-arkui/arkui-ts/ts-container-tabcontent.md)、[ListItemGroup](../../../application-dev/reference/apis-arkui/arkui-ts/ts-container-listitemgroup.md)、[ListItem](../../../application-dev/reference/apis-arkui/arkui-ts/ts-container-listitem.md)、[ArcListItem](../../../application-dev/reference/apis-arkui/arkui-ts/ts-container-arclistitem.md)、[GridItem](../../../application-dev/reference/apis-arkui/arkui-ts/ts-container-griditem.md)、[Refresh](../../../application-dev/reference/apis-arkui/arkui-ts/ts-container-refresh.md)、[TextPicker](../../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-textpicker.md)、[TimePicker](../../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-timepicker.md)、[DatePicker](../../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-datepicker.md)、[CalendarPicker](../../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-calendarpicker.md)、[UIPickerComponent](../../../application-dev/reference/apis-arkui/arkui-ts/ts-container-ui-picker-component.md)、[MenuItem](../../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-menuitem.md)和[menuItemGroup](../../../application-dev/reference/apis-arkui/arkui-ts/ts-basic-components-menuitemgroup.md)。 |

**起始API Level**

12

**变更发生版本**

从OpenHarmony SDK 7.0.0.22开始。

**变更的接口/组件**

WithThemeInterface、setDefaultTheme。

**适配指导**

1. 若希望上述组件在WithTheme下保持变更前的行为，即继续跟随系统样式或系统深浅色模式，可将该组件放入`WithTheme({ colorMode: ThemeColorMode.SYSTEM })`组件下。

   ```ts
   @Entry
   @Component
   struct WithThemeExample {
     @State message: string = 'Hello World';
     @State arr: number[] = [];
     private index: number = 0;
     build() {
       Row() {
         Column() {
           Button("Add Element")
             .onClick(() => {
               this.arr.push(this.index++);
             })
           WithTheme({ colorMode: ThemeColorMode.DARK }) {
             List() {
               ForEach(this.arr, (item: number, index) => {
                 ListItem() {
                   Column() {
                     WithTheme({ colorMode: ThemeColorMode.SYSTEM }) {
                       Column() {
                         Button("Button In ForEach with COLOR_MODE_SYSTEM")
                       }
                     }
                   }
                 }
               })
             }
             .width('100%')
             .height('100%')
           }
         }
         .width('100%')
       }
       .height('100%')
     }
   }
   ```

2. 如果WithTheme容器内的部分组件使用了固定颜色值，组件放入WithTheme中，生效WithTheme设置的样式时，可能影响显示效果。可通过将该组件放入新的WithTheme容器中，并将该容器的colorMode设置为ThemeColorMode.SYSTEM，恢复为变更前的行为。

   ```ts
   @Entry
   @Component
   struct WithThemeExample {
     @State arr: number[] = [];
     private index: number = 0
   
     build() {
       Row() {
         Column() {
           Button("Add Element")
             .onClick(() => {
               this.arr.push(this.index++);
             })
           WithTheme({ colorMode: ThemeColorMode.DARK }) {
             List() {
               ForEach(this.arr, (item: number, index) => {
                 ListItem() {
                   WithTheme({ colorMode: ThemeColorMode.SYSTEM }) {
                     Column() {
                       Text("Set ColorMode SYSTEM")
                         .fontColor("#FF383838")
                     }
                     .backgroundColor($r('sys.color.background_primary'))
   
                   }
                 }
               })
             }
             .width('100%')
             .height('100%')
           }
         }
         .width('100%')
       }
       .height('100%')
     }
   }
   ```
