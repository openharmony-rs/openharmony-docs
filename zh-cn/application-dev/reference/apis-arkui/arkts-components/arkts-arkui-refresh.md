# Refresh

Refresh是提供下拉刷新交互的容器组件，适用于列表数据刷新、页面内容更新等需要用户触发数据更新的场景。它支持自定义刷新区域显示内容和文本、设置下拉偏移量和跟手系数、控制最大下拉距离等，可灵活适配不同应用的下拉刷新需求，提供一致且流 畅的刷新体验。
> **说明：** > > - 该组件从API version 12开始支持与垂直滚动的Swiper和 > Web的联动。当Swiper设置 > loop属性为true时，Refresh无法和Swiper产生联动。 > > - Refresh和内容大小小于组件自身的List组件嵌套使用并且中间还有其他组件时，手势可能会被中间组件响应，导致Refresh未产生下拉刷新效果。此时可以将 > [alwaysEnabled](arkts-arkui-edgeeffectoptions-i.md)参数设为true，List会响应手势并通过嵌套滚动带动Refresh组件产生下拉刷新效果。具体可以参考 > 示例9（不满一屏场景实现下拉刷新）。 > > - 组件内部已绑定手势实现跟手滚动等功能，需要增加自定义手势操作时请参考手势拦截增强进行处理。 > > - 组件无法通过鼠标按下拖动操作进行下拉刷新。

## 子组件

支持单个子组件。从API version 11开始，Refresh子组件会跟随手势下拉而下移。

## Refresh

```TypeScript
Refresh(value: RefreshOptions)
```

创建Refresh容器。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [RefreshOptions](arkts-arkui-refreshoptions-i.md) | 是 | 刷新组件参数。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [RefreshOptions](arkts-arkui-refreshoptions-i.md) | 用于设置Refresh组件参数。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [RefreshStatus](arkts-arkui-refreshstatus-e.md) | RefreshStatus刷新状态枚举。 |

## 示例

刷新区域使用默认刷新样式。

```TypeScript
// xxx.ets
@Entry
@Component
struct RefreshExample {
  @State isRefreshing: boolean = false;
  @State arr: string[] = ['0', '1', '2', '3', '4', '5', '6', '7', '8', '9', '10'];

  build() {
    Column() {
      Row() {
        Button('开始刷新').onClick(() => {
          this.isRefreshing = true;
        })
        Button('停止刷新').onClick(() => {
          this.isRefreshing = false;
        })
      }

      Refresh({ refreshing: $$this.isRefreshing }) {
        List() {
          ForEach(this.arr, (item: string) => {
            ListItem() {
              Text('' + item)
                .width('70%')
                .height(80)
                .fontSize(16)
                .margin(10)
                .textAlign(TextAlign.Center)
                .borderRadius(10)
                .backgroundColor(0xFFFFFF)
            }
          }, (item: string) => item)
        }
        .onScrollIndex((first: number) => {
          console.info(first.toString());
        })
        .width('100%')
        .height('100%')
        .alignListItem(ListItemAlign.Center)
        .scrollBar(BarState.Off)
      }
      .onStateChange((refreshStatus: RefreshStatus) => {
        console.info('Refresh onStateChange state is ' + refreshStatus);
      })
      .onOffsetChange((value: number) => {
        console.info('Refresh onOffsetChange offset:' + value);
      })
      .onRefreshing(() => {
        setTimeout(() => {
          this.isRefreshing = false;
        }, 2000)
        console.info('onRefreshing test');
      })
      .backgroundColor(0x89CFF0)
      .refreshOffset(64)
      .pullToRefresh(true)
    }
  }
}
```

