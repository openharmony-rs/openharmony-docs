# TabContent

The **TabContent** component is used only in the **Tabs** component. It corresponds to the content view of a switched tab page.

> **NOTE**

> - By default, the [clip](arkts-arkui-common-comp-commonmethod-c.md#clip) attribute of this component is set to **true**. > If you want to extend the content area to the outside of the component, disable the **clip** attribute first.

## Child Components

This component supports only one child component.

> **NOTE:** 
> 
> Built-in system and custom components, and rendering control types (
> [if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md),
> [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md), and
> [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)) are supported.

## TabContent

```TypeScript
TabContent()
```

Creates the **TabContent** component, which represents the content associated with a specific tab.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [BoardStyle](arkts-arkui-tabcontent-comp-boardstyle-i.md) | Represents a board style object. |
| [DrawableTabBarIndicator](arkts-arkui-tabcontent-comp-drawabletabbarindicator-i.md) | Uses an image resource as the indicator. |
| [IndicatorStyle](arkts-arkui-tabcontent-comp-indicatorstyle-i.md) | Represents an indicator style object. |
| [LabelStyle](arkts-arkui-tabcontent-comp-labelstyle-i.md) | Represents a style object for the label text and font. |
| [TabBarIconStyle](arkts-arkui-tabcontent-comp-tabbariconstyle-i.md) | Represents a label icon style object. |
| [TabBarOptions](arkts-arkui-tabcontent-comp-tabbaroptions-i.md) | Defines the options for configuring images and text content on the tabs. |

### Types

| Name | Description |
| --- | --- |
| [DrawableDescriptor](arkts-arkui-tabcontent-comp-drawabledescriptor-t.md) | Defines the input parameter object of the **drawable** attribute in the **DrawableTabBarIndicator** object. |

### Enums

| Name | Description |
| --- | --- |
| [LayoutMode](arkts-arkui-tabcontent-comp-layoutmode-e.md) | Enumerates the layout modes of the images and texts on the bottom tabs. |
| [SelectedMode](arkts-arkui-tabcontent-comp-selectedmode-e.md) | Enumerates the display modes of selected subtabs. |
| [TabVisibility](arkts-arkui-tabcontent-comp-tabvisibility-e.md) | Enumerates the visibility of the tab. |

## Examples

### Example 1: Implementing Custom Tab Switching Synchronization

This example demonstrates how to use [onAnimationStart](ts-container-tabs.md#onanimationstart11) and [onChange](ts-container-tabs.md#onchange) to implement synchronized switching between the tab bar and tab content.

> NOTE
> 
> The resources used in this example are not located in the src > main > resource directory. Starting from DevEco Studio 6.0.0 Beta2, the resources that are located outside the resources directory are not packaged by default when a project or module is created. To package these resources, go to buildOptions > resOptions > copyCodeResource in the module's build-profile.json5 file, and set enable to true. For details, see the description of [resOptions](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-hvigor-build-profile#section754823013348).



```TypeScript
// xxx.ets
@Entry
@Component
struct TabContentExample {
  @State fontColor: string = '#182431';
  @State selectedFontColor: string = '#007DFF';
  @State currentIndex: number = 0;
  @State selectedIndex: number = 0;
  // Create a Tabs controller to control the switching of TabContent.
  private controller: TabsController = new TabsController();

  // Customize the TabBar builder to switch the icon and text color based on the selection status.
  @Builder tabBuilder(index: number) {
    Column() {
      // The common directory is at the same level as the pages directory.
      Image(this.selectedIndex === index ? '/common/public_icon_on.svg' : '/common/public_icon_off.svg')
        .width(24)
        .height(24)
        .margin({ bottom: 4 })
        .objectFit(ImageFit.Contain)
      Text(`Tab${index + 1}`)
        .fontColor(this.selectedIndex === index ? this.selectedFontColor : this.fontColor)
        .fontSize(10)
        .fontWeight(500)
        .lineHeight(14)
    }.width('100%')
  }

  build() {
    Column() {
      // Create the Tabs component, set the position of the tab bar to the bottom, and bind the controller.
      Tabs({ barPosition: BarPosition.End, controller: this.controller }) {
        TabContent() {
          Column() {
            Text('Tab1')
              .fontSize(36)
              .fontColor('#182431')
              .fontWeight(500)
              .opacity(0.4)
              .margin({ top: 30, bottom: 56.5 })
            Divider()
              .strokeWidth(0.5)
              .color('#182431')
              .opacity(0.05)
          }.width('100%')
        }.tabBar(this.tabBuilder(0)) // Set the tab bar to a custom style.

        TabContent() {
          Column() {
            Text('Tab2')
              .fontSize(36)
              .fontColor('#182431')
              .fontWeight(500)
              .opacity(0.4)
              .margin({ top: 30, bottom: 56.5 })
            Divider()
              .strokeWidth(0.5)
              .color('#182431')
              .opacity(0.05)
          }.width('100%')
        }.tabBar(this.tabBuilder(1))

        TabContent() {
          Column() {
            Text('Tab3')
              .fontSize(36)
              .fontColor('#182431')
              .fontWeight(500)
              .opacity(0.4)
              .margin({ top: 30, bottom: 56.5 })
            Divider()
              .strokeWidth(0.5)
              .color('#182431')
              .opacity(0.05)
          }.width('100%')
        }.tabBar(this.tabBuilder(2))

        TabContent() {
          Column() {
            Text('Tab4')
              .fontSize(36)
              .fontColor('#182431')
              .fontWeight(500)
              .opacity(0.4)
              .margin({ top: 30, bottom: 56.5 })
            Divider()
              .strokeWidth(0.5)
              .color('#182431')
              .opacity(0.05)
          }.width('100%')
        }.tabBar(this.tabBuilder(3))
      }
      .vertical(false)
      .barHeight(56)
      .onChange((index: number) => {
        // currentIndex controls the tab page displayed in TabContent, and selectedIndex controls the color switching of the custom TabBar.
        this.currentIndex = index;
        this.selectedIndex = index;
      })
      .onAnimationStart((index: number, targetIndex: number, event: TabsAnimationEvent) => {
        // If the index of the current tab is the same as that of the target tab, the status does not need to be updated.
        if (index === targetIndex) {
          return;
        }
        // selectedIndex controls the color switching for the image and text in the custom tab bar.
        this.selectedIndex = targetIndex;
      })
      .width(360)
      .height(190)
      .backgroundColor('#F1F3F5')
      .margin({ top: 38 })
    }.width('100%')
  }
}
```

### Example 2: Implementing a Custom Side Tabs

This example demonstrates how to create side tabs using [vertical](./ts-container-tabs.md#vertical) and [barPosition](./ts-container-tabs.md#barposition9).

> NOTE
> 
> The resources used in this example are not located in the src > main > resource directory. Starting from DevEco Studio 6.0.0 Beta2, the resources that are located outside the resources directory are not packaged by default when a project or module is created. To package these resources, go to buildOptions > resOptions > copyCodeResource in the module's build-profile.json5 file, and set enable to true. For details, see the description of [resOptions](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-hvigor-build-profile#section754823013348).



```TypeScript
// xxx.ets
@Entry
@Component
struct TabContentExample {
  @State fontColor: string = '#182431';
  @State selectedFontColor: string = '#007DFF';
  @State currentIndex: number = 0;
  @State selectedIndex: number = 0;
  private controller: TabsController = new TabsController();

  @Builder tabBuilder(index: number) {
    Column() {
      // The common directory is at the same level as the pages directory.
      Image(this.selectedIndex === index ? '/common/public_icon_on.svg' : '/common/public_icon_off.svg')
        .width(24)
        .height(24)
        .margin({ bottom: 4 })
        .objectFit(ImageFit.Contain)
      Text('Tab')
        .fontColor(this.selectedIndex === index ? this.selectedFontColor : this.fontColor)
        .fontSize(10)
        .fontWeight(500)
        .lineHeight(14)
    }.width('100%').height('100%').justifyContent(FlexAlign.Center)
  }

  build() {
    Column() {
      // Create the Tabs component, set the position of the TabBar to the start end, and bind the controller.
      Tabs({ barPosition: BarPosition.Start, controller: this.controller }) {
        TabContent()
          .tabBar(this.tabBuilder(0)) // Set the TabBar to a custom style.
        TabContent()
          .tabBar(this.tabBuilder(1))
        TabContent()
          .tabBar(this.tabBuilder(2))
        TabContent()
          .tabBar(this.tabBuilder(3))
      }
      .vertical(true)
      .barWidth(96)
      .barHeight(414)
      .onChange((index: number) => {
        // currentIndex controls the tab page displayed in TabContent, and selectedIndex controls the color switching of the custom TabBar.
        this.currentIndex = index;
        this.selectedIndex = index;
      })
      .onAnimationStart((index: number, targetIndex: number, event: TabsAnimationEvent) => {
        // If the index of the current tab page is the same as that of the target tab page, the status does not need to be updated.
        if (index === targetIndex) {
          return;
        }
        // selectedIndex controls the color switching for the image and text in the custom tab bar.
        this.selectedIndex = targetIndex;
      })
      .width(96)
      .height(414)
      .backgroundColor('#F1F3F5')
      .margin({ top: 52 })
    }.width('100%')
  }
}
```

### Example 3: Implementing Different Styles of Tabs

This example demonstrates how to create subtabs, bottom tabs, and side tabs using [SubTabBarStyle](arkts-arkui-tabcontent-comp-subtabbarstyle-c.md) and [BottomTabBarStyle](arkts-arkui-tabcontent-comp-bottomtabbarstyle-c.md).



```TypeScript
// xxx.ets
@Entry
@Component
struct TabBarStyleExample {
  build() {
    Column({ space: 5 }) {
      Text('Subtab style')
      Column() {
        // Create the Tabs component and set the position of the tab bar to the start.
        Tabs({ barPosition: BarPosition.Start }) {
          TabContent() {
            Column().width('100%').height('100%').backgroundColor(Color.Pink)
          }.tabBar(new SubTabBarStyle('Pink')) // Set the tab bar to the sub tab approved sample style.
          .onWillShow(() => {
            // Triggered when the TabContent is about to be displayed.
            console.info('Pink will show');
          })
          .onWillHide(() => {
            // Triggered when the TabContent is about to be hidden.
            console.info('Pink will hide');
          })

          TabContent() {
            Column().width('100%').height('100%').backgroundColor(Color.Yellow)
          }.tabBar(new SubTabBarStyle('Yellow'))
          .onWillShow(() => {
            console.info('Yellow will show');
          })
          .onWillHide(() => {
            console.info('Yellow will hide');
          })

          TabContent() {
            Column().width('100%').height('100%').backgroundColor(Color.Blue)
          }.tabBar(new SubTabBarStyle('Blue'))
          .onWillShow(() => {
            console.info('Blue will show');
          })
          .onWillHide(() => {
            console.info('Blue will hide');
          })

          TabContent() {
            Column().width('100%').height('100%').backgroundColor(Color.Green)
          }.tabBar(new SubTabBarStyle('Green'))
          .onWillShow(() => {
            console.info('Green will show');
          })
          .onWillHide(() => {
            console.info('Green will hide');
          })
        }
        .vertical(false)
        .scrollable(true)
        .barMode(BarMode.Fixed)
        .onChange((index: number) => {
          console.info(index.toString());
        })
        .width('100%')
        .backgroundColor(0xF1F3F5)
      }.width('100%').height(200)
      Text('Bottom tab style')
      Column() {
        // Create a Tabs component and set the position of the tab bar to the bottom.
        Tabs({ barPosition: BarPosition.End }) {
          TabContent() {
            Column().width('100%').height('100%').backgroundColor(Color.Pink)
          }.tabBar(new BottomTabBarStyle($r('sys.media.ohos_app_icon'), 'Pink')) // Set the tab bar to the bottom page in approved sample style.
          .onWillShow(() => {
            console.info('Pink will show');
          })
          .onWillHide(() => {
            console.info('Pink will hide');
          })

          TabContent() {
            Column().width('100%').height('100%').backgroundColor(Color.Yellow)
          }.tabBar(new BottomTabBarStyle($r('sys.media.ohos_app_icon'), 'Yellow'))
          .onWillShow(() => {
            console.info('Yellow will show');
          })
          .onWillHide(() => {
            console.info('Yellow will hide');
          })

          TabContent() {
            Column().width('100%').height('100%').backgroundColor(Color.Blue)
          }.tabBar(new BottomTabBarStyle($r('sys.media.ohos_app_icon'), 'Blue'))
          .onWillShow(() => {
            console.info('Blue will show');
          })
          .onWillHide(() => {
            console.info('Blue will hide');
          })

          TabContent() {
            Column().width('100%').height('100%').backgroundColor(Color.Green)
          }.tabBar(new BottomTabBarStyle($r('sys.media.ohos_app_icon'), 'Green'))
          .onWillShow(() => {
            console.info('Green will show');
          })
          .onWillHide(() => {
            console.info('Green will hide');
          })
        }
        .vertical(false)
        .scrollable(true)
        .barMode(BarMode.Fixed)
        .onChange((index: number) => {
          console.info(index.toString());
        })
        .width('100%')
        .backgroundColor(0xF1F3F5)
      }.width('100%').height(200)
      Text('Side tab style')
      Column() {
        Tabs({ barPosition: BarPosition.Start }) {
          TabContent() {
            Column().width('100%').height('100%').backgroundColor(Color.Pink)
          }.tabBar(new BottomTabBarStyle($r('sys.media.ohos_app_icon'), 'Pink'))
          .onWillShow(() => {
            console.info('Pink will show');
          })
          .onWillHide(() => {
            console.info('Pink will hide');
          })

          TabContent() {
            Column().width('100%').height('100%').backgroundColor(Color.Yellow)
          }.tabBar(new BottomTabBarStyle($r('sys.media.ohos_app_icon'), 'Yellow'))
          .onWillShow(() => {
            console.info('Yellow will show');
          })
          .onWillHide(() => {
            console.info('Yellow will hide');
          })

          TabContent() {
            Column().width('100%').height('100%').backgroundColor(Color.Blue)
          }.tabBar(new BottomTabBarStyle($r('sys.media.ohos_app_icon'), 'Blue'))
          .onWillShow(() => {
            console.info('Blue will show');
          })
          .onWillHide(() => {
            console.info('Blue will hide');
          })

          TabContent() {
            Column().width('100%').height('100%').backgroundColor(Color.Green)
          }.tabBar(new BottomTabBarStyle($r('sys.media.ohos_app_icon'), 'Green'))
          .onWillShow(() => {
            console.info('Green will show');
          })
          .onWillHide(() => {
            console.info('Green will hide');
          })
        }
        .vertical(true) // Set the tab mode to vertical.
        .scrollable(true).barMode(BarMode.Fixed)
        .onChange((index: number) => {
          console.info(index.toString());
        })
        .width('100%')
        .backgroundColor(0xF1F3F5)
      }.width('100%').height(400)
    }
  }
}
```

### Example 4: Setting the Indicator for Subtabs

This example demonstrates how to set the indicator for subtabs using the [indicator](#indicator10) property in SubTabBarStyle.



```TypeScript
// xxx.ets
@Entry
@Component
struct TabsAttr {
  private controller: TabsController = new TabsController();
  @State indicatorColor: Color = Color.Blue;
  @State indicatorWidth: number = 40;
  @State indicatorHeight: number = 10;
  @State indicatorBorderRadius: number = 5;
  @State indicatorSpace: number = 10;
  @State subTabBorderRadius: number = 20;
  @State selectedMode: SelectedMode = SelectedMode.INDICATOR;
  private colorFlag: boolean = true;
  private widthFlag: boolean = true;
  private heightFlag: boolean = true;
  private borderFlag: boolean = true;
  private spaceFlag: boolean = true;

  build() {
    Column() {
      Button('Change Indicator Color').width('100%').margin({ bottom: '12vp' })
        .onClick((event?: ClickEvent) => {
          // Configure the animation for the underline color attribute.
          if (this.colorFlag) {
            this.getUIContext()?.animateTo({
              duration: 1000, // Animation duration.
              curve: Curve.Linear, // Animation curve.
              delay: 200, // Animation delay.
              iterations: 1, // Number of playback times.
              playMode: PlayMode.Normal, // Animation playback mode.
              onFinish: () => {
                console.info('play end');
              }
            }, () => {
              this.indicatorColor = Color.Red;
            });
          } else {
            this.getUIContext()?.animateTo({
              duration: 1000, // Animation duration.
              curve: Curve.Linear, // Animation curve.
              delay: 200, // Animation delay.
              iterations: 1, // Number of playback times.
              playMode: PlayMode.Normal, // Animation playback mode.
              onFinish: () => {
                console.info('play end');
              }
            }, () => {
              this.indicatorColor = Color.Yellow;
            });
          }
          this.colorFlag = !this.colorFlag;
        })
      Button('Change Indicator Height').width('100%').margin({ bottom: '12vp' })
        .onClick((event?: ClickEvent) => {
          // Configure the animation for the underline height attribute.
          if (this.heightFlag) {
            this.getUIContext()?.animateTo({
              duration: 1000, // Animation duration.
              curve: Curve.Linear, // Animation curve.
              delay: 200, // Animation delay.
              iterations: 1, // Number of playback times.
              playMode: PlayMode.Normal, // Animation playback mode.
              onFinish: () => {
                console.info('play end');
              }
            }, () => {
              this.indicatorHeight = 20;
            });
          } else {
            this.getUIContext()?.animateTo({
              duration: 1000, // Animation duration.
              curve: Curve.Linear, // Animation curve.
              delay: 200, // Animation delay.
              iterations: 1, // Number of playback times.
              playMode: PlayMode.Normal, // Animation playback mode.
              onFinish: () => {
                console.info('play end');
              }
            }, () => {
              this.indicatorHeight = 10;
            });
          }
          this.heightFlag = !this.heightFlag;
        })
      Button('Change Indicator Width').width('100%').margin({ bottom: '12vp' })
        .onClick((event?: ClickEvent) => {
          // Configure the animation for the underline width attribute.
          if (this.widthFlag) {
            this.getUIContext()?.animateTo({
              duration: 1000, // Animation duration.
              curve: Curve.Linear, // Animation curve.
              delay: 200, // Animation delay.
              iterations: 1, // Number of playback times.
              playMode: PlayMode.Normal, // Animation playback mode.
              onFinish: () => {
                console.info('play end');
              }
            }, () => {
              this.indicatorWidth = 30;
            });
          } else {
            this.getUIContext()?.animateTo({
              duration: 1000, // Animation duration.
              curve: Curve.Linear, // Animation curve.
              delay: 200, // Animation delay.
              iterations: 1, // Number of playback times.
              playMode: PlayMode.Normal, // Animation playback mode.
              onFinish: () => {
                console.info('play end');
              }
            }, () => {
              this.indicatorWidth = 50;
            });
          }
          this.widthFlag = !this.widthFlag;
        })
      Button('Change Indicator Corner Radius').width('100%').margin({ bottom: '12vp' })
        .onClick((event?: ClickEvent) => {
          // Configure the animation for the underline corner radius attribute.
          if (this.borderFlag) {
            this.getUIContext()?.animateTo({
              duration: 1000, // Animation duration.
              curve: Curve.Linear, // Animation curve.
              delay: 200, // Animation delay.
              iterations: 1, // Number of playback times.
              playMode: PlayMode.Normal, // Animation playback mode.
              onFinish: () => {
                console.info('play end');
              }
            }, () => {
              this.indicatorBorderRadius = 0;
            });
          } else {
            this.getUIContext()?.animateTo({
              duration: 1000, // Animation duration.
              curve: Curve.Linear, // Animation curve.
              delay: 200, // Animation delay.
              iterations: 1, // Number of playback times.
              playMode: PlayMode.Normal, // Animation playback mode.
              onFinish: () => {
                console.info('play end');
              }
            }, () => {
              this.indicatorBorderRadius = 5;
            });
          }
          this.borderFlag = !this.borderFlag;
        })
      Button('Change Indicator Spacing').width('100%').margin({ bottom: '12vp' })
        .onClick((event?: ClickEvent) => {
          // Configure the animation for the underline spacing attribute.
          if (this.spaceFlag) {
            this.getUIContext()?.animateTo({
              duration: 1000, // Animation duration.
              curve: Curve.Linear, // Animation curve.
              delay: 200, // Animation delay.
              iterations: 1, // Number of playback times.
              playMode: PlayMode.Normal, // Animation playback mode.
              onFinish: () => {
                console.info('play end');
              }
            }, () => {
              this.indicatorSpace = 20;
            });
          } else {
            this.getUIContext()?.animateTo({
              duration: 1000, // Animation duration.
              curve: Curve.Linear, // Animation curve.
              delay: 200, // Animation delay.
              iterations: 1, // Number of playback times.
              playMode: PlayMode.Normal, // Animation playback mode.
              onFinish: () => {
                console.info('play end');
              }
            }, () => {
              this.indicatorSpace = 10;
            });
          }
          this.spaceFlag = !this.spaceFlag;
        })
      Tabs({ barPosition: BarPosition.End, controller: this.controller }) {
        TabContent() {
          Column().width('100%').height('100%').backgroundColor(Color.Pink).borderRadius('12vp')
        }.tabBar(SubTabBarStyle.of('pink')
          .indicator({
            color: this.indicatorColor, // Indicator color.
            height: this.indicatorHeight, // Indicator height.
            width: this.indicatorWidth, // Indicator width.
            borderRadius: this.indicatorBorderRadius, // Rounded corner radius of the indicator.
            marginTop: this.indicatorSpace // Spacing between the indicator and text.
          })
          .selectedMode(this.selectedMode)
          .board({ borderRadius: this.subTabBorderRadius })
          .labelStyle({})
        )

        TabContent() {
          Column().width('100%').height('100%').backgroundColor(Color.Yellow).borderRadius('12vp')
        }.tabBar('yellow')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor(Color.Blue).borderRadius('12vp')
        }.tabBar('blue')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor(Color.Green).borderRadius('12vp')
        }.tabBar('green')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor(Color.Gray).borderRadius('12vp')
        }.tabBar('gray')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor(Color.Orange).borderRadius('12vp')
        }.tabBar('orange')
      }
      .vertical(false)
      .scrollable(true)
      .barMode(BarMode.Scrollable)
      .barHeight(140)
      .animationDuration(400)
      .onChange((index: number) => {
        console.info(index.toString());
      })
      .backgroundColor(0xF5F5F5)
      .height(320)
    }.width('100%').height(250).padding({ top: '24vp', left: '24vp', right: '24vp' })
  }
}
```

### Example 5: Setting Adaptive Height for Subtab Text

This example demonstrates how to achieve adaptive height for subtab text using [heightAdaptivePolicy](#labelstyle10).



```TypeScript
// xxx.ets
@Entry
@Component
struct TabsTextOverflow {
  private controller: TabsController = new TabsController();

  build() {
    Column() {
      Tabs({ barPosition: BarPosition.Start, controller: this.controller }) {
        TabContent() {
          Column() {
            Text('Use an ellipsis').fontSize(30).fontColor(0xFF000000)
          }.width('100%').height('100%').backgroundColor(Color.Pink)
        }
        .tabBar(SubTabBarStyle.of('Start [Use an ellipsis; Use an ellipsis] End')
          .labelStyle({
            overflow: TextOverflow.Ellipsis,
            maxLines: 1,
            minFontSize: 10,
            heightAdaptivePolicy: TextHeightAdaptivePolicy.MAX_LINES_FIRST,
            font: { size: 20 }
          }))

        TabContent() {
          Column() {
            Text('Scale down and then clip').fontSize(30).fontColor(0xFF000000)
          }.width('100%').height('100%').backgroundColor(Color.Pink)
        }
        .tabBar(SubTabBarStyle.of('Start [Scale down and then clip; Scale down and then clip] End')
          .labelStyle({
            overflow: TextOverflow.Clip,
            maxLines: 1,
            minFontSize: 15,
            maxFontSize: 15,
            heightAdaptivePolicy: TextHeightAdaptivePolicy.MIN_FONT_SIZE_FIRST,
            font: { size: 20 }
          }))

        TabContent() {
          Column() {
            Text('Scale down, start a new line, and then clip').fontSize(30).fontColor(0xFF000000)
          }.width('100%').height('100%').backgroundColor(Color.Pink)
        }
        .tabBar(SubTabBarStyle.of('Start [Scale down, start a new line, and then clip; Scale down, start a new line, and then clip] End')
          .labelStyle({
            overflow: TextOverflow.Clip,
            maxLines: 2,
            minFontSize: 15,
            maxFontSize: 15,
            heightAdaptivePolicy: TextHeightAdaptivePolicy.MIN_FONT_SIZE_FIRST,
            font: { size: 20 }
          }))

        TabContent() {
          Column() {
            Text('Start a new line').fontSize(30).fontColor(0xFF000000)
          }
          .width('100%').height('100%').backgroundColor(Color.Pink)
        }.tabBar(SubTabBarStyle.of('Start [Start a new line; Start a new line; Start a new line; Start a new line; Start a new line] End')
          .labelStyle({
            overflow: TextOverflow.Clip,
            maxLines: 10,
            minFontSize: 10,
            heightAdaptivePolicy: TextHeightAdaptivePolicy.MAX_LINES_FIRST,
            font: { size: 20 }
          }))
      }
      .vertical(true).scrollable(true)
      .barMode(BarMode.Fixed)
      .barHeight(720)
      .barWidth(200).animationDuration(400)
      .onChange((index: number) => {
        console.info(index.toString());
      })
      .height('100%').width('100%')
    }
    .height('100%')
  }
}
```

### Example 6: Setting Basic Attributes for Bottom Tabs

This example demonstrates how to set basic attributes for bottom tabs using [padding](#padding10), [verticalAlign](#verticalalign10), [layoutMode](#layoutmode10), and [symmetricExtensible](arkts-arkui-tabcontent-comp-bottomtabbarstyle-c.md#symmetricextensible).



```TypeScript
// xxx.ets
@Entry
@Component
struct TabContentExample6 {
  private controller: TabsController = new TabsController();
  @State text: string = '2';
  @State tabPadding: number = 0;
  @State symmetricExtensible: boolean = false;
  @State layoutMode: LayoutMode = LayoutMode.VERTICAL;
  @State verticalAlign: VerticalAlign = VerticalAlign.Center;

  build() {
    Column() {
      Row() {
        Button('padding+10 ' + this.tabPadding)
          .width('47%')
          .height(50)
          .margin({ top: 5 })
          .onClick((event?: ClickEvent) => {
            this.tabPadding += 10;
          })
          .margin({ right: '6%', bottom: '12vp' })
        Button('padding-10 ' + this.tabPadding)
          .width('47%')
          .height(50)
          .margin({ top: 5 })
          .onClick((event?: ClickEvent) => {
            this.tabPadding -= 10;
          })
          .margin({ bottom: '12vp' })
      }

      Row() {
        Button('Add Text')
          .width('47%')
          .height(50)
          .margin({ top: 5 })
          .onClick((event?: ClickEvent) => {
            this.text += 'Add Text';
          })
          .margin({ right: '6%', bottom: '12vp' })
        Button('Reset Text')
          .width('47%')
          .height(50)
          .margin({ top: 5 })
          .onClick((event?: ClickEvent) => {
            this.text = '2';
          })
          .margin({ bottom: '12vp' })
      }

      Row() {
        Button('Set SymmetricExtensible to ' + this.symmetricExtensible)
          .width('100%')
          .height(50)
          .margin({ top: 5 })
          .onClick((event?: ClickEvent) => {
            this.symmetricExtensible = !this.symmetricExtensible;
          })
          .margin({ bottom: '12vp' })
      }

      Row() {
        Button('Vertical Layout')
          .width('47%')
          .height(50)
          .margin({ top: 5 })
          .onClick((event?: ClickEvent) => {
            this.layoutMode = LayoutMode.VERTICAL;
          })
          .margin({ right: '6%', bottom: '12vp' })
        Button('Horizontal Layout')
          .width('47%')
          .height(50)
          .margin({ top: 5 })
          .onClick((event?: ClickEvent) => {
            this.layoutMode = LayoutMode.HORIZONTAL;
          })
          .margin({ bottom: '12vp' })
      }

      Row() {
        Button('VerticalAlign.Top')
          .width('100%')
          .height(50)
          .margin({ top: 5 })
          .onClick((event?: ClickEvent) => {
            this.verticalAlign = VerticalAlign.Top;
          })
          .margin({ bottom: '12vp' })
      }

      Row() {
        Button('VerticalAlign.Center')
          .width('100%')
          .height(50)
          .margin({ top: 5 })
          .onClick((event?: ClickEvent) => {
            this.verticalAlign = VerticalAlign.Center;
          })
          .margin({ bottom: '12vp' })
      }

      Row() {
        Button('VerticalAlign.Bottom')
          .width('100%')
          .height(50)
          .margin({ top: 5 })
          .onClick((event?: ClickEvent) => {
            this.verticalAlign = VerticalAlign.Bottom;
          })
          .margin({ bottom: '12vp' })
      }


      Tabs({ barPosition: BarPosition.End, controller: this.controller }) {
        TabContent() {
          Column().width('100%').height('100%').backgroundColor(Color.Pink)
        }.tabBar(BottomTabBarStyle.of($r('sys.media.ohos_app_icon'), '1'))

        TabContent() {
          Column().width('100%').height('100%').backgroundColor(Color.Green)
        }.tabBar(BottomTabBarStyle.of($r('sys.media.ohos_app_icon'), this.text)
          .padding(this.tabPadding)
          .verticalAlign(this.verticalAlign)
          .layoutMode(this.layoutMode)
          .symmetricExtensible(this.symmetricExtensible))

        TabContent() {
          Column().width('100%').height('100%').backgroundColor(Color.Blue)
        }.tabBar(BottomTabBarStyle.of($r('sys.media.ohos_app_icon'), '3'))
      }
      .animationDuration(300)
      .height('60%')
      .backgroundColor(0xf1f3f5)
      .barMode(BarMode.Fixed)
    }
    .width('100%')
    .height(500)
    .margin({ top: 5 })
    .padding('24vp')
  }
}
```

### Example 7: Setting Text and Icon Colors for Subtabs and Bottom Tabs

This example demonstrates how to change the text color of subtabs and bottom tabs using unselectedColor and selectedColor in [LabelStyle](#labelstyle10) and

how to change the icon color of bottom tabs using unselectedColor and selectedColor in [iconStyle](#iconstyle12).

> NOTE
> 
> The resources used in this example are not located in the src > main > resource directory. Starting from DevEco Studio 6.0.0 Beta2, the resources that are located outside the resources directory are not packaged by default when a project or module is created. To package these resources, go to buildOptions > resOptions > copyCodeResource in the module's build-profile.json5 file, and set enable to true. For details, see the description of [resOptions](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-hvigor-build-profile#section754823013348).



```TypeScript
// xxx.ets
@Entry
@Component
struct TabBarStyleExample {
  build() {
    Column({ space: 5 }) {
      Text('Subtab style')
      Column() {
        Tabs({ barPosition: BarPosition.Start }) {
          TabContent() {
            Column().width('100%').height('100%').backgroundColor(Color.Pink)
          }.tabBar(new SubTabBarStyle('Pink')
            .labelStyle({ unselectedColor: Color.Red, selectedColor: Color.Green }))

          TabContent() {
            Column().width('100%').height('100%').backgroundColor(Color.Yellow)
          }.tabBar(new SubTabBarStyle('Yellow')
            .labelStyle({ unselectedColor: Color.Red, selectedColor: Color.Green }))

          TabContent() {
            Column().width('100%').height('100%').backgroundColor(Color.Blue)
          }.tabBar(new SubTabBarStyle('Blue')
            .labelStyle({ unselectedColor: Color.Red, selectedColor: Color.Green }))

          TabContent() {
            Column().width('100%').height('100%').backgroundColor(Color.Green)
          }.tabBar(new SubTabBarStyle('Green')
            .labelStyle({ unselectedColor: Color.Red, selectedColor: Color.Green })
          )
        }
        .vertical(false)
        .scrollable(true)
        .barMode(BarMode.Fixed)
        .onChange((index: number) => {
          console.info(index.toString());
        })
        .width('100%')
        .backgroundColor(0xF1F3F5)
      }.width('100%').height(200)

      Text('Bottom tab style')
      Column() {
        Tabs({ barPosition: BarPosition.End }) {
          TabContent() {
            Column().width('100%').height('100%').backgroundColor(Color.Pink)
          }
          // The common directory is at the same level as the pages directory.
          .tabBar(new BottomTabBarStyle('/common/public_icon_off.svg', 'pink')
            .labelStyle({ unselectedColor: Color.Red, selectedColor: Color.Green })
            .iconStyle({ unselectedColor: Color.Red, selectedColor: Color.Green })
          )

          TabContent() {
            Column().width('100%').height('100%').backgroundColor(Color.Yellow)
          }.tabBar(new BottomTabBarStyle('/common/public_icon_off.svg', 'Yellow')
            .labelStyle({ unselectedColor: Color.Red, selectedColor: Color.Green })
            .iconStyle({ unselectedColor: Color.Red, selectedColor: Color.Green })
          )

          TabContent() {
            Column().width('100%').height('100%').backgroundColor(Color.Blue)
          }.tabBar(new BottomTabBarStyle('/common/public_icon_off.svg', 'Blue')
            .labelStyle({ unselectedColor: Color.Red, selectedColor: Color.Green })
            .iconStyle({ unselectedColor: Color.Red, selectedColor: Color.Green })
          )

          TabContent() {
            Column().width('100%').height('100%').backgroundColor(Color.Green)
          }.tabBar(new BottomTabBarStyle('/common/public_icon_off.svg', 'Green')
            .labelStyle({ unselectedColor: Color.Red, selectedColor: Color.Green })
            .iconStyle({ unselectedColor: Color.Red, selectedColor: Color.Green })
          )
        }
        .vertical(false)
        .scrollable(true)
        .barMode(BarMode.Fixed)
        .onChange((index: number) => {
          console.info(index.toString());
        })
        .width('100%')
        .backgroundColor(0xF1F3F5)
      }.width('100%').height(200)
    }
  }
}
```

### Example 8: Using Symbol Icons for Bottom Tabs

This example shows how to use symbols as icons in [BottomTabBarStyle](arkts-arkui-tabcontent-comp-bottomtabbarstyle-c.md).



```TypeScript
// xxx.ets
import { SymbolGlyphModifier } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State symbolModifier1: SymbolGlyphModifier = new SymbolGlyphModifier($r('sys.symbol.ohos_wifi'));
  @State symbolModifier2: SymbolGlyphModifier = new SymbolGlyphModifier($r('sys.symbol.ellipsis_bubble'));
  @State symbolModifier3: SymbolGlyphModifier = new SymbolGlyphModifier($r('sys.symbol.dot_video'));
  @State symbolModifier4: SymbolGlyphModifier = new SymbolGlyphModifier($r('sys.symbol.exposure'));
  build() {
    Column({space: 5}) {
      Text('Bottom tab style')
      Column() {
        Tabs({barPosition: BarPosition.End}) {
          TabContent() {
            Column().width('100%').height('100%').backgroundColor(Color.Pink)
          }.tabBar(new BottomTabBarStyle({
            normal: this.symbolModifier1,
          }, 'Pink'))
          .onWillShow(() => {
            console.info('Pink will show');
          })
          .onWillHide(() => {
            console.info('Pink will hide');
          })

          TabContent() {
            Column().width('100%').height('100%').backgroundColor(Color.Orange)
          }.tabBar(new BottomTabBarStyle({
            normal: this.symbolModifier2,
          }, 'Orange'))
          .onWillShow(() => {
            console.info('Orange will show');
          })
          .onWillHide(() => {
            console.info('Orange will hide');
          })

          TabContent() {
            Column().width('100%').height('100%').backgroundColor(Color.Blue)
          }.tabBar(new BottomTabBarStyle({
            normal: this.symbolModifier3,
          }, 'Blue'))
          .onWillShow(() => {
            console.info('Blue will show');
          })
          .onWillHide(() => {
            console.info('Blue will hide');
          })

          TabContent() {
            Column().width('100%').height('100%').backgroundColor(Color.Green)
          }.tabBar(new BottomTabBarStyle({
            normal: this.symbolModifier4,
          }, 'Green'))
          .onWillShow(() => {
            console.info('Green will show');
          })
          .onWillHide(() => {
            console.info('Green will hide');
          })
        }
        .vertical(false)
        .scrollable(true)
        .barMode(BarMode.Fixed)
        .onChange((index: number) => {
          console.info(index.toString());
        })
        .width('100%')
        .backgroundColor(0xF1F3F5)
      }.width('100%').height(200)
    }
  }
}
```

### Example 9: Setting TabBar Using ComponentContent

This example demonstrates how to use ComponentContent to encapsulate component content and set the [TabBar](arkts-arkui-tabcontent-comp-attribute.md#tabbar). The update API of ComponentContent is used to update the TabBar.



```TypeScript
// xxx.ets
import { ComponentContent, UIContext } from '@kit.ArkUI';

class Params {
  text: string = '';
  fontColor: string = '';

  constructor(text: string, fontColor: string) {
    this.text = text;
    this.fontColor = fontColor;
  }
}

@Builder
function buildText(params: Params) {
  Column() {
    Text(params.text)
      .fontColor(params.fontColor)
      .fontSize(20)
      .fontWeight(FontWeight.Bold)
      .margin(20)
  }
}

@Entry
@Component
struct Index {
  @State currentIndex: number = 0;
  @State message1: string = 'tabBar1';
  @State message2: string = 'tabBar2';
  unselectedFontColor: string = '#182431';
  selectedFontColor: string = '#007DFF';
  context: UIContext = this.getUIContext();
  private count1 = 0;
  private count2 = 0;
  private controller: TabsController = new TabsController();

  getTabBar1() {
    this.tabBar1.update(new Params(this.message1,
      this.currentIndex === 0 ? this.selectedFontColor : this.unselectedFontColor));
    return this.tabBar1;
  }

  getTabBar2() {
    this.tabBar2.update(new Params(this.message2,
      this.currentIndex === 1 ? this.selectedFontColor : this.unselectedFontColor));
    return this.tabBar2;
  }

  tabBar1: ComponentContent<Params> =
    new ComponentContent<Params>(this.context, wrapBuilder<[Params]>(buildText),
      new Params(this.message1, this.selectedFontColor));
  tabBar2: ComponentContent<Params> =
    new ComponentContent<Params>(this.context, wrapBuilder<[Params]>(buildText),
      new Params(this.message2, this.unselectedFontColor));

  build() {
    Row() {
      Column() {
        Button('Update tabBar1').width('90%').margin(20)
          .onClick((event?: ClickEvent) => {
            this.count1 += 1;
            this.message1 = 'Update 1_' + this.count1.toString();
            this.tabBar1.update(new Params(this.message1, this.unselectedFontColor));
          })
        Button('Update tabBar2').width('90%').margin(20)
          .onClick((event?: ClickEvent) => {
            this.count2 += 1;
            this.message2 = 'Update 2_' + this.count2.toString();
            this.tabBar2.update(new Params(this.message2, this.unselectedFontColor));
          })
        Tabs({ barPosition: BarPosition.Start, controller: this.controller }) {
          TabContent() {
            Column().width('100%').height('100%').backgroundColor(Color.Pink).borderRadius('12vp')
          }.tabBar(this.getTabBar1())

          TabContent() {
            Column().width('100%').height('100%').backgroundColor(Color.Blue).borderRadius('12vp')
          }.tabBar(this.getTabBar2())
        }
        .vertical(false)
        .barWidth(414)
        .barHeight(96)
        .width(414)
        .height(414)
        .backgroundColor('#F1F3F5')
        .margin({ top: 20 })
        .onChange((index: number) => {
          this.currentIndex = index;
        })
      }
      .width('100%')
      .height('100%')
    }
    .height('100%')
  }
}
```

### Example 10: Preloading Child Nodes Using ComponentContent

This example demonstrates how to use ComponentContent to set the TabBar and preload child nodes using the [preloadItems](ts-container-tabs.md#preloaditems12) API of TabsController.



```TypeScript
// xxx.ets
import { BusinessError } from '@kit.BasicServicesKit';
import { ComponentContent } from '@kit.ArkUI';

class Params {
  text: string = '';
  fontColor: string = '';

  constructor(text: string, fontColor: string) {
    this.text = text;
    this.fontColor = fontColor;
  }
}

@Component
struct imageCom {
  build() {
    Image($r('app.media.startIcon'))
      .alt($r('app.media.background'))
      .width(15)
      .height(15)
  }
}

@Builder
function TabBuilder(params: Params) {
  Column({ space: 4 }) {
    imageCom()

    Text(params.text)
      .fontSize(10)
      .fontColor(params.fontColor)
  }
}

@Entry
@Component
struct TabsPreloadItems {
  @State currentIndex: number = 0;
  private tabsController: TabsController = new TabsController();
  context: UIContext = this.getUIContext();
  unselectedFontColor: string = '#182431';
  selectedFontColor: string = '#007DFF';

  getTabBar1() {
    this.tabBar1.update(new Params('green',
      this.currentIndex === 0 ? this.selectedFontColor : this.unselectedFontColor));
    return this.tabBar1;
  }

  getTabBar2() {
    this.tabBar2.update(new Params('blue',
      this.currentIndex === 1 ? this.selectedFontColor : this.unselectedFontColor));
    return this.tabBar2;
  }

  getTabBar3() {
    this.tabBar3.update(new Params('yellow',
      this.currentIndex === 2 ? this.selectedFontColor : this.unselectedFontColor));
    return this.tabBar3;
  }

  getTabBar4() {
    this.tabBar4.update(new Params('pink',
      this.currentIndex === 3 ? this.selectedFontColor : this.unselectedFontColor));
    return this.tabBar4;
  }

  tabBar1: ComponentContent<Params> =
    new ComponentContent<Params>(this.context, wrapBuilder<[Params]>(TabBuilder),
      new Params('green', this.selectedFontColor));
  tabBar2: ComponentContent<Params> =
    new ComponentContent<Params>(this.context, wrapBuilder<[Params]>(TabBuilder),
      new Params('blue', this.unselectedFontColor));
  tabBar3: ComponentContent<Params> =
    new ComponentContent<Params>(this.context, wrapBuilder<[Params]>(TabBuilder),
      new Params('yellow', this.unselectedFontColor));
  tabBar4: ComponentContent<Params> =
    new ComponentContent<Params>(this.context, wrapBuilder<[Params]>(TabBuilder),
      new Params('pink', this.unselectedFontColor));

  build() {
    Column() {
      Tabs({ index: this.currentIndex, controller: this.tabsController }) {
        TabContent() {
          MyComponent({ color: '#00CB87' })
        }.tabBar(this.getTabBar1())

        TabContent() {
          MyComponent({ color: '#007DFF' })
        }.tabBar(this.getTabBar2())

        TabContent() {
          MyComponent({ color: '#FFBF00' })
        }.tabBar(this.getTabBar3())

        TabContent() {
          MyComponent({ color: '#E67C92' })
        }.tabBar(this.getTabBar4())
      }
      .width(360)
      .height(296)
      .backgroundColor('#F1F3F5')
      .onChange((index: number) => {
        this.currentIndex = index;
      })

      Button('preload items: [1,2,3]')
        .margin(5)
        .onClick(() => {
          // Preload the child nodes whose indexes are 1 to 3.
          this.tabsController.preloadItems([1, 2, 3])
            .then(() => {
              console.info('preloadItems success.');
            })
            .catch((error: BusinessError) => {
              console.error(`preloadItems failed. Code: ${error.code}, message: ${error.message}`);
            });
        })

      Button('preload items: [1]')
        .margin(5)
        .onClick(() => {
          // Preload the child node whose index is 1.
          this.tabsController.preloadItems([1])
            .then(() => {
              console.info('preloadItems success.');
            })
            .catch((error: BusinessError) => {
              console.error(`preloadItems failed. Code: ${error.code}, message: ${error.message}`);
            });
        })
      Button('preload items: [3]')
        .margin(5)
        .onClick(() => {
          // Preload the child node whose index is 3.
          this.tabsController.preloadItems([3])
            .then(() => {
              console.info('preloadItems success.');
            })
            .catch((error: BusinessError) => {
              console.error(`preloadItems failed. Code: ${error.code}, message: ${error.message}`);
            });
        })
    }
  }
}

@Component
struct MyComponent {
  private color: string = '';

  aboutToAppear(): void {
    console.info('aboutToAppear backgroundColor:' + this.color);
  }

  aboutToDisappear(): void {
    console.info('aboutToDisappear backgroundColor:' + this.color);
  }

  build() {
    Column()
      .width('100%')
      .height('100%')
      .backgroundColor(this.color)
  }
}
```

### Example 11: Setting the Indicator of a Subtab to an Image

Since API version 22, this example uses the [indicator](#indicator22) attribute in SubTabBarStyle to implement the subtab indicator in image format.

```TypeScript
import { DrawableDescriptor } from '@kit.ArkUI';

@Entry
@Component
struct TabsIndicatorExample {
  @State pixmapDesc: DrawableDescriptor | null = null;

  async aboutToAppear() {
    const resManager = this.getUIContext().getHostContext()?.resourceManager;
    if (!resManager) {
      return;
    }
    // Replace $r('app.media.indicator') with the image resource file you use.
    let pixmapDescResult = resManager.getDrawableDescriptor($r('app.media.indicator').id);
    if (pixmapDescResult) {
      this.pixmapDesc = pixmapDescResult as DrawableDescriptor;
    }
  }

  build() {
    Column() {
      Tabs() {
        TabContent() {
          Column().width('100%').height('100%').backgroundColor(Color.Pink)
        }.tabBar(SubTabBarStyle.of('TabBar 1')
          .indicator({
            drawable: this.pixmapDesc,
            height: 10,
            width: 70,
            borderRadius: 5,
            marginTop: 5
          }))

        TabContent() {
          Column().width('100%').height('100%').backgroundColor(Color.Green)
        }.tabBar(SubTabBarStyle.of('TabBar 2')
          .indicator({
            drawable: this.pixmapDesc,
            height: 10,
            width: 70,
            borderRadius: 5,
            marginTop: 5
          }))
      }
      .height('60%')
      .backgroundColor(0xf1f3f5)
      .barMode(BarMode.Fixed)
      .barHeight(120)
      .vertical(false)
    }
    .width('100%')
    .height(500)
    .padding('24vp')
  }
}
```
