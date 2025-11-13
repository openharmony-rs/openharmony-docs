# ArkUI子系统Changelog

## cl.arkui.1 WithThemeInterface接口行为变更

**访问级别**

公开接口

**变更原因**

当前，在[WithTheme](../../../application-dev/reference/apis-arkui/arkui-ts/ts-container-with-theme.md)组件中添加特定组件、动态加载组件或动态切换[WithTheme](../../../application-dev/reference/apis-arkui/arkui-ts/ts-container-with-theme.md)主题样式时，部分组件未能正确应用[WithTheme](../../../application-dev/reference/apis-arkui/arkui-ts/ts-container-with-theme.md)所设置的主题样式，与预期设计效果不符。为提升主题功能的一致性与完整性，现需对上述场景下的组件行为进行优化适配。

**变更影响**

此变更涉及应用适配。

**场景一**：组件动态添加至WithTheme组件中后，进行系统深浅色切换。

变更前：系统深浅色模式切换时，已被动态添加到WithTheme中的组件不生效WithTheme中设置的深浅色模式，其样式跟随系统深浅色切换。
  
变更后：系统深浅色模式切换时，已被动态添加到WithTheme中的组件将生效WithTheme中设置的深浅色模式，其样式不跟随系统深浅色切换。

| 涉及场景           | 涉及组件                                                                                                                                                           |
|----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 容器组件 + ForEach<br>容器组件 + Repeat | Button、Menu、MenuItem、DatePicker、TextPicker、TimePicker、Counter、Progress、TextClock、LoadingProgress、Scroll、TextArea、Search、AlphabetIndexer、Tabs、TabContent、Swiper。|

**场景二**：组件动态添加至WithTheme组件中后，动态修改WithTheme的主题样式。

变更前：WithTheme的主题样式的主题样式被动态修改后，已被动态添加到WithTheme中的组件不生效WithTheme中更新的主题样式。

变更后：WithTheme的主题样式的主题样式被动态修改后，已被动态添加到WithTheme中的组件将生效WithTheme中更新的主题样式。

| 涉及场景           | 涉及组件                                                                                                                                                           |
|----------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 容器组件 + ForEach<br>容器组件 + Repeat | Button、Menu、MenuItem、DatePicker、TextPicker、TimePicker、Counter、Progress、TextClock、LoadingProgress、Scroll、TextArea、Search、AlphabetIndexer、Tabs、TabContent、Swiper。|

**场景三**：WithTheme组件下存在Button等组件，通过点击事件等方式在该组件位置处弹出特定组件。

变更前：弹出的组件不受WithTheme组件中设置的主题样式影响，显示为系统样式。

变更后：弹出的组件会根据WithTheme组件中设置的主题样式进行显示。

涉及组件：DatePicker、TextPicker、TimePicker、AlphabetIndexer。

**场景四**：组件未适配WithTheme能力。

变更前：组件不受WithTheme影响，显示为系统默认样式。

变更后：组件受到WithTheme影响，优先显示WithTheme组件中设置的样式。

涉及组件：RichEditor。

**起始API Level**

12

**变更发生版本**

从OpenHarmony SDK 6.1.0.26开始。

**变更的接口/组件**

WithThemeInterface。


**适配指导**

1、若想保持组件样式跟随系统深浅色变化，可将该组件放入深浅色模式设置为ThemeColorMode.SYSTEM的WithTheme组件中。

```ts
@Entry
@Component
struct WithThemeExample {
  build() {
    Row() {
      Column() {
        WithTheme({colorMode: ThemeColorMode.SYSTEM}) {
          Button("Button In COLOR_MODE_SYSTEM")
        }
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

2、若想动态添加到WithTheme组件下容器组件中的节点跟随系统样式变化，可将该组件放置到深浅色模式设置为ThemeColorMode.SYSTEM的WithTheme组件下，再进行动态添加。

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
        }
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

3、当WithTheme组件内部分组件使用了颜色固定值，导致主题切换时显示效果不一致，可通过以下方式调整：

* 方案一：修改该组件的颜色设置，避免使用固定值。

* 方案二：将该组件放入一个新的 WithTheme 组件中，并将此容器的深浅色模式设置为 ThemeColorMode.SYSTEM。
