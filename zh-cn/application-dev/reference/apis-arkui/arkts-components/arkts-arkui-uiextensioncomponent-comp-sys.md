# UIExtensionComponent(System API) (System API)

**UIExtensionComponent**用于将其他应用提供的UI嵌入到本应用UI中。嵌入内容运行在另一个进程中，本应用不参与其布局和渲染。

通常用于需要进程隔离的模块化开发场景。

## 约束

该组件不支持预览。

待启动的能力必须是UIExtensionAbility，即带UI的扩展能力。关于如何实现UIExtensionAbility的详细信息，请参见[@ohos.app.ability.UIExtensionAbility（带UI的ExtensionAbility基类）](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiextensionability-uiextensionability-c.md)。

组件的宽高必须显式设置为非零有效值。

不支持到达边缘后继续滚动的场景。当**UIExtensionComponent**宿主和UIExtensionAbility都支持内容滚动时，基于手势的滚动会导致**UIExtensionComponent**内外同时响应，包括但不限于[Scroll](arkts-arkui-scroll-comp.md#scroll)、[Swiper](arkts-arkui-swiper-comp.md#swiper)、[List](arkts-arkui-list-comp.md#list)、[Grid](arkts-arkui-grid-comp.md#grid)等可滚动容器。关于如何避免**UIExtensionComponent**内外同时滚动的详细信息，请参见[示例2](../../../reference/apis-arkui/arkui-ts/ts-container-ui-extension-component-sys.md#example-2-isolating-scrolling-inside-and-outside-of-uiextensioncomponent)。

## 子组件

不支持

## UIExtensionComponent

```TypeScript
UIExtensionComponent(
    want: import('../api/@ohos.app.ability.Want').default,
    options?: UIExtensionOptions
  )
```

构造UIExtensionComponent。<br>在使用UIExtensionComponent时调用。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| want | import('../api/@ohos.app.ability.Want').default | 是 | 表示UIExtensionAbility的want |
| options | [UIExtensionOptions](arkts-arkui-uiextensioncomponent-comp-uiextensionoptions-i-sys.md) | 否 | UIExtensionComponentAttribute的构造配置 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [TerminationInfo](arkts-arkui-uiextensioncomponent-comp-terminationinfo-i-sys.md) | 用于表示被拉起的UIExtensionAbility通过调用`terminateSelfWithResult`或者`terminateSelf`正常退出时的返回结果。 |
| [UIExtensionOptions](arkts-arkui-uiextensioncomponent-comp-uiextensionoptions-i-sys.md) | 用于在UIExtensionComponent进行构造时传递可选的构造参数。 |
| [UIExtensionProxy](arkts-arkui-uiextensioncomponent-comp-uiextensionproxy-i-sys.md) | 用于在双方建立连接成功后，组件使用方将数据发送给被拉起的Ability，并订阅和取消订阅扩展Ability的注册事件。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ReceiveCallback](arkts-arkui-uiextensioncomponent-comp-receivecallback-t-sys.md) | 回调函数，用于封装被拉起的Ability发送的数据。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [DpiFollowStrategy](arkts-arkui-uiextensioncomponent-comp-dpifollowstrategy-e-sys.md) | 表示不同类型的DpiFollowStrategy的枚举。 |
| [WindowModeFollowStrategy](arkts-arkui-uiextensioncomponent-comp-windowmodefollowstrategy-e-sys.md) | 窗口Mode跟随策略，用于设置窗口Mode，使其能够跟随宿主或UIExtensionAbility。 |

## 示例

### 示例1 (加载UIExtension)

UIExtensionComponent组件使用分为使用方和提供方。本示例仅展示组件使用的方法和扩展的Ability，实际运行需在设备中安装bundleName为"com.example.newdemo"，abilityName为"UIExtensionProvider"的Ability扩展。

组件使用方

使用方入口界面Index.ets内容如下：

