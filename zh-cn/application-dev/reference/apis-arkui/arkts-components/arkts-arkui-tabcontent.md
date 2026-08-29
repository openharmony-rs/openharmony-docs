# TabContent

仅在[Tabs](../../apis-avsession-kit/arkts-apis/arkts-avsession-avmusictemplate-customelement-i.md#tabs)中使用，对应一个切换页签的内容视图。
> **说明：**
> - 该组件默认设置了clip属性的值为true，若需要扩展内容区到组件外显示，需先关闭clip属性。

## 子组件

支持单个子组件。

> **说明：**
> 
> 可内置系统组件和自定义组件，支持渲染控制类型（[if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md)、
> [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md)和
> [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)）。

## TabContent

```TypeScript
TabContent()
```

创建TabContent页签和内容。

> **说明：**
> 
> TabContent组件仅能作为Tabs组件的子组件使用，否则会导致组件无法正常显示。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [BoardStyle](arkts-arkui-boardstyle-i.md) | 背板风格对象。 |
| [DrawableTabBarIndicator](arkts-arkui-drawabletabbarindicator-i.md) | 使用图片资源作为下划线的对象。 |
| [IndicatorStyle](arkts-arkui-indicatorstyle-i.md) | 下划线风格对象。 |
| [LabelStyle](arkts-arkui-labelstyle-i.md) | label文本和字体的样式对象。 |
| [TabBarIconStyle](arkts-arkui-tabbariconstyle-i.md) | Label图标样式对象。 |
| [TabBarOptions](arkts-arkui-tabbaroptions-i.md) | 设置页签内的图片和文字内容。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [DrawableDescriptor](arkts-arkui-drawabledescriptor-t.md) | 作为DrawableTabBarIndicator对象中drawable属性的入参对象。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [LayoutMode](arkts-arkui-layoutmode-e.md) | 页签内容排布方式枚举。 |
| [SelectedMode](arkts-arkui-selectedmode-e.md) | 选中子页签的显示模式枚举。 |

## 示例

此示例的资源不在src > main > resource目录下，从DevEco Studio 6.0.0 Beta2开始，新建工程或者模块时，默认创建的模块不会对非resources目录下的资源进行打包，需使能相关开关：模块的build-profile.json5中buildOptions > resOptions > copyCodeResource > enable设置为true，详见[resOptions](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ide-hvigor-build-profile#section754823013348)中相关介绍。

```TypeScript
// xxx.ets
@Entry
@Component
struct TabContentExample {
  @State fontColor: string = '#182431';
  @State selectedFontColor: string = '#007DFF';
  @State currentIndex: number = 0;
  @State selectedIndex: number = 0;
  // 创建Tabs控制器，用于控制TabContent切换
  private controller: TabsController = new TabsController();

  // 自定义TabBar构建器，根据选中状态切换图标和文字颜色
  @Builder tabBuilder(index: number) {
    Column() {
      // common目录与pages同级
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
      // 创建Tabs组件，设置TabBar位置在底部并绑定控制器
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
        }.tabBar(this.tabBuilder(0)) // 设置TabBar为自定义样式

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
        // currentIndex控制TabContent显示页签，selectedIndex控制自定义TabBar颜色切换
        this.currentIndex = index;
        this.selectedIndex = index;
      })
      .onAnimationStart((index: number, targetIndex: number, event: TabsAnimationEvent) => {
        // 当前页签索引与目标索引一致时，无需更新状态
        if (index === targetIndex) {
          return;
        }
        // selectedIndex控制自定义TabBar内Image和Text颜色切换
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

此示例的资源不在src > main > resource目录下，从DevEco Studio 6.0.0 Beta2开始，新建工程或者模块时，默认创建的模块不会对非resources目录下的资源进行打包，需使能相关开关：模块的build-profile.json5中buildOptions > resOptions > copyCodeResource > enable设置为true，详见[resOptions](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ide-hvigor-build-profile#section754823013348)中相关介绍。

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
      // common目录与pages同级
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
      // 创建Tabs组件，设置TabBar位置在起始端并绑定控制器
      Tabs({ barPosition: BarPosition.Start, controller: this.controller }) {
        TabContent()
          .tabBar(this.tabBuilder(0)) // 设置TabBar为自定义样式
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
        // currentIndex控制TabContent显示页签，selectedIndex控制自定义TabBar颜色切换
        this.currentIndex = index;
        this.selectedIndex = index;
      })
      .onAnimationStart((index: number, targetIndex: number, event: TabsAnimationEvent) => {
        // 当前页签索引与目标索引一致时，无需更新状态
        if (index === targetIndex) {
          return;
        }
        // selectedIndex控制自定义TabBar内Image和Text颜色切换
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

本示例使用了[SubTabBarStyle](arkts-arkui-subtabbarstyle-c.md)、[BottomTabBarStyle](arkts-arkui-bottomtabbarstyle-c.md)实现了子页签、底部页签和侧边页签。

```TypeScript
// xxx.ets
@Entry
@Component
struct TabBarStyleExample {
  build() {
    Column({ space: 5 }) {
      Text('子页签样式')
      Column() {
        // 创建Tabs组件，设置TabBar位置在起始端
        Tabs({ barPosition: BarPosition.Start }) {
          TabContent() {
            Column().width('100%').height('100%').backgroundColor(Color.Pink)
          }.tabBar(new SubTabBarStyle('Pink')) // 设置TabBar为子页签样式
          .onWillShow(() => {
            // TabContent将要显示时触发回调
            console.info('Pink will show');
          })
          .onWillHide(() => {
            // TabContent将要隐藏时触发回调
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
      Text('底部页签样式')
      Column() {
        // 创建Tabs组件，设置TabBar位置在底部
        Tabs({ barPosition: BarPosition.End }) {
          TabContent() {
            Column().width('100%').height('100%').backgroundColor(Color.Pink)
          }.tabBar(new BottomTabBarStyle($r('sys.media.ohos_app_icon'), 'Pink')) // 设置TabBar为底部页签样式
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
      Text('侧边页签样式')
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
        .vertical(true) // 设置为侧边页签模式
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

本示例通过SubTabBarStyle中的indicator属性，实现了子页签下划线基本属性的展示。

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
      Button('下划线颜色变化').width('100%').margin({ bottom: '12vp' })
        .onClick((event?: ClickEvent) => {
          // 对下划线颜色属性进行动画配置
          if (this.colorFlag) {
            this.getUIContext()?.animateTo({
              duration: 1000, // 动画时长
              curve: Curve.Linear, // 动画曲线
              delay: 200, // 动画延迟
              iterations: 1, // 播放次数
              playMode: PlayMode.Normal, // 动画模式
              onFinish: () => {
                console.info('play end');
              }
            }, () => {
              this.indicatorColor = Color.Red;
            });
          } else {
            this.getUIContext()?.animateTo({
              duration: 1000, // 动画时长
              curve: Curve.Linear, // 动画曲线
              delay: 200, // 动画延迟
              iterations: 1, // 播放次数
              playMode: PlayMode.Normal, // 动画模式
              onFinish: () => {
                console.info('play end');
              }
            }, () => {
              this.indicatorColor = Color.Yellow;
            });
          }
          this.colorFlag = !this.colorFlag;
        })
      Button('下划线高度变化').width('100%').margin({ bottom: '12vp' })
        .onClick((event?: ClickEvent) => {
          // 对下划线高度属性进行动画配置
          if (this.heightFlag) {
            this.getUIContext()?.animateTo({
              duration: 1000, // 动画时长
              curve: Curve.Linear, // 动画曲线
              delay: 200, // 动画延迟
              iterations: 1, // 播放次数
              playMode: PlayMode.Normal, // 动画模式
              onFinish: () => {
                console.info('play end');
              }
            }, () => {
              this.indicatorHeight = 20;
            });
          } else {
            this.getUIContext()?.animateTo({
              duration: 1000, // 动画时长
              curve: Curve.Linear, // 动画曲线
              delay: 200, // 动画延迟
              iterations: 1, // 播放次数
              playMode: PlayMode.Normal, // 动画模式
              onFinish: () => {
                console.info('play end');
              }
            }, () => {
              this.indicatorHeight = 10;
            });
          }
          this.heightFlag = !this.heightFlag;
        })
      Button('下划线宽度变化').width('100%').margin({ bottom: '12vp' })
        .onClick((event?: ClickEvent) => {
          // 对下划线宽度属性进行动画配置
          if (this.widthFlag) {
            this.getUIContext()?.animateTo({
              duration: 1000, // 动画时长
              curve: Curve.Linear, // 动画曲线
              delay: 200, // 动画延迟
              iterations: 1, // 播放次数
              playMode: PlayMode.Normal, // 动画模式
              onFinish: () => {
                console.info('play end');
              }
            }, () => {
              this.indicatorWidth = 30;
            });
          } else {
            this.getUIContext()?.animateTo({
              duration: 1000, // 动画时长
              curve: Curve.Linear, // 动画曲线
              delay: 200, // 动画延迟
              iterations: 1, // 播放次数
              playMode: PlayMode.Normal, // 动画模式
              onFinish: () => {
                console.info('play end');
              }
            }, () => {
              this.indicatorWidth = 50;
            });
          }
          this.widthFlag = !this.widthFlag;
        })
      Button('下划线圆角半径变化').width('100%').margin({ bottom: '12vp' })
        .onClick((event?: ClickEvent) => {
          // 对下划线圆角半径属性进行动画配置
          if (this.borderFlag) {
            this.getUIContext()?.animateTo({
              duration: 1000, // 动画时长
              curve: Curve.Linear, // 动画曲线
              delay: 200, // 动画延迟
              iterations: 1, // 播放次数
              playMode: PlayMode.Normal, // 动画模式
              onFinish: () => {
                console.info('play end');
              }
            }, () => {
              this.indicatorBorderRadius = 0;
            });
          } else {
            this.getUIContext()?.animateTo({
              duration: 1000, // 动画时长
              curve: Curve.Linear, // 动画曲线
              delay: 200, // 动画延迟
              iterations: 1, // 播放次数
              playMode: PlayMode.Normal, // 动画模式
              onFinish: () => {
                console.info('play end');
              }
            }, () => {
              this.indicatorBorderRadius = 5;
            });
          }
          this.borderFlag = !this.borderFlag;
        })
      Button('下划线间距变化').width('100%').margin({ bottom: '12vp' })
        .onClick((event?: ClickEvent) => {
          // 对下划线间距属性进行动画配置
          if (this.spaceFlag) {
            this.getUIContext()?.animateTo({
              duration: 1000, // 动画时长
              curve: Curve.Linear, // 动画曲线
              delay: 200, // 动画延迟
              iterations: 1, // 播放次数
              playMode: PlayMode.Normal, // 动画模式
              onFinish: () => {
                console.info('play end');
              }
            }, () => {
              this.indicatorSpace = 20;
            });
          } else {
            this.getUIContext()?.animateTo({
              duration: 1000, // 动画时长
              curve: Curve.Linear, // 动画曲线
              delay: 200, // 动画延迟
              iterations: 1, // 播放次数
              playMode: PlayMode.Normal, // 动画模式
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
            color: this.indicatorColor, // 下划线颜色
            height: this.indicatorHeight, // 下划线高度
            width: this.indicatorWidth, // 下划线宽度
            borderRadius: this.indicatorBorderRadius, // 下划线圆角半径
            marginTop: this.indicatorSpace // 下划线与文字间距
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

本示例通过heightAdaptivePolicy实现了子页签文本高度自适应。

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
            Text('单行省略号截断').fontSize(30).fontColor(0xFF000000)
          }.width('100%').height('100%').backgroundColor(Color.Pink)
        }
        .tabBar(SubTabBarStyle.of('开始【单行省略号截断单行省略号截断单行省略号截断单行省略号截断单行省略号截断单行省略号截断单行省略号截断单行省略号截断单行省略号截断单行省略号截断】结束')
          .labelStyle({
            overflow: TextOverflow.Ellipsis,
            maxLines: 1,
            minFontSize: 10,
            heightAdaptivePolicy: TextHeightAdaptivePolicy.MAX_LINES_FIRST,
            font: { size: 20 }
          }))

        TabContent() {
          Column() {
            Text('先缩小再截断').fontSize(30).fontColor(0xFF000000)
          }.width('100%').height('100%').backgroundColor(Color.Pink)
        }
        .tabBar(SubTabBarStyle.of('开始【先缩小再截断先缩小再截断先缩小再截断先缩小再截断先缩小再截断先缩小再截断先缩小再截断先缩小再截断先缩小再截断先缩小再截断先缩小再截断先缩小再截断先缩小再截断先缩小再截断】结束')
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
            Text('先缩小再换行再截断').fontSize(30).fontColor(0xFF000000)
          }.width('100%').height('100%').backgroundColor(Color.Pink)
        }
        .tabBar(SubTabBarStyle.of('开始【先缩小再换行再截断先缩小再换行再截断先缩小再换行再截断先缩小再换行再截断先缩小再换行再截断先缩小再换行再截断先缩小再换行再截断先缩小再换行再截断】结束')
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
            Text('换行').fontSize(30).fontColor(0xFF000000)
          }
          .width('100%').height('100%').backgroundColor(Color.Pink)
        }.tabBar(SubTabBarStyle.of('开始【换行换行换行换行换行换行换行换行换行换行换行换行换行换行换行】结束')
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

本示例通过padding、verticalAlign、layoutMode、[symmetricExtensible](arkts-arkui-bottomtabbarstyle-c.md#symmetricextensible)实现了底部页签基本属性的展示。

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
        Button('文本增加 ')
          .width('47%')
          .height(50)
          .margin({ top: 5 })
          .onClick((event?: ClickEvent) => {
            this.text += '文本增加';
          })
          .margin({ right: '6%', bottom: '12vp' })
        Button('文本重置')
          .width('47%')
          .height(50)
          .margin({ top: 5 })
          .onClick((event?: ClickEvent) => {
            this.text = '2';
          })
          .margin({ bottom: '12vp' })
      }

      Row() {
        Button('symmetricExtensible改变 ' + this.symmetricExtensible)
          .width('100%')
          .height(50)
          .margin({ top: 5 })
          .onClick((event?: ClickEvent) => {
            this.symmetricExtensible = !this.symmetricExtensible;
          })
          .margin({ bottom: '12vp' })
      }

      Row() {
        Button('layoutMode垂直 ')
          .width('47%')
          .height(50)
          .margin({ top: 5 })
          .onClick((event?: ClickEvent) => {
            this.layoutMode = LayoutMode.VERTICAL;
          })
          .margin({ right: '6%', bottom: '12vp' })
        Button('layoutMode水平 ')
          .width('47%')
          .height(50)
          .margin({ top: 5 })
          .onClick((event?: ClickEvent) => {
            this.layoutMode = LayoutMode.HORIZONTAL;
          })
          .margin({ bottom: '12vp' })
      }

      Row() {
        Button('verticalAlign朝上')
          .width('100%')
          .height(50)
          .margin({ top: 5 })
          .onClick((event?: ClickEvent) => {
            this.verticalAlign = VerticalAlign.Top;
          })
          .margin({ bottom: '12vp' })
      }

      Row() {
        Button('verticalAlign居中')
          .width('100%')
          .height(50)
          .margin({ top: 5 })
          .onClick((event?: ClickEvent) => {
            this.verticalAlign = VerticalAlign.Center;
          })
          .margin({ bottom: '12vp' })
      }

      Row() {
        Button('verticalAlign朝下')
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

此示例的资源不在src > main > resource目录下，从DevEco Studio 6.0.0 Beta2开始，新建工程或者模块时，默认创建的模块不会对非resources目录下的资源进行打包，需使能相关开关：模块的build-profile.json5中buildOptions > resOptions > copyCodeResource > enable设置为true，详见[resOptions](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ide-hvigor-build-profile#section754823013348)中相关介绍。

```TypeScript
// xxx.ets
@Entry
@Component
struct TabBarStyleExample {
  build() {
    Column({ space: 5 }) {
      Text('子页签样式')
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

      Text('底部页签样式')
      Column() {
        Tabs({ barPosition: BarPosition.End }) {
          TabContent() {
            Column().width('100%').height('100%').backgroundColor(Color.Pink)
          }
          // common目录与pages同级
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

该示例实现了[BottomTabBarStyle](arkts-arkui-bottomtabbarstyle-c.md)图片传入Symbol。

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
      Text('底部页签样式')
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

该示例实现了通过ComponentContent封装组件内容，设置[TabBar](arkts-arkui-tabcontent-attribute.md#tabbar)。通过ComponentContent的update函数更新TabBar。

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
        Button('更新tabBar1').width('90%').margin(20)
          .onClick((event?: ClickEvent) => {
            this.count1 += 1;
            this.message1 = 'Update 1_' + this.count1.toString();
            this.tabBar1.update(new Params(this.message1, this.unselectedFontColor));
          })
        Button('更新tabBar2').width('90%').margin(20)
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

该示例实现了通过ComponentContent设置TabBar，使用TabsController的preloadItems预加载子节点。

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
          // 预加载index为1~3的子节点
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
          // 预加载index为1的子节点
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
          // 预加载index为3的子节点
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

从API version 22开始，新增了入参类型包含图片的indicator属性。

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
    // $r('app.media.indicator')需要替换为开发者所需的图像资源文件。
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
