# UIExtensionComponent(System API) (System API)

**UIExtensionComponent** is used to embed UIs provided by other applications in the local application UI. The embedded content runs in another process, and the local application does not participate in its layout and rendering.

It is usually used in modular development scenarios where process isolation is required.

## Constraints

This component does not support preview.

The ability to be started must be a UIExtensionAbility, an extension ability with UI. For details about how to implement a UIExtensionAbility, see [@ohos.app.ability.UIExtensionAbility (Base Class for ExtensionAbilities with UI)](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiextensionability-uiextensionability-c.md).

The width and height of the component must be explicitly set to non-zero valid values.

The scenario where scrolling continues after the edge is reached is not supported. When both the **UIExtensionComponent** host and the UIExtensionAbility support content scrolling, gesture-based scrolling will cause simultaneous responses from both inside and outside the **UIExtensionComponent**. This includes, but is not limited to, scrollable containers such as [Scroll](arkts-arkui-scroll-comp.md#scroll), [Swiper](arkts-arkui-swiper-comp.md#swiper), [List](arkts-arkui-list-comp.md#list), and [Grid](arkts-arkui-grid-comp.md#grid). For details about how to avoid the simultaneous scrolling inside and outside the **UIExtensionComponent**, see [Example 2](../../../reference/apis-arkui/arkui-ts/ts-container-ui-extension-component-sys.md#example-2-isolating-scrolling-inside-and-outside-of-uiextensioncomponent).

## Child Components

Not supported

## UIExtensionComponent

```TypeScript
UIExtensionComponent(
    want: import('../api/@ohos.app.ability.Want').default,
    options?: UIExtensionOptions
  )
```

Construct the UIExtensionComponent.<br> Called when the UIExtensionComponent is used.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | import('../api/@ohos.app.ability.Want').default | Yes | Ability to start. |
| options | [UIExtensionOptions](arkts-arkui-uiextensioncomponent-comp-uiextensionoptions-i-sys.md) | No | Construction parameters. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [TerminationInfo](arkts-arkui-uiextensioncomponent-comp-terminationinfo-i-sys.md) | Indicates the information when the provider of the embedded UI is terminated. |
| [UIExtensionOptions](arkts-arkui-uiextensioncomponent-comp-uiextensionoptions-i-sys.md) | Describes the optional construction parameters during **UIExtensionComponent** construction. |
| [UIExtensionProxy](arkts-arkui-uiextensioncomponent-comp-uiextensionproxy-i-sys.md) | Implements a **UIExtensionProxy** instance for the component host to send data to, subscribe to, or unsubscribe from the started UIExtensionAbility through the connection established between the two parties. |

### Types

| Name | Description |
| --- | --- |
| [ReceiveCallback](arkts-arkui-uiextensioncomponent-comp-receivecallback-t-sys.md) | Triggered to encapsulate the data sent by the started ability. |

### Enums

| Name | Description |
| --- | --- |
| [DpiFollowStrategy](arkts-arkui-uiextensioncomponent-comp-dpifollowstrategy-e-sys.md) | Enumeration of different types of DpiFollowStrategy. |
| [WindowModeFollowStrategy](arkts-arkui-uiextensioncomponent-comp-windowmodefollowstrategy-e-sys.md) | Enumerates the following strategies of the window mode. |

## Examples

### Example 1: Loading a UIExtension

The UIExtensionComponent component can be used by both the host and provider. This example shows only the method used by the component and the UIExtensionAbility. For the code to run properly, you need to install the ability whose bundleName is com.example.newdemo and abilityName is UIExtensionProvider on the device.

Component host

The content of the user's entry page Index.ets is as follows:

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
  private initPlaceholder = new ComponentContent(this.getUIContext(), wrapBuilder(LoadingBuilder), new Params);
  private areaChangePlaceholder = new ComponentContent(this.getUIContext(), wrapBuilder(AreaChangePlaceholderBuilder), new Params);

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
            console.info('Lee onReceive, for test');
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

        Button ("Send to UIExtensionAbility").onClick(() => {
          if (this.proxy != undefined) {
            this.proxy.send({data: "Hello 1"});

            try {
              let re = this.proxy.sendSync({data: "Hello 2"});
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

Component provider

The provider has three files that need to be modified:

/src/main/ets/uiextensionability/UIExtensionProvider.ets

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

Entry page file of the provider's extension Ability: /src/main/ets/pages/extension.ets

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
          Button("Send to Component").onClick(() => {
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

          Button("Redirect").onClick(() => {
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
      const popDestinationInfo = this.pathStack.pop(); // Pop the top element out of the navigation stack.
      console.info('pop' + 'return value' + JSON.stringify(popDestinationInfo));
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

The provider's extension Ability. Add the corresponding configuration to the module configuration file /src/main/module.json5.

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

### Example 2: Isolating Scrolling Inside and Outside of UIExtensionComponent

This example demonstrates a scenario where both the UIExtensionComponent host and the UIExtensionAbility use [Scroll](ts-container-scroll.md) containers. By setting gesture interception on UIExtensionComponent, it achieves that external components do not respond to scrolling when the internal layer of the UIExtensionComponent is being scrolled.

Gesture usage:

Scrolling inside the component: scrolling within the component using touch gestures

Scrolling outside the component: scrolling of the outer container using the scrollbar

Before running, ensure that an ability whose bundleName is com.example.newdemo and abilityName as UIExtensionProvider is installed on the device.

The entry point file UIExtensionProvider.ets and the module configuration file UIExtensionProvider.ets are identical to those in [Example 1](#example-1-loading-a-uiextension).

The provider's extension Ability and module configuration file are the same as the module.json5 code of the extension module in [Example 1](#example-1-loading-a-uiextension).

Example of the user's component usage:

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
      // Scrollable container component.
      Scroll(this.scroller) {
        Column() {
          Text(this.message1).fontSize(30)
          Text(this.message2).fontSize(30)
          Text(this.message3).fontSize(30)

          // Repeat components to create scrollable content.
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
               // Use gesture interception to prevent external components from responding to scrolling.
              .gesture(PanGesture().onActionStart(() => {
                console.info('UIExtensionComponent PanGesture onAction');
              }))
              .border({ width: 5, color: Color.Blue })
              .onReceive((data) => {
                console.info('Lee onReceive, for test');
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
      .scrollable(ScrollDirection.Vertical) // The scrollbar scrolls in the vertical direction.
      .scrollBar(BarState.On) // The scrollbar is always displayed.
      .scrollBarColor(Color.Gray) // The scrollbar color is gray.
      .scrollBarWidth(10) // The scrollbar width is 10.
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

extension.ets (entry page file of the provider's UIExtensionAbility)

```TypeScript
@Entry
@Component
struct Extension {
  private scroller: Scroller = new Scroller();
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8];

  build() {
    Column() {
      // Scrollable container component.
      Scroll(this.scroller) {
        Column() {
          Text('Test demo')
            .fontSize(20)
            .fontWeight(FontWeight.Bold)
          // Repeat components to create scrollable content.
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