```TypeScript
import { ComponentContent } from '@kit.ArkUI';

class Params {
}
@Builder
function LoadingBuilder(params: Params) {
  Column() {
   LoadingProgress()
      .color(Color.Blue)
  }
}
@Builder
function AreaChangePlaceholderBuilder(params: Params) {
  Column() {
  }
  .width('100%')
  .height('100%')
  .backgroundColor(Color.Orange)
}
@Entry
@Component
struct Second {
  @State message1: string = 'Hello World 1';
  @State message2: string = 'Hello World 2';
  @State message3: string = 'Hello World 3';
  @State wid: number = 300;
  @State hei: number = 300;
  @State windowStrategy: WindowModeFollowStrategy = WindowModeFollowStrategy.FOLLOW_UI_EXTENSION_ABILITY_WINDOW_MODE;
  private proxy: UIExtensionProxy | null = null;
  private initPlaceholder = new ComponentContent(this.getUIContext(), wrapBuilder(LoadingBuilder), new Params());
  private areaChangePlaceholder = new ComponentContent(this.getUIContext(), wrapBuilder(AreaChangePlaceholderBuilder), new Params());

  aboutToDisappear(): void {
    console.info('start do proxy off!');
    this.proxy?.off('syncReceiverRegister');
    this.proxy?.off('asyncReceiverRegister');
  }

  build() {
    Row() {
      Column() {
        Text(this.message1).fontSize(30)
        Text(this.message2).fontSize(30)
        Text(this.message3).fontSize(30)
        UIExtensionComponent({
          bundleName : "com.example.newdemo",
          abilityName: "UIExtensionProvider",
          parameters: {
            "ability.want.params.uiExtensionType": "sys/commonUI"
          }},
          {
            placeholder: this.initPlaceholder,
            areaChangePlaceholder: {
              "FOLD_TO_EXPAND" : this.areaChangePlaceholder,
            },
            windowModeFollowStrategy: this.windowStrategy
          })
          .width(this.wid)
          .height(this.hei)
          .border({width: 5, color: Color.Blue})
          .onReceive((data) => {
            console.info('onReceive, for test');
            this.message3 = JSON.stringify(data['data']);
          })
          .onError((info) => {
            console.error(`onError: code = ${info.code}, message = ${info.message}`);
          })
          .onTerminated((info) => {
            console.info('onTerminated: code =' + info.code + ', want = ' + JSON.stringify(info.want));
          })
          .onRemoteReady((proxy) => {
            console.info('onRemoteReady, for test');
            this.proxy = proxy;

            this.proxy.on("syncReceiverRegister", syncRegisterCallback1);

            this.proxy.on("asyncReceiverRegister", (proxy1) => {
              console.info('on invoke for test, type is asyncReceiverRegister');
            });
          })

        Button("点击向UIExtensionAbility发送数据").onClick(() => {
          if (this.proxy != undefined) {
            this.proxy.send({data: "你好1"});

            try {
              let re = this.proxy.sendSync({data: "你好2"});
              console.info("for test, re=" + JSON.stringify(re));
            } catch (err) {
              console.error(`sendSync failed for test. Code: ${err.code}, message: ${err.message}`);
            }
          }
        })
      }
      .width('100%')
    }
    .height('100%')
  }
}

function syncRegisterCallback1(proxy: UIExtensionProxy) {
  console.info("on invoke for test, syncRegisterCallback1, type is syncReceiverRegister");
};

function syncRegisterCallback2(proxy: UIExtensionProxy) {
  console.info("on invoke for test, syncRegisterCallback2, type is syncReceiverRegister");
};
```

组件提供方

提供方包含三个文件需要修改：

提供方新增扩展入口文件/src/main/ets/uiextensionability/UIExtensionProvider.ets

