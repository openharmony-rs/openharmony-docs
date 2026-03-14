# ArkUI子系统 Changelog

## cl.arkui.1 WithTheme 相关组件行为变更

**访问级别**

公开接口

**变更原因**

为提升主题功能的一致性与完整性，需对下述场景下的组件行为进行优化适配。

1、当前已支持[WithTheme](../../../application-dev/reference/apis-arkui/arkui-ts/ts-container-with-theme.md)的组件中，特定场景下部分组件未能正确应用[WithTheme](../../../application-dev/reference/apis-arkui/arkui-ts/ts-container-with-theme.md)所设置的主题样式，与预期设计效果不符。
- 弹窗类组件不跟随宿主节点的局部主题/深浅色样式。
- 部分组件动态添加至[WithTheme](../../../application-dev/reference/apis-arkui/arkui-ts/ts-container-with-theme.md)中后，不会跟随局部主题/深浅色变化而变化。

2、对于尚未支持[WithTheme](../../../application-dev/reference/apis-arkui/arkui-ts/ts-container-with-theme.md)的组件，其样式不会响应 `WithTheme` 或默认主题[setDefaultTheme](../../../application-dev/reference/apis-arkui/js-apis-arkui-theme.md#setdefaulttheme)设置的主题样式。

**变更影响**

此变更涉及应用适配。

**场景一：弹窗类组件跟随宿主节点的WithTheme样式**

变更前：弹窗类组件弹出时，不跟随宿主节点的局部主题或深浅色样式。

变更后：弹窗类组件弹出时，会跟随宿主节点的局部主题或深浅色样式。

| 涉及场景 | 涉及组件 |
| --- | --- |
| 弹窗类组件 | Menu、Popup、bindSheet |

**场景二：动态添加到WithTheme的组件响应主题变化**

变更前：当WithTheme的主题样式或深浅色发生动态变化时，后续动态添加到WithTheme中的组件不会同步响应这些变化。

变更后：当WithTheme的主题样式或深浅色发生动态变化时，后续动态添加到WithTheme中的组件会同步响应这些变化。

| 涉及场景 | 涉及组件 |
| --- | --- |
| 动态添加场景 | Button、Menu、MenuItem、DatePicker、TextPicker、TimePicker、Counter、Progress、TextClock、LoadingProgress、Scroll、AlphabetIndexer、Tabs、TabContent、Swiper |

---

**场景三：组件新增WithTheme支持能力**

变更前：组件不受WithTheme/setDefaultTheme设置的样式影响，显示为系统默认样式。

变更后：组件会响应WithTheme/setDefaultTheme设置的样式，并优先显示对应的主题效果。

| 涉及场景 | 涉及组件 |
| --- | --- |
| 组件新增WithTheme支持能力 | TextArea、Search、RichEditor、Image、ImageAnimator、Picker、PatternLock、QRCode、DataPanel、文本选中菜单、Badge、styleString、LocalBuilder |

**起始API Level**

12

**变更发生版本**

从OpenHarmony SDK 6.1.0.26开始。

**变更的接口/组件**

WithThemeInterface、setDefaultTheme。

**适配指导**

1、若希望上述组件在WithTheme下保持变更前的行为，即继续跟随系统样式或系统深浅色模式，可将该组件放入colorMode设置为ThemeColorMode.SYSTEM的WithTheme容器中。

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

        WithTheme({ colorMode: ThemeColorMode.SYSTEM }) {
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
        }
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

2、如果WithTheme容器内的部分组件使用了固定颜色值，可能会导致主题切换后显示效果不一致。可通过以下方式调整：

方案一：调整该组件的颜色设置，避免使用固定值。

方案二：将该组件放入新的WithTheme容器中，并将该容器的colorMode设置为ThemeColorMode.SYSTEM。