通过[promptText](#refreshoptions对象说明)参数设置刷新区域显示文本。

```TypeScript
// xxx.ets
@Entry
@Component
struct RefreshExample {
  @State isRefreshing: boolean = false;
  @State promptText: string = 'Refreshing...';
  @State arr: string[] = ['0', '1', '2', '3', '4', '5', '6', '7', '8', '9', '10'];

  build() {
    Column() {
      Refresh({ refreshing: $$this.isRefreshing, promptText: this.promptText }) {
        List() {
          ForEach(this.arr, (item: string) => {
            ListItem() {
              Text(item)
                .width('70%')
                .height(80)
                .fontSize(16)
                .margin(10)
                .textAlign(TextAlign.Center)
                .borderRadius(10)
                .backgroundColor(0xFFFFFF)
            }
          }, (item: string) => item)
        }
        .onScrollIndex((first: number) => {
          console.info(first.toString());
        })
        .width('100%')
        .height('100%')
        .alignListItem(ListItemAlign.Center)
        .scrollBar(BarState.Off)
      }
      .backgroundColor(0x89CFF0)
      .pullToRefresh(true)
      .refreshOffset(96)
      .onStateChange((refreshStatus: RefreshStatus) => {
        console.info('Refresh onStateChange state is ' + refreshStatus);
      })
      .onOffsetChange((value: number) => {
        console.info('Refresh onOffsetChange offset:' + value);
      })
      .onRefreshing(() => {
        setTimeout(() => {
          this.isRefreshing = false;
        }, 2000)
        console.info('onRefreshing test');
      })
    }
  }
}
```

通过[builder](#refreshoptions对象说明)参数自定义刷新区域显示内容。

```TypeScript
// xxx.ets
@Entry
@Component
struct RefreshExample {
  @State isRefreshing: boolean = false;
  @State arr: string[] = ['0', '1', '2', '3', '4', '5', '6', '7', '8', '9', '10'];

  @Builder
  customRefreshComponent() {
    Stack() {
      Row() {
        LoadingProgress().height(32)
        Text('Refreshing...').fontSize(16).margin({ left: 20 })
      }
      .alignItems(VerticalAlign.Center)
    }
    .align(Alignment.Center)
    .clip(true)
    // 设置最小高度约束保证自定义组件高度随刷新区域高度变化时自定义组件高度不会低于minHeight。
    .constraintSize({ minHeight: 32 })
    .width('100%')
  }

  build() {
    Column() {
      Refresh({ refreshing: $$this.isRefreshing, builder: this.customRefreshComponent() }) {
        List() {
          ForEach(this.arr, (item: string) => {
            ListItem() {
              Text('' + item)
                .width('70%')
                .height(80)
                .fontSize(16)
                .margin(10)
                .textAlign(TextAlign.Center)
                .borderRadius(10)
                .backgroundColor(0xFFFFFF)
            }
          }, (item: string) => item)
        }
        .onScrollIndex((first: number) => {
          console.info(first.toString());
        })
        .width('100%')
        .height('100%')
        .alignListItem(ListItemAlign.Center)
        .scrollBar(BarState.Off)
      }
      .backgroundColor(0x89CFF0)
      .pullToRefresh(true)
      .refreshOffset(64)
      .onStateChange((refreshStatus: RefreshStatus) => {
        console.info('Refresh onStateChange state is ' + refreshStatus);
      })
      .onRefreshing(() => {
        setTimeout(() => {
          this.isRefreshing = false;
        }, 2000)
        console.info('onRefreshing test');
      })
    }
  }
}
```

通过[refreshingContent](#refreshoptions对象说明)参数自定义刷新区域显示内容。

```TypeScript
// xxx.ets
import { ComponentContent } from '@kit.ArkUI';

class Params {
  refreshStatus: RefreshStatus = RefreshStatus.Inactive;

  constructor(refreshStatus: RefreshStatus) {
    this.refreshStatus = refreshStatus;
  }
}

@Builder
function customRefreshingContent(params: Params) {
  Stack() {
    Row() {
      LoadingProgress().height(32)
      Text('refreshStatus: ' + params.refreshStatus).fontSize(16).margin({ left: 20 })
    }
    .alignItems(VerticalAlign.Center)
  }
  .align(Alignment.Center)
  .clip(true)
  // 设置最小高度约束保证自定义组件高度随刷新区域高度变化时自定义组件高度不会低于minHeight。
  .constraintSize({ minHeight: 32 })
  .width('100%')
}

@Entry
@Component
struct RefreshExample {
  @State isRefreshing: boolean = false;
  @State arr: string[] = ['0', '1', '2', '3', '4', '5', '6', '7', '8', '9', '10'];
  @State refreshStatus: RefreshStatus = RefreshStatus.Inactive;
  private contentNode?: ComponentContent<Object> = undefined;
  private params: Params = new Params(RefreshStatus.Inactive);

  aboutToAppear(): void {
    let uiContext = this.getUIContext();
    this.contentNode = new ComponentContent(uiContext, wrapBuilder(customRefreshingContent), this.params);
  }

  build() {
    Column() {
      Refresh({ refreshing: $$this.isRefreshing, refreshingContent: this.contentNode }) {
        List() {
          ForEach(this.arr, (item: string) => {
            ListItem() {
              Text('' + item)
                .width('70%')
                .height(80)
                .fontSize(16)
                .margin(10)
                .textAlign(TextAlign.Center)
                .borderRadius(10)
                .backgroundColor(0xFFFFFF)
            }
          }, (item: string) => item)
        }
        .onScrollIndex((first: number) => {
          console.info(first.toString());
        })
        .width('100%')
        .height('100%')
        .alignListItem(ListItemAlign.Center)
        .scrollBar(BarState.Off)
      }
      .backgroundColor(0x89CFF0)
      .pullToRefresh(true)
      .refreshOffset(96)
      .onStateChange((refreshStatus: RefreshStatus) => {
        this.refreshStatus = refreshStatus;
        this.params.refreshStatus = refreshStatus;
        // 更新自定义组件内容。
        this.contentNode?.update(this.params);
        console.info('Refresh onStateChange state is ' + refreshStatus);
      })
      .onRefreshing(() => {
        setTimeout(() => {
          this.isRefreshing = false;
        }, 2000)
        console.info('onRefreshing test');
      })
    }
  }
}
```

通过[pullDownRatio](arkts-arkui-refresh-attribute.md#pulldownratio)属性和[onOffsetChange](#onoffsetchange12)事件实现最大下拉距离。

```TypeScript
// xxx.ets
import { ComponentContent } from '@kit.ArkUI';

@Builder
function customRefreshingContent() {
  Stack() {
    Row() {
      LoadingProgress().height(32)
    }
    .alignItems(VerticalAlign.Center)
  }
  .align(Alignment.Center)
  .clip(true)
  // 设置最小高度约束保证自定义组件高度随刷新区域高度变化时自定义组件高度不会低于minHeight。
  .constraintSize({ minHeight: 32 })
  .width('100%')
}

@Entry
@Component
struct RefreshExample {
  @State isRefreshing: boolean = false;
  @State arr: string[] = ['0', '1', '2', '3', '4', '5', '6', '7', '8', '9', '10'];
  @State maxRefreshingHeight: number = 100.0;
  @State ratio: number = 1;
  private contentNode?: ComponentContent<Object> = undefined;

  aboutToAppear(): void {
    let uiContext = this.getUIContext();
    this.contentNode = new ComponentContent(uiContext, wrapBuilder(customRefreshingContent));
  }

  build() {
    Column() {
      Refresh({ refreshing: $$this.isRefreshing, refreshingContent: this.contentNode }) {
        List() {
          ForEach(this.arr, (item: string) => {
            ListItem() {
              Text('' + item)
                .width('70%')
                .height(80)
                .fontSize(16)
                .margin(10)
                .textAlign(TextAlign.Center)
                .borderRadius(10)
                .backgroundColor(0xFFFFFF)
            }
          }, (item: string) => item)
        }
        .onScrollIndex((first: number) => {
          console.info(first.toString());
        })
        .width('100%')
        .height('100%')
        .alignListItem(ListItemAlign.Center)
        .scrollBar(BarState.Off)
      }
      .backgroundColor(0x89CFF0)
      .pullDownRatio(this.ratio)
      .pullToRefresh(true)
      .refreshOffset(64)
      .onOffsetChange((offset: number) => {
        // 越接近最大距离，下拉跟手系数越小。
        this.ratio = 1 - Math.pow((offset / this.maxRefreshingHeight), 3);
      })
      .onStateChange((refreshStatus: RefreshStatus) => {
        console.info('Refresh onStateChange state is ' + refreshStatus);
      })
      .onRefreshing(() => {
        setTimeout(() => {
          this.isRefreshing = false;
        }, 2000)
        console.info('onRefreshing test');
      })
    }
  }
}
```

Refresh组件与[List](ts-container-list.md)组件组合实现下拉刷新上拉加载更多效果。

```TypeScript
// xxx.ets
@Entry
@Component
struct ListRefreshLoad {
  @State arr: Array<number> = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
  @State refreshing: boolean = false;
  @State refreshOffset: number = 0;
  @State refreshState: RefreshStatus = RefreshStatus.Inactive;
  @State isLoading: boolean = false;

  @Builder
  refreshBuilder() {
    Stack({ alignContent: Alignment.Bottom }) {
      // 可以通过刷新状态控制是否存在Progress组件。
      // 当刷新状态处于下拉中或刷新中状态时Progress组件才存在。
      if (this.refreshState != RefreshStatus.Inactive && this.refreshState != RefreshStatus.Done) {
        Progress({ value: this.refreshOffset, total: 64, type: ProgressType.Ring })
          .width(32).height(32)
          .style({ status: this.refreshing ? ProgressStatus.LOADING : ProgressStatus.PROGRESSING })
          .margin(10)
      }
    }
    .clip(true)
    .height('100%')
    .width('100%')
  }

  @Builder
  footer() {
    Row() {
      LoadingProgress().height(32).width(48)
      Text('加载中')
    }.width('100%')
    .height(64)
    .justifyContent(FlexAlign.Center)
    // 当不处于加载中状态时隐藏组件。
    .visibility(this.isLoading ? Visibility.Visible : Visibility.Hidden)
  }

  build() {
    Refresh({ refreshing: $$this.refreshing, builder: this.refreshBuilder() }) {
      List() {
        ForEach(this.arr, (item: number) => {
          ListItem() {
            Text('' + item)
              .width('100%')
              .height(80)
              .fontSize(16)
              .textAlign(TextAlign.Center)
              .backgroundColor(0xFFFFFF)
          }.borderWidth(1)
        }, (item: number) => item.toString())

        ListItem() {
          this.footer();
        }
      }
      .onScrollIndex((start: number, end: number) => {
        // 当达到列表末尾时，触发新数据加载。
        if (end >= this.arr.length - 1) {
          this.isLoading = true;
          // 模拟新数据加载。
          setTimeout(() => {
            for (let i = 0; i < 10; i++) {
              this.arr.push(this.arr.length);
            }
            this.isLoading = false;
          }, 700)
        }
      })
      .scrollBar(BarState.Off)
      // 开启边缘滑动效果。
      .edgeEffect(EdgeEffect.Spring, { alwaysEnabled: true })
    }
    .width('100%')
    .height('100%')
    .backgroundColor(0xDCDCDC)
    .onOffsetChange((offset: number) => {
      this.refreshOffset = offset;
    })
    .onStateChange((state: RefreshStatus) => {
      this.refreshState = state;
    })
    .onRefreshing(() => {
      // 模拟数据刷新。
      setTimeout(() => {
        this.refreshing = false;
      }, 2000)
    })
  }
}
```

从API version 20开始，通过[maxPullDownDistance](arkts-arkui-refresh-attribute.md#maxpulldowndistance)属性设置最大下拉距离。

```TypeScript
// xxx.ets
@Entry
@Component
struct RefreshExample {
  @State isRefreshing: boolean = false;
  @State arr: string[] = ['0', '1', '2', '3', '4', '5', '6', '7', '8', '9', '10'];

  build() {
    Column() {
      Refresh({ refreshing: $$this.isRefreshing }) {
        List() {
          ForEach(this.arr, (item: string) => {
            ListItem() {
              Text('' + item)
                .width('70%')
                .height(80)
                .fontSize(16)
                .margin(10)
                .textAlign(TextAlign.Center)
                .borderRadius(10)
                .backgroundColor(0xFFFFFF)
            }
          }, (item: string) => item)
        }
        .onScrollIndex((first: number) => {
          console.info(first.toString());
        })
        .width('100%')
        .height('100%')
        .alignListItem(ListItemAlign.Center)
        .scrollBar(BarState.Off)
      }
      .maxPullDownDistance(150)
      .onStateChange((refreshStatus: RefreshStatus) => {
        console.info('Refresh onStateChange state is ' + refreshStatus);
      })
      .onOffsetChange((value: number) => {
        console.info('Refresh onOffsetChange offset:' + value);
      })
      .onRefreshing(() => {
        setTimeout(() => {
          this.isRefreshing = false;
        }, 2000)
        console.info('onRefreshing test');
      })
      .backgroundColor(0x89CFF0)
      .refreshOffset(64)
      .pullToRefresh(true)
    }
  }
}
```

通过[pullDownRatio](arkts-arkui-refresh-attribute.md#pulldownratio)属性禁止下拉刷新。

```TypeScript
// xxx.ets
@Entry
@Component
struct RefreshExample {
  @State isRefreshing: boolean = false;
  @State ratio: number | undefined = undefined;
  @State arr: string[] = ['0', '1', '2', '3', '4', '5', '6', '7', '8', '9', '10'];

  build() {
    Column() {
      Row() {
        Button('禁止下拉刷新').onClick(() => {
          this.ratio = 0;
        })
        Button('允许下拉刷新').onClick(() => {
          this.ratio = undefined;
        })
      }
      Refresh({ refreshing: $$this.isRefreshing }) {
          List() {
            ForEach(this.arr, (item: string) => {
              ListItem() {
                Text('' + item)
                  .width('70%')
                  .height(80)
                  .fontSize(16)
                  .margin(10)
                  .textAlign(TextAlign.Center)
                  .borderRadius(10)
                  .backgroundColor(0xFFFFFF)
              }
            }, (item: string) => item)
          }
          .onScrollIndex((first: number) => {
            console.info(first.toString());
          })
          .width('100%')
          .height('100%')
          .alignListItem(ListItemAlign.Center)
          .scrollBar(BarState.Off)
      }
      .backgroundColor(0x89CFF0)
      .refreshOffset(64)
      .pullToRefresh(true)
      .pullDownRatio(this.ratio)
      .onStateChange((refreshStatus: RefreshStatus) => {
        console.info('Refresh onStateChange state is ' + refreshStatus);
      })
      .onOffsetChange((value: number) => {
        console.info('Refresh onOffsetChange offset:' + value);
      })
      .onRefreshing(() => {
        setTimeout(() => {
          this.isRefreshing = false;
        }, 2000)
        console.info('onRefreshing test');
      })
    }
  }
}
```

调用[edgeEffect](ts-container-scrollable-common.md#edgeeffect11)时，将options参数的[alwaysEnabled](ts-container-scrollable-common.md#edgeeffectoptions11对象说明)设置为true，可以在不满一屏的情况下实现Refresh组件的下拉刷新效果。

```TypeScript
// xxx.ets
@Entry
@Component
struct RefreshExample {
  @State isRefreshing: boolean = false;
  @State alwaysEnabled: boolean = false;

  build() {
    Column() {
      Refresh({ refreshing: $$this.isRefreshing }) {
        Column() {
          List() {
            ListItem() {
              Text('alwaysEnabled:' + this.alwaysEnabled)
                .width('70%')
                .height(80)
                .fontSize(16)
                .margin(10)
                .textAlign(TextAlign.Center)
                .borderRadius(10)
                .backgroundColor(0xFFFFFF)
                .onClick(() => {
                  this.alwaysEnabled = !this.alwaysEnabled;
                })
            }
          }
          .width('100%')
          .height('100%')
          .alignListItem(ListItemAlign.Center)
          .scrollBar(BarState.Auto)
          // List组件内容大小小于组件自身且alwaysEnabled为false时，List不会响应手势，此时手势会被Column组件响应，不会产生下拉刷新效果
          // alwaysEnabled设为true，List会响应手势并通过嵌套滚动带动Refresh组件产生下拉刷新效果
          .edgeEffect(EdgeEffect.Spring, { alwaysEnabled: this.alwaysEnabled })
        }
        .gesture(
          PanGesture({ direction: PanDirection.Vertical })
        )
      }
      .onStateChange((refreshStatus: RefreshStatus) => {
        console.info('Refresh onStateChange state is ' + refreshStatus);
      })
      .onOffsetChange((value: number) => {
        console.info('Refresh onOffsetChange offset:' + value);
      })
      .onRefreshing(() => {
        setTimeout(() => {
          this.isRefreshing = false;
        }, 2000)
      })
      .backgroundColor(0x89CFF0)
      .refreshOffset(64)
      .pullToRefresh(true)
    }
  }
}
```

从API version 23开始，新增pullUpToCancelRefresh接口。

```TypeScript
// xxx.ets
import { ComponentContent } from '@kit.ArkUI';

class Params {
  refreshStatus: RefreshStatus = RefreshStatus.Inactive;

  constructor(refreshStatus: RefreshStatus) {
    this.refreshStatus = refreshStatus;
  }
}

@Builder
function customRefreshingContent(params: Params) {
  Stack() {
    Row() {
      LoadingProgress().height(32)
      Text('refreshStatus: ' + params.refreshStatus).fontSize(16).margin({ left: 20 })
    }
    .alignItems(VerticalAlign.Center)
  }
  .align(Alignment.Center)
  .clip(true)
  .constraintSize({ minHeight: 32 })
  .width('100%')
}

@Entry
@Component
struct RefreshExample {
  @State isRefreshing: boolean = false;
  @State arr: string[] = ['0', '1', '2', '3', '4', '5', '6', '7', '8', '9', '10'];
  @State refreshStatus: RefreshStatus = RefreshStatus.Inactive;
  private contentNode?: ComponentContent<Object> = undefined;
  private params: Params = new Params(RefreshStatus.Inactive);

  aboutToAppear(): void {
    let uiContext = this.getUIContext();
    this.contentNode = new ComponentContent(uiContext, wrapBuilder(customRefreshingContent), this.params);
  }

  build() {
    Column() {
      Refresh({ refreshing: $$this.isRefreshing, refreshingContent: this.contentNode }) {
        List() {
          ForEach(this.arr, (item: string) => {
            ListItem() {
              Text('' + item)
                .width('70%')
                .height(80)
                .fontSize(16)
                .margin(10)
                .textAlign(TextAlign.Center)
                .borderRadius(10)
                .backgroundColor(0xFFFFFF)
            }
          }, (item: string) => item)
        }
        .onScrollIndex((first: number) => {
          console.info(first.toString());
        })
        .width('100%')
        .height('100%')
        .alignListItem(ListItemAlign.Center)
        .scrollBar(BarState.Off)
      }
      .backgroundColor(0x89CFF0)
      .pullToRefresh(true)
      .pullUpToCancelRefresh(false)
      .refreshOffset(96)
      .onStateChange((refreshStatus: RefreshStatus) => {
        this.refreshStatus = refreshStatus;
        this.params.refreshStatus = refreshStatus;
        this.contentNode?.update(this.params);
        console.info('Refresh onStateChange state is ' + refreshStatus);
      })
      .onRefreshing(() => {
        // 模拟刷新数据，生成新的连续数据项。
        setTimeout(() => {
          const newArr: string[] = [];
          const lastNum = parseInt(this.arr[this.arr.length - 1]);
          for (let i = 0; i < 11; i++) {
            newArr.push((lastNum + 1 + i).toString());
          }
          this.arr = newArr;

          this.isRefreshing = false;
        }, 6000)
        console.info('onRefreshing test');
      })
    }
  }
}
```