```TypeScript
import { UIExtensionAbility, UIExtensionContentSession, Want } from '@kit.AbilityKit';

const TAG: string = '[UIExtAbility]'
export default class UIExtAbility extends UIExtensionAbility {

  onCreate() {
    console.info(TAG, `UIExtAbility onCreate`);
  }

  onForeground() {
    console.info(TAG, `UIExtAbility onForeground`);
  }

  onBackground() {
    console.info(TAG, `UIExtAbility onBackground`);
  }

  onDestroy() {
    console.info(TAG, `UIExtAbility onDestroy`);
  }

  onSessionCreate(want: Want, session: UIExtensionContentSession) {
    console.info(TAG, `UIExtAbility onSessionCreate, want: ${JSON.stringify(want)}`);
    let param: Record<string, UIExtensionContentSession> = {
      'session': session
    };
    let storage: LocalStorage = new LocalStorage(param);
    session.loadContent('pages/extension', storage);
  }

  onSessionDestroy(session: UIExtensionContentSession) {
    console.info(TAG, `UIExtAbility onSessionDestroy`);
  }
}
```

提供方扩展Ability入口页面文件/src/main/ets/pages/extension.ets

```TypeScript
import { UIExtensionContentSession } from '@kit.AbilityKit';

AppStorage.setOrCreate('message', 'UIExtensionAbility');

@Entry
@Component
struct Extension {
  @StorageLink('message') storageLink: string = '';
  private session: UIExtensionContentSession | undefined = undefined;
  pathStack: NavPathStack = new NavPathStack();

  @Builder
  PageMap(name: string) {
    if (name === "hello") {
      PageOne();
    }
  }

  aboutToAppear() {
    this.session = this.getUIContext().getLocalStorage()?.get<UIExtensionContentSession>('session');
  }

  onPageShow() {
    if (this.session != undefined) {
      this.session.setReceiveDataCallback((data) => {
        this.storageLink = JSON.stringify(data);
        console.info("invoke for test, handle callback set by setReceiveDataCallback successfully");
      })

      this.session.setReceiveDataForResultCallback(onReceiveDataForResult);
    }
  }

  build() {
    Navigation(this.pathStack) {
      Row() {
        Column() {
          Text(this.storageLink)
            .fontSize(20)
            .fontWeight(FontWeight.Bold)
          Button("点击向Component发送数据").onClick(() => {
            if (this.session != undefined) {
              this.session.sendData({"data": 543321});
              console.info('send 543321, for test');
            }
          })
          Button("terminate").onClick(() => {
            if (this.session != undefined) {
              this.session.terminateSelf();
            }
            this.getUIContext().getLocalStorage()?.clear();
          })
          Button("terminate with result").onClick(() => {
            if (this.session != undefined) {
              this.session.terminateSelfWithResult({
                resultCode: 0,
                want: {
                  bundleName: "myBundleName",
                  parameters: { "result": 123456 }
                }
              });
            }
            this.getUIContext().getLocalStorage()?.clear();
          })

          Button("点击跳转").onClick(() => {
            this.pathStack.pushPath({ name: "hello"});
          })
        }
      }
      .height('100%')
    }.navDestination(this.PageMap)
    .mode(NavigationMode.Stack)
  }
}

// pageOne
@Component
export struct PageOne {
  pathStack: NavPathStack = new NavPathStack();

  build() {
    NavDestination() {
      Column() {
        Text("Hello World")
      }.width('100%').height('100%')
    }.title("pageOne")
    .onBackPressed(() => {
      const popDestinationInfo = this.pathStack.pop(); // 弹出路由栈栈顶元素
      console.info('pop' + '返回值' + JSON.stringify(popDestinationInfo));
      return true;
    })
    .onReady((context: NavDestinationContext) => {
      this.pathStack = context.pathStack;
    })
  }
}

function onReceiveDataForResult(data: Record<string, Object>): Record<string, Object> {
  let linkToMsg: SubscribedAbstractProperty<string> = AppStorage.link('message');
  linkToMsg.set(JSON.stringify(data));
  console.info("invoke for test, handle callback set by setReceiveDataForResultCallback successfully");
  return data;
}
```

提供方扩展Ability，module配置文件/src/main/module.json5添加对应配置

```TypeScript
{
    "name": "UIExtensionProvider",
    "srcEntry": "./ets/uiextensionability/UIExtensionProvider.ets",
    "description": "1",
    "label": "$string:EntryAbility_label",
    "type": "sys/commonUI",
    "exported": true
}
```

### 示例2 (UIExtensionComponent内外部同时响应滚动时隔离处理)

本示例展示了当UIExtensionComponent组件使用方和扩展的Ability同时使用[Scroll](ts-container-scroll.md)容器的场景，通过对UIExtensionComponent设置手势拦截处理，实现当UIExtensionComponent内部滚动时，外部组件不响应滚动。

手势使用方式：

组件内部滚动：手指在组件内部进行滚动操作；

组件外部滚动：拖动外部滚动条进行滚动。

实际运行时需先在设备中安装bundleName为"com.example.newdemo"，abilityName为"UIExtensionProvider"的Ability扩展。

提供方扩展入口文件UIExtensionProvider.ets与[示例1](#示例1-加载uiextension)扩展入口文件UIExtensionProvider.ets代码一致。

提供方扩展Ability的module配置文件与[示例1](#示例1-加载uiextension)扩展module配置文件module.json5代码一致。

使用方组件使用示例：

```TypeScript
@Entry
@Component
struct Second {
  @State message1: string = 'Hello World 1';
  @State message2: string = 'Hello World 2';
  @State message3: string = 'Hello World 3';
  @State wid: number = 300;
  @State hei: number = 300;
  private scroller: Scroller = new Scroller();
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6];

  build() {
    Column() {
      // 可滚动的容器组件
      Scroll(this.scroller) {
        Column() {
          Text(this.message1).fontSize(30)
          Text(this.message2).fontSize(30)
          Text(this.message3).fontSize(30)

          // 重复设置组件，构造滚动内容
          ForEach(this.arr, (item: number) => {
            UIExtensionComponent({
                bundleName: "com.example.newdemo",
                abilityName: "UIExtensionProvider",
                parameters: {
                  "ability.want.params.uiExtensionType": "sys/commonUI"
                }
              })
              .width(this.wid)
              .height(this.hei)
              // 设置手势拦截，UIExtensionComponent外部组件不响应滚动
              .gesture(PanGesture().onActionStart(() => {
                console.info('UIExtensionComponent PanGesture onAction');
              }))
              .border({ width: 5, color: Color.Blue })
              .onReceive((data) => {
                console.info('onReceive, for test');
                this.message3 = JSON.stringify(data['data']);
              })
              .onTerminated((info) => {
                console.info('onTerminated: code =' + info.code + ', want = ' + JSON.stringify(info.want));
              })
              .onRemoteReady((proxy) => {
                console.info('onRemoteReady, for test');
              })
            }, (item: number) => item.toString())
        }
        .width('100%')
      }
      .scrollable(ScrollDirection.Vertical) // 滚动方向纵向
      .scrollBar(BarState.On) // 滚动条常驻显示
      .scrollBarColor(Color.Gray) // 滚动条颜色
      .scrollBarWidth(10) // 滚动条宽度
      .friction(0.6)
      .edgeEffect(EdgeEffect.None)
      .onWillScroll((xOffset: number, yOffset: number, scrollState: ScrollState) => {
        console.info(xOffset + ' ' + yOffset);
      })
      .onScrollEdge((side: Edge) => {
        console.info('To the edge');
      })
      .onScrollStop(() => {
        console.info('Scroll Stop');
      })
    }
    .height('100%')
  }
}
```

提供方扩展Ability入口页面文件extension.ets

```TypeScript
@Entry
@Component
struct Extension {
  private scroller: Scroller = new Scroller();
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8];

  build() {
    Column() {
      // 可滚动的容器组件
      Scroll(this.scroller) {
        Column() {
          Text('Test demo')
            .fontSize(20)
            .fontWeight(FontWeight.Bold)
          // 重复设置组件，构造滚动内容
          ForEach(this.arr, (item: number) => {
            Text(item.toString())
              .width('90%')
              .height(150)
              .backgroundColor(Color.Pink)
              .borderRadius(15)
              .fontSize(16)
              .textAlign(TextAlign.Center)
              .margin({ top: 10 })
          }, (item: number) => item.toString())
        }
      }

    }
    .height('100%')
  }
}
```
