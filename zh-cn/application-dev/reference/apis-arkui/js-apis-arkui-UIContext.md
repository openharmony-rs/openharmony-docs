# @ohos.arkui.UIContext (UIContext)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xiang-shouxing-->
<!--Designer: @xiang-shouxing-->
<!--Tester: @sally__-->

在Stage模型中，WindowStage/Window可以通过[loadContent](js-apis-window.md#loadcontent9)接口加载页面并创建UI的实例，并将页面内容渲染到关联的窗口中，所以UI实例和窗口是一一关联的。一些全局的UI接口是和具体UI实例的执行上下文相关的，在当前接口调用时，通过追溯调用链跟踪到UI的上下文，来确定具体的UI实例。若在非UI页面中或者一些异步回调中调用这类接口，可能无法跟踪到当前UI的上下文，导致接口执行失败。

> **说明：**
>
> 本模块首批接口从API version 10开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> 示例效果请以真机运行为准，当前DevEco Studio预览器不支持。

## 导入模块

```ts
import {
  AtomicServiceBar, ComponentUtils, ContextMenuController, CursorController, DragController, Font, KeyboardAvoidMode, MediaQuery, OverlayManager,
  PromptAction, Router, UIContext, UIInspector, UIObserver, PageInfo, SwiperDynamicSyncScene, SwiperDynamicSyncSceneType, MeasureUtils, FrameCallback,
  OverlayManagerOptions, TargetInfo, MarqueeDynamicSyncScene, MarqueeDynamicSyncSceneType
} from "@kit.ArkUI";
```

## UIContext

以下API需先使用ohos.window中的[getUIContext()](js-apis-window.md#getuicontext10)方法获取UIContext实例，再通过此实例调用对应方法。或者可以通过自定义组件内置方法[getUIContext()](arkui-ts/ts-custom-component-api.md#getuicontext)获取。本文中UIContext对象以uiContext表示。

**示例：**

```ts
//两种方法获取到的UIContext没有差异
//index.ets
import { UIContext } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  build() {
    Column() {
      Button("Button")
          .onClick(()=>{
            //通过自定义组件内置方法获取
            this.getUIContext()
            //其他运行逻辑
          })
    }  
  }
}

//EntryAbility.ets
import { AbilityConstant, ConfigurationConstant, UIAbility, Want } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { window } from '@kit.ArkUI';

const DOMAIN = 0x0000;

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage): void {
    //通过ohos.window获取
    windowStage.getMainWindowSync().getUIContext()
    //其他运行逻辑
  }
}
```

### getFont

getFont(): Font

获取Font对象。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型            | 说明          |
| ------------- | ----------- |
| [Font](#font) | 返回Font实例对象。 |

**示例：**

完整示例请参考[Font](#font)中的示例。

### getComponentUtils

getComponentUtils(): ComponentUtils

获取ComponentUtils对象。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型                                | 说明                    |
| --------------------------------- | --------------------- |
| [ComponentUtils](#componentutils) | 返回ComponentUtils实例对象。 |

**示例：**

完整示例请参考[getComponentUtils](js-apis-arkui-componentUtils.md)中的示例。

### getUIInspector

getUIInspector(): UIInspector

获取UIInspector对象。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型                          | 说明                 |
| --------------------------- | ------------------ |
| [UIInspector](#uiinspector) | 返回UIInspector实例对象。 |

**示例：**

完整示例请参考[UIInspector](#uiinspector)中的示例。

### getUIObserver<sup>11+</sup>

getUIObserver(): UIObserver

获取UIObserver对象。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型                          | 说明                 |
| --------------------------- | ------------------ |
| [UIObserver](#uiobserver11) | 返回UIObserver实例对象。 |

**示例：**

```ts
@Component
struct PageOne {
  build() {
    NavDestination() {
      Text("pageOne")
    }.title("pageOne")
  }
}

@Entry
@Component
struct Index {
  private stack: NavPathStack = new NavPathStack();

  @Builder
  PageBuilder(name: string) {
    PageOne()
  }

  aboutToAppear() {
    this.getUIContext().getUIObserver().on('navDestinationUpdate', (info) => {
      console.info('NavDestination state update', JSON.stringify(info));
    });
  }

  aboutToDisappear() {
    this.getUIContext().getUIObserver().off('navDestinationUpdate');
  }

  build() {
    Column() {
      Navigation(this.stack) {
        Button("push").onClick(() => {
          this.stack.pushPath({ name: "pageOne" });
        })
      }
      .title("Navigation")
      .navDestination(this.PageBuilder)
    }
    .width('100%')
    .height('100%')
  }
}
```

### getMediaQuery

getMediaQuery(): MediaQuery

获取MediaQuery对象。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型                        | 说明                |
| ------------------------- | ----------------- |
| [MediaQuery](#mediaquery) | 返回MediaQuery实例对象。 |

**示例：**

完整示例请参考[mediaquery示例](js-apis-mediaquery.md#示例)。

### getRouter

getRouter(): Router

获取Router对象。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型                | 说明            |
| ----------------- | ------------- |
| [Router](#router) | 返回Router实例对象。 |

**示例：**

完整示例请参考[pushUrl](#pushurl)。

### getPromptAction

getPromptAction(): PromptAction

获取PromptAction对象。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型                            | 说明                  |
| ----------------------------- | ------------------- |
| [PromptAction](#promptaction) | 返回PromptAction实例对象。 |

**示例：**

完整示例请参考[PromptAction](#promptaction)中的示例。

### getOverlayManager<sup>12+</sup>

getOverlayManager(): OverlayManager

获取OverlayManager对象。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：**: SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型                           | 说明                 |
| ----------------------------- | ------------------- |
| [OverlayManager](#overlaymanager12) | 返回OverlayManager实例对象。 |

### setOverlayManagerOptions<sup>15+</sup>

setOverlayManagerOptions(options: OverlayManagerOptions): boolean

设置[OverlayManager](#overlaymanager12)参数。用于在使用OverlayManager能力之前先初始化overlayManager的参数，包括是否需要渲染overlay根节点等属性。该方法需要在执行getOverlayManager方法之前执行生效，且该方法只生效一次。

**原子化服务API：** 从API version 15开始，该接口支持在原子化服务中使用。

**系统能力：**: SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名   | 类型                                       | 必填   | 说明                                    |
| ----- | ---------------------------------------- | ---- | ------------------------------------- |
| options | [OverlayManagerOptions](#overlaymanageroptions15) | 是 | OverlayManager参数。|

**返回值：** 

| 类型    | 说明           |
| ------- | -------------- |
| boolean | 是否设置成功。<br/>返回true表示设置成功。返回false表示设置失败。 |

**示例：**

<!--code_no_check-->
```ts
uiContext.setOverlayManagerOptions({ renderRootOverlay: true, enableBackPressedEvent: true });
```

### getOverlayManagerOptions<sup>15+</sup>

getOverlayManagerOptions(): OverlayManagerOptions

用于获取当前[OverlayManager](#overlaymanager12)参数。

**原子化服务API：** 从API version 15开始，该接口支持在原子化服务中使用。

**系统能力：**: SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型                           | 说明                 |
| ----------------------------- | ------------------- |
| [OverlayManagerOptions](#overlaymanageroptions15) | 返回当前OverlayManagerOptions。 |

**示例：**

<!--code_no_check-->
```ts
uiContext.getOverlayManagerOptions();
```

### animateTo

animateTo(value: AnimateParam, event: () => void): void

提供animateTo接口来指定由于闭包代码导致的状态变化插入过渡动效。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名   | 类型                                       | 必填   | 说明                                    |
| ----- | ---------------------------------------- | ---- | ------------------------------------- |
| value | [AnimateParam](arkui-ts/ts-explicit-animation.md#animateparam对象说明) | 是    | 设置动画效果相关参数。                           |
| event | () => void                               | 是    | 指定显示动效的闭包函数，在闭包函数中导致的状态变化系统会自动插入过渡动画。 |

**示例：**

```ts
// xxx.ets
@Entry
@Component
struct AnimateToExample {
  @State widthSize: number = 250;
  @State heightSize: number = 100;
  @State rotateAngle: number = 0;
  private flag: boolean = true;
  uiContext: UIContext | undefined = undefined;

  aboutToAppear() {
    this.uiContext = this.getUIContext();
    if (!this.uiContext) {
      console.warn("no uiContext");
      return;
    }
  }

  build() {
    Column() {
      Button('change size')
        .width(this.widthSize)
        .height(this.heightSize)
        .margin(30)
        .onClick(() => {
          if (this.flag) {
            this.uiContext?.animateTo({
              duration: 2000,
              curve: Curve.EaseOut,
              iterations: 3,
              playMode: PlayMode.Normal,
              onFinish: () => {
                console.info('play end');
              }
            }, () => {
              this.widthSize = 150;
              this.heightSize = 60;
            });
          } else {
            this.uiContext?.animateTo({}, () => {
              this.widthSize = 250;
              this.heightSize = 100;
            });
          }
          this.flag = !this.flag;
        })
      Button('stop rotating')
        .margin(50)
        .rotate({ x: 0, y: 0, z: 1, angle: this.rotateAngle })
        .onAppear(() => {
          // 组件出现时开始做动画
          this.uiContext?.animateTo({
            duration: 1200,
            curve: Curve.Friction,
            delay: 500,
            iterations: -1, // 设置-1表示动画无限循环
            playMode: PlayMode.Alternate,
            expectedFrameRateRange: {
              min: 10,
              max: 120,
              expected: 60,
            }
          }, () => {
            this.rotateAngle = 90
          });
        })
        .onClick(() => {
          this.uiContext?.animateTo({ duration: 0 }, () => {
            // this.rotateAngle之前为90，在duration为0的动画中修改属性，可以停止该属性之前的动画，按新设置的属性显示
            this.rotateAngle = 0;
          });
        })
    }.width('100%').margin({ top: 5 })
  }
}
```

### getSharedLocalStorage<sup>12+</sup>

getSharedLocalStorage(): LocalStorage | undefined

获取当前stage共享的LocalStorage实例。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**返回值：**

| 类型                             | 描述                |
| ------------------------------ | ----------------- |
| [LocalStorage](arkui-ts/ts-state-management.md#localstorage9)&nbsp;\|&nbsp;undefined | 返回LocalStorage实例。共享的LocalStorage实例不存在时返回undefined。 |

**示例：**

```ts
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { window } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  storage: LocalStorage = new LocalStorage();

  onWindowStageCreate(windowStage: window.WindowStage) {
    windowStage.loadContent('pages/Index', this.storage);
  }
}
```

```ts
// Index.ets

@Entry
@Component
struct SharedLocalStorage {
  localStorage = this.getUIContext().getSharedLocalStorage();

  build() {
    Row() {
      Column() {
        Button("Change Local Storage to 47")
          .onClick(() => {
            this.localStorage?.setOrCreate("propA", 47);
          })
        Button("Get Local Storage")
          .onClick(() => {
            console.info(`localStorage: ${this.localStorage?.get("propA")}`);
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### getHostContext<sup>12+</sup>

getHostContext(): Context | undefined

获得当前元能力的Context。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**模型约束：** 此接口仅可在Stage模型下使用。

**返回值：**

| 类型 | 说明                             |
| ------ | ------------------------------- |
| [Context](#context12)&nbsp;\|&nbsp;undefined | 返回当前组件所在Ability的Context，Context的具体类型为当前Ability关联的Context对象。例如：在UIAbility窗口中的页面调用该接口，返回类型为[UIAbilityContext](../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md#uiabilitycontext-1)。在ExtensionAbility窗口中的页面调用该接口，返回类型为[ExtensionContext](../apis-ability-kit/js-apis-inner-application-extensionContext.md)。ability上下文不存在时返回undefined。 |

**示例：**

```ts
@Entry
@Component
struct Index {
  uiContext = this.getUIContext();

  build() {
    Row() {
      Column() {
        Text("cacheDir='"+this.uiContext?.getHostContext()?.cacheDir+"'")
          .fontSize(25)
          .border({ color:Color.Red, width:2 })
          .padding(50)
        Text("bundleCodeDir='"+this.uiContext?.getHostContext()?.bundleCodeDir+"'")
          .fontSize(25)
          .border({ color:Color.Red, width:2 })
          .padding(50)
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### getFrameNodeById<sup>12+</sup>

getFrameNodeById(id: string): FrameNode | null

通过组件的id获取组件树的实体节点。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名   | 类型                                       | 必填   | 说明                                    |
| ----- | ---------------------------------------- | ---- | ------------------------------------- |
| id | string | 是    | 节点对应的[组件标识](arkui-ts/ts-universal-attributes-component-id.md)。       |

**返回值：**

| 类型                                       | 说明            |
| ---------------------------------------- | ------------- |
| [FrameNode](js-apis-arkui-frameNode.md)  \| null | 返回的组件树的实体节点或者空节点。 |

> **说明：**
>
> getFrameNodeById通过遍历查询对应id的节点，性能较差。推荐使用[getAttachedFrameNodeById](#getattachedframenodebyid12)。

**示例：**

完整示例请参考[获取根节点示例](js-apis-arkui-frameNode.md#获取根节点示例)。

### getAttachedFrameNodeById<sup>12+</sup>

getAttachedFrameNodeById(id: string): FrameNode | null

通过组件的id获取当前窗口上的实体节点。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名   | 类型                                       | 必填   | 说明                                    |
| ----- | ---------------------------------------- | ---- | ------------------------------------- |
| id | string | 是    | 节点对应的[组件标识](arkui-ts/ts-universal-attributes-component-id.md)。                          |

**返回值：**

| 类型                                       | 说明            |
| ---------------------------------------- | ------------- |
| [FrameNode](js-apis-arkui-frameNode.md)  \| null | 返回的组件树的实体节点或者空节点。 |

> **说明：**
>
> getAttachedFrameNodeById仅能查询上屏节点。

**示例：**

```ts
@Entry
@Component
struct MyComponent {
  @State message: string = 'Hello World';

  build() {
    RelativeContainer() {
      Text(this.message)
        .id('HelloWorld')
        .fontSize($r('app.float.page_text_font_size'))
        .fontWeight(FontWeight.Bold)
        .alignRules({
          center: { anchor: '__container__', align: VerticalAlign.Center },
          middle: { anchor: '__container__', align: HorizontalAlign.Center }
        })
        .onClick(() => {
          let node = this.getUIContext().getAttachedFrameNodeById("HelloWorld");
          console.log(`Find HelloWorld Tag:${node!.getNodeType()} id:${node!.getUniqueId()}`);
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

### getFrameNodeByUniqueId<sup>12+</sup>

getFrameNodeByUniqueId(id: number): FrameNode | null

提供getFrameNodeByUniqueId接口通过组件的uniqueId获取组件树的实体节点。
1. 当uniqueId对应的是系统组件时，返回组件所对应的FrameNode；
2. 当uniqueId对应的是自定义组件时，若其有渲染内容，则返回该自定义组件的根节点，类型为__Common__；若其无渲染内容，则返回其第一个子组件的FrameNode。
3. 当uniqueId无对应的组件时，返回null。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名   | 类型                                       | 必填   | 说明                                    |
| ----- | ---------------------------------------- | ---- | ------------------------------------- |
| id | number | 是    | 节点对应的UniqueId                          |

**返回值：**

| 类型                                       | 说明            |
| ---------------------------------------- | ------------- |
| [FrameNode](js-apis-arkui-frameNode.md)  \| null | 返回的组件树的实体节点或者空节点。 |

**示例：**

```ts
import { UIContext, FrameNode } from '@kit.ArkUI';

@Entry
@Component
struct MyComponent {
  aboutToAppear() {
    let uniqueId: number = this.getUniqueId();
    let uiContext: UIContext = this.getUIContext();
    if (uiContext) {
      let node: FrameNode | null = uiContext.getFrameNodeByUniqueId(uniqueId);
    }
  }

  build() {
    // ...
  }
}
```

### getPageInfoByUniqueId<sup>12+</sup>

getPageInfoByUniqueId(id: number): PageInfo

提供getPageInfoByUniqueId接口通过组件的uniqueId获取该节点对应的Router和NavDestination页面信息。
1. 当uniqueId对应的节点在Page节点中，routerPageInfo属性为其对应的Router信息；
2. 当uniqueId对应的节点在NavDestination节点中，navDestinationInfo属性为其对应的NavDestination信息；
3. 当uniqueId对应的节点无对应的Router或NavDestination信息时，对应的属性为undefined；
4. 模态弹窗并不在任何Page节点中。当uniqueId对应的节点在模态弹窗中,例如[CustomDialog](./arkui-ts/ts-methods-custom-dialog-box.md)、[bindSheet](./arkui-ts/ts-universal-attributes-sheet-transition.md#bindsheet)和[bindContentCover](./arkui-ts/ts-universal-attributes-modal-transition.md#bindcontentcover)构建的模态页面中，routerPageInfo属性为undefined。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名   | 类型                                       | 必填   | 说明                                    |
| ----- | ---------------------------------------- | ---- | ------------------------------------- |
| id | number | 是    | 节点对应的UniqueId                          |

**返回值：**

| 类型                                       | 说明            |
| ---------------------------------------- | ------------- |
| [PageInfo](#pageinfo12) | 返回节点对应的Router和NavDestination信息。 |

**示例：**

```ts
import { UIContext, PageInfo } from '@kit.ArkUI';

@Entry
@Component
struct PageInfoExample {
  @Provide('pageInfos') pageInfos: NavPathStack = new NavPathStack();

  build() {
    Column() {
      Navigation(this.pageInfos) {
        NavDestination() {
          MyComponent()
        }
      }.id('navigation')
    }
  }
}

@Component
struct MyComponent {
  @State content: string = '';

  build() {
    Column() {
      Text('PageInfoExample')
      Button('click').onClick(() => {
        const uiContext: UIContext = this.getUIContext();
        const uniqueId: number = this.getUniqueId();
        const pageInfo: PageInfo = uiContext.getPageInfoByUniqueId(uniqueId);
        console.info('pageInfo: ' + JSON.stringify(pageInfo));
        console.info('navigationInfo: ' + JSON.stringify(uiContext.getNavigationInfoByUniqueId(uniqueId)));
      })
      TextArea({
        text: this.content
      })
      .width('100%')
      .height(100)
    }
    .width('100%')
    .alignItems(HorizontalAlign.Center)
  }
}
```

### getNavigationInfoByUniqueId<sup>12+</sup>

getNavigationInfoByUniqueId(id: number): observer.NavigationInfo | undefined

提供getNavigationInfoByUniqueId接口通过组件的uniqueId获取该节点对应的Navigation页面信息。
1. 当uniqueId对应的节点在Navigation节点中，返回其对应的Navigation信息；
2. 当uniqueId对应的节点无对应的Navigation信息时，返回undefined。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名   | 类型                                       | 必填   | 说明                                    |
| ----- | ---------------------------------------- | ---- | ------------------------------------- |
| id | number | 是    | 节点对应的UniqueId                          |

**返回值：**

| 类型                                       | 说明            |
| ---------------------------------------- | ------------- |
| observer.[NavigationInfo](js-apis-arkui-observer.md#navigationinfo12) \| undefined | 返回节点对应的Navigation信息。 |

**示例：**

请参考[getPageInfoByUniqueId](#getpageinfobyuniqueid12)的示例。

### showAlertDialog

showAlertDialog(options: AlertDialogParamWithConfirm | AlertDialogParamWithButtons | AlertDialogParamWithOptions): void

显示警告弹窗组件，可设置文本内容与响应回调。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名     | 类型                                       | 必填   | 说明                  |
| ------- | ---------------------------------------- | ---- | ------------------- |
| options | [AlertDialogParamWithConfirm](arkui-ts/ts-methods-alert-dialog-box.md#alertdialogparamwithconfirm对象说明)&nbsp;\|&nbsp;[AlertDialogParamWithButtons](arkui-ts/ts-methods-alert-dialog-box.md#alertdialogparamwithbuttons对象说明)&nbsp;\|&nbsp;[AlertDialogParamWithOptions](arkui-ts/ts-methods-alert-dialog-box.md#alertdialogparamwithoptions10对象说明) | 是    | 定义并显示AlertDialog组件。 |


**示例：**

```ts
@Entry
@Component
struct Index {
  uiContext: UIContext = this.getUIContext()

  build() {
    Column() {
      Button('showAlertDialog')
        .onClick(() => {
          this.uiContext.showAlertDialog(
            {
              title: 'title',
              message: 'text',
              autoCancel: true,
              alignment: DialogAlignment.Bottom,
              offset: { dx: 0, dy: -20 },
              gridCount: 3,
              confirm: {
                value: 'button',
                action: () => {
                  console.info('Button-clicking callback')
                }
              },
              cancel: () => {
                console.info('Closed callbacks')
              }
            }
          );
        })
    }.height('100%').width('100%').justifyContent(FlexAlign.Center)
  }
}
```

### showActionSheet

showActionSheet(value: ActionSheetOptions): void

定义列表弹窗并弹出。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型                                                         | 必填 | 说明                 |
| ------ | ------------------------------------------------------------ | ---- | -------------------- |
| value  | [ActionSheetOptions](arkui-ts/ts-methods-action-sheet.md#actionsheetoptions对象说明) | 是   | 配置列表弹窗的参数。 |

**示例：**

```ts
@Entry
@Component
struct Index {
  uiContext: UIContext = this.getUIContext()

  build() {
    Column() {
      Button('showActionSheet')
        .onClick(() => {
          this.uiContext.showActionSheet({
            title: 'ActionSheet title',
            message: 'message',
            autoCancel: true,
            confirm: {
              value: 'Confirm button',
              action: () => {
                console.info('Get ActionSheet handled');
              }
            },
            cancel: () => {
              console.info('ActionSheet canceled');
            },
            alignment: DialogAlignment.Bottom,
            offset: { dx: 0, dy: -10 },
            sheets: [
              {
                title: 'apples',
                action: () => {
                  console.info('apples');
                }
              },
              {
                title: 'bananas',
                action: () => {
                  console.info('bananas');
                }
              },
              {
                title: 'pears',
                action: () => {
                  console.info('pears');
                }
              }
            ]
          });
        })
    }.height('100%').width('100%').justifyContent(FlexAlign.Center)
  }
}
```

### showDatePickerDialog

showDatePickerDialog(options: DatePickerDialogOptions): void

定义日期滑动选择器弹窗并弹出。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 该接口在Wearable设备上使用时，应用程序运行异常，异常信息中提示接口未定义，在其他设备中可正常调用。

**参数：** 

| 参数名  | 类型                                                         | 必填 | 说明                           |
| ------- | ------------------------------------------------------------ | ---- | ------------------------------ |
| options | [DatePickerDialogOptions](arkui-ts/ts-methods-datepicker-dialog.md#datepickerdialogoptions对象说明) | 是   | 配置日期滑动选择器弹窗的参数。 |

**示例：**

```ts
// xxx.ets
@Entry
@Component
struct DatePickerDialogExample {
  selectedDate: Date = new Date("2010-1-1");

  build() {
    Column() {
      Button("DatePickerDialog")
        .margin(20)
        .onClick(() => {
          this.getUIContext().showDatePickerDialog({
            start: new Date("2000-1-1"),
            end: new Date("2100-12-31"),
            selected: this.selectedDate,
            showTime: true,
            useMilitaryTime: false,
            dateTimeOptions: { hour: "numeric", minute: "2-digit" },
            onDateAccept: (value: Date) => {
              // 通过Date的setFullYear方法设置按下确定按钮时的日期，这样当弹窗再次弹出时显示选中的是上一次确定的日期
              this.selectedDate = value;
              console.info("DatePickerDialog:onDateAccept()" + value.toString());
            },
            onCancel: () => {
              console.info("DatePickerDialog:onCancel()");
            },
            onDateChange: (value: Date) => {
              console.info("DatePickerDialog:onDateChange()" + value.toString());
            },
            onDidAppear: () => {
              console.info("DatePickerDialog:onDidAppear()");
            },
            onDidDisappear: () => {
              console.info("DatePickerDialog:onDidDisappear()");
            },
            onWillAppear: () => {
              console.info("DatePickerDialog:onWillAppear()");
            },
            onWillDisappear: () => {
              console.info("DatePickerDialog:onWillDisappear()");
            }
          })
        })
    }.width('100%')
  }
}
```

### showTimePickerDialog

showTimePickerDialog(options: TimePickerDialogOptions): void

定义时间滑动选择器弹窗并弹出。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 该接口在Wearable设备上使用时，应用程序运行异常，异常信息中提示接口未定义，在其他设备中可正常调用。

**参数：** 

| 参数名  | 类型                                                         | 必填 | 说明                           |
| ------- | ------------------------------------------------------------ | ---- | ------------------------------ |
| options | [TimePickerDialogOptions](arkui-ts/ts-methods-timepicker-dialog.md#timepickerdialogoptions对象说明) | 是   | 配置时间滑动选择器弹窗的参数。 |

**示例：**

```ts
// xxx.ets

class SelectTime{
  selectTime: Date = new Date('2020-12-25T08:30:00');
  hours(h:number,m:number){
    this.selectTime.setHours(h, m);
  }
}

@Entry
@Component
struct TimePickerDialogExample {
  @State selectTime: Date = new Date('2023-12-25T08:30:00');

  build() {
    Column() {
      Button('showTimePickerDialog')
        .margin(30)
        .onClick(() => {
          this.getUIContext().showTimePickerDialog({
            selected: this.selectTime,
            onAccept: (value: TimePickerResult) => {
              // 设置selectTime为按下确定按钮时的时间，这样当弹窗再次弹出时显示选中的为上一次确定的时间
              let time = new SelectTime();
              if(value.hour && value.minute){
                time.hours(value.hour, value.minute);
              }
              console.info("TimePickerDialog:onAccept()" + JSON.stringify(value));
            },
            onCancel: () => {
              console.info("TimePickerDialog:onCancel()");
            },
            onChange: (value: TimePickerResult) => {
              console.info("TimePickerDialog:onChange()" + JSON.stringify(value));
            }
          });
        })
    }.width('100%').margin({ top: 5 })
  }
}
```

### showTextPickerDialog

showTextPickerDialog(options: TextPickerDialogOptions): void

定义文本滑动选择器弹窗并弹出。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**设备行为差异：** 该接口在Wearable设备上使用时，应用程序运行异常，异常信息中提示接口未定义，在其他设备中可正常调用。

**参数：** 

| 参数名  | 类型                                                         | 必填 | 说明                           |
| ------- | ------------------------------------------------------------ | ---- | ------------------------------ |
| options | [TextPickerDialogOptions](arkui-ts/ts-methods-textpicker-dialog.md#textpickerdialogoptions对象说明) | 是   | 配置文本滑动选择器弹窗的参数。 |

**示例：**

```ts
// xxx.ets

class SelectedValue{
  select: number = 2;
  set(val: number){
    this.select = val;
  }
}
class SelectedArray{
  select: number[] = [];
  set(val: number[]){
    this.select = val;
  }
}
@Entry
@Component
struct TextPickerDialogExample {
  @State selectTime: Date = new Date('2023-12-25T08:30:00');
  private fruits: string[] = ['apple1', 'orange2', 'peach3', 'grape4', 'banana5'];
  private select: number  = 0;
  build() {
    Column() {
      Button('showTextPickerDialog')
        .margin(30)
        .onClick(() => {
          this.getUIContext().showTextPickerDialog({
            range: this.fruits,
            selected: this.select,
            onAccept: (value: TextPickerResult) => {
              // 设置select为按下确定按钮时候的选中项index，这样当弹窗再次弹出时显示选中的是上一次确定的选项
              let selectedVal = new SelectedValue();
              let selectedArr = new SelectedArray();
              if (value.index){
                value.index instanceof Array?selectedArr.set(value.index) : selectedVal.set(value.index);
              }
              console.info("TextPickerDialog:onAccept()" + JSON.stringify(value));
            },
            onCancel: () => {
              console.info("TextPickerDialog:onCancel()");
            },
            onChange: (value: TextPickerResult) => {
              console.info("TextPickerDialog:onChange()" + JSON.stringify(value));
            }
          });
        })
    }.width('100%').margin({ top: 5 })
  }
}
```

### createAnimator

createAnimator(options: AnimatorOptions): AnimatorResult

定义Animator类。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：**  SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名     | 类型                                       | 必填   | 说明      |
| ------- | ---------------------------------------- | ---- | ------- |
| options | [AnimatorOptions](js-apis-animator.md#animatoroptions) | 是    | 定义动画选项。 |

**返回值：**

| 类型                                       | 说明            |
| ---------------------------------------- | ------------- |
| [AnimatorResult](js-apis-animator.md#animatorresult) | Animator结果接口。 |


**错误码**：

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |

**示例：**

```ts
// EntryAbility.ets
import { AbilityConstant, Configuration, ConfigurationConstant, UIAbility, Want } from '@kit.AbilityKit';
import { AnimatorOptions, window } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    // 创建主窗口，设置此功能的主页
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onWindowStageCreate');
    windowStage.loadContent('pages/Index', (err, data) => {
      if (err.code) {
        hilog.error(0x0000, 'testTag', 'Failed to load the content. Cause: %{public}s', JSON.stringify(err) ?? '');
        return;
      }
      hilog.info(0x0000, 'testTag', 'Succeeded in loading the content. Data: %{public}s', JSON.stringify(data) ?? '');
      let uiContext = windowStage.getMainWindowSync().getUIContext();
      let options:AnimatorOptions = {
        duration: 1500,
        easing: "friction",
        delay: 0,
        fill: "forwards",
        direction: "normal",
        iterations: 3,
        begin: 200.0,
        end: 400.0
      };
      uiContext.createAnimator(options);
    });
  }
}
```

### createAnimator<sup>18+</sup>

createAnimator(options: AnimatorOptions | SimpleAnimatorOptions): AnimatorResult

创建animator动画结果对象（AnimatorResult）。与[createAnimator](#createanimator)相比，新增对[SimpleAnimatorOptions](js-apis-animator.md#simpleanimatoroptions18)类型入参的支持。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：**  SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名     | 类型                                       | 必填   | 说明      |
| ------- | ---------------------------------------- | ---- | ------- |
| options | [AnimatorOptions](js-apis-animator.md#animatoroptions) \| [SimpleAnimatorOptions](js-apis-animator.md#simpleanimatoroptions18) | 是    | 定义动画选项。 |

**返回值：**

| 类型                                       | 说明            |
| ---------------------------------------- | ------------- |
| [AnimatorResult](js-apis-animator.md#animatorresult) | Animator结果接口。 |

**错误码**：

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |

**示例：**

```ts
import { AbilityConstant, Configuration, ConfigurationConstant, UIAbility, Want } from '@kit.AbilityKit';
import { SimpleAnimatorOptions, window } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    // 创建主窗口，设置此功能的主页
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onWindowStageCreate');
    windowStage.loadContent('pages/Index', (err, data) => {
      if (err.code) {
        hilog.error(0x0000, 'testTag', 'Failed to load the content. Cause: %{public}s', JSON.stringify(err) ?? '');
        return;
      }
      hilog.info(0x0000, 'testTag', 'Succeeded in loading the content. Data: %{public}s', JSON.stringify(data) ?? '');
      let uiContext = windowStage.getMainWindowSync().getUIContext();
      let options: SimpleAnimatorOptions = new SimpleAnimatorOptions(100, 200).duration(2000);
      uiContext.createAnimator(options);
    });
  }
}
```

### runScopedTask

runScopedTask(callback: () => void): void

在当前UI上下文执行传入的回调函数。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：**  SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名      | 类型         | 必填   | 说明   |
| -------- | ---------- | ---- | ---- |
| callback | () => void | 是    | 回调函数 |

**示例：**

```ts
@Entry
@Component
struct Index {
  uiContext = this.getUIContext();

  build() {
    Row() {
      Column() {
        Button("run task").onClick(()=>{
          this.uiContext.runScopedTask(()=>{
            // do something
          })
        })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### setKeyboardAvoidMode<sup>11+</sup>

setKeyboardAvoidMode(value: KeyboardAvoidMode): void

配置虚拟键盘弹出时，页面的避让模式。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：**  SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名      | 类型         | 必填   | 说明   |
| -------- | ---------- | ---- | ---- |
| value | [KeyboardAvoidMode](#keyboardavoidmode11)| 是    | 键盘避让时的页面避让模式。<br />默认值:KeyboardAvoidMode.OFFSET |

>  **说明：**
>
>  KeyboardAvoidMode.RESIZE模式会压缩页面大小，页面中设置百分比宽高的组件会跟随页面压缩，而直接设置宽高的组件会按设置的固定大小布局。设置KeyboardAvoidMode的RESIZE模式时，expandSafeArea([SafeAreaType.KEYBOARD],[SafeAreaEdge.BOTTOM])不生效。
>
>  KeyboardAvoidMode.NONE模式配置页面不避让键盘，页面会被抬起的键盘遮盖。
>
>  setKeyboardAvoidMode针对页面生效，对于弹窗类组件不生效，比如Dialog、Popup、Menu、BindSheet、BindContentCover、Toast、OverlayManager。弹窗类组件的避让模式可以参考[CustomDialogControllerOptions对象说明](./arkui-ts/ts-methods-custom-dialog-box.md#customdialogcontrolleroptions对象说明)。

**示例：**

完整示例请参考[示例4（设置键盘避让模式为压缩）](./arkui-ts/ts-universal-attributes-expand-safe-area.md#示例4设置键盘避让模式为压缩)、[示例5（设置键盘避让模式为上抬）](./arkui-ts/ts-universal-attributes-expand-safe-area.md#示例5设置键盘避让模式为上抬)以及[示例6（切换避让模式）](./arkui-ts/ts-universal-attributes-expand-safe-area.md#示例6切换避让模式)。

```ts
// EntryAbility.ets
import { KeyboardAvoidMode, UIContext } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

onWindowStageCreate(windowStage: window.WindowStage) {
    // Main window is created, set main page for this ability
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onWindowStageCreate');

    windowStage.loadContent('pages/Index', (err, data) => {
      let uiContext: UIContext = windowStage.getMainWindowSync().getUIContext();
      uiContext.setKeyboardAvoidMode(KeyboardAvoidMode.RESIZE);
      if (err.code) {
        hilog.error(0x0000, 'testTag', 'Failed to load the content. Cause: %{public}s', JSON.stringify(err) ?? '');
        return;
      }
      hilog.info(0x0000, 'testTag', 'Succeeded in loading the content. Data: %{public}s', JSON.stringify(data) ?? '');
    });
  }
```

### getKeyboardAvoidMode<sup>11+</sup>

getKeyboardAvoidMode(): KeyboardAvoidMode

获取虚拟键盘弹出时，页面的避让模式。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：**  SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型         | 说明   |
| ---------- | ---- |
| [KeyboardAvoidMode](#keyboardavoidmode11)| 返回当前的页面避让模式。|

**示例：**

完整示例请参考[示例4（设置键盘避让模式为压缩）](./arkui-ts/ts-universal-attributes-expand-safe-area.md#示例4设置键盘避让模式为压缩)、[示例5（设置键盘避让模式为上抬）](./arkui-ts/ts-universal-attributes-expand-safe-area.md#示例5设置键盘避让模式为上抬)以及[示例6（切换避让模式）](./arkui-ts/ts-universal-attributes-expand-safe-area.md#示例6切换避让模式)。

```ts
// EntryAbility.ets
import { KeyboardAvoidMode, UIContext } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

onWindowStageCreate(windowStage: window.WindowStage) {
    // Main window is created, set main page for this ability
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onWindowStageCreate');

    windowStage.loadContent('pages/Index', (err, data) => {
      let uiContext: UIContext = windowStage.getMainWindowSync().getUIContext();
      let KeyboardAvoidMode = uiContext.getKeyboardAvoidMode();
      hilog.info(0x0000, "KeyboardAvoidMode:", JSON.stringify(KeyboardAvoidMode));
      if (err.code) {
        hilog.error(0x0000, 'testTag', 'Failed to load the content. Cause: %{public}s', JSON.stringify(err) ?? '');
        return;
      }
      hilog.info(0x0000, 'testTag', 'Succeeded in loading the content. Data: %{public}s', JSON.stringify(data) ?? '');
    });
  }

```

### getAtomicServiceBar<sup>11+</sup>

getAtomicServiceBar(): Nullable\<AtomicServiceBar>

获取AtomicServiceBar对象，通过该对象设置原子化服务menuBar的属性。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：**  SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型                                              | 说明                                                         |
| ------------------------------------------------- | ------------------------------------------------------------ |
| Nullable<[AtomicServiceBar](#atomicservicebar11)> | 如果是原子化服务则返回AtomicServerBar类型，否则返回undefined。 |

**示例：**

```ts
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { UIContext, AtomicServiceBar, window } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';
export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    // Main window is created, set main page for this ability
    hilog.info(0x0000, 'testTag', 'Ability onWindowStageCreate');
    windowStage.loadContent('pages/Index', (err, data) => {
      let uiContext: UIContext = windowStage.getMainWindowSync().getUIContext();
      let atomicServiceBar: Nullable<AtomicServiceBar> = uiContext.getAtomicServiceBar();
      if (atomicServiceBar != undefined) {
        hilog.info(0x0000, 'testTag', 'Get AtomServiceBar Successfully.');
      } else {
        hilog.error(0x0000, 'testTag', 'Get AtomicServiceBar failed.');
      }
    });
  }
}
```
### getDragController<sup>11+</sup>

getDragController(): DragController

获取DragController对象，可通过该对象创建并发起拖拽。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：**  SystemCapability.ArkUI.ArkUI.Full

**返回值：**

|类型|说明|
|----|----|
|[DragController](js-apis-arkui-dragController.md#ohosarkuidragcontroller-dragcontroller)| 获取DragController对象。|

**示例：**

完整示例请参考[DragController](#dragcontroller11)中的示例。

### keyframeAnimateTo<sup>11+</sup>

keyframeAnimateTo(param: KeyframeAnimateParam, keyframes: Array&lt;KeyframeState&gt;): void

产生关键帧动画。该接口的使用说明请参考[keyframeAnimateTo](arkui-ts/ts-keyframeAnimateTo.md)。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：**  SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型                                              | 必填 | 说明                      |
| ------------ | ---------------------------------------------------- | ------- | ---------------------------- |
| param        | [KeyframeAnimateParam](arkui-ts/ts-keyframeAnimateTo.md#keyframeanimateparam对象说明) | 是      | 关键帧动画的整体动画参数。     |
| keyframes    | Array&lt;[KeyframeState](arkui-ts/ts-keyframeAnimateTo.md#keyframestate对象说明)&gt;  | 是      | 所有的关键帧状态。            |

**示例：**

```ts
// xxx.ets
import { UIContext } from '@kit.ArkUI';

@Entry
@Component
struct KeyframeDemo {
  @State myScale: number = 1.0;
  uiContext: UIContext | undefined = undefined;

  aboutToAppear() {
    this.uiContext = this.getUIContext();
  }

  build() {
    Column() {
      Circle()
        .width(100)
        .height(100)
        .fill("#46B1E3")
        .margin(100)
        .scale({ x: this.myScale, y: this.myScale })
        .onClick(() => {
          if (!this.uiContext) {
            console.info("no uiContext, keyframe failed");
            return;
          }
          this.myScale = 1;
          // 设置关键帧动画整体播放3次
          this.uiContext.keyframeAnimateTo({
              iterations: 3,
              expectedFrameRateRange: {
                min: 10,
                max: 120,
                expected: 60,
              }
            }, [
            {
              // 第一段关键帧动画时长为800ms，scale属性做从1到1.5的动画
              duration: 800,
              event: () => {
                this.myScale = 1.5;
              }
            },
            {
              // 第二段关键帧动画时长为500ms，scale属性做从1.5到1的动画
              duration: 500,
              event: () => {
                this.myScale = 1;
              }
            }
          ]);
        })
    }.width('100%').margin({ top: 5 })
  }
}
```

### getFocusController<sup>12+</sup>

getFocusController(): FocusController

获取[FocusController](js-apis-arkui-UIContext.md#focuscontroller12)对象，可通过该对象控制焦点。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：**  SystemCapability.ArkUI.ArkUI.Full

**返回值：**

|类型|说明|
|----|----|
|[FocusController](js-apis-arkui-UIContext.md#focuscontroller12)| 获取FocusController对象。|

**示例：**

完整示例请参考[FocusController](js-apis-arkui-UIContext.md#focuscontroller12)中的示例。

### getFilteredInspectorTree<sup>12+</sup>

getFilteredInspectorTree(filters?: Array\<string\>): string

获取组件树及组件属性。此接口耗时较长，仅适用于测试场景。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：**  SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名  | 类型            | 必填 | 说明                                                         |
| ------- | --------------- | ---- | ------------------------------------------------------------ |
| filters | Array\<string\> | 否   | 需要获取的组件属性的过滤列表。目前仅支持过滤字段：<br/>"id"：组件唯一标识。<br/>"src"：资源来源。 <br/>"content"：元素、组件或对象所包含的信息或数据。<br/>"editable"：是否可编辑。<br/>"scrollable"：是否可滚动。<br/>"selectable"：是否可选择。<br/>"focusable"：是否可聚焦。<br/>"focused"：是否已聚焦。<br/>如果在filters参数中包含以上一个或者多个字段，则未包含的字段会在组件属性查询结果中被过滤掉。如果用户未传入filters参数或者filters参数为空数组，则以上字段全部不会在组件属性查询结果中被过滤掉。<br/>从API version 20开始，支持该过滤字段：<br/>"isLayoutInspector"：返回组件树是否包含[自定义组件](../../ui/state-management/arkts-create-custom-components.md)。如果用户未传入filters参数或者filters数组不包含isLayoutInspector，返回的组件树将缺少自定义组件的信息。<br/>其余字段仅供测试场景使用。 |

**返回值：** 

| 类型   | 说明                               |
| ------ | ---------------------------------- |
| string | 获取组件树及组件属性的JSON字符串。组件中每个字段的含义请参考[getInspectorInfo](./js-apis-arkui-frameNode.md#getinspectorinfo12)的返回值说明。 |

**错误码**：

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------- |
| 401      | Parameter error. Possible causes: <br /> 1. Mandatory parameters are left unspecified. <br /> 2. Incorrect parameters types. <br /> 3. Parameter verification failed.  |

**示例：**

<!--code_no_check-->
```ts
uiContext.getFilteredInspectorTree(['id', 'src', 'content']);
```

<!--code_no_check-->
```ts
// xxx.ets
import { UIContext } from '@kit.ArkUI';
@Entry
@Component
struct ComponentPage {
  loopConsole(inspectorStr: string, i: string) {
    console.log(`InsTree ${i}| type: ${JSON.parse(inspectorStr).$type}, ID: ${JSON.parse(inspectorStr).$ID}`)
    if (JSON.parse(inspectorStr).$children) {
      i += '-'
      for (let index = 0; index < JSON.parse(inspectorStr).$children.length; index++) {
        this.loopConsole(JSON.stringify(JSON.parse(inspectorStr).$children[index]), i)
      }
    }
  }

  build() {
    Column() {
      Button('content').onClick(() => {
        const uiContext: UIContext = this.getUIContext();
        let inspectorStr = uiContext.getFilteredInspectorTree(['content']);
        console.log(`InsTree : ${inspectorStr}`)
        inspectorStr = JSON.stringify(JSON.parse(inspectorStr))
        this.loopConsole(inspectorStr, '-')
      })
      Button('isLayoutInspector').onClick(() => {
        const uiContext: UIContext = this.getUIContext();
        let inspectorStr = uiContext.getFilteredInspectorTree(['isLayoutInspector']);
        console.log(`InsTree : ${inspectorStr}`)
        inspectorStr = JSON.stringify(JSON.parse(inspectorStr).content)
        this.loopConsole(inspectorStr, '-')
      })
    }
    .width('100%')
    .height('100%')
  }
}
```

当传入"content"过滤字段时，返回的JSON字符串结构如下：

<!--code_no_check-->
```ts
InsTree : {"$type":"root","width":"720.000000","height":"1280.000000","$resolution":"1.500000","$children":[{"$type":"Column","$ID":15,"type":"build-in","$rect":"[0.00, 72.00],[720.00,1208.00]","$debugLine":"","$attrs":{},"$children":[{"$type":"Button","$ID":16,"type":"build-in","$rect":"[293.00, 72.00],[427.00,132.00]","$debugLine":"","$attrs":{}},{"$type":"Button","$ID":18,"type":"build-in","$rect":"[237.00, 132.00],[484.00,192.00]","$debugLine":"","$attrs":{}}]}]}\
InsTree -| type: root, ID: undefined
InsTree --| type: Column, ID: 15
InsTree ---| type: Button, ID: 16
InsTree ---| type: Button, ID: 18
```

从API version 20开始，当传入"isLayoutInspector"过滤字段时，返回的JSON字符串结构新增外层结构"type"与"content"，其中"content"包含未增加该字段时的原有JSON字符串结构；同时，返回值结构中增添自定义组件。返回的JSON字符串结构如下：

<!--code_no_check-->
```ts
InsTree : {"type":"root","content":{"$type":"root","width":"720.000000","height":"1280.000000","$resolution":"1.500000","$children":[{"$type":"JsView","$ID":13,"type":"custom","state":{"observedPropertiesInfo":[],"viewInfo":{"componentName":"ComponentPage","id":14,"isV2":false,"isViewActive_":true}},"$rect":"[0.00, 72.00],[720.00,1208.00]","$debugLine":"{\"$line\":\"(0:0)\"}","viewTag":"ComponentPage","$attrs":{"viewKey":"13"},"$children":[{"$type":"Column","$ID":15, "type":"build-in","$rect":"[0.00, 72.00],[720.00,1208.00]","$debugLine":"","$attrs":{ ...
InsTree -| type: root, ID: undefined
InsTree --| type: JsView, ID: 13
InsTree ---| type: Column, ID: 15
InsTree ----| type: Button, ID: 16
InsTree ----| type: Button, ID: 18
```

### getFilteredInspectorTreeById<sup>12+</sup>

getFilteredInspectorTreeById(id: string, depth: number, filters?: Array\<string\>): string

获取指定的组件及其子组件的属性。此接口耗时较长，仅适用于测试场景。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：**  SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名  | 类型            | 必填 | 说明                                                         |
| ------- | --------------- | ---- | ------------------------------------------------------------ |
| id      | string          | 是   | 指定的[组件标识](arkui-ts/ts-universal-attributes-component-id.md)id。 |
| depth   | number          | 是   | 获取子组件的层数。当取值0时，获取指定的组件及其所有的子孙组件的属性。当取值1时，仅获取指定的组件的属性。当取值2时，指定的组件及其1层子组件的属性。以此类推。 |
| filters | Array\<string\> | 否   | 需要获取的组件属性的过滤列表。目前仅支持过滤字段：<br/>"id"：组件唯一标识。<br/>"src"：资源来源。 <br/>"content"：元素、组件或对象所包含的信息或数据。<br/>"editable"：是否可编辑。<br/>"scrollable"：是否可滚动。<br/>"selectable"：是否可选择。<br/>"focusable"：是否可聚焦。<br/>"focused"：是否已聚焦。<br/>如果在filters参数中包含以上一个或者多个字段，则未包含的字段会在组件属性查询结果中被过滤掉。如果用户未传入filters参数或者filters参数为空数组，则以上字段全部不会在组件属性查询结果中被过滤掉。<br/>其余字段仅供测试场景使用。 |

**返回值：** 

| 类型   | 说明                                         |
| ------ | -------------------------------------------- |
| string | 获取指定的组件及其子组件的属性的JSON字符串。组件中每个字段的含义请参考[getInspectorInfo](./js-apis-arkui-frameNode.md#getinspectorinfo12)的返回值说明。 |


**错误码**：

以下错误码详细介绍请参考[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | -------- |
| 401      | Parameter error. Possible causes: <br /> 1. Mandatory parameters are left unspecified. <br /> 2. Incorrect parameters types. <br /> 3. Parameter verification failed.  |

**示例：**

<!--code_no_check-->
```ts
uiContext.getFilteredInspectorTreeById('testId', 0, ['id', 'src', 'content']);
```

<!--code_no_check-->
```ts
import { UIContext } from '@kit.ArkUI';
@Entry
@Component
struct ComponentPage {
  build() {
    Column() {
      Text("Hello World")
        .fontSize(20)
        .id("TEXT")
      Button('getFilteredInspectorTreeById').onClick(() => {
        const uiContext: UIContext = this.getUIContext();
        try {
          let inspectorStr = uiContext.getFilteredInspectorTreeById('TEXT', 1, ["id", "src"]);
          console.info(`result1: ${inspectorStr}`);
          inspectorStr = JSON.stringify(JSON.parse(inspectorStr)['$children'][0]);
          console.info(`result2: ${inspectorStr}`);
          inspectorStr = uiContext.getFilteredInspectorTreeById('TEXT', 1, ["src"]);
          inspectorStr = JSON.stringify(JSON.parse(inspectorStr)['$children'][0]);
          console.info(`result3: ${inspectorStr}`);
        } catch(e) {
          console.info(`getFilteredInspectorTreeById error: ${e}`);
        }
      })
    }
    .width('100%')
    .height('100%')
  }
}
```
返回的JSON字符串结构如下：
<!--code_no_check-->
```ts
result1: {"$type":"root","width":"1260.000000","height":"2720.000000","$resolution":"3.250000","$children":[{"$type":"Text","$ID":6,"type":"build-in","$rect":"[457.00, 123.00],[804.00,199.00]","$debugLine":"","$attrs":{"id":"TEXT","isLayoutDirtyMarked":false,"isRenderDirtyMarked":false,"isMeasureBoundary":false,"hasPendingRequest":false,"isFirstBuilding":false}}]}
result2: {"$type":"Text","$ID":6,"type":"build-in","$rect":"[457.00, 123.00],[804.00,199.00]","$debugLine":"","$attrs":{"id":"TEXT","isLayoutDirtyMarked":false,"isRenderDirtyMarked":false,"isMeasureBoundary":false,"hasPendingRequest":false,"isFirstBuilding":false}}
result3: {"$type":"Text","$ID":6,"type":"build-in","$rect":"[457.00, 123.00],[804.00,199.00]","$debugLine":"","$attrs":{"isLayoutDirtyMarked":false,"isRenderDirtyMarked":false,"isMeasureBoundary":false,"hasPendingRequest":false,"isFirstBuilding":false}}
```
若需获取getFilteredInspectorTreeById方法中首个参数id指定的组件，须参照示例代码将getFilteredInspectorTreeById方法结果先转换为json对象，随后提取$children数组的首项。通过result2和result3的结果对比可知，如果filters参数由["id", "src"]改为["src"]，获取到的\$attrs属性将缺少"id"这一key。


### getCursorController<sup>12+</sup>

getCursorController(): CursorController

获取[CursorController](js-apis-arkui-UIContext.md#cursorcontroller12)对象，可通过该对象控制光标。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：**  SystemCapability.ArkUI.ArkUI.Full

**返回值：**

|类型|说明|
|----|----|
|[CursorController](js-apis-arkui-UIContext.md#cursorcontroller12)| 获取CursorController对象。|

**示例：**

完整示例请参考[CursorController](#cursorcontroller12)中的示例。

### getContextMenuController<sup>12+</sup>

getContextMenuController(): ContextMenuController

获取[ContextMenuController](#contextmenucontroller12)对象，可通过该对象控制菜单。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：**  SystemCapability.ArkUI.ArkUI.Full

**返回值：**

|类型|说明|
|----|----|
|[ContextMenuController](#contextmenucontroller12)| 获取ContextMenuController对象。|

### getMeasureUtils<sup>12+</sup>

getMeasureUtils(): MeasureUtils

允许用户通过UIContext对象，获取MeasureUtils对象进行文本计算。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：**  SystemCapability.ArkUI.ArkUI.Full

**返回值：** 

| 类型   | 说明                                         |
| ------ | -------------------------------------------- |
| [MeasureUtils](js-apis-arkui-UIContext.md#measureutils12) | 提供文本宽度、高度等相关计算。 |

**示例：**

完整示例请参考[MeasureUtils](#measureutils12)中的示例。

### getComponentSnapshot<sup>12+</sup>

getComponentSnapshot(): ComponentSnapshot

获取ComponentSnapshot对象，可通过该对象获取组件截图的能力。

典型使用场景（如长截图）及最佳实践请参考[使用组件截图](../../ui/arkts-uicontext-component-snapshot.md)。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：**  SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型                                                         | 说明                        |
| ------------------------------------------------------------ | --------------------------- |
| [ComponentSnapshot](js-apis-arkui-UIContext.md#componentsnapshot12) | 获取ComponentSnapshot对象。 |

**示例：**

完整示例请参考[ComponentSnapshot](#componentsnapshot12)中的示例。

### vp2px<sup>12+</sup>

vp2px(value : number) : number

将vp单位的数值转换为以px为单位的数值。

转换公式为：px值 = vp值 × 像素密度

像素密度：当前窗口生效的像素密度值，即屏幕物理像素密度[VirtualScreenConfig.density](js-apis-display.md#virtualscreenconfig16)。

> **说明：**
>
> getUIContext需在[windowStage.loadContent](./js-apis-window.md#loadcontent9)之后调用，确保UIContext初始化完成后调用此接口，否则无法返回准确结果。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型   | 必填 | 说明                                   |
| ------ | ------ | ---- | -------------------------------------- |
| value | number | 是   | 将vp单位的数值转换为以px为单位的数值。<br/>取值范围：(-∞, +∞) |

**返回值：**

| 类型   | 说明           |
| ------ | -------------- |
| number | 转换后的数值。<br/>取值范围：(-∞, +∞) |

**示例：**

```ts
@Entry
@Component
struct MatrixExample {
  build() {
    Column({ space: 100 }) {
      Text('Hello1')
        .textAlign(TextAlign.Center)
        .width(100)
        .height(60)
        .backgroundColor(0xAFEEEE)
        .borderWidth(1)
        .rotate({
          z: 1,
          angle: 90,
          centerX: this.getUIContext().vp2px(50),
          centerY: this.getUIContext().vp2px(30)
        })
    }.width('100%')
    .height('100%')
  }
}
```

### px2vp<sup>12+</sup>

px2vp(value : number) : number

将px单位的数值转换为以vp为单位的数值。

转换公式为：vp值 = px值 ÷ 像素密度

像素密度：当前窗口生效的像素密度值，即屏幕物理像素密度[VirtualScreenConfig.density](js-apis-display.md#virtualscreenconfig16)。

> **说明：**
>
> getUIContext需在[windowStage.loadContent](./js-apis-window.md#loadcontent9)之后调用，确保UIContext初始化完成后调用此接口，否则无法返回准确结果。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型   | 必填 | 说明                                   |
| ------ | ------ | ---- | -------------------------------------- |
| value | number | 是   | 将px单位的数值转换为以vp为单位的数值。<br/>取值范围：(-∞, +∞) |

**返回值：**

| 类型   | 说明           |
| ------ | -------------- |
| number | 转换后的数值。<br/>取值范围：(-∞, +∞) |

**示例：**

```ts
@Entry
@Component
struct MatrixExample {
  build() {
    Column({ space: 100 }) {
      Text('Hello1')
        .textAlign(TextAlign.Center)
        .width(100)
        .height(60)
        .backgroundColor(0xAFEEEE)
        .borderWidth(1)
        .rotate({
          z: 1,
          angle: 90,
          centerX: this.getUIContext().px2vp(50),
          centerY: this.getUIContext().px2vp(30)
        })
    }.width('100%')
    .height('100%')
  }
}
```

### fp2px<sup>12+</sup>

fp2px(value : number) : number

将fp单位的数值转换为以px为单位的数值。

转换公式为：px值 = fp值 × 像素密度 × 字体缩放比例

像素密度：当前窗口生效的像素密度值，即屏幕物理像素密度[VirtualScreenConfig.density](js-apis-display.md#virtualscreenconfig16)。

字体缩放比例：系统设置的字体缩放系数，对应 [Configuration.fontScale](arkui-ts/ts-types.md#configuration)。

> **说明：**
>
> getUIContext需在[windowStage.loadContent](./js-apis-window.md#loadcontent9)之后调用，确保UIContext初始化完成后调用此接口，否则无法返回准确结果。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型   | 必填 | 说明                                   |
| ------ | ------ | ---- | -------------------------------------- |
| value | number | 是   | 将fp单位的数值转换为以px为单位的数值。<br/>取值范围：(-∞, +∞) |

**返回值：**

| 类型   | 说明           |
| ------ | -------------- |
| number | 转换后的数值。<br/>取值范围：(-∞, +∞) |

**示例：**

```ts
@Entry
@Component
struct MatrixExample {
  build() {
    Column({ space: 100 }) {
      Text('Hello1')
        .textAlign(TextAlign.Center)
        .width(100)
        .height(60)
        .backgroundColor(0xAFEEEE)
        .borderWidth(1)
        .rotate({
          z: 1,
          angle: 90,
          centerX: this.getUIContext().fp2px(50),
          centerY: this.getUIContext().fp2px(30)
        })
    }.width('100%')
    .height('100%')
  }
}
```

### px2fp<sup>12+</sup>

px2fp(value : number) : number

将px单位的数值转换为以fp为单位的数值。

转换公式为：fp值 = px值 ÷ 像素密度 ÷ 字体缩放比例

像素密度：当前窗口生效的像素密度值，通常就是屏幕物理像素密度[VirtualScreenConfig.density](js-apis-display.md#virtualscreenconfig16)。

字体缩放比例：系统设置的字体缩放系数，对应 [Configuration.fontScale](arkui-ts/ts-types.md#configuration)。

> **说明：**
>
> getUIContext需在[windowStage.loadContent](./js-apis-window.md#loadcontent9)之后调用，确保UIContext初始化完成后调用此接口，否则无法返回准确结果。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型   | 必填 | 说明                                   |
| ------ | ------ | ---- | -------------------------------------- |
| value | number | 是   | 将px单位的数值转换为以fp为单位的数值。<br/>取值范围：(-∞, +∞) |

**返回值：**

| 类型   | 说明           |
| ------ | -------------- |
| number | 转换后的数值。<br/>取值范围：(-∞, +∞) |

**示例：**

```ts
@Entry
@Component
struct MatrixExample {
  build() {
    Column({ space: 100 }) {
      Text('Hello1')
        .textAlign(TextAlign.Center)
        .width(100)
        .height(60)
        .backgroundColor(0xAFEEEE)
        .borderWidth(1)
        .rotate({
          z: 1,
          angle: 90,
          centerX: this.getUIContext().px2fp(50),
          centerY: this.getUIContext().px2fp(30)
        })
    }.width('100%')
    .height('100%')
  }
}
```

### lpx2px<sup>12+</sup>

lpx2px(value : number) : number

将lpx单位的数值转换为以px为单位的数值。

转换公式为：px值 = lpx值 × 实际屏幕宽度与逻辑宽度（通过[designWidth](../../quick-start/module-configuration-file.md#pages标签)配置）的比值。

> **说明：**
>
> getUIContext需在[windowStage.loadContent](./js-apis-window.md#loadcontent9)之后调用，确保UIContext初始化完成后调用此接口，否则无法返回准确结果。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型   | 必填 | 说明                                    |
| ------ | ------ | ---- | --------------------------------------- |
| value | number | 是   | 将lpx单位的数值转换为以px为单位的数值。<br/>取值范围：(-∞, +∞) |

**返回值：**

| 类型   | 说明           |
| ------ | -------------- |
| number | 转换后的数值。<br/>取值范围：(-∞, +∞) |

**示例：**

```ts
@Entry
@Component
struct MatrixExample {
  build() {
    Column({ space: 100 }) {
      Text('Hello1')
        .textAlign(TextAlign.Center)
        .width(100)
        .height(60)
        .backgroundColor(0xAFEEEE)
        .borderWidth(1)
        .rotate({
          z: 1,
          angle: 90,
          centerX: this.getUIContext().lpx2px(50),
          centerY: this.getUIContext().lpx2px(30)
        })
    }.width('100%')
    .height('100%')
  }
}
```

### px2lpx<sup>12+</sup>

px2lpx(value : number) : number

将px单位的数值转换为以lpx为单位的数值。

转换公式为：lpx值 = px值 ÷ 实际屏幕宽度与逻辑宽度（通过[designWidth](../../quick-start/module-configuration-file.md#pages标签)配置）的比值。

> **说明：**
>
> getUIContext需在[windowStage.loadContent](./js-apis-window.md#loadcontent9)之后调用，确保UIContext初始化完成后调用此接口，否则无法返回准确结果。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型   | 必填 | 说明                                    |
| ------ | ------ | ---- | --------------------------------------- |
| value | number | 是   | 将px单位的数值转换为以lpx为单位的数值。<br/>取值范围：(-∞, +∞) |

**返回值：**

| 类型   | 说明           |
| ------ | -------------- |
| number | 转换后的数值。<br/>取值范围：(-∞, +∞) |

**示例：**

```ts
@Entry
@Component
struct MatrixExample {
  build() {
    Column({ space: 100 }) {
      Text('Hello1')
        .textAlign(TextAlign.Center)
        .width(100)
        .height(60)
        .backgroundColor(0xAFEEEE)
        .borderWidth(1)
        .rotate({
          z: 1,
          angle: 90,
          centerX: this.getUIContext().px2lpx(50),
          centerY: this.getUIContext().px2lpx(30)
        })
    }.width('100%')
    .height('100%')
  }
}
```

### getWindowName<sup>12+</sup>

getWindowName(): string | undefined

获取当前实例所在窗口的名称。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：**  SystemCapability.ArkUI.ArkUI.Full

**返回值：** 

| 类型   | 说明                                         |
| ------ | -------------------------------------------- |
| string \| undefined | 当前实例所在窗口的名称。若窗口不存在，则返回undefined。 |

**示例：**

```ts
import { window } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

  aboutToAppear() {
    const windowName = this.getUIContext().getWindowName();
    console.info('WindowName ' + windowName);
    const currWindow = window.findWindow(windowName);
    const windowProperties = currWindow.getWindowProperties();
    console.info(`Window width ${windowProperties.windowRect.width}, height ${windowProperties.windowRect.height}`);
  }

  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### getWindowWidthBreakpoint<sup>13+</sup>

getWindowWidthBreakpoint(): WidthBreakpoint

获取当前实例所在窗口的宽度断点枚举值。具体枚举值根据窗口宽度vp值确定，详见 [WidthBreakpoint](./arkui-ts/ts-appendix-enums.md#widthbreakpoint13)。

**原子化服务API：** 从API version 13开始，该接口支持在原子化服务中使用。

**系统能力：**  SystemCapability.ArkUI.ArkUI.Full

**返回值：** 

| 类型   | 说明                                         |
| ------ | -------------------------------------------- |
| [WidthBreakpoint](./arkui-ts/ts-appendix-enums.md#widthbreakpoint13) | 当前实例所在窗口的宽度断点枚举值。若窗口宽度为 0vp，则返回WIDTH_XS。 |

**示例：**

```ts
import { UIContext } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(30)
          .fontWeight(FontWeight.Bold)
        Button() {
          Text('test')
            .fontSize(30)
        }
        .onClick(() => {
          let uiContext: UIContext = this.getUIContext();
          let widthBp: WidthBreakpoint = uiContext.getWindowWidthBreakpoint();
          console.info(`Window widthBp: ${widthBp}`);
        })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### getWindowHeightBreakpoint<sup>13+</sup>

getWindowHeightBreakpoint(): HeightBreakpoint

获取当前实例所在窗口的高度断点。具体枚举值根据窗口高宽比确定，详见 [HeightBreakpoint](./arkui-ts/ts-appendix-enums.md#heightbreakpoint13)。

**原子化服务API：** 从API version 13开始，该接口支持在原子化服务中使用。

**系统能力：**  SystemCapability.ArkUI.ArkUI.Full

**返回值：** 

| 类型   | 说明                                         |
| ------ | -------------------------------------------- |
| [HeightBreakpoint](./arkui-ts/ts-appendix-enums.md#heightbreakpoint13) | 当前实例所在窗口的宽高比对应的高度断点枚举值。若窗口高宽比为0，则返回HEIGHT_SM。 |

**示例：**

```ts
import { UIContext } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(30)
          .fontWeight(FontWeight.Bold)
        Button() {
          Text('test')
            .fontSize(30)
        }
        .onClick(() => {
          let uiContext: UIContext = this.getUIContext();
          let heightBp: HeightBreakpoint = uiContext.getWindowHeightBreakpoint();
          console.info(`Window heightBP: ${heightBp}`);
        })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### postFrameCallback<sup>12+</sup>

postFrameCallback(frameCallback: FrameCallback): void

注册一个回调，仅在下一帧渲染时调用。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型   | 必填 | 说明                                    |
| ------ | ------ | ---- | --------------------------------------- |
| frameCallback | [FrameCallback](#framecallback12) | 是   | 下一帧需要执行的回调。 |

**示例：**

```ts
import {FrameCallback } from '@kit.ArkUI';

class MyFrameCallback extends FrameCallback {
  private tag: string;

  constructor(tag: string) {
    super();
    this.tag = tag;
  }

  onFrame(frameTimeNanos: number) {
    console.info('MyFrameCallback ' + this.tag + ' ' + frameTimeNanos.toString());
  }
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Button('点击触发postFrameCallback')
        .onClick(() => {
          this.getUIContext().postFrameCallback(new MyFrameCallback("normTask"));
        })
    }
  }
}
```

### postDelayedFrameCallback<sup>12+</sup>

postDelayedFrameCallback(frameCallback: FrameCallback, delayTime: number): void

注册一个回调，在延迟一段时间后的下一帧进行渲染时执行。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型   | 必填 | 说明                                    |
| ------ | ------ | ---- | --------------------------------------- |
| frameCallback | [FrameCallback](#framecallback12) | 是   | 下一帧需要执行的回调。 |
| delayTime | number | 是   | 延迟的时间，以毫秒为单位。传入null、undefined或小于0的值，会按0处理。 |

**示例：**

```ts
import {FrameCallback } from '@kit.ArkUI';

class MyFrameCallback extends FrameCallback {
  private tag: string;

  constructor(tag: string) {
    super();
    this.tag = tag;
  }

  onFrame(frameTimeNanos: number) {
    console.info('MyFrameCallback ' + this.tag + ' ' + frameTimeNanos.toString());
  }
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Button('点击触发postDelayedFrameCallback')
        .onClick(() => {
          this.getUIContext().postDelayedFrameCallback(new MyFrameCallback("delayTask"), 5);
        })
    }
  }
}
```

### requireDynamicSyncScene<sup>12+</sup>

requireDynamicSyncScene(id: string): Array&lt;DynamicSyncScene&gt;

请求组件的动态帧率场景，用于自定义场景相关帧率配置。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型   | 必填 | 说明                                    |
| ------ | ------ | ---- | --------------------------------------- |
| id | string | 是    | 节点对应的[组件标识](arkui-ts/ts-universal-attributes-component-id.md)。|

**返回值：** 

| 类型   | 说明                                         |
| ------ | -------------------------------------------- |
| Array&lt;DynamicSyncScene&gt; | 获取DynamicSyncScene对象数组。 |

**示例：**

```ts
import { SwiperDynamicSyncSceneType, SwiperDynamicSyncScene } from '@kit.ArkUI';

@Entry
@Component
struct Frame {
  @State ANIMATION: ExpectedFrameRateRange = { min: 0, max: 120, expected: 90 };
  @State GESTURE: ExpectedFrameRateRange = { min: 0, max: 120, expected: 30};
  private scenes: SwiperDynamicSyncScene[] = [];

  build() {
    Column() {
      Text("动画"+ JSON.stringify(this.ANIMATION))
      Text("跟手"+ JSON.stringify(this.GESTURE))
      Row(){
        Swiper() {
          Text("one")
          Text("two")
          Text("three")
        }
        .width('100%')
        .height('300vp')
        .id("dynamicSwiper")
        .backgroundColor(Color.Blue)
        .autoPlay(true)
        .onAppear(()=>{
          this.scenes = this.getUIContext().requireDynamicSyncScene("dynamicSwiper") as SwiperDynamicSyncScene[];
        })
      }

      Button("set frame")
        .onClick(() => {
          this.scenes.forEach((scenes: SwiperDynamicSyncScene) => {

            if (scenes.type == SwiperDynamicSyncSceneType.ANIMATION) {
              scenes.setFrameRateRange(this.ANIMATION);
            }

            if (scenes.type == SwiperDynamicSyncSceneType.GESTURE) {
              scenes.setFrameRateRange(this.GESTURE);
            }
          });
        })
    }
  }
}
```

### openBindSheet<sup>12+</sup>

openBindSheet\<T extends Object>(bindSheetContent: ComponentContent\<T>, sheetOptions?: SheetOptions, targetId?: number): Promise&lt;void&gt;

创建并弹出以bindSheetContent作为内容的半模态页面，使用Promise异步回调。通过该接口弹出的半模态页面样式完全按照bindSheetContent中设置的样式显示。

> **说明：**
>
> 1. 使用该接口时，若未传入有效的targetId，则不支持设置SheetOptions.preferType为POPUP模式、不支持设置SheetOptions.mode为EMBEDDED模式。
>
> 2. 由于[updateBindSheet](#updatebindsheet12)和[closeBindSheet](#closebindsheet12)依赖bindSheetContent去更新或者关闭指定的半模态页面，开发者需自行维护传入的bindSheetContent。
>
> 3. 不支持设置SheetOptions.UIContext。
>

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名     | 类型                                       | 必填   | 说明      |
| ------- | ---------------------------------------- | ---- | ------- |
| bindSheetContent | [ComponentContent\<T>](./js-apis-arkui-ComponentContent.md) | 是 | 半模态页面中显示的组件内容。 |
| sheetOptions | [SheetOptions](arkui-ts/ts-universal-attributes-sheet-transition.md#sheetoptions) | 否    |   半模态页面样式。<br/>**说明：** <br/>1. 不支持设置SheetOptions.uiContext，该属性的值固定为当前实例的UIContext。<br/>2. 若不传递targetId，则不支持设置SheetOptions.preferType为POPUP样式，若设置了POPUP样式则使用CENTER样式替代。<br/>3. 若不传递targetId，则不支持设置SheetOptions.mode为EMBEDDED模式，默认为OVERLAY模式。<br/>4. 其余属性的默认值参考[SheetOptions](arkui-ts/ts-universal-attributes-sheet-transition.md#sheetoptions)文档。 |
| targetId | number | 否    |   需要绑定组件的ID，若不指定则不绑定任何组件。 |

**返回值：**

| 类型                                       | 说明      |
| ---------------------------------------- | ------- |
|   Promise&lt;void&gt;           |    返回Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[半模态错误码](errorcode-bindSheet.md)错误码。

| 错误码ID  | 错误信息                               |
| ------ | ---------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 120001 | The bindSheetContent is incorrect. |
| 120002 | The bindSheetContent already exists. |
| 120004 | The targetId does not exist. |
| 120005 | The node of targetId is not in the component tree. |
| 120006 | The node of targetId is not a child of the page node or NavDestination node. |

**示例：**

```ts
import { FrameNode, ComponentContent } from "@kit.ArkUI";
import { BusinessError } from '@kit.BasicServicesKit';

class Params {
  text: string = "";

  constructor(text: string) {
    this.text = text;
  }
}

let contentNode: ComponentContent<Params>;
let gUIContext: UIContext;

@Builder
function buildText(params: Params) {
  Column() {
    Text(params.text)
    Button('Update BindSheet')
      .fontSize(20)
      .onClick(() => {
        gUIContext.updateBindSheet(contentNode, {
          backgroundColor: Color.Pink,
        }, true)
          .then(() => {
            console.info('updateBindSheet success');
          })
          .catch((err: BusinessError) => {
            console.info('updateBindSheet error: ' + err.code + ' ' + err.message);
          })
      })

    Button('Close BindSheet')
      .fontSize(20)
      .onClick(() => {
        gUIContext.closeBindSheet(contentNode)
          .then(() => {
            console.info('closeBindSheet success');
          })
          .catch((err: BusinessError) => {
            console.info('closeBindSheet error: ' + err.code + ' ' + err.message);
          })
      })
  }
}

@Entry
@Component
struct UIContextBindSheet {
  @State message: string = 'BindSheet';

  aboutToAppear() {
    gUIContext = this.getUIContext();
    contentNode = new ComponentContent(this.getUIContext(), wrapBuilder(buildText), new Params(this.message));
  }

  build() {
    RelativeContainer() {
      Column() {
        Button('Open BindSheet')
          .fontSize(20)
          .onClick(() => {
            let uiContext = this.getUIContext();
            let uniqueId = this.getUniqueId();
            let frameNode: FrameNode | null = uiContext.getFrameNodeByUniqueId(uniqueId);
            let targetId = frameNode?.getFirstChild()?.getUniqueId();
            uiContext.openBindSheet(contentNode, {
              height: SheetSize.MEDIUM,
              backgroundColor: Color.Green,
              title: { title: "Title", subtitle: "subtitle" }
            }, targetId)
              .then(() => {
                console.info('openBindSheet success');
              })
              .catch((err: BusinessError) => {
                console.info('openBindSheet error: ' + err.code + ' ' + err.message);
              })
          })
      }
    }
    .height('100%')
    .width('100%')
  }
}
```

### updateBindSheet<sup>12+</sup>

updateBindSheet\<T extends Object>(bindSheetContent: ComponentContent\<T>, sheetOptions: SheetOptions, partialUpdate?: boolean ): Promise&lt;void&gt;

更新bindSheetContent对应的半模态页面的样式，使用Promise异步回调。

> **说明：**
>
> 不支持更新SheetOptions.UIContext、SheetOptions.mode、回调函数。
>

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名     | 类型                                       | 必填   | 说明      |
| ------- | ---------------------------------------- | ---- | ------- |
| bindSheetContent | [ComponentContent\<T>](./js-apis-arkui-ComponentContent.md) | 是 | 半模态页面中显示的组件内容。 |
| sheetOptions | [SheetOptions](arkui-ts/ts-universal-attributes-sheet-transition.md#sheetoptions) | 是    |   半模态页面样式。<br/>**说明：** <br/>不支持更新SheetOptions.uiContext、SheetOptions.mode、回调函数。 |
| partialUpdate | boolean | 否    |   半模态页面更新方式, 默认值为false。<br/>**说明：** <br/>1. true为增量更新，保留当前值，更新SheetOptions中的指定属性。 <br/>2. false为全量更新，除SheetOptions中的指定属性，其他属性恢复默认值。 |

**返回值：**

| 类型                                       | 说明      |
| ---------------------------------------- | ------- |
|   Promise&lt;void&gt;           |    返回Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[半模态错误码](errorcode-bindSheet.md)错误码。

| 错误码ID  | 错误信息                               |
| ------ | ---------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 120001 | The bindSheetContent is incorrect. |
| 120003 | The bindSheetContent cannot be found. |

**示例：**

```ts
import { FrameNode, ComponentContent } from "@kit.ArkUI";
import { BusinessError } from '@kit.BasicServicesKit';

class Params {
  text: string = "";

  constructor(text: string) {
    this.text = text;
  }
}

let contentNode: ComponentContent<Params>;
let gUIContext: UIContext;

@Builder
function buildText(params: Params) {
  Column() {
    Text(params.text)
    Button('Update BindSheet')
      .fontSize(20)
      .onClick(() => {
        gUIContext.updateBindSheet(contentNode, {
          backgroundColor: Color.Pink,
        }, true)
          .then(() => {
            console.info('updateBindSheet success');
          })
          .catch((err: BusinessError) => {
            console.info('updateBindSheet error: ' + err.code + ' ' + err.message);
          })
      })

    Button('Close BindSheet')
      .fontSize(20)
      .onClick(() => {
        gUIContext.closeBindSheet(contentNode)
          .then(() => {
            console.info('closeBindSheet success');
          })
          .catch((err: BusinessError) => {
            console.info('closeBindSheet error: ' + err.code + ' ' + err.message);
          })
      })
  }
}

@Entry
@Component
struct UIContextBindSheet {
  @State message: string = 'BindSheet';

  aboutToAppear() {
    gUIContext = this.getUIContext();
    contentNode = new ComponentContent(this.getUIContext(), wrapBuilder(buildText), new Params(this.message));
  }

  build() {
    RelativeContainer() {
      Column() {
        Button('Open BindSheet')
          .fontSize(20)
          .onClick(() => {
            let uiContext = this.getUIContext();
            let uniqueId = this.getUniqueId();
            let frameNode: FrameNode | null = uiContext.getFrameNodeByUniqueId(uniqueId);
            let targetId = frameNode?.getFirstChild()?.getUniqueId();
            uiContext.openBindSheet(contentNode, {
              height: SheetSize.MEDIUM,
              backgroundColor: Color.Green,
              title: { title: "Title", subtitle: "subtitle" }
            }, targetId)
              .then(() => {
                console.info('openBindSheet success');
              })
              .catch((err: BusinessError) => {
                console.info('openBindSheet error: ' + err.code + ' ' + err.message);
              })
          })
      }
    }
    .height('100%')
    .width('100%')
  }
}
```

### closeBindSheet<sup>12+</sup>

closeBindSheet\<T extends Object>(bindSheetContent: ComponentContent\<T>): Promise&lt;void&gt;

关闭bindSheetContent对应的半模态页面，使用Promise异步回调。

> **说明：**
>
> 使用此接口关闭半模态页面时，不会触发shouldDismiss回调。
>

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名     | 类型                                       | 必填   | 说明      |
| ------- | ---------------------------------------- | ---- | ------- |
| bindSheetContent | [ComponentContent\<T>](./js-apis-arkui-ComponentContent.md) | 是 | 半模态页面中显示的组件内容。 |

**返回值：**

| 类型                                       | 说明      |
| ---------------------------------------- | ------- |
|   Promise&lt;void&gt;           |    返回Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[半模态错误码](errorcode-bindSheet.md)错误码。

| 错误码ID  | 错误信息                               |
| ------ | ---------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 120001 | The bindSheetContent is incorrect. |
| 120003 | The bindSheetContent cannot be found. |

**示例：**

```ts
import { FrameNode, ComponentContent } from "@kit.ArkUI";
import { BusinessError } from '@kit.BasicServicesKit';

class Params {
  text: string = "";

  constructor(text: string) {
    this.text = text;
  }
}

let contentNode: ComponentContent<Params>;
let gUIContext: UIContext;

@Builder
function buildText(params: Params) {
  Column() {
    Text(params.text)
    Button('Update BindSheet')
      .fontSize(20)
      .onClick(() => {
        gUIContext.updateBindSheet(contentNode, {
          backgroundColor: Color.Pink,
        }, true)
          .then(() => {
            console.info('updateBindSheet success');
          })
          .catch((err: BusinessError) => {
            console.info('updateBindSheet error: ' + err.code + ' ' + err.message);
          })
      })

    Button('Close BindSheet')
      .fontSize(20)
      .onClick(() => {
        gUIContext.closeBindSheet(contentNode)
          .then(() => {
            console.info('closeBindSheet success');
          })
          .catch((err: BusinessError) => {
            console.info('closeBindSheet error: ' + err.code + ' ' + err.message);
          })
      })
  }
}

@Entry
@Component
struct UIContextBindSheet {
  @State message: string = 'BindSheet';

  aboutToAppear() {
    gUIContext = this.getUIContext();
    contentNode = new ComponentContent(this.getUIContext(), wrapBuilder(buildText), new Params(this.message));
  }

  build() {
    RelativeContainer() {
      Column() {
        Button('Open BindSheet')
          .fontSize(20)
          .onClick(() => {
            let uiContext = this.getUIContext();
            let uniqueId = this.getUniqueId();
            let frameNode: FrameNode | null = uiContext.getFrameNodeByUniqueId(uniqueId);
            let targetId = frameNode?.getFirstChild()?.getUniqueId();
            uiContext.openBindSheet(contentNode, {
              height: SheetSize.MEDIUM,
              backgroundColor: Color.Green,
              title: { title: "Title", subtitle: "subtitle" }
            }, targetId)
              .then(() => {
                console.info('openBindSheet success');
              })
              .catch((err: BusinessError) => {
                console.info('openBindSheet error: ' + err.code + ' ' + err.message);
              })
          })
      }
    }
    .height('100%')
    .width('100%')
  }
}
```

### isFollowingSystemFontScale<sup>13+</sup>

isFollowingSystemFontScale(): boolean

获取当前UI上下文是否跟随系统字体倍率。

**原子化服务API：** 从API version 13开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型      | 说明            |
|---------|---------------|
| boolean | 当前UI上下文是否跟随系统字体倍率。<br/> true表示UI上下文跟随系统倍率，false表示UI上下文不跟随系统倍率。 |

**示例：**

<!--code_no_check-->
```ts
uiContext.isFollowingSystemFontScale();
```

### getMaxFontScale<sup>13+</sup>

getMaxFontScale(): number

获取当前UI上下文最大字体倍率。

**原子化服务API：** 从API version 13开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型      | 说明        |
|---------|-----------|
| number | 当前UI上下文最大字体倍率。 |

**示例：**

<!--code_no_check-->
```ts
uiContext.getMaxFontScale();
```

### bindTabsToScrollable<sup>13+</sup>

bindTabsToScrollable(tabsController: TabsController, scroller: Scroller): void

绑定Tabs组件和可滚动容器组件（支持[List](./arkui-ts/ts-container-list.md)、[Scroll](./arkui-ts/ts-container-scroll.md)、[Grid](./arkui-ts/ts-container-grid.md)、[WaterFlow](./arkui-ts/ts-container-waterflow.md)），当滑动可滚动容器组件时，会触发所有与其绑定的Tabs组件的TabBar的显示和隐藏动效，上滑隐藏，下滑显示。一个TabsController可与多个Scroller绑定，一个Scroller也可与多个TabsController绑定。

>  **说明：**
>
>  当多个可滚动容器组件绑定了同一个Tabs组件时，只要滑动任意一个可滚动容器组件，就会触发TabBar的显示或隐藏。且当任意一个可滚动容器组件滑动到底部时，会立即触发TabBar的显示动效。因此不建议同时触发多个可滚动容器组件的滑动。

**原子化服务API：** 从API version 13开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名     | 类型                                       | 必填   | 说明      |
| ------- | ---------------------------------------- | ---- | ------- |
| tabsController | [TabsController](./arkui-ts/ts-container-tabs.md#tabscontroller) | 是 | Tabs组件的控制器。 |
| scroller | [Scroller](./arkui-ts/ts-container-scroll.md#scroller) | 是 | 可滚动容器组件的控制器。 |

**示例：**

```ts
@Entry
@Component
struct TabsExample {
  private arr: string[] = [];
  private parentTabsController: TabsController = new TabsController();
  private childTabsController: TabsController = new TabsController();
  private listScroller: Scroller = new Scroller();
  private parentScroller: Scroller = new Scroller();
  private childScroller: Scroller = new Scroller();

  aboutToAppear(): void {
    for (let i = 0; i < 20; i++) {
      this.arr.push(i.toString());
    }
    let context = this.getUIContext();
    context.bindTabsToScrollable(this.parentTabsController, this.listScroller);
    context.bindTabsToScrollable(this.childTabsController, this.listScroller);
    context.bindTabsToNestedScrollable(this.parentTabsController, this.parentScroller, this.childScroller);
  }

  aboutToDisappear(): void {
    let context = this.getUIContext();
    context.unbindTabsFromScrollable(this.parentTabsController, this.listScroller);
    context.unbindTabsFromScrollable(this.childTabsController, this.listScroller);
    context.unbindTabsFromNestedScrollable(this.parentTabsController, this.parentScroller, this.childScroller);
  }

  build() {
    Tabs({ barPosition: BarPosition.End, controller: this.parentTabsController }) {
      TabContent() {
        Tabs({ controller: this.childTabsController }) {
          TabContent() {
            List({ space: 20, initialIndex: 0, scroller: this.listScroller }) {
              ForEach(this.arr, (item: string) => {
                ListItem() {
                  Text(item)
                    .width('100%')
                    .height(100)
                    .fontSize(16)
                    .textAlign(TextAlign.Center)
                    .borderRadius(10)
                    .backgroundColor(Color.Gray)
                }
              }, (item: string) => item)
            }
            .scrollBar(BarState.Off)
            .width('90%')
            .height('100%')
            .contentStartOffset(56)
            .contentEndOffset(52)
          }.tabBar(SubTabBarStyle.of('顶部页签'))
        }
        .width('100%')
        .height('100%')
        .barOverlap(true) // 使TabBar叠加在TabContent上，当TabBar向上或向下隐藏后，原位置处不为空白
        .clip(true) // 对超出Tabs组件范围的子组件进行裁剪，防止TabBar向上或向下隐藏后误触TabBar
      }.tabBar(BottomTabBarStyle.of($r('app.media.startIcon'), 'scroller联动多个TabsController'))

      TabContent() {
        Scroll(this.parentScroller) {
            List({ space: 20, initialIndex: 0, scroller: this.childScroller }) {
              ForEach(this.arr, (item: string) => {
                ListItem() {
                  Text(item)
                    .width('100%')
                    .height(100)
                    .fontSize(16)
                    .textAlign(TextAlign.Center)
                    .borderRadius(10)
                    .backgroundColor(Color.Gray)
                }
              }, (item: string) => item)
            }
            .scrollBar(BarState.Off)
            .width('90%')
            .height('100%')
            .contentEndOffset(52)
            .nestedScroll({ scrollForward: NestedScrollMode.SELF_FIRST, scrollBackward: NestedScrollMode.SELF_FIRST })
        }
        .width('100%')
        .height('100%')
        .scrollBar(BarState.Off)
        .scrollable(ScrollDirection.Vertical)
        .edgeEffect(EdgeEffect.Spring)
      }.tabBar(BottomTabBarStyle.of($r('app.media.startIcon'), '嵌套的scroller联动TabsController'))
    }
    .width('100%')
    .height('100%')
    .barOverlap(true) // 使TabBar叠加在TabContent上，当TabBar向上或向下隐藏后，原位置处不为空白
    .clip(true) // 对超出Tabs组件范围的子组件进行裁剪，防止TabBar向上或向下隐藏后误触TabBar
  }
}
```

![bindTabsToScrollable](figures/bindTabsToScrollable.gif)

### unbindTabsFromScrollable<sup>13+</sup>

unbindTabsFromScrollable(tabsController: TabsController, scroller: Scroller): void

解除Tabs组件和可滚动容器组件的绑定。

**原子化服务API：** 从API version 13开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名     | 类型                                       | 必填   | 说明      |
| ------- | ---------------------------------------- | ---- | ------- |
| tabsController | [TabsController](./arkui-ts/ts-container-tabs.md#tabscontroller) | 是 | Tabs组件的控制器。 |
| scroller | [Scroller](./arkui-ts/ts-container-scroll.md#scroller) | 是 | 可滚动容器组件的控制器。 |

**示例：**

参考[bindTabsToScrollable](#bindtabstoscrollable13)接口示例。

### bindTabsToNestedScrollable<sup>13+</sup>

bindTabsToNestedScrollable(tabsController: TabsController, parentScroller: Scroller, childScroller: Scroller): void

绑定Tabs组件和嵌套的可滚动容器组件（支持[List](./arkui-ts/ts-container-list.md)、[Scroll](./arkui-ts/ts-container-scroll.md)、[Grid](./arkui-ts/ts-container-grid.md)、[WaterFlow](./arkui-ts/ts-container-waterflow.md)），当滑动父组件或子组件时，会触发所有与其绑定的Tabs组件的TabBar的显示和隐藏动效，上滑隐藏，下滑显示。一个TabsController可与多个嵌套的Scroller绑定，嵌套的Scroller也可与多个TabsController绑定。

**原子化服务API：** 从API version 13开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名     | 类型                                       | 必填   | 说明      |
| ------- | ---------------------------------------- | ---- | ------- |
| tabsController | [TabsController](./arkui-ts/ts-container-tabs.md#tabscontroller) | 是 | Tabs组件的控制器。 |
| parentScroller | [Scroller](./arkui-ts/ts-container-scroll.md#scroller) | 是 | 可滚动容器组件的控制器。 |
| childScroller | [Scroller](./arkui-ts/ts-container-scroll.md#scroller) | 是 | 可滚动容器组件的控制器。其对应组件为parentScroller对应组件的子组件，且组件间存在嵌套滚动关系。 |

**示例：**

参考[bindTabsToScrollable](#bindtabstoscrollable13)接口示例。

### unbindTabsFromNestedScrollable<sup>13+</sup>

unbindTabsFromNestedScrollable(tabsController: TabsController, parentScroller: Scroller, childScroller: Scroller): void

解除Tabs组件和嵌套的可滚动容器组件的绑定。

**原子化服务API：** 从API version 13开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名     | 类型                                       | 必填   | 说明      |
| ------- | ---------------------------------------- | ---- | ------- |
| tabsController | [TabsController](./arkui-ts/ts-container-tabs.md#tabscontroller) | 是 | Tabs组件的控制器。 |
| parentScroller | [Scroller](./arkui-ts/ts-container-scroll.md#scroller) | 是 | 可滚动容器组件的控制器。 |
| childScroller | [Scroller](./arkui-ts/ts-container-scroll.md#scroller) | 是 | 可滚动容器组件的控制器。其对应组件为parentScroller对应组件的子组件，且组件间存在嵌套滚动关系。 |

**示例：**

参考[bindTabsToScrollable](#bindtabstoscrollable13)接口示例。

### enableSwipeBack<sup>18+</sup>

enableSwipeBack(enabled: Optional\<boolean\>): void

设置是否支持应用内横向滑动返回上一级。

**原子化服务API:** 从API version 18 开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名     | 类型    | 必填   | 说明      |
| --- | --- | --- | --- |
| enabled | Optional\<boolean> | 是 | 是否支持应用内横向滑动返回，默认值为true。<br>当值为true时，支持应用内横向滑动返回。<br>当值为false时，不支持应用内横向滑动返回。|

**示例：**

```js
@Entry
@Component
struct Index {
  @State isEnable: boolean = true;

  build() {
    RelativeContainer() {
      Button(`enable swipe back: ${this.isEnable}`).onClick(() => {
        this.isEnable = !this.isEnable;
        this.getUIContext().enableSwipeBack(this.isEnable);
      })
    }
    .height('100%')
    .width('100%')
  }
}
```

### getTextMenuController<sup>16+</sup>

getTextMenuController(): TextMenuController

获取[TextMenuController](#textmenucontroller16)对象，可通过该对象控制文本选择菜单。

**原子化服务API:** 从API version 16 开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

|类型|说明|
|----|----|
|[TextMenuController](#textmenucontroller16)| 获取TextMenuController对象。|

**示例：**

参考[TextMenuController](#textmenucontroller16)接口示例。

### createUIContextWithoutWindow<sup>17+</sup>

static createUIContextWithoutWindow(context: common.UIAbilityContext | common.ExtensionContext) : UIContext | undefined

创建一个不依赖窗口的UI实例，并返回其UI上下文。该接口所创建的UI实例是单例。

> **说明：**
>
> 返回的UI上下文只可用于创建[自定义节点](../../ui/arkts-user-defined-node.md)，不能执行其他UI操作。

**原子化服务API:** 从API version 17 开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名  | 类型                                     | 必填 | 说明        |
| ------- | ---------------------------------------- | ---- | ----------- |
| context | common.[UIAbilityContext](../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md) \| common.[ExtensionContext](../apis-ability-kit/js-apis-inner-application-extensionContext.md) | 是    | [UIAbility](../apis-ability-kit/js-apis-app-ability-uiAbility.md)或[ExtensionAbility](../apis-ability-kit/js-apis-app-ability-extensionAbility.md)所对应的上下文环境。 |

**返回值：**

|类型|说明|
|----|----|
| UIContext \| undefined | 创建的UI实例的上下文，创建失败时返回undefined。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[UI上下文](errorcode-uicontext.md)错误码。

| 错误码ID  | 错误信息                        |
| ------ | ---------------------------------- |
| 401    | Parameter error. Possible causes: <br> 1. The number of parameters is incorrect.<br> 2. Invalid parameter type of context. |
| 100001 | Internal error. |


**示例：**

```ts
// EntryAbility.ets
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { UIContext } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onCreate');
    let uiContext : UIContext | undefined = UIContext.createUIContextWithoutWindow(this.context);
  }

  // ......
}
```

### destroyUIContextWithoutWindow<sup>17+</sup>

static destroyUIContextWithoutWindow(): void

销毁[createUIContextWithoutWindow](#createuicontextwithoutwindow17)创建的UI实例。

**原子化服务API:** 从API version 17 开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

```ts
// EntryAbility.ets
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { UIContext } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onCreate');
    let uiContext : UIContext | undefined = UIContext.createUIContextWithoutWindow(this.context);
    UIContext.destroyUIContextWithoutWindow();
  }

  // ......
}
```

### dispatchKeyEvent<sup>15+</sup>

dispatchKeyEvent(node: number | string, event: KeyEvent): boolean

按键事件应分发给指定的组件。为了确保行为的可预测性，目标组件必须位于分发组件的子树中。

**原子化服务API：** 从API version 15开始，该接口支持在原子化服务中使用。

**系统能力：**  SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型                          | 必填 | 说明               |
| ------ | ----------------------------- | ---- | ------------------ |
| node  | number \| string | 是   | 组件的id或者节点UniqueID。 |
| event  |[KeyEvent](./arkui-ts/ts-universal-events-key.md#keyevent对象说明) | 是   | KeyEvent对象。 |

**返回值：**

| 类型      | 说明            |
|---------|---------------|
| boolean | 按键事件是否成功分发给指定的组件。<br/> true表示分发成功，false表示分发失败。 |

**示例：**

```ts
@Entry
@Component
struct Index {
  build() {
    Row() {
      Row() {
        Button('Button1').id('Button1').onKeyEvent((event) => {
          console.log("Button1");
          return true;
        })
        Button('Button2').id('Button2').onKeyEvent((event) => {
          console.log("Button2");
          return true;
        })
      }
      .width('100%')
      .height('100%')
      .id('Row1')
      .onKeyEventDispatch((event) => {
        let context = this.getUIContext();
        context.getFocusController().requestFocus('Button1');
        return context.dispatchKeyEvent('Button1', event);
      })

    }
    .height('100%')
    .width('100%')
    .onKeyEventDispatch((event) => {
      if (event.type == KeyType.Down) {
        let context = this.getUIContext();
        context.getFocusController().requestFocus('Row1');
        return context.dispatchKeyEvent('Row1', event);
      }
      return true;
    })
  }
}
```
### setPixelRoundMode<sup>18+</sup>

setPixelRoundMode(mode: PixelRoundMode): void

配置当前页面的像素取整模式。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：**  SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名      | 类型         | 必填   | 说明   |
| -------- | ---------- | ---- | ---- |
| mode | [PixelRoundMode](./arkui-ts/ts-appendix-enums.md#pixelroundmode18)| 是    | 像素取整模式。<br />默认值：PixelRoundMode.PIXEL_ROUND_ON_LAYOUT_FINISH |

**示例：**

```ts
// EntryAbility.ets
import { UIContext } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

onWindowStageCreate(windowStage: window.WindowStage) {
    // Main window is created, set main page for this ability
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onWindowStageCreate');

    windowStage.loadContent('pages/Index', (err, data) => {
      let uiContext :UIContext = windowStage.getMainWindowSync().getUIContext();
      uiContext.setPixelRoundMode(PixelRoundMode.PIXEL_ROUND_ON_LAYOUT_FINISH);
      if (err.code) {
        hilog.error(0x0000, 'testTag', 'Failed to load the content. Cause: %{public}s', JSON.stringify(err) ?? '');
        return;
      }
      hilog.info(0x0000, 'testTag', 'Succeeded in loading the content. Data: %{public}s', JSON.stringify(data) ?? '');
    });
  }
```

### getPixelRoundMode<sup>18+</sup>

getPixelRoundMode(): PixelRoundMode

获取当前页面的像素取整模式。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：**  SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型         | 说明   |
| ---------- | ---- |
| [PixelRoundMode](./arkui-ts/ts-appendix-enums.md#pixelroundmode18)| 当前页面的像素取整模式。|

**示例：**

```ts
// EntryAbility.ets
import { UIContext } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

onWindowStageCreate(windowStage: window.WindowStage) {
    // Main window is created, set main page for this ability
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onWindowStageCreate');

    windowStage.loadContent('pages/Index', (err, data) => {
      let uiContext: UIContext = windowStage.getMainWindowSync().getUIContext();
      console.info("pixelRoundMode : " + uiContext.getPixelRoundMode().valueOf());
      if (err.code) {
        hilog.error(0x0000, 'testTag', 'Failed to load the content. Cause: %{public}s', JSON.stringify(err) ?? '');
        return;
      }
      hilog.info(0x0000, 'testTag', 'Succeeded in loading the content. Data: %{public}s', JSON.stringify(data) ?? '');
    });
  }
```
## Font

以下API需先使用UIContext中的[getFont()](#getfont)方法获取到Font对象，再通过该对象调用对应方法。

### registerFont

registerFont(options: font.FontOptions): void

在字体管理中注册自定义字体。

该接口为异步接口，不支持并发调用。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名     | 类型                                       | 必填   | 说明          |
| ------- | ---------------------------------------- | ---- | ----------- |
| options | [font.FontOptions](js-apis-font.md#fontoptions) | 是    | 注册的自定义字体信息。<br/>**说明：**<br/>推荐使用字体引擎的[loadFontSync](../apis-arkgraphics2d/js-apis-graphics-text.md#loadfontsync)接口注册自定义字体。<br/>设置注册字体文件的路径，读取系统沙箱路径内的资源时，建议使用file://路径前缀的字符串，需要确保沙箱目录路径下的文件存在并且有可读权限。 |

**示例：**

<!--code_no_check-->
```ts
// xxx.ets
import { Font } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';
  private uiContext: UIContext = this.getUIContext();
  private font: Font = this.uiContext.getFont();

  aboutToAppear() {
    this.font.registerFont({
      familyName: 'medium',
      familySrc: '/font/medium.ttf' // font文件夹与pages目录同级
    })
  }

  build() {
    Column() {
      Text(this.message)
        .align(Alignment.Center)
        .fontSize(20)
        .fontFamily('medium') // medium：注册自定义字体的名字（$r('app.string.mediumFamilyName')、'mediumRawFile'等已注册字体也能正常使用）
    }.width('100%')
  }
}
```
### getSystemFontList

getSystemFontList(): Array\<string> 

获取系统支持的字体名称列表。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型             | 说明        |
| -------------- | --------- |
| Array\<string> | 系统的字体名列表。 |

>  **说明：**
>
>  该接口仅在2in1设备上生效。

**示例：** 

<!--code_no_check-->
```ts
// xxx.ets
import { Font } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  private uiContext: UIContext = this.getUIContext();
  private font: Font = this.uiContext.getFont();
  fontList: Array<string> = new Array<string>();

  build() {
    Column() {
      Button("getSystemFontList")
        .width('60%')
        .height('6%')
        .onClick(() => {
          this.fontList = this.font.getSystemFontList();
          console.log('getSystemFontList', JSON.stringify(this.fontList))
        })
    }.width('100%')
  }
}
```

### getFontByName

getFontByName(fontName: string): font.FontInfo

根据传入的系统字体名称获取系统字体的相关信息。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名      | 类型     | 必填   | 说明      |
| -------- | ------ | ---- | ------- |
| fontName | string | 是    | 系统的字体名。 |

**返回值：** 

| 类型                                      | 说明           |
| ----------------------------------------- | -------------- |
| [font.FontInfo](js-apis-font.md#fontinfo10) | 字体的详细信息。 |

**示例：** 

<!--code_no_check-->
```ts
// xxx.ets
import { Font, font } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  private uiContext: UIContext = this.getUIContext();
  private font: Font = this.uiContext.getFont();
  fontInfo: font.FontInfo = this.font.getFontByName('')

  build() {
    Column() {
      Button("getFontByName")
        .width('60%')
        .height('6%')
        .onClick(() => {
          this.fontInfo = this.font.getFontByName('HarmonyOS Sans Italic');
          console.info("getFontByName(): path = " + this.fontInfo.path);
          console.info("getFontByName(): postScriptName = " + this.fontInfo.postScriptName);
          console.info("getFontByName(): fullName = " + this.fontInfo.fullName);
          console.info("getFontByName(): Family = " + this.fontInfo.family);
          console.info("getFontByName(): Subfamily = " + this.fontInfo.subfamily);
          console.info("getFontByName(): weight = " + this.fontInfo.weight);
          console.info("getFontByName(): width = " + this.fontInfo.width);
          console.info("getFontByName(): italic = " + this.fontInfo.italic);
          console.info("getFontByName(): monoSpace = " + this.fontInfo.monoSpace);
          console.info("getFontByName(): symbolic = " + this.fontInfo.symbolic);
        })
    }.width('100%')
  }
}
```

## Context<sup>12+</sup>

type Context = common.Context

当前组件所在Ability的上下文。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**模型约束：** 此接口仅可在Stage模型下使用。

| 类型 |说明   |
| ------ | ------------------- |
| [common.Context](../apis-ability-kit/js-apis-app-ability-common.md#context) |Context的具体类型为当前Ability关联的Context对象。|

## ComponentUtils

以下API需先使用UIContext中的[getComponentUtils()](#getcomponentutils)方法获取到ComponentUtils对象，再通过该对象调用对应方法。

### getRectangleById

getRectangleById(id: string): componentUtils.ComponentInfo

获取组件大小、位置、平移、缩放、旋转及仿射矩阵属性信息。

> **说明：**
>
> 该接口需要在目标组件布局、完成以后获取目标组件区域大小信息，建议在[onAppear](./arkui-ts/ts-universal-events-show-hide.md#onappear)中使用该接口。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名  | 类型     | 必填   | 说明        |
| ---- | ------ | ---- | --------- |
| id   | string | 是    | 组件唯一标识id。 |

**返回值：**

| 类型                                                         | 说明                                             |
| ------------------------------------------------------------ | ------------------------------------------------ |
| [componentUtils.ComponentInfo](js-apis-arkui-componentUtils.md#componentinfo) | 组件大小、位置、平移缩放旋转及仿射矩阵属性信息。 |

**错误码：** 

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID  | 错误信息                |
| ------ | ------------------- |
| 100001 | UI execution context not found. |

**示例：**

<!--code_no_check-->
```ts
import { ComponentUtils } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

  build() {
    RelativeContainer() {
      Text(this.message)
        .id('HelloWorld')
        .fontSize($r('app.float.page_text_font_size'))
        .fontWeight(FontWeight.Bold)
        .alignRules({
          center: { anchor: '__container__', align: VerticalAlign.Center },
          middle: { anchor: '__container__', align: HorizontalAlign.Center }
        })
        .onClick(() => {
          this.message = 'Welcome';
          let componentUtils: ComponentUtils = this.getUIContext().getComponentUtils();
          let modePosition = componentUtils.getRectangleById("HelloWorld");
          let width = modePosition.size.width; //获取组件的宽度
          let height = modePosition.size.height; //获取组件的高度
          let localOffsetX = modePosition.localOffset.x; // 获取组件相对于父组件的x轴偏移
          let localOffsetY = modePosition.localOffset.y; // 获取组件相对于父组件的y轴偏移
          console.info(`width: ${width}, height: ${height}, localOffsetX: ${localOffsetX}, localOffsetY: ${localOffsetY}`);
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

## UIInspector

以下API需先使用UIContext中的[getUIInspector()](#getuiinspector)方法获取到UIInspector对象，再通过该对象调用对应方法。

### createComponentObserver

createComponentObserver(id: string): inspector.ComponentObserver

注册组件布局和组件绘制送显完成回调通知。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名  | 类型     | 必填   | 说明      |
| ---- | ------ | ---- | ------- |
| id   | string | 是    | 指定组件id，该id通过通用属性[id](./arkui-ts/ts-universal-attributes-component-id.md#id)或者[key](./arkui-ts/ts-universal-attributes-component-id.md#key12)设置。 |

**返回值：** 

| 类型                                                         | 说明                                               |
| ------------------------------------------------------------ | -------------------------------------------------- |
| [inspector.ComponentObserver](js-apis-arkui-inspector.md#componentobserver) | 组件回调事件监听句柄，用于注册和取消注册监听回调。 |

**示例：**

<!--code_no_check-->
```ts
import { inspector, UIInspector } from '@kit.ArkUI'

@Entry
@Component
struct UIInspectorExample {
  build() {
    Column() {
      Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Start }) {
        Row({ space: 5 }) {
          Text("UIInspector")
            .width(110)
            .height(110)
            .border({ width: 1 })
            .id('TEXT_ID')
        }.width(80).width(80)
      }.width(80).width(80)
    }.height(320).width(360).padding({ right: 10, top: 10 })
  }

  uiInspector: UIInspector = this.getUIContext().getUIInspector();
  listener:inspector.ComponentObserver = this.uiInspector.createComponentObserver("TEXT_ID")

  aboutToAppear() {
    let onLayoutComplete:()=>void=():void=>{
      console.info("TEXT_ID layout complete")
    }
    let onDrawComplete:()=>void=():void=>{
      console.info("TEXT_ID draw complete")
    }

    this.listener.on('layout', onLayoutComplete)
    this.listener.on('draw', onDrawComplete)

    // 通过句柄向对应的查询条件取消注册回调，由开发者自行决定在何时调用。
    // this.listener.off('layout', onLayoutComplete)
    // this.listener.off('draw', onDrawComplete)
  }
}
```

## PageInfo<sup>12+</sup>
Router和NavDestination等页面信息，若无对应的Router或NavDestination页面信息，则对应属性为undefined。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| routerPageInfo | observer.[RouterPageInfo](js-apis-arkui-observer.md#routerpageinfo) | 否 | Router信息。 |
| navDestinationInfo | observer.[NavDestinationInfo](js-apis-arkui-observer.md#navdestinationinfo) | 否 | NavDestination信息。 |

## UIObserver<sup>11+</sup>

以下API需先使用UIContext中的[getUIObserver()](#getuiobserver11)方法获取到UIObserver对象，再通过该对象调用对应方法。

> **说明：**
>
> UIObserver仅能监听到本进程内的相关信息，不支持获取<!--Del-->[UIExtensionComponent](../../reference/apis-arkui/arkui-ts/ts-container-ui-extension-component-sys.md)等<!--DelEnd-->跨进程场景的信息。
>

### on('navDestinationUpdate')<sup>11+</sup>

on(type: 'navDestinationUpdate', callback: Callback\<observer.NavDestinationInfo\>): void

监听NavDestination组件的状态变化。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名   | 类型                                                  | 必填 | 说明                                                         |
| -------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                                                | 是   | 监听事件，固定为'navDestinationUpdate'，即NavDestination组件的状态变化。 |
| callback | Callback\<observer.[NavDestinationInfo](js-apis-arkui-observer.md#navdestinationinfo)\> | 是   | 回调函数。返回当前的NavDestination组件状态。                 |

**示例：**

<!--code_no_check-->
```ts
// Index.ets
// 演示 uiObserver.on('navDestinationUpdate', callback)
// uiObserver.off('navDestinationUpdate', callback)

@Component
struct PageOne {
  build() {
    NavDestination() {
      Text("pageOne")
    }.title("pageOne")
  }
}

@Entry
@Component
struct Index {
  private stack: NavPathStack = new NavPathStack();

  @Builder
  PageBuilder(name: string) {
    PageOne()
  }

  aboutToAppear() {
    this.getUIContext().getUIObserver().on('navDestinationUpdate', (info) => {
      console.info('NavDestination state update', JSON.stringify(info));
    });
  }

  aboutToDisappear() {
    this.getUIContext().getUIObserver().off('navDestinationUpdate');
  }

  build() {
    Column() {
      Navigation(this.stack) {
        Button("push").onClick(() => {
          this.stack.pushPath({ name: "pageOne" });
        })
      }
      .title("Navigation")
      .navDestination(this.PageBuilder)
    }
    .width('100%')
    .height('100%')
  }
}
```

### off('navDestinationUpdate')<sup>11+</sup>

off(type: 'navDestinationUpdate', callback?: Callback\<observer.NavDestinationInfo\>): void

取消监听NavDestination组件的状态变化。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名   | 类型                                                  | 必填 | 说明                                                         |
| -------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                                                | 是   | 监听事件，固定为'navDestinationUpdate'，即NavDestination组件的状态变化。 |
| callback | Callback\<observer.[NavDestinationInfo](js-apis-arkui-observer.md#navdestinationinfo)\> | 否   | 回调函数。返回当前的NavDestination组件状态。                 |

**示例：** 

参考[uiObserver.on('navDestinationUpdate')](#onnavdestinationupdate11)示例。

### on('navDestinationUpdate')<sup>11+</sup>

on(type: 'navDestinationUpdate', options: { navigationId: ResourceStr }, callback: Callback\<observer.NavDestinationInfo\>): void

监听NavDestination组件的状态变化。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | 是   | 监听事件，固定为'navDestinationUpdate'，即NavDestination组件的状态变化。 |
| options  | { navigationId: [ResourceStr](arkui-ts/ts-types.md#resourcestr) } | 是   | 指定监听的Navigation的id。                                   |
| callback | Callback\<observer.[NavDestinationInfo](js-apis-arkui-observer.md#navdestinationinfo)\>        | 是   | 回调函数。返回当前的NavDestination组件状态。                 |

**示例：**

<!--code_no_check-->
```ts
// Index.ets
// 演示 uiObserver.on('navDestinationUpdate', navigationId, callback)
// uiObserver.off('navDestinationUpdate', navigationId, callback)
@Component
struct PageOne {
  build() {
    NavDestination() {
      Text("pageOne")
    }.title("pageOne")
  }
}

@Entry
@Component
struct Index {
  private stack: NavPathStack = new NavPathStack();

  @Builder
  PageBuilder(name: string) {
    PageOne()
  }

  aboutToAppear() {
    this.getUIContext().getUIObserver().on('navDestinationUpdate', { navigationId: "testId" }, (info) => {
      console.info('NavDestination state update', JSON.stringify(info));
    });
  }

  aboutToDisappear() {
    this.getUIContext().getUIObserver().off('navDestinationUpdate', { navigationId: "testId" });
  }

  build() {
    Column() {
      Navigation(this.stack) {
        Button("push").onClick(() => {
          this.stack.pushPath({ name: "pageOne" });
        })
      }
      .id("testId")
      .title("Navigation")
      .navDestination(this.PageBuilder)
    }
    .width('100%')
    .height('100%')
  }
}
```

### off('navDestinationUpdate')<sup>11+</sup>

off(type: 'navDestinationUpdate', options: { navigationId: ResourceStr }, callback?: Callback\<observer.NavDestinationInfo\>): void

取消监听NavDestination组件的状态变化。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | 是   | 监听事件，固定为'navDestinationUpdate'，即NavDestination组件的状态变化。 |
| options  | { navigationId: [ResourceStr](arkui-ts/ts-types.md#resourcestr) } | 是   | 指定监听的Navigation的id。                                   |
| callback | Callback\<observer.[NavDestinationInfo](js-apis-arkui-observer.md#navdestinationinfo)\>        | 否   | 回调函数。返回当前的NavDestination组件状态。                 |

**示例：**

参考[uiObserver.on('navDestinationUpdate')](#onnavdestinationupdate11-1)示例。

### on('scrollEvent')<sup>12+</sup>

on(type: 'scrollEvent', callback: Callback\<observer.ScrollEventInfo\>): void

监听所有滚动组件滚动事件的开始和结束。滚动组件包括[List](./arkui-ts/ts-container-list.md)、[Grid](./arkui-ts/ts-container-grid.md)、[Scroll](./arkui-ts/ts-container-scroll.md)、[WaterFlow](./arkui-ts/ts-container-waterflow.md)、[ArcList](./arkui-ts/ts-container-arclist.md)。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名   | 类型                                                  | 必填 | 说明                                                         |
| -------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                                                | 是   | 监听事件，固定为'scrollEvent'，即滚动事件的开始和结束。      |
| callback | Callback\<observer.[ScrollEventInfo](js-apis-arkui-observer.md#scrolleventinfo12)\> | 是   | 回调函数。返回滚动事件的信息。   |

**示例：**

参考[off('scrollEvent')](#offscrollevent12-1)示例。

### off('scrollEvent')<sup>12+</sup>

off(type: 'scrollEvent', callback?: Callback\<observer.ScrollEventInfo\>): void

取消监听所有滚动组件滚动事件的开始和结束。滚动组件包括[List](./arkui-ts/ts-container-list.md)、[Grid](./arkui-ts/ts-container-grid.md)、[Scroll](./arkui-ts/ts-container-scroll.md)、[WaterFlow](./arkui-ts/ts-container-waterflow.md)、[ArcList](./arkui-ts/ts-container-arclist.md)。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名   | 类型                                                  | 必填 | 说明                                                         |
| -------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                                                | 是   | 监听事件，固定为'scrollEvent'，即滚动事件的开始和结束。      |
| callback | Callback\<observer.[ScrollEventInfo](js-apis-arkui-observer.md#scrolleventinfo12)\> | 否   | 回调函数。返回滚动事件的信息。   |

**示例：**

参考[off('scrollEvent')](#offscrollevent12-1)示例。

### on('scrollEvent')<sup>12+</sup>

on(type: 'scrollEvent', options: observer.ObserverOptions, callback: Callback\<observer.ScrollEventInfo\>): void

监听指定id的滚动组件滚动事件的开始和结束。滚动组件包括[List](./arkui-ts/ts-container-list.md)、[Grid](./arkui-ts/ts-container-grid.md)、[Scroll](./arkui-ts/ts-container-scroll.md)、[WaterFlow](./arkui-ts/ts-container-waterflow.md)、[ArcList](./arkui-ts/ts-container-arclist.md)。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | 是   | 监听事件，固定为'scrollEvent'，即滚动事件的开始和结束。 |
| options  | [observer.ObserverOptions](js-apis-arkui-observer.md#observeroptions12) | 是   | Observer选项，包含指定监听的滚动组件的id。                    |
| callback | Callback\<observer.[ScrollEventInfo](js-apis-arkui-observer.md#scrolleventinfo12)\>        | 是   | 回调函数。返回滚动事件的信息。                 |

**示例：**

参考[off('scrollEvent')](#offscrollevent12-1)示例。

### off('scrollEvent')<sup>12+</sup>

off(type: 'scrollEvent', options: observer.ObserverOptions, callback?: Callback\<observer.ScrollEventInfo\>): void

取消监听指定id的滚动组件滚动事件的开始和结束。滚动组件包括[List](./arkui-ts/ts-container-list.md)、[Grid](./arkui-ts/ts-container-grid.md)、[Scroll](./arkui-ts/ts-container-scroll.md)、[WaterFlow](./arkui-ts/ts-container-waterflow.md)、[ArcList](./arkui-ts/ts-container-arclist.md)。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | 是   | 监听事件，固定为'scrollEvent'，即滚动事件的开始和结束。 |
| options  | [observer.ObserverOptions](js-apis-arkui-observer.md#observeroptions12) | 是   | Observer选项，包含指定监听的滚动组件的id。                    |
| callback | Callback\<observer.[ScrollEventInfo](js-apis-arkui-observer.md#scrolleventinfo12)\>        | 否   | 回调函数。返回滚动事件的信息。                 |

**示例：**

```ts
import { UIObserver } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  scroller: Scroller = new Scroller();
  observer: UIObserver = this.getUIContext().getUIObserver();
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7];

  build() {
    Column() {
      Column() {
        Scroll(this.scroller) {
          Column() {
            ForEach(this.arr, (item: number) => {
              Text(item.toString())
                .width('90%')
                .height(150)
                .backgroundColor(0xFFFFFF)
                .borderRadius(15)
                .fontSize(16)
                .textAlign(TextAlign.Center)
                .margin({ top: 10 })
            }, (item: string) => item)
          }.width('100%')
        }
        .id('testId')
        .height('80%')
      }
      .width('100%')

      Row() {
        Button('UIObserver on')
          .onClick(() => {
            this.observer.on('scrollEvent', (info) => {
              console.info('scrollEventInfo', JSON.stringify(info));
            });
          })
        Button('UIObserver off')
          .onClick(() => {
            this.observer.off('scrollEvent');
          })
      }

      Row() {
        Button('UIObserverWithId on')
          .onClick(() => {
            this.observer.on('scrollEvent', { id: 'testId' }, (info) => {
              console.info('scrollEventInfo', JSON.stringify(info));
            });
          })
        Button('UIObserverWithId off')
          .onClick(() => {
            this.observer.off('scrollEvent', { id: 'testId' });
          })
      }
    }
    .height('100%')
  }
}
```

### on('routerPageUpdate')<sup>11+</sup>

on(type: 'routerPageUpdate', callback: Callback\<observer.RouterPageInfo\>): void

监听router中page页面的状态变化。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | 是   | 监听事件，固定为'routerPageUpdate'，即router中page页面的状态变化。 |
| callback | Callback\<observer.[RouterPageInfo](js-apis-arkui-observer.md#routerpageinfo)\>        | 是   | 回调函数。携带pageInfo，返回当前的page页面状态。                 |

**示例：**

完整示例请参考[on('navDestinationUpdate')](#onnavdestinationupdate11)中的示例。

<!--code_no_check-->
```ts
import { UIContext, UIObserver } from '@kit.ArkUI';

let observer:UIObserver = this.getUIContext().getUIObserver();
observer.on('routerPageUpdate', (info) => {
    console.info('RouterPage state updated, called by ' + `${info.name}`);
});
```

### off('routerPageUpdate')<sup>11+</sup>

off(type: 'routerPageUpdate', callback?: Callback\<observer.RouterPageInfo\>): void

取消监听router中page页面的状态变化。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | 是   | 监听事件，固定为'routerPageUpdate'，即router中page页面的状态变化。 |
| callback | Callback\<observer.[RouterPageInfo](js-apis-arkui-observer.md#routerpageinfo)\>        | 否   | 需要被注销的回调函数。                 |

**示例：**

完整示例请参考[on('navDestinationUpdate')](#onnavdestinationupdate11)中的示例。

<!--code_no_check-->
```ts
import { UIContext, UIObserver } from '@kit.ArkUI';

let observer:UIObserver = this.getUIContext().getUIObserver();
function callBackFunc(info:observer.RouterPageInfo) {};
// callBackFunc is defined and used before
observer.off('routerPageUpdate', callBackFunc);
```

### on('densityUpdate')<sup>12+</sup>

on(type: 'densityUpdate', callback: Callback\<observer.DensityInfo\>): void

监听屏幕像素密度变化。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | 是   | 监听事件，固定为'densityUpdate'，即屏幕像素密度变化。 |
| callback | Callback\<observer.[DensityInfo](./js-apis-arkui-observer.md#densityinfo12)\>        | 是   | 回调函数。携带densityInfo，返回变化后的屏幕像素密度。                 |

```ts
import { uiObserver } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State density: number = 0;
  @State message: string = '未注册监听';

  densityUpdateCallback = (info: uiObserver.DensityInfo) => {
    this.density = info.density;
    this.message = '变化后的DPI：' + this.density.toString();
  }

  build() {
    Column() {
      Text(this.message)
        .fontSize(24)
        .fontWeight(FontWeight.Bold)
      Button('注册屏幕像素密度变化监听')
        .onClick(() => {
          this.message = '已注册监听';
          this.getUIContext().getUIObserver().on('densityUpdate', this.densityUpdateCallback);
        })
    }
  }
}
```

### off('densityUpdate')<sup>12+</sup>

off(type: 'densityUpdate', callback?: Callback\<observer.DensityInfo\>): void

取消监听屏幕像素密度的变化。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名   | 类型                                                                 | 必填 | 说明                                                                                         |
| -------- | -------------------------------------------------------------------- | ---- | -------------------------------------------------------------------------------------------- |
| type     | string                                                               | 是   | 监听事件，固定为'densityUpdate'，即屏幕像素密度变化。                                        |
| callback | Callback\<observer.[DensityInfo](./js-apis-arkui-observer.md#densityinfo12)\> | 否   | 需要被注销的回调函数。若不指定具体的回调函数，则注销该UIContext下所有densityUpdate事件监听。 |

```ts
import { uiObserver } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State density: number = 0;
  @State message: string = '未注册监听';

  densityUpdateCallback = (info: uiObserver.DensityInfo) => {
    this.density = info.density;
    this.message = '变化后的DPI：' + this.density.toString();
  }

  build() {
    Column() {
      Text(this.message)
        .fontSize(24)
        .fontWeight(FontWeight.Bold)
      Button('注册屏幕像素密度变化监听')
        .margin({ bottom: 10 })
        .onClick(() => {
          this.message = '已注册监听';
          this.getUIContext().getUIObserver().on('densityUpdate', this.densityUpdateCallback);
        })
      Button('解除注册屏幕像素密度变化监听')
        .onClick(() => {
          this.message = '未注册监听';
          this.getUIContext().getUIObserver().off('densityUpdate', this.densityUpdateCallback);
        })
    }
  }
}
```

### on('willDraw')<sup>12+</sup>

on(type: 'willDraw', callback: Callback\<void\>): void

监听每一帧绘制指令下发情况。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | 是   | 监听事件，固定为'willDraw'，即是否将要绘制。 |
| callback | Callback\<void\>        | 是   | 回调函数。                 |

```ts
import { uiObserver } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  willDrawCallback = () => {
    console.info("willDraw指令下发");
  }
  build() {
    Column() {
      Button('注册绘制指令下发监听')
        .onClick(() => {
          this.getUIContext().getUIObserver().on('willDraw', this.willDrawCallback);
        })
    }
  }
}
```

### off('willDraw')<sup>12+</sup>

off(type: 'willDraw', callback?: Callback\<void\>): void

取消监听每一帧绘制指令下发情况。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | 是   | 监听事件，固定为'willDraw'，即是否将要绘制。 |
| callback | Callback\<void\>        | 否   | 需要被注销的回调函数。                  |

```ts
import { uiObserver } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  willDrawCallback = () => {
    console.info("willDraw指令下发")
  }

  build() {
    Column() {
      Button('注册绘制指令下发监听')
        .margin({ bottom: 10 })
        .onClick(() => {
          this.getUIContext().getUIObserver().on('willDraw', this.willDrawCallback);
        })
      Button('解除注册绘制指令下发监听')
        .onClick(() => {
          this.getUIContext().getUIObserver().off('willDraw', this.willDrawCallback);
        })
    }
  }
}
```

### on('didLayout')<sup>12+</sup>

on(type: 'didLayout', callback: Callback\<void\>): void

监听每一帧布局完成情况。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | 是   | 监听事件，固定为'didLayout'，即是否布局完成。 |
| callback | Callback\<void\>        | 是   | 回调函数。                 |

```ts
import { uiObserver } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  didLayoutCallback = () => {
    console.info("layout布局完成");
  }
  build() {
    Column() {
      Button('注册布局完成监听')
        .onClick(() => {
          this.getUIContext().getUIObserver().on('didLayout', this.didLayoutCallback);
        })
    }
  }
}
```

### off('didLayout')<sup>12+</sup>

off(type: 'didLayout', callback?: Callback\<void\>): void

取消监听每一帧布局完成情况。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | 是   | 监听事件，固定为'didLayout'，即是否布局完成。 |
| callback | Callback\<void\>        | 否   | 需要被注销的回调函数。                  |

```ts
import { uiObserver } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  didLayoutCallback = () => {
    console.info("layout布局完成");
  }

  build() {
    Column() {
      Button('注册布局完成监听')
        .margin({ bottom: 10 })
        .onClick(() => {
          this.getUIContext().getUIObserver().on('didLayout', this.didLayoutCallback);
        })
      Button('解除注册注册布局完成监听')
        .onClick(() => {
          this.getUIContext().getUIObserver().off('didLayout', this.didLayoutCallback);
        })
    }
  }
}
```

### on('navDestinationSwitch')<sup>12+</sup>

on(type: 'navDestinationSwitch', callback: Callback\<observer.NavDestinationSwitchInfo\>): void

监听Navigation的页面切换事件。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | 是   | 监听事件，固定为'navDestinationSwitch'，即Navigation的页面切换事件。 |
| callback | Callback\<observer.[NavDestinationSwitchInfo](js-apis-arkui-observer.md#navdestinationswitchinfo12)\>        | 是   | 回调函数。携带NavDestinationSwitchInfo，返回页面切换事件的信息。                 |

**示例：**

```ts
// Index.ets
// 演示 UIObserver.on('navDestinationSwitch', callback)
// UIObserver.off('navDestinationSwitch', callback)
import { uiObserver } from '@kit.ArkUI';

@Component
struct PageOne {
  build() {
    NavDestination() {
      Text("pageOne")
    }.title("pageOne")
  }
}

function callBackFunc(info: uiObserver.NavDestinationSwitchInfo) {
  console.info(`testTag navDestinationSwitch from: ${JSON.stringify(info.from)} to: ${JSON.stringify(info.to)}`);
}

@Entry
@Component
struct Index {
  private stack: NavPathStack = new NavPathStack();

  @Builder
  PageBuilder(name: string) {
    PageOne()
  }

  aboutToAppear() {
    let obs = this.getUIContext().getUIObserver();
    obs.on('navDestinationSwitch', callBackFunc);
  }

  aboutToDisappear() {
    let obs = this.getUIContext().getUIObserver();
    obs.off('navDestinationSwitch', callBackFunc);
  }

  build() {
    Column() {
      Navigation(this.stack) {
        Button("push").onClick(() => {
          this.stack.pushPath({name: "pageOne"});
        })
      }
      .title("Navigation")
      .navDestination(this.PageBuilder)
    }
    .width('100%')
    .height('100%')
  }
}
```

### off('navDestinationSwitch')<sup>12+</sup>

off(type: 'navDestinationSwitch', callback?: Callback\<observer.NavDestinationSwitchInfo\>): void

取消监听Navigation的页面切换事件。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | 是   | 监听事件，固定为'navDestinationSwitch'，即Navigation的页面切换事件。 |
| callback | Callback\<observer.[NavDestinationSwitchInfo](js-apis-arkui-observer.md#navdestinationswitchinfo12)\>        | 否   | 需要被注销的回调函数。                 |

**示例代码参考上述UIObserver.on('navDestinationSwitch')接口的示例代码**

### on('navDestinationSwitch')<sup>12+</sup>

on(type: 'navDestinationSwitch', observerOptions: observer.NavDestinationSwitchObserverOptions, callback: Callback\<observer.NavDestinationSwitchInfo\>): void

监听Navigation的页面切换事件。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | 是   | 监听事件，固定为'navDestinationSwitch'，即Navigation的页面切换事件。 |
| observerOptions | observer.[NavDestinationSwitchObserverOptions](js-apis-arkui-observer.md#navdestinationswitchobserveroptions12)        | 是   | 监听选项。   |
| callback | Callback\<observer.[NavDestinationSwitchInfo](js-apis-arkui-observer.md#navdestinationswitchinfo12)\>        | 是   | 回调函数。携带NavDestinationSwitchInfo，返回页面切换事件的信息。                 |

**示例：**

```ts
// Index.ets
// 演示 UIObserver.on('navDestinationSwitch', NavDestinationSwitchObserverOptions, callback)
// UIObserver.off('navDestinationSwitch', NavDestinationSwitchObserverOptions, callback)
import { uiObserver } from '@kit.ArkUI';

@Component
struct PageOne {
  build() {
    NavDestination() {
      Text("pageOne")
    }.title("pageOne")
  }
}

function callBackFunc(info: uiObserver.NavDestinationSwitchInfo) {
  console.info(`testTag navDestinationSwitch from: ${JSON.stringify(info.from)} to: ${JSON.stringify(info.to)}`);
}

@Entry
@Component
struct Index {
  private stack: NavPathStack = new NavPathStack();

  @Builder
  PageBuilder(name: string) {
    PageOne()
  }

  aboutToAppear() {
    let obs = this.getUIContext().getUIObserver();
    obs.on('navDestinationSwitch', { navigationId: "myNavId" }, callBackFunc);
  }

  aboutToDisappear() {
    let obs = this.getUIContext().getUIObserver();
    obs.off('navDestinationSwitch', { navigationId: "myNavId" }, callBackFunc);
  }

  build() {
    Column() {
      Navigation(this.stack) {
        Button("push").onClick(() => {
          this.stack.pushPath({name: "pageOne"});
        })
      }
      .id("myNavId")
      .title("Navigation")
      .navDestination(this.PageBuilder)
    }
    .width('100%')
    .height('100%')
  }
}
```

### off('navDestinationSwitch')<sup>12+</sup>

off(type: 'navDestinationSwitch', observerOptions: observer.NavDestinationSwitchObserverOptions, callback?: Callback\<observer.NavDestinationSwitchInfo\>): void

取消监听Navigation的页面切换事件。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | 是   | 监听事件，固定为'navDestinationSwitch'，即Navigation的页面切换事件。 |
| observerOptions | observer.[NavDestinationSwitchObserverOptions](js-apis-arkui-observer.md#navdestinationswitchobserveroptions12)        | 是   | 监听选项。   |
| callback | Callback\<observer.[NavDestinationSwitchInfo](js-apis-arkui-observer.md#navdestinationswitchinfo12)\>        | 否   | 需要被注销的回调函数。                 |

**示例代码参考上述UIObserver.on('navDestinationSwitch')接口的示例代码**

### on('willClick')<sup>12+</sup>

on(type: 'willClick', callback: GestureEventListenerCallback): void

监听点击事件指令下发情况。回调类型为[GestureEventListenerCallback](#gestureeventlistenercallback12)。暂不支持屏幕朗读触控模式。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | 是   | 监听事件，固定为'willClick'，用于监听点击事件指令下发情况，所注册回调将于点击事件触发前触发。 |
| callback | [GestureEventListenerCallback](#gestureeventlistenercallback12) | 是   | 回调函数。可以获得点击事件的GestureEvent和组件的FrameNode。  |

**示例：**

```ts
// 定义监听回调函数
function willClickGestureCallback(event: GestureEvent, node?: FrameNode) {
  console.info('Example willClickCallback GestureEvent is called');
}

function willClickCallback(event: ClickEvent, node?: FrameNode) {
  console.info('Example willClickCallback ClickEvent is called');
}

function didClickGestureCallback(event: GestureEvent, node?: FrameNode) {
  console.info('Example didClickCallback GestureEvent is called');
}

function didClickCallback(event: ClickEvent, node?: FrameNode) {
  console.info('Example didClickCallback ClickEvent is called');
}

@Entry
@Component
struct ClickExample {
  @State clickCount: number = 0;
  @State tapGestureCount: number = 0;

  aboutToAppear(): void {
    // 添加监听
    let observer = this.getUIContext().getUIObserver();
    observer.on('willClick', willClickGestureCallback);
    observer.on('willClick', willClickCallback);
    observer.on('didClick', didClickGestureCallback);
    observer.on('didClick', didClickCallback);
  }

  aboutToDisappear(): void {
    // 取消监听
    let observer = this.getUIContext().getUIObserver();
    observer.off('willClick', willClickGestureCallback);
    observer.off('willClick', willClickCallback);
    // 如果不选择回调，则会取消所有监听的回调
    observer.off('didClick');
  }

  build() {
    Column() {
      /**
       * onClick和TapGesture在后端的处理是一致的
       * 所以无论是触发onClick还是触发TapGesture
       * on('willClick')两种类型入参的回调（GestureEvent和ClickEvent）都会被触发
       * 同理，on('didClick')的两种回调也会被触发
       */
      Column() {
        Text('Click Count: ' + this.clickCount)
      }
      .height(200)
      .width(300)
      .padding(20)
      .border({ width: 3 })
      .margin(50)
      .onClick((event: ClickEvent) => {
        this.clickCount++;
        console.info('Example Click event is called');
      })

      Column() {
        Text('TapGesture Count: ' + this.tapGestureCount)
      }
      .height(200)
      .width(300)
      .padding(20)
      .border({ width: 3 })
      .margin(50)
      .gesture(TapGesture({ count: 2 }).onAction((event: TapGestureEvent) => {
        this.tapGestureCount++;
        console.info('Example Click event is called');
      }))
    }
  }
}
```

### off('willClick')<sup>12+</sup>

off(type: 'willClick', callback?: GestureEventListenerCallback): void

取消监听点击事件指令下发情况。暂不支持屏幕朗读触控模式。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名   | 类型                                                         | 必填 | 说明                                                  |
| -------- | ------------------------------------------------------------ | ---- | ----------------------------------------------------- |
| type     | string                                                       | 是   | 监听事件，固定为'willClick'，即点击事件指令下发情况。 |
| callback | [GestureEventListenerCallback](#gestureeventlistenercallback12) | 否   | 需要被注销的回调函数。                                |

**示例：**

完整示例请参考[on('willClick')](#onwillclick12)中的示例。

### on('didClick')<sup>12+</sup>

on(type: 'didClick', callback: GestureEventListenerCallback): void

监听点击事件指令下发情况。回调类型为[GestureEventListenerCallback](#gestureeventlistenercallback12)。暂不支持屏幕朗读触控模式。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | 是   | 监听事件，固定为'didClick'，用于监听点击事件指令下发情况，所注册回调将于点击事件触发后触发。 |
| callback | [GestureEventListenerCallback](#gestureeventlistenercallback12) | 是   | 回调函数。可以获得点击事件的GestureEvent和组件的FrameNode。  |

**示例：**

完整示例请参考[on('willClick')](#onwillclick12)中的示例。

### off('didClick')<sup>12+</sup>

off(type: 'didClick', callback?: GestureEventListenerCallback): void

取消监听点击事件指令下发情况。暂不支持屏幕朗读触控模式。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名   | 类型                                                         | 必填 | 说明                                                 |
| -------- | ------------------------------------------------------------ | ---- | ---------------------------------------------------- |
| type     | string                                                       | 是   | 监听事件，固定为'didClick'，即点击事件指令下发情况。 |
| callback | [GestureEventListenerCallback](#gestureeventlistenercallback12) | 否   | 需要被注销的回调函数。                               |

**示例：**

完整示例请参考[on('willClick')](#onwillclick12)中的示例。

### on('willClick')<sup>12+</sup>

on(type: 'willClick', callback: ClickEventListenerCallback): void

监听点击事件指令下发情况。回调类型为[ClickEventListenerCallback](#clickeventlistenercallback12)。暂不支持屏幕朗读触控模式。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名   | 类型                                                        | 必填 | 说明                                                         |
| -------- | ----------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                                                      | 是   | 监听事件，固定为'willClick'，用于监听点击事件指令下发情况，所注册回调将于点击事件触发前触发。 |
| callback | [ClickEventListenerCallback](#clickeventlistenercallback12) | 是   | 回调函数。可以获得点击事件的ClickEvent和组件的FrameNode。    |

**示例：**

完整示例请参考[on('willClick')](#onwillclick12)中的示例。

### off('willClick')<sup>12+</sup>

off(type: 'willClick', callback?: ClickEventListenerCallback): void

取消监听点击事件指令下发情况。暂不支持屏幕朗读触控模式。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名   | 类型                                                        | 必填 | 说明                                                  |
| -------- | ----------------------------------------------------------- | ---- | ----------------------------------------------------- |
| type     | string                                                      | 是   | 监听事件，固定为'willClick'，即点击事件指令下发情况。 |
| callback | [ClickEventListenerCallback](#clickeventlistenercallback12) | 否   | 需要被注销的回调函数。                                |

**示例：**

完整示例请参考[on('willClick')](#onwillclick12)中的示例。

### on('didClick')<sup>12+</sup>

on(type: 'didClick', callback: ClickEventListenerCallback): void

监听点击事件指令下发情况。回调类型为[ClickEventListenerCallback](#clickeventlistenercallback12)。暂不支持屏幕朗读触控模式。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名   | 类型                                                        | 必填 | 说明                                                         |
| -------- | ----------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                                                      | 是   | 监听事件，固定为'didClick'，用于监听点击事件指令下发情况，所注册回调将于点击事件触发后触发。 |
| callback | [ClickEventListenerCallback](#clickeventlistenercallback12) | 是   | 回调函数。可以获得点击事件的ClickEvent和组件的FrameNode。    |

**示例：**

完整示例请参考[on('willClick')](#onwillclick12)中的示例。

### off('didClick')<sup>12+</sup>

off(type: 'didClick', callback?: ClickEventListenerCallback): void

取消监听点击事件指令下发情况。暂不支持屏幕朗读触控模式。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名   | 类型                                                        | 必填 | 说明                                                 |
| -------- | ----------------------------------------------------------- | ---- | ---------------------------------------------------- |
| type     | string                                                      | 是   | 监听事件，固定为'didClick'，即点击事件指令下发情况。 |
| callback | [ClickEventListenerCallback](#clickeventlistenercallback12) | 否   | 需要被注销的回调函数。                               |

**示例：**

完整示例请参考[on('willClick')](#onwillclick12)中的示例。

### on('tabContentUpdate')<sup>12+</sup>

on(type: 'tabContentUpdate', callback: Callback\<observer.TabContentInfo\>): void

监听TabContent页面的切换事件。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | 是   | 监听事件，固定为'tabContentUpdate'，即TabContent页面的切换事件。 |
| callback | Callback\<observer.[TabContentInfo](js-apis-arkui-observer.md#tabcontentinfo12)\> | 是   | 回调函数。携带TabContentInfo，返回TabContent页面切换事件的信息。 |

**示例：**

```ts
import { uiObserver } from '@kit.ArkUI';

function callbackFunc(info: uiObserver.TabContentInfo) {
  console.info('tabContentUpdate', JSON.stringify(info));
}

@Entry
@Component
struct TabsExample {

  aboutToAppear(): void {
    let observer = this.getUIContext().getUIObserver();
    observer.on('tabContentUpdate', callbackFunc);
  }

  aboutToDisappear(): void {
    let observer = this.getUIContext().getUIObserver();
    observer.off('tabContentUpdate', callbackFunc);
  }

  build() {
    Column() {
      Tabs() {
        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#00CB87')
        }.tabBar('green').id('tabContentId0')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#007DFF')
        }.tabBar('blue').id('tabContentId1')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#FFBF00')
        }.tabBar('yellow').id('tabContentId2')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#E67C92')
        }.tabBar('pink').id('tabContentId3')
      }
      .width(360)
      .height(296)
      .backgroundColor('#F1F3F5')
      .id('tabsId')
    }.width('100%')
  }
}
```

### off('tabContentUpdate')<sup>12+</sup>

off(type: 'tabContentUpdate', callback?: Callback\<observer.TabContentInfo\>): void

取消监听TabContent页面的切换事件。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | 是   | 监听事件，固定为'tabContentUpdate'，即TabContent页面的切换事件。 |
| callback | Callback\<observer.[TabContentInfo](js-apis-arkui-observer.md#tabcontentinfo12)\> | 否   | 需要被注销的回调函数。 |

**示例：**

参考[on('tabContentUpdate')](#ontabcontentupdate12)接口示例。

### on('tabContentUpdate')<sup>12+</sup>

on(type: 'tabContentUpdate', options: observer.ObserverOptions, callback: Callback\<observer.TabContentInfo\>): void

监听TabContent页面的切换事件。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | 是   | 监听事件，固定为'tabContentUpdate'，即TabContent页面的切换事件。 |
| options  | observer.[ObserverOptions](js-apis-arkui-observer.md#observeroptions12) | 是   | 指定监听的Tabs组件的id。 |
| callback | Callback\<observer.[TabContentInfo](js-apis-arkui-observer.md#tabcontentinfo12)\> | 是   | 回调函数。携带TabContentInfo，返回TabContent页面切换事件的信息。 |

**示例：**

```ts
import { uiObserver } from '@kit.ArkUI';

function callbackFunc(info: uiObserver.TabContentInfo) {
  console.info('tabContentUpdate', JSON.stringify(info));
}

@Entry
@Component
struct TabsExample {

  aboutToAppear(): void {
    let observer = this.getUIContext().getUIObserver();
    observer.on('tabContentUpdate', { id: 'tabsId' }, callbackFunc);
  }

  aboutToDisappear(): void {
    let observer = this.getUIContext().getUIObserver();
    observer.off('tabContentUpdate', { id: 'tabsId' }, callbackFunc);
  }

  build() {
    Column() {
      Tabs() {
        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#00CB87')
        }.tabBar('green').id('tabContentId0')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#007DFF')
        }.tabBar('blue').id('tabContentId1')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#FFBF00')
        }.tabBar('yellow').id('tabContentId2')

        TabContent() {
          Column().width('100%').height('100%').backgroundColor('#E67C92')
        }.tabBar('pink').id('tabContentId3')
      }
      .width(360)
      .height(296)
      .backgroundColor('#F1F3F5')
      .id('tabsId')
    }.width('100%')
  }
}
```

### off('tabContentUpdate')<sup>12+</sup>

off(type: 'tabContentUpdate', options: observer.ObserverOptions, callback?: Callback\<observer.TabContentInfo\>): void

取消监听TabContent页面的切换事件。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | 是   | 监听事件，固定为'tabContentUpdate'，即TabContent页面的切换事件。 |
| options  | observer.[ObserverOptions](js-apis-arkui-observer.md#observeroptions12) | 是   | 指定监听的Tabs组件的id。 |
| callback | Callback\<observer.[TabContentInfo](js-apis-arkui-observer.md#tabcontentinfo12)\> | 否   | 需要被注销的回调函数。 |

**示例：**

参考[on('tabContentUpdate')](#ontabcontentupdate12-1)接口示例。

### on('beforePanStart')<sup>19+</sup>

on(type: 'beforePanStart', callback: PanListenerCallback): void

监听Pan手势[onActionStart](arkui-ts/ts-basic-gestures-pangesture.md#事件)事件，在onActionStart事件执行之前执行callback回调。支持手指滑动、鼠标滑动、鼠标滚轮和触摸板拖动，暂不支持屏幕朗读触控模式。

**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名   | 类型                                                        | 必填 | 说明                                                         |
| -------- | ----------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                                                      | 是   | 监听事件，固定为'beforePanStart'，用于监听Pan手势onActionStart事件执行前的指令下发情况，所注册回调将于Pan手势onActionStart事件触发前触发。 |
| callback | [PanListenerCallback](#panlistenercallback19) | 是   | 回调函数。可以获得Pan手势事件的GestureEvent，GestureRecognizer和组件的FrameNode。   |

**示例：**

```ts
// 在页面Component中使用
import { uiObserver } from '@kit.ArkUI';
import router from '@ohos.router';

let TEST_TAG: string = 'node';

function callbackFunc() {
  console.info('on == beforePanStart');
}

function afterPanCallBack() {
  console.info('on == afterPanStart');
}

function beforeEndCallBack() {
  console.info('on == beforeEnd');
}

function afterEndCallBack() {
  console.info('on == afterEnd');
}

function beforeStartCallBack() {
  console.info('on == beforeStartCallBack');
}

function panGestureCallBack(event: GestureEvent, current: GestureRecognizer, node?: FrameNode) {
  TEST_TAG = 'panGestureEvent';
  console.info('===' + TEST_TAG + '=== event.repeat is ' + event.repeat);
  console.info('===' + TEST_TAG + '=== event target is ' + event.target.id);
  TEST_TAG = 'panGestureCurrent';
  console.info('===' + TEST_TAG + '=== current.getTag() is ' + current.getTag());
  TEST_TAG = 'panGestureNode';
  console.info('===' + TEST_TAG + '=== node?.getId() is ' + node?.getId());
}


@Entry
@Component
struct PanExample {
  @State offsetX: number = 0;
  @State offsetY: number = 0;
  @State positionX: number = 0;
  @State positionY: number = 0;
  private panOption: PanGestureOptions = new PanGestureOptions({direction: PanDirection.All });

  aboutToAppear(): void {
    let observer = this.getUIContext().getUIObserver();
    observer.on('beforePanStart', callbackFunc);
    observer.on('beforePanStart', panGestureCallBack);
    observer.on('beforePanStart', beforeStartCallBack);
    observer.on('afterPanStart', afterPanCallBack);
    observer.on('beforePanEnd', beforeEndCallBack);
    observer.on('afterPanEnd', afterEndCallBack);
  }

  aboutToDisappear(): void {
    let observer = this.getUIContext().getUIObserver();
    observer.off('beforePanStart', callbackFunc);
    observer.off('beforePanStart');
    observer.off('afterPanStart', afterPanCallBack);
    observer.off('beforePanEnd');
    observer.off('afterPanEnd');
  }
  build() {
    Column(){
      Column(){
        Text('PanGesture :\nX: ' + this.offsetX + '\n' + 'Y: ' + this.offsetY)
      }
      .height(200)
      .width(300)
      .padding(20)
      .border({ width: 3 })
      .margin(50)
      .translate({ x: this.offsetX, y: this.offsetY, z: 0 })
      .id('columnOuter')
      .gesture(
        PanGesture(this.panOption)
          .onActionStart((event: GestureEvent) => {
            console.info('Pan start');
          })
          .onActionUpdate((event: GestureEvent) => {
            if (event) {
              this.offsetX = this.positionX + event.offsetX;
              this.offsetY = this.positionY + event.offsetY;
            }
          })
          .onActionEnd((event: GestureEvent) => {
            this.positionX = this.offsetX;
            this.positionY = this.offsetY;
            console.info('Pan end');
            }))
          }
  }
}
```

### off('beforePanStart')<sup>19+</sup>

off(type: 'beforePanStart', callback?: PanListenerCallback): void

取消[on('beforePanStart')](#onbeforepanstart19)监听Pan手势[onActionStart](arkui-ts/ts-basic-gestures-pangesture.md#事件)事件执行前的callback回调。

**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名   | 类型                                                        | 必填 | 说明                                                 |
| -------- | ----------------------------------------------------------- | ---- | ---------------------------------------------------- |
| type     | string                                                      | 是   | 监听事件，固定为'beforePanStart'，即Pan手势onActionStart事件执行前的指令下发情况。 |
| callback | [PanListenerCallback](#panlistenercallback19) | 否   | 需要被注销的回调函数。                               |

**示例：**

参考[on('beforePanStart')](#onbeforepanstart19)接口示例。

### on('afterPanStart')<sup>19+</sup>

on(type: 'afterPanStart', callback: PanListenerCallback): void

监听Pan手势[onActionStart](arkui-ts/ts-basic-gestures-pangesture.md#事件)事件执行后的指令下发情况，在onActionStart事件执行之后执行callback回调。支持手指滑动、鼠标滑动、鼠标滚轮和触摸板拖动，暂不支持屏幕朗读触控模式。

**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名   | 类型                                                        | 必填 | 说明                                                         |
| -------- | ----------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                                                      | 是   | 监听事件，固定为'afterPanStart'，用于监听Pan手势onActionStart事件执行后的指令下发情况，所注册回调将于Pan手势onActionStart事件触发后触发。 |
| callback | [PanListenerCallback](#panlistenercallback19) | 是   | 回调函数。可以获得Pan手势事件的GestureEvent，GestureRecognizer和组件的FrameNode。   |

**示例：**

参考[on('beforePanStart')](#onbeforepanstart19)接口示例

### off('afterPanStart')<sup>19+</sup>

off(type: 'afterPanStart', callback?: PanListenerCallback): void

取消[on('afterPanStart')](#onafterpanstart19)监听Pan手势[onActionStart](arkui-ts/ts-basic-gestures-pangesture.md#事件)事件执行后的callback回调。

**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名   | 类型                                                        | 必填 | 说明                                                 |
| -------- | ----------------------------------------------------------- | ---- | ---------------------------------------------------- |
| type     | string                                                      | 是   | 监听事件，固定为'afterPanStart'，即Pan手势onActionStart事件执行后的指令下发情况。 |
| callback | [PanListenerCallback](#panlistenercallback19) | 否   | 需要被注销的回调函数。                               |

**示例：**

参考[on('beforePanStart')](#onbeforepanstart19)接口示例

### on('beforePanEnd')<sup>19+</sup>

on(type: 'beforePanEnd', callback: PanListenerCallback): void

监听Pan手势[onActionEnd](arkui-ts/ts-basic-gestures-pangesture.md#事件)事件执行前的指令下发情况，在onActionEnd事件执行之前执行callback回调。支持手指滑动、鼠标滑动、鼠标滚轮和触摸板拖动，暂不支持屏幕朗读触控模式。

**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名   | 类型                                                        | 必填 | 说明                                                         |
| -------- | ----------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                                                      | 是   | 监听事件，固定为'beforePanEnd'，用于监听Pan手势onActionEnd事件执行前的指令下发情况，所注册回调将于Pan手势onActionEnd事件触发前触发。 |
| callback | [PanListenerCallback](#panlistenercallback19) | 是   | 回调函数。可以获得Pan手势事件的GestureEvent，GestureRecognizer和组件的FrameNode。   |

**示例：**

参考[on('beforePanStart')](#onbeforepanstart19)接口示例

### off('beforePanEnd')<sup>19+</sup>

off(type: 'beforePanEnd', callback?: PanListenerCallback): void

取消[on('beforePanEnd')](#onbeforepanend19)监听Pan手势[onActionEnd](arkui-ts/ts-basic-gestures-pangesture.md#事件)事件执行前的callback回调。

**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名   | 类型                                                        | 必填 | 说明                                                 |
| -------- | ----------------------------------------------------------- | ---- | ---------------------------------------------------- |
| type     | string                                                      | 是   | 监听事件，固定为'beforePanEnd'，即Pan手势onActionEnd事件执行前的指令下发情况。 |
| callback | [PanListenerCallback](#panlistenercallback19) | 否   | 需要被注销的回调函数。                               |

**示例：**

参考[on('beforePanStart')](#onbeforepanstart19)接口示例

### on('afterPanEnd')<sup>19+</sup>

on(type: 'afterPanEnd', callback: PanListenerCallback): void

监听Pan手势[onActionEnd](arkui-ts/ts-basic-gestures-pangesture.md#事件)事件执行后的指令下发情况，在onActionEnd事件执行之后执行callback回调。支持手指滑动、鼠标滑动、鼠标滚轮和触摸板拖动，暂不支持屏幕朗读触控模式。

**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名   | 类型                                                        | 必填 | 说明                                                         |
| -------- | ----------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string                                                      | 是   | 监听事件，固定为'beforePanEnd'，用于监听Pan手势onActionEnd事件执行后的指令下发情况，所注册回调将于Pan手势onActionEnd事件触发后触发。 |
| callback | [PanListenerCallback](#panlistenercallback19) | 是   | 回调函数。可以获得Pan手势事件的GestureEvent，GestureRecognizer和组件的FrameNode。   |

**示例：**

参考[on('beforePanStart')](#onbeforepanstart19)接口示例

### off('afterPanEnd')<sup>19+</sup>

off(type: 'afterPanEnd', callback?: PanListenerCallback): void

取消[on('afterPanEnd')](#onafterpanend19)监听Pan手势[onActionEnd](arkui-ts/ts-basic-gestures-pangesture.md#事件)事件执行后的callback回调。

**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名   | 类型                                                        | 必填 | 说明                                                 |
| -------- | ----------------------------------------------------------- | ---- | ---------------------------------------------------- |
| type     | string                                                      | 是   | 监听事件，固定为'afterPanEnd'，即Pan手势onActionEnd事件执行后的指令下发情况。 |
| callback | [PanListenerCallback](#panlistenercallback19) | 否   | 需要被注销的回调函数。                               |

**示例：**

参考[on('beforePanStart')](#onbeforepanstart19)接口示例


## PanListenerCallback<sup>19+</sup>
type PanListenerCallback = (event: GestureEvent, current: GestureRecognizer, node?: FrameNode) => void

Pan手势事件监听函数类型。

**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名  | 类型              | 必填 | 说明                                |
| ------- | ----------------- | ---- | --------------------------------- |
| event   | [GestureEvent](../apis-arkui/arkui-ts/ts-gesture-settings.md#gestureevent对象说明)      | 是   | 触发事件监听的手势事件的相关信息。   |
| current | [GestureRecognizer](arkui-ts/ts-gesture-blocking-enhancement.md#gesturerecognizer) | 是   | 触发事件监听的手势识别器的相关信息。  |
| node    | [FrameNode](js-apis-arkui-frameNode.md#framenode)         | 否   | 触发事件监听的手势事件所绑定的组件。 |

## GestureEventListenerCallback<sup>12+</sup>
type GestureEventListenerCallback = (event: GestureEvent, node?: FrameNode) => void

ArkTS GestureEvent事件监听函数类型。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名  | 类型   | 必填 | 说明                          |
| ------- | ------ | ---- | --------------------------- |
| event | [GestureEvent](../apis-arkui/arkui-ts/ts-gesture-settings.md#gestureevent对象说明) | 是 | 触发事件监听的手势事件的相关信息。 |
| node | [FrameNode](js-apis-arkui-frameNode.md#framenode) | 否 | 触发事件监听的手势事件所绑定的组件。 |

## ClickEventListenerCallback<sup>12+</sup>
type ClickEventListenerCallback = (event: ClickEvent, node?: FrameNode) => void

ArkTS GestureEvent事件监听函数类型。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名  | 类型   | 必填 | 说明                          |
| ------- | ------ | ---- | --------------------------- |
| event | [ClickEvent](../apis-arkui/arkui-ts/ts-universal-events-click.md#clickevent对象说明) | 是 | 触发事件监听的点击事件的相关信息。 |
| node | [FrameNode](js-apis-arkui-frameNode.md#framenode) | 否 | 触发事件监听的点击事件所绑定的组件。 |

## MediaQuery

以下API需先使用UIContext中的[getMediaQuery()](#getmediaquery)方法获取到MediaQuery对象，再通过该对象调用对应方法。

### matchMediaSync

matchMediaSync(condition: string): mediaQuery.MediaQueryListener

设置媒体查询的查询条件，并返回对应的监听句柄。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名       | 类型     | 必填   | 说明                                       |
| --------- | ------ | ---- | ---------------------------------------- |
| condition | string | 是    | 媒体事件的匹配条件，具体可参考[媒体查询语法规则](../../ui/arkts-layout-development-media-query.md#语法规则)。 |

**返回值：**

| 类型                                                         | 说明                                         |
| ------------------------------------------------------------ | -------------------------------------------- |
| [mediaQuery.MediaQueryListener](js-apis-mediaquery.md#mediaquerylistener) | 媒体事件监听句柄，用于注册和去注册监听回调。 |

**示例：**

完整示例请参考[mediaquery示例](js-apis-mediaquery.md#示例)。

## Router

以下API需先使用UIContext中的[getRouter()](#getrouter)方法获取到Router对象，再通过该对象调用对应方法。

### pushUrl

pushUrl(options: router.RouterOptions): Promise&lt;void&gt;

跳转到应用内的指定页面，通过Promise获取跳转异常的返回结果。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名     | 类型                                       | 必填   | 说明        |
| ------- | ---------------------------------------- | ---- | --------- |
| options | [router.RouterOptions](js-apis-router.md#routeroptions) | 是    | 跳转页面描述信息。 |

**返回值：**

| 类型                  | 说明      |
| ------------------- | ------- |
| Promise&lt;void&gt; | 返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.router(页面路由)](errorcode-router.md)错误码。

| 错误码ID  | 错误信息                               |
| ------ | ---------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001 | Internal error. |
| 100002 | Uri error. The URI of the page to redirect is incorrect or does not exist.           |
| 100003 | Page stack error. Too many pages are pushed.  |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  async routePage() {
    this.getUIContext().getRouter().pushUrl({
        url: 'pages/routerpage2',
        params: {
          data1: 'message',
          data2: {
            data3: [123, 456, 789]
          }
        }
      })
      .then(() => {
        console.info('succeeded');
      })
      .catch((error: BusinessError) => {
        console.error(`pushUrl failed, code is ${error.code}, message is ${error.message}`);
      })
  }

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Button() {
        Text('next page')
          .fontSize(25)
          .fontWeight(FontWeight.Bold)
      }.type(ButtonType.Capsule)
      .margin({ top: 20 })
      .backgroundColor('#ccc')
      .onClick(() => {
        this.routePage();
      })
    }
    .width('100%')
    .height('100%')
  }
}
```

### pushUrl

pushUrl(options: router.RouterOptions, callback: AsyncCallback&lt;void&gt;): void

跳转到应用内的指定页面。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名      | 类型                                       | 必填   | 说明        |
| -------- | ---------------------------------------- | ---- | --------- |
| options  | [router.RouterOptions](js-apis-router.md#routeroptions) | 是    | 跳转页面描述信息。 |
| callback | AsyncCallback&lt;void&gt;                | 是    | 异常响应回调。   |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.router(页面路由)](errorcode-router.md)错误码。

| 错误码ID  | 错误信息                               |
| ------ | ---------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001 | Internal error. |
| 100002 | Uri error. The URI of the page to redirect is incorrect or does not exist.           |
| 100003 | Page stack error. Too many pages are pushed.  |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  async routePage() {
    this.getUIContext().getRouter().pushUrl({
      url: 'pages/routerpage2',
      params: {
        data1: 'message',
        data2: {
          data3: [123, 456, 789]
        }
      }
    }, (err: Error) => {
      if (err) {
        let message = (err as BusinessError).message;
        let code = (err as BusinessError).code;
        console.error(`pushUrl failed, code is ${code}, message is ${message}`);
        return;
      }
      console.info('pushUrl success');
    })
  }

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Button() {
        Text('next page')
          .fontSize(25)
          .fontWeight(FontWeight.Bold)
      }.type(ButtonType.Capsule)
      .margin({ top: 20 })
      .backgroundColor('#ccc')
      .onClick(() => {
        this.routePage();
      })
    }
    .width('100%')
    .height('100%')
  }
}
```

### pushUrl

pushUrl(options: router.RouterOptions, mode: router.RouterMode): Promise&lt;void&gt;

跳转到应用内的指定页面，通过Promise获取跳转异常的返回结果。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名     | 类型                                       | 必填   | 说明         |
| ------- | ---------------------------------------- | ---- | ---------- |
| options | [router.RouterOptions](js-apis-router.md#routeroptions) | 是    | 跳转页面描述信息。  |
| mode    | [router.RouterMode](js-apis-router.md#routermode9) | 是    | 跳转页面使用的模式。 |

**返回值：**

| 类型                  | 说明      |
| ------------------- | ------- |
| Promise&lt;void&gt; | 返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.router(页面路由)](errorcode-router.md)错误码。

| 错误码ID  | 错误信息                               |
| ------ | ---------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001 | Internal error. |
| 100002 | Uri error. The URI of the page to redirect is incorrect or does not exist.           |
| 100003 | Page stack error. Too many pages are pushed.  |

**示例：**

```ts
class RouterTmp {
  Standard: router.RouterMode = router.RouterMode.Standard;
}

let rtm: RouterTmp = new RouterTmp();

@Entry
@Component
struct Index {
  async routePage() {
    this.getUIContext().getRouter().pushUrl({
        url: 'pages/routerpage2',
        params: {
          data1: 'message',
          data2: {
            data3: [123, 456, 789]
          }
        }
      }, rtm.Standard)
      .then(() => {
        console.info('succeeded');
      })
      .catch((error: BusinessError) => {
        console.error(`pushUrl failed, code is ${error.code}, message is ${error.message}`);
      })
  }

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Button() {
        Text('next page')
          .fontSize(25)
          .fontWeight(FontWeight.Bold)
      }.type(ButtonType.Capsule)
      .margin({ top: 20 })
      .backgroundColor('#ccc')
      .onClick(() => {
        this.routePage();
      })
    }
    .width('100%')
    .height('100%')
  }
}
```

### pushUrl

pushUrl(options: router.RouterOptions, mode: router.RouterMode, callback: AsyncCallback&lt;void&gt;): void

跳转到应用内的指定页面。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名      | 类型                                       | 必填   | 说明         |
| -------- | ---------------------------------------- | ---- | ---------- |
| options  | [router.RouterOptions](js-apis-router.md#routeroptions) | 是    | 跳转页面描述信息。  |
| mode     | [router.RouterMode](js-apis-router.md#routermode9) | 是    | 跳转页面使用的模式。 |
| callback | AsyncCallback&lt;void&gt;                | 是    | 异常响应回调。    |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.router(页面路由)](errorcode-router.md)错误码。

| 错误码ID  | 错误信息                               |
| ------ | ---------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001 | Internal error. |
| 100002 | Uri error. The URI of the page to redirect is incorrect or does not exist.           |
| 100003 | Page stack error. Too many pages are pushed.  |

**示例：**

```ts
import { router } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

class RouterTmp {
  Standard: router.RouterMode = router.RouterMode.Standard;
}

let rtm: RouterTmp = new RouterTmp();

@Entry
@Component
struct Index {
  async routePage() {
    this.getUIContext().getRouter().pushUrl({
      url: 'pages/routerpage2',
      params: {
        data1: 'message',
        data2: {
          data3: [123, 456, 789]
        }
      }
    }, rtm.Standard, (err) => {
      if (err) {
        let message = (err as BusinessError).message;
        let code = (err as BusinessError).code;
        console.error(`pushUrl failed, code is ${code}, message is ${message}`);
        return;
      }
      console.info('pushUrl success');
    })
  }

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Button() {
        Text('next page')
          .fontSize(25)
          .fontWeight(FontWeight.Bold)
      }.type(ButtonType.Capsule)
      .margin({ top: 20 })
      .backgroundColor('#ccc')
      .onClick(() => {
        this.routePage();
      })
    }
    .width('100%')
    .height('100%')
  }
}
```

### replaceUrl

replaceUrl(options: router.RouterOptions): Promise&lt;void&gt;

用应用内的某个页面替换当前页面，并销毁被替换的页面，通过Promise获取跳转异常的返回的结果。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名     | 类型                                       | 必填   | 说明        |
| ------- | ---------------------------------------- | ---- | --------- |
| options | [router.RouterOptions](js-apis-router.md#routeroptions) | 是    | 替换页面描述信息。 |

**返回值：**

| 类型                  | 说明      |
| ------------------- | ------- |
| Promise&lt;void&gt; | 返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.router(页面路由)](errorcode-router.md)错误码。

| 错误码ID  | 错误信息                                     |
| ------ | ---------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001 | The UI execution context is not found. This error code is thrown only in the standard system. |
| 200002 | Uri error. The URI of the page to be used for replacement is incorrect or does not exist.                 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  async routePage() {
    this.getUIContext().getRouter().replaceUrl({
        url: 'pages/detail',
        params: {
          data1: 'message'
        }
      })
      .then(() => {
        console.info('succeeded');
      })
      .catch((error: BusinessError) => {
        console.error(`pushUrl failed, code is ${error.code}, message is ${error.message}`);
      })
  }

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Button() {
        Text('next page')
          .fontSize(25)
          .fontWeight(FontWeight.Bold)
      }.type(ButtonType.Capsule)
      .margin({ top: 20 })
      .backgroundColor('#ccc')
      .onClick(() => {
        this.routePage();
      })
    }
    .width('100%')
    .height('100%')
  }
}
```

### replaceUrl

replaceUrl(options: router.RouterOptions, callback: AsyncCallback&lt;void&gt;): void

用应用内的某个页面替换当前页面，并销毁被替换的页面。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名      | 类型                                       | 必填   | 说明        |
| -------- | ---------------------------------------- | ---- | --------- |
| options  | [router.RouterOptions](js-apis-router.md#routeroptions) | 是    | 替换页面描述信息。 |
| callback | AsyncCallback&lt;void&gt;                | 是    | 异常响应回调。   |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.router(页面路由)](errorcode-router.md)错误码。

| 错误码ID  | 错误信息                                     |
| ------ | ---------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001 | The UI execution context is not found. This error code is thrown only in the standard system. |
| 200002 | Uri error. The URI of the page to be used for replacement is incorrect or does not exist. |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  async routePage() {
    this.getUIContext().getRouter().replaceUrl({
      url: 'pages/detail',
      params: {
        data1: 'message'
      }
    }, (err: Error) => {
      if (err) {
        let message = (err as BusinessError).message;
        let code = (err as BusinessError).code;
        console.error(`replaceUrl failed, code is ${code}, message is ${message}`);
        return;
      }
      console.info('replaceUrl success');
    })
  }

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Button() {
        Text('next page')
          .fontSize(25)
          .fontWeight(FontWeight.Bold)
      }.type(ButtonType.Capsule)
      .margin({ top: 20 })
      .backgroundColor('#ccc')
      .onClick(() => {
        this.routePage();
      })
    }
    .width('100%')
    .height('100%')
  }
}
```

### replaceUrl

replaceUrl(options: router.RouterOptions, mode: router.RouterMode): Promise&lt;void&gt;

用应用内的某个页面替换当前页面，并销毁被替换的页面，通过Promise获取跳转异常的返回结果。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名     | 类型                                       | 必填   | 说明         |
| ------- | ---------------------------------------- | ---- | ---------- |
| options | [router.RouterOptions](js-apis-router.md#routeroptions) | 是    | 替换页面描述信息。  |
| mode    | [router.RouterMode](js-apis-router.md#routermode9) | 是    | 跳转页面使用的模式。 |

**返回值：**

| 类型                  | 说明      |
| ------------------- | ------- |
| Promise&lt;void&gt; | 返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.router(页面路由)](errorcode-router.md)错误码。

| 错误码ID  | 错误信息                                     |
| ------ | ---------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001 | Failed to get the delegate. This error code is thrown only in the standard system. |
| 200002 | Uri error. The URI of the page to be used for replacement is incorrect or does not exist.                 |

**示例：**

```ts
import { router } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

class RouterTmp {
  Standard: router.RouterMode = router.RouterMode.Standard;
}

let rtm: RouterTmp = new RouterTmp();

@Entry
@Component
struct Index {
  async routePage() {
    this.getUIContext().getRouter().replaceUrl({
        url: 'pages/detail',
        params: {
          data1: 'message'
        }
      }, rtm.Standard)
      .then(() => {
        console.info('succeeded');
      })
      .catch((error: BusinessError) => {
        console.error(`pushUrl failed, code is ${error.code}, message is ${error.message}`);
      })
  }

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Button() {
        Text('next page')
          .fontSize(25)
          .fontWeight(FontWeight.Bold)
      }.type(ButtonType.Capsule)
      .margin({ top: 20 })
      .backgroundColor('#ccc')
      .onClick(() => {
        this.routePage();
      })
    }
    .width('100%')
    .height('100%')
  }
}
```

### replaceUrl

replaceUrl(options: router.RouterOptions, mode: router.RouterMode, callback: AsyncCallback&lt;void&gt;): void

用应用内的某个页面替换当前页面，并销毁被替换的页面。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名      | 类型                                       | 必填   | 说明         |
| -------- | ---------------------------------------- | ---- | ---------- |
| options  | [router.RouterOptions](js-apis-router.md#routeroptions) | 是    | 替换页面描述信息。  |
| mode     | [router.RouterMode](js-apis-router.md#routermode9) | 是    | 跳转页面使用的模式。 |
| callback | AsyncCallback&lt;void&gt;                | 是    | 异常响应回调。    |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.router(页面路由)](errorcode-router.md)错误码。

| 错误码ID  | 错误信息                                     |
| ------ | ---------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001 | The UI execution context is not found. This error code is thrown only in the standard system. |
| 200002 | Uri error. The URI of the page to be used for replacement is incorrect or does not exist.               |

**示例：**

```ts
import { router } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

class RouterTmp {
  Standard: router.RouterMode = router.RouterMode.Standard;
}

let rtm: RouterTmp = new RouterTmp();

@Entry
@Component
struct Index {
  async routePage() {
    this.getUIContext().getRouter().replaceUrl({
      url: 'pages/detail',
      params: {
        data1: 'message'
      }
    }, rtm.Standard, (err: Error) => {
      if (err) {
        let message = (err as BusinessError).message;
        let code = (err as BusinessError).code;
        console.error(`replaceUrl failed, code is ${code}, message is ${message}`);
        return;
      }
      console.info('replaceUrl success');
    });
  }

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Button() {
        Text('next page')
          .fontSize(25)
          .fontWeight(FontWeight.Bold)
      }.type(ButtonType.Capsule)
      .margin({ top: 20 })
      .backgroundColor('#ccc')
      .onClick(() => {
        this.routePage();
      })
    }
    .width('100%')
    .height('100%')
  }
}
```

### pushNamedRoute

pushNamedRoute(options: router.NamedRouterOptions): Promise&lt;void&gt;

跳转到指定的命名路由页面，通过Promise获取跳转异常的返回结果。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名     | 类型                                       | 必填   | 说明        |
| ------- | ---------------------------------------- | ---- | --------- |
| options | [router.NamedRouterOptions](js-apis-router.md#namedrouteroptions10) | 是    | 跳转页面描述信息。 |

**返回值：**

| 类型                  | 说明      |
| ------------------- | ------- |
| Promise&lt;void&gt; | 返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.router(页面路由)](errorcode-router.md)错误码。

| 错误码ID  | 错误信息                               |
| ------ | ---------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001 | Internal error. |
| 100003 | Page stack error. Too many pages are pushed.  |
| 100004 | Named route error. The named route does not exist.   |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  async routePage() {
    this.getUIContext().getRouter().pushNamedRoute({
        name: 'myPage',
        params: {
          data1: 'message',
          data2: {
            data3: [123, 456, 789]
          }
        }
      })
      .then(() => {
        console.info('succeeded');
      })
      .catch((error: BusinessError) => {
        console.error(`pushUrl failed, code is ${error.code}, message is ${error.message}`);
      })
  }

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Button() {
        Text('next page')
          .fontSize(25)
          .fontWeight(FontWeight.Bold)
      }.type(ButtonType.Capsule)
      .margin({ top: 20 })
      .backgroundColor('#ccc')
      .onClick(() => {
        this.routePage();
      })
    }
    .width('100%')
    .height('100%')
  }
}
```

### pushNamedRoute

pushNamedRoute(options: router.NamedRouterOptions, callback: AsyncCallback&lt;void&gt;): void

跳转到指定的命名路由页面。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名      | 类型                                       | 必填   | 说明        |
| -------- | ---------------------------------------- | ---- | --------- |
| options  | [router.NamedRouterOptions](js-apis-router.md#namedrouteroptions10) | 是    | 跳转页面描述信息。 |
| callback | AsyncCallback&lt;void&gt;                | 是    | 异常响应回调。   |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.router(页面路由)](errorcode-router.md)错误码。

| 错误码ID  | 错误信息                               |
| ------ | ---------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001 | Internal error. |
| 100003 | Page stack error. Too many pages are pushed.  |
| 100004 | Named route error. The named route does not exist.  |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  async routePage() {
    this.getUIContext().getRouter().pushNamedRoute({
      name: 'myPage',
      params: {
        data1: 'message',
        data2: {
          data3: [123, 456, 789]
        }
      }
    }, (err: Error) => {
      if (err) {
        let message = (err as BusinessError).message;
        let code = (err as BusinessError).code;
        console.error(`pushNamedRoute failed, code is ${code}, message is ${message}`);
        return;
      }
      console.info('pushNamedRoute success');
    })
  }

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Button() {
        Text('next page')
          .fontSize(25)
          .fontWeight(FontWeight.Bold)
      }.type(ButtonType.Capsule)
      .margin({ top: 20 })
      .backgroundColor('#ccc')
      .onClick(() => {
        this.routePage();
      })
    }
    .width('100%')
    .height('100%')
  }
}
```
### pushNamedRoute

pushNamedRoute(options: router.NamedRouterOptions, mode: router.RouterMode): Promise&lt;void&gt;

跳转到指定的命名路由页面，通过Promise获取跳转异常的返回结果。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名     | 类型                                       | 必填   | 说明         |
| ------- | ---------------------------------------- | ---- | ---------- |
| options | [router.NamedRouterOptions](js-apis-router.md#namedrouteroptions10) | 是    | 跳转页面描述信息。  |
| mode    | [router.RouterMode](js-apis-router.md#routermode9) | 是    | 跳转页面使用的模式。 |

**返回值：**

| 类型                  | 说明      |
| ------------------- | ------- |
| Promise&lt;void&gt; | 返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.router(页面路由)](errorcode-router.md)错误码。

| 错误码ID  | 错误信息                               |
| ------ | ---------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001 | Internal error. |
| 100003 | Page stack error. Too many pages are pushed.  |
| 100004 | Named route error. The named route does not exist.  |

**示例：**

```ts
import { router } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

class RouterTmp{
  Standard:router.RouterMode = router.RouterMode.Standard;
}
let rtm:RouterTmp = new RouterTmp();

@Entry
@Component
struct Index {
  async routePage() {
    this.getUIContext().getRouter().pushNamedRoute({
        name: 'myPage',
        params: {
          data1: 'message',
          data2: {
            data3: [123, 456, 789]
          }
        }
      }, rtm.Standard)
      .then(() => {
        console.info('succeeded');
      })
      .catch((error: BusinessError) => {
        console.error(`pushUrl failed, code is ${error.code}, message is ${error.message}`);
      })
  }

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Button() {
        Text('next page')
          .fontSize(25)
          .fontWeight(FontWeight.Bold)
      }.type(ButtonType.Capsule)
      .margin({ top: 20 })
      .backgroundColor('#ccc')
      .onClick(() => {
        this.routePage();
      })
    }
    .width('100%')
    .height('100%')
  }
}
```

### pushNamedRoute

pushNamedRoute(options: router.NamedRouterOptions, mode: router.RouterMode, callback: AsyncCallback&lt;void&gt;): void

跳转到指定的命名路由页面。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名      | 类型                                       | 必填   | 说明         |
| -------- | ---------------------------------------- | ---- | ---------- |
| options  | [router.NamedRouterOptions](js-apis-router.md#namedrouteroptions10) | 是    | 跳转页面描述信息。  |
| mode     | [router.RouterMode](js-apis-router.md#routermode9) | 是    | 跳转页面使用的模式。 |
| callback | AsyncCallback&lt;void&gt;                | 是    | 异常响应回调。    |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.router(页面路由)](errorcode-router.md)错误码。

| 错误码ID  | 错误信息                               |
| ------ | ---------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001 | Internal error. |
| 100003 | Page stack error. Too many pages are pushed.  |
| 100004 | Named route error. The named route does not exist.   |

**示例：**

```ts
import { router } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

class RouterTmp {
  Standard: router.RouterMode = router.RouterMode.Standard;
}

let rtm: RouterTmp = new RouterTmp();

@Entry
@Component
struct Index {
  async routePage() {
    this.getUIContext().getRouter().pushNamedRoute({
      name: 'myPage',
      params: {
        data1: 'message',
        data2: {
          data3: [123, 456, 789]
        }
      }
    }, rtm.Standard, (err: Error) => {
      if (err) {
        let message = (err as BusinessError).message;
        let code = (err as BusinessError).code;
        console.error(`pushNamedRoute failed, code is ${code}, message is ${message}`);
        return;
      }
      console.info('pushNamedRoute success');
    })
  }

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Button() {
        Text('next page')
          .fontSize(25)
          .fontWeight(FontWeight.Bold)
      }.type(ButtonType.Capsule)
      .margin({ top: 20 })
      .backgroundColor('#ccc')
      .onClick(() => {
        this.routePage();
      })
    }
    .width('100%')
    .height('100%')
  }
}
```

### replaceNamedRoute

replaceNamedRoute(options: router.NamedRouterOptions): Promise&lt;void&gt;

用指定的命名路由页面替换当前页面，并销毁被替换的页面，通过Promise获取跳转异常的返回结果。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名     | 类型                                       | 必填   | 说明        |
| ------- | ---------------------------------------- | ---- | --------- |
| options | [router.NamedRouterOptions](js-apis-router.md#namedrouteroptions10) | 是    | 替换页面描述信息。 |

**返回值：**

| 类型                  | 说明      |
| ------------------- | ------- |
| Promise&lt;void&gt; | 返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.router(页面路由)](errorcode-router.md)错误码。

| 错误码ID  | 错误信息                                     |
| ------ | ---------------------------------------- |
| 401      | if the number of parameters is less than 1 or the type of the url parameter is not string. |
| 100001 | The UI execution context is not found. This error code is thrown only in the standard system. |
| 100004 | Named route error. The named route does not exist.        |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  async routePage() {
    this.getUIContext().getRouter().replaceNamedRoute({
        name: 'myPage',
        params: {
          data1: 'message'
        }
      })
      .then(() => {
        console.info('succeeded');
      })
      .catch((error: BusinessError) => {
        console.error(`pushUrl failed, code is ${error.code}, message is ${error.message}`);
      })
  }

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Button() {
        Text('next page')
          .fontSize(25)
          .fontWeight(FontWeight.Bold)
      }.type(ButtonType.Capsule)
      .margin({ top: 20 })
      .backgroundColor('#ccc')
      .onClick(() => {
        this.routePage();
      })
    }
    .width('100%')
    .height('100%')
  }
}
```

### replaceNamedRoute

replaceNamedRoute(options: router.NamedRouterOptions, callback: AsyncCallback&lt;void&gt;): void

用指定的命名路由页面替换当前页面，并销毁被替换的页面。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名      | 类型                                       | 必填   | 说明        |
| -------- | ---------------------------------------- | ---- | --------- |
| options  | [router.NamedRouterOptions](js-apis-router.md#namedrouteroptions10) | 是    | 替换页面描述信息。 |
| callback | AsyncCallback&lt;void&gt;                | 是    | 异常响应回调。   |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.router(页面路由)](errorcode-router.md)错误码。

| 错误码ID  | 错误信息                                     |
| ------ | ---------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001 | The UI execution context is not found. This error code is thrown only in the standard system. |
| 100004 | Named route error. The named route does not exist.         |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  async routePage() {
    this.getUIContext().getRouter().replaceNamedRoute({
      name: 'myPage',
      params: {
        data1: 'message'
      }
    }, (err: Error) => {
      if (err) {
        let message = (err as BusinessError).message;
        let code = (err as BusinessError).code;
        console.error(`replaceNamedRoute failed, code is ${code}, message is ${message}`);
        return;
      }
      console.info('replaceNamedRoute success');
    })
  }

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Button() {
        Text('next page')
          .fontSize(25)
          .fontWeight(FontWeight.Bold)
      }.type(ButtonType.Capsule)
      .margin({ top: 20 })
      .backgroundColor('#ccc')
      .onClick(() => {
        this.routePage();
      })
    }
    .width('100%')
    .height('100%')
  }
}
```

### replaceNamedRoute

replaceNamedRoute(options: router.NamedRouterOptions, mode: router.RouterMode): Promise&lt;void&gt;

用指定的命名路由页面替换当前页面，并销毁被替换的页面，通过Promise获取跳转异常的返回结果。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名     | 类型                                       | 必填   | 说明         |
| ------- | ---------------------------------------- | ---- | ---------- |
| options | [router.NamedRouterOptions](js-apis-router.md#namedrouteroptions10) | 是    | 替换页面描述信息。  |
| mode    | [router.RouterMode](js-apis-router.md#routermode9) | 是    | 跳转页面使用的模式。 |


**返回值：**

| 类型                  | 说明      |
| ------------------- | ------- |
| Promise&lt;void&gt; | 返回结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.router(页面路由)](errorcode-router.md)错误码。

| 错误码ID  | 错误信息                                     |
| ------ | ---------------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001 | Failed to get the delegate. This error code is thrown only in the standard system. |
| 100004 | Named route error. The named route does not exist.       |

**示例：**

```ts
import { router } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

class RouterTmp {
  Standard: router.RouterMode = router.RouterMode.Standard;
}

let rtm: RouterTmp = new RouterTmp();

@Entry
@Component
struct Index {
  async routePage() {
    this.getUIContext().getRouter().replaceNamedRoute({
        name: 'myPage',
        params: {
          data1: 'message'
        }
      }, rtm.Standard)
      .then(() => {
        console.info('succeeded');
      })
      .catch((error: BusinessError) => {
        console.error(`pushUrl failed, code is ${error.code}, message is ${error.message}`);
      })
  }

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Button() {
        Text('next page')
          .fontSize(25)
          .fontWeight(FontWeight.Bold)
      }.type(ButtonType.Capsule)
      .margin({ top: 20 })
      .backgroundColor('#ccc')
      .onClick(() => {
        this.routePage();
      })
    }
    .width('100%')
    .height('100%')
  }
}
```

### replaceNamedRoute

replaceNamedRoute(options: router.NamedRouterOptions, mode: router.RouterMode, callback: AsyncCallback&lt;void&gt;): void

用指定的命名路由页面替换当前页面，并销毁被替换的页面。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名      | 类型                                       | 必填   | 说明         |
| -------- | ---------------------------------------- | ---- | ---------- |
| options  | [router.NamedRouterOptions](js-apis-router.md#namedrouteroptions10) | 是    | 替换页面描述信息。  |
| mode     | [router.RouterMode](js-apis-router.md#routermode9) | 是    | 跳转页面使用的模式。 |
| callback | AsyncCallback&lt;void&gt;                | 是    | 异常响应回调。    |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.router(页面路由)](errorcode-router.md)错误码。

| 错误码ID  | 错误信息                                     |
| ------ | ---------------------------------------- |
| 401      | if the number of parameters is less than 1 or the type of the url parameter is not string. |
| 100001 | The UI execution context is not found. This error code is thrown only in the standard system. |
| 100004 | Named route error. The named route does not exist.        |

**示例：**

```ts
import { router } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

class RouterTmp {
  Standard: router.RouterMode = router.RouterMode.Standard;
}

let rtm: RouterTmp = new RouterTmp();

@Entry
@Component
struct Index {
  async routePage() {
    this.getUIContext().getRouter().replaceNamedRoute({
      name: 'myPage',
      params: {
        data1: 'message'
      }
    }, rtm.Standard, (err: Error) => {
      if (err) {
        let message = (err as BusinessError).message;
        let code = (err as BusinessError).code;
        console.error(`replaceNamedRoute failed, code is ${code}, message is ${message}`);
        return;
      }
      console.info('replaceNamedRoute success');
    })
  }

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Button() {
        Text('next page')
          .fontSize(25)
          .fontWeight(FontWeight.Bold)
      }.type(ButtonType.Capsule)
      .margin({ top: 20 })
      .backgroundColor('#ccc')
      .onClick(() => {
        this.routePage();
      })
    }
    .width('100%')
    .height('100%')
  }
}
```

### back

back(options?: router.RouterOptions ): void

返回上一页面或指定的页面。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名     | 类型                                       | 必填   | 说明                                       |
| ------- | ---------------------------------------- | ---- | ---------------------------------------- |
| options | [router.RouterOptions](js-apis-router.md#routeroptions) | 否    | 返回页面描述信息，其中参数url指路由跳转时会返回到指定url的界面，如果页面栈上没有url页面，则不响应该情况。如果url未设置，则返回上一页，页面不会重新构建，页面栈里面的page不会回收，出栈后会被回收。 |

**示例：**

完整示例请参考[PushUrl](#pushurl)中的示例。

<!--code_no_check-->
```ts
import { Router , UIContext } from '@kit.ArkUI';
let uiContext: UIContext = this.getUIContext();
let router: Router = uiContext.getRouter();
router.back({url:'pages/detail'});    
```

### back<sup>12+</sup>

back(index: number, params?: Object): void

返回指定的页面。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名     | 类型                              | 必填   | 说明         |
| ------- | ------------------------------- | ---- | ---------- |
| index | number | 是    | 跳转目标页面的索引值。 <br/> 取值范围：[0, +∞) |
| params    | Object      | 否    | 页面返回时携带的参数。 |

**示例：**

完整示例请参考[PushUrl](#pushurl)中的示例。

<!--code_no_check-->
```ts
import { Router , UIContext } from '@kit.ArkUI';
let uiContext: UIContext = this.getUIContext();

let router: Router = uiContext.getRouter();
router.back(1);
```

完整示例请参考[PushUrl](#pushurl)中的示例。

<!--code_no_check-->
```ts
import { Router , UIContext } from '@kit.ArkUI';
let uiContext: UIContext = this.getUIContext();

let router: Router = uiContext.getRouter();
router.back(1, {info:'来自Home页'}); //携带参数返回
```

### clear

clear(): void

清空页面栈中的所有历史页面，仅保留当前页面作为栈顶页面。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

完整示例请参考[PushUrl](#pushurl)中的示例。

<!--code_no_check-->
```ts
import { Router , UIContext } from '@kit.ArkUI';
let uiContext: UIContext = this.getUIContext();

let router: Router = uiContext.getRouter();
router.clear();    
```

### getLength

getLength(): string

获取当前在页面栈内的页面数量。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型     | 说明                 |
| ------ | ------------------ |
| string | 页面数量，页面栈支持最大数值是32。 |

**示例：**

完整示例请参考[PushUrl](#pushurl)中的示例。

<!--code_no_check-->
```ts
import { Router , UIContext } from '@kit.ArkUI';
let uiContext: UIContext = this.getUIContext();

let router: Router = uiContext.getRouter();
let size = router.getLength();        
console.info('pages stack size = ' + size);    
```

### getState

getState(): router.RouterState

获取当前页面的状态信息。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型                                       | 说明      |
| ---------------------------------------- | ------- |
| router.[RouterState](js-apis-router.md#routerstate) | 页面状态信息。 |

**示例：**

完整示例请参考[PushUrl](#pushurl)中的示例。

<!--code_no_check-->
```ts
import { Router , UIContext } from '@kit.ArkUI';
let uiContext: UIContext = this.getUIContext();

let router: Router = uiContext.getRouter();
let page = router.getState();
console.info('current index = ' + page.index);
console.info('current name = ' + page.name);
console.info('current path = ' + page.path);
```

### getStateByIndex<sup>12+</sup>

getStateByIndex(index: number): router.RouterState | undefined

通过索引值获取对应页面的状态信息。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名     | 类型                              | 必填   | 说明         |
| ------- | ------------------------------- | ---- | ---------- |
| index    | number | 是   | 表示要获取的页面索引。 <br/> 取值范围：[0, +∞) |

**返回值：**

| 类型                          | 说明      |
| --------------------------- | ------- |
| router.[RouterState](js-apis-router.md#routerstate) \| undefined | 返回页面状态信息。索引不存在时返回undefined。 |

**示例：** 

完整示例请参考[PushUrl](#pushurl)中的示例。

<!--code_no_check-->
```ts
import { Router , UIContext } from '@kit.ArkUI';
let uiContext: UIContext = this.getUIContext();

let router: Router = uiContext.getRouter();
let options: router.RouterState | undefined = router.getStateByIndex(1);
if (options != undefined) {
  console.info('index = ' + options.index);
  console.info('name = ' + options.name);
  console.info('path = ' + options.path);
  console.info('params = ' + options.params);
}
```
### getStateByUrl<sup>12+</sup>

getStateByUrl(url: string): Array<router.[RouterState](js-apis-router.md#routerstate)>

通过url获取当前页面的状态信息。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名     | 类型                              | 必填   | 说明         |
| ------- | ------------------------------- | ---- | ---------- |
| url    | string | 是   | 表示要获取对应页面信息的url。  |

**返回值：**

| 类型                          | 说明      |
| --------------------------- | ------- |
| Array<router.[RouterState](js-apis-router.md#routerstate)> | 页面状态信息。 |

**示例：** 

完整示例请参考[PushUrl](#pushurl)中的示例。

<!--code_no_check-->
```ts
import { Router , UIContext } from '@kit.ArkUI';
let uiContext: UIContext = this.getUIContext();
let router: Router = uiContext.getRouter();
let options:Array<router.RouterState> = router.getStateByUrl('pages/index');
for (let i: number = 0; i < options.length; i++) {
  console.info('index = ' + options[i].index);
  console.info('name = ' + options[i].name);
  console.info('path = ' + options[i].path);
  console.info('params = ' + options[i].params);
}
```

### showAlertBeforeBackPage

showAlertBeforeBackPage(options: router.EnableAlertOptions): void

开启页面返回询问对话框。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名     | 类型                                       | 必填   | 说明        |
| ------- | ---------------------------------------- | ---- | --------- |
| options | [router.EnableAlertOptions](js-apis-router.md#enablealertoptions) | 是    | 文本弹窗信息描述。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.router(页面路由)](errorcode-router.md)错误码。

| 错误码ID  | 错误信息                               |
| ------ | ---------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001 | Internal error. |

**示例：**

完整示例请参考[PushUrl](#pushurl)中的示例。

<!--code_no_check-->
```ts
import { Router , UIContext } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';
let uiContext: UIContext = this.getUIContext();
let router: Router = uiContext.getRouter();
try {
  router.showAlertBeforeBackPage({            
    message: 'Message Info'        
  });
} catch(error) {
  let message = (error as BusinessError).message;
  let code = (error as BusinessError).code;
  console.error(`showAlertBeforeBackPage failed, code is ${code}, message is ${message}`);
}
```

### hideAlertBeforeBackPage

hideAlertBeforeBackPage(): void

禁用页面返回询问对话框。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

完整示例请参考[PushUrl](#pushurl)中的示例。

<!--code_no_check-->
```ts
import { Router , UIContext } from '@kit.ArkUI';
let uiContext: UIContext = this.getUIContext();

let router: Router = uiContext.getRouter();
router.hideAlertBeforeBackPage();    
```

### getParams

getParams(): Object

获取发起跳转的页面往当前页传入的参数。

> **说明：**
>
> getParams只获取当前页面的参数，并不会清除页面关联的参数。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型     | 说明                |
| ------ | ----------------- |
| Object | 发起跳转的页面往当前页传入的参数。 |

**示例：**

完整示例请参考[PushUrl](#pushurl)中的示例。

<!--code_no_check-->
```ts
import { Router , UIContext } from '@kit.ArkUI';
let uiContext: UIContext = this.getUIContext();

let router: Router = uiContext.getRouter();
router.getParams();
```

## CustomBuilderWithId<sup>18+</sup>

type CustomBuilderWithId = (id: number)&nbsp;=&gt;&nbsp;void

组件属性、方法参数可使用CustomBuilderWithId类型来自定义UI描述，并且可以指定组件ID生成用户自定义组件。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| id | number | 是 | 组件ID |

## TargetInfo<sup>18+</sup>

指定组件绑定的目标节点。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 名称 | 类型 | 只读 | 可选 | 说明 |
| -------- | -------- | -------- | -------- | -------- |
| id | string&nbsp;\|&nbsp;number | 否 | 否 | 指定popup或menu绑定的目标节点。<br/>**说明：** <br/>1. 当id是number时，对应组件实例的UniquelD，此id由系统保证唯一性。<br/>2. 当id是string时，对应[通用属性id](arkui-ts/ts-universal-attributes-component-id.md#id)所指定的组件，此id的唯一性需由开发者确保，但实际可能会有多个。 |
| componentId | number | 否 | 是 | 目标节点所在的自定义组件的UniquelD。当上述id指定为string类型时，可通过此属性圈定范围。方便开发者在一定范围内保证id: string的唯一性。 |

## PromptAction

以下API需先使用UIContext中的[getPromptAction()](#getpromptaction)方法获取到PromptAction对象，再通过该对象调用对应方法。

### showToast

showToast(options: promptAction.ShowToastOptions): void

创建并显示文本提示框。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名     | 类型                                       | 必填   | 说明      |
| ------- | ---------------------------------------- | ---- | ------- |
| options | [promptAction.ShowToastOptions](js-apis-promptAction.md#showtoastoptions) | 是    | 文本弹窗选项。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.promptAction(弹窗)](errorcode-promptAction.md)错误码。

| 错误码ID  | 错误信息                               |
| ------ | ---------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001 | Internal error. |

**示例：**

该示例通过调用showToast接口，显示文本提示框。

```ts
import { PromptAction } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  promptAction: PromptAction = this.getUIContext().getPromptAction();

  build() {
    Column() {
      Button('showToast')
        .onClick(() => {
          try {
            this.promptAction.showToast({
              message: 'Message Info',
              duration: 2000
            });
          } catch (error) {
            let message = (error as BusinessError).message;
            let code = (error as BusinessError).code;
            console.error(`showToast args error code is ${code}, message is ${message}`);
          };
        })
    }.height('100%').width('100%').justifyContent(FlexAlign.Center)
  }
}
```

### openToast<sup>18+</sup>

openToast(options: promptAction.ShowToastOptions): Promise&lt;number&gt;

显示文本提示框并通过Promise返回其id。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名  | 类型                                                         | 必填 | 说明           |
| ------- | ------------------------------------------------------------ | ---- | -------------- |
| options | [promptAction.ShowToastOptions](js-apis-promptAction.md#showtoastoptions) | 是   | 文本弹窗选项。 |

**返回值**

| 类型             | 说明                                 |
| ---------------- | ------------------------------------ |
| Promise&lt;number&gt; | 返回供closeToast使用的文本提示框id。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.promptAction(弹窗)](errorcode-promptAction.md)错误码。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed. |
| 100001   | Internal error.                                              |

**示例：**

该示例通过调用openToast和closeToast接口，展示了弹出以及关闭文本提示框的功能。

```ts
import { PromptAction } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  @State toastId: number = 0;
  promptAction: PromptAction = this.getUIContext().getPromptAction();

  build() {
    Column() {
      Button('Open Toast')
        .height(100)
        .onClick(() => {
          this.promptAction.openToast({
            message: 'Toast Message',
            duration: 10000,
          }).then((toastId: number) => {
            this.toastId = toastId;
          })
            .catch((error: BusinessError) => {
              console.error(`openToast error code is ${error.code}, message is ${error.message}`);
            })
        })
      Blank().height(50)
      Button('Close Toast')
        .height(100)
        .onClick(() => {
          try {
            this.promptAction.closeToast(this.toastId);
          } catch (error) {
            let message = (error as BusinessError).message;
            let code = (error as BusinessError).code;
            console.error(`CloseToast error code is ${code}, message is ${message}`);
          };
        })
    }.height('100%').width('100%').justifyContent(FlexAlign.Center)
  }
}
```

### closeToast<sup>18+</sup>

closeToast(toastId: number): void

关闭文本提示框。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数**

| 参数名  | 类型   | 必填 | 说明                          |
| ------- | ------ | ---- | ----------------------------- |
| toastId | number | 是   | openToast返回的文本提示框id。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.promptAction(弹窗)](errorcode-promptAction.md)错误码。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed. |
| 100001   | Internal error.                                              |

**示例：**

示例请看[openToast18](#opentoast18)的示例。

### showDialog

showDialog(options: promptAction.ShowDialogOptions, callback: AsyncCallback&lt;promptAction.ShowDialogSuccessResponse&gt;): void

创建并显示对话框，对话框响应结果异步返回。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：**  SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名      | 类型                                       | 必填   | 说明           |
| -------- | ---------------------------------------- | ---- | ------------ |
| options  | [promptAction.ShowDialogOptions](js-apis-promptAction.md#showdialogoptions) | 是    | 页面显示对话框信息描述。 |
| callback | AsyncCallback&lt;[promptAction.ShowDialogSuccessResponse](js-apis-promptAction.md#showdialogsuccessresponse)&gt; | 是    | 对话框响应结果回调。   |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.promptAction(弹窗)](errorcode-promptAction.md)错误码。

| 错误码ID  | 错误信息                               |
| ------ | ---------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001 | Internal error. |

**示例：**

该示例通过调用showDialog接口，展示了弹出对话框以及返回对话框响应结果的功能。

```ts
import { PromptAction } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  promptAction: PromptAction = this.getUIContext().getPromptAction();

  build() {
    Column() {
      Button('showDialog')
        .onClick(() => {
          try {
            this.promptAction.showDialog({
              title: 'showDialog Title Info',
              message: 'Message Info',
              buttons: [
                {
                  text: 'button1',
                  color: '#000000'
                },
                {
                  text: 'button2',
                  color: '#000000'
                }
              ]
            }, (err, data) => {
              if (err) {
                console.error('showDialog err: ' + err);
                return;
              }
              console.info('showDialog success callback, click button: ' + data.index);
            });
          } catch (error) {
            let message = (error as BusinessError).message;
            let code = (error as BusinessError).code;
            console.error(`showDialog args error code is ${code}, message is ${message}`);
          };
        })
    }.height('100%').width('100%').justifyContent(FlexAlign.Center)
  }
}
```

### showDialog

showDialog(options: promptAction.ShowDialogOptions): Promise&lt;promptAction.ShowDialogSuccessResponse&gt;

创建并显示对话框，通过Promise获取对话框响应结果。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：**  SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名     | 类型                                       | 必填   | 说明     |
| ------- | ---------------------------------------- | ---- | ------ |
| options | [promptAction.ShowDialogOptions](js-apis-promptAction.md#showdialogoptions) | 是    | 对话框选项。 |

**返回值：**

| 类型                                       | 说明       |
| ---------------------------------------- | -------- |
| Promise&lt;[promptAction.ShowDialogSuccessResponse](js-apis-promptAction.md#showdialogsuccessresponse)&gt; | 对话框响应结果。 |

**错误码：**

以下错误码的详细介绍请参见[ 通用错误码](../errorcode-universal.md)和[ohos.promptAction(弹窗)](errorcode-promptAction.md)错误码。

| 错误码ID  | 错误信息                               |
| ------ | ---------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001 | Internal error. |

**示例：**

该示例通过调用showDialog接口，展示了弹出对话框以及通过Promise获取对话框响应结果的功能。

```ts
import { PromptAction } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  promptAction: PromptAction = this.getUIContext().getPromptAction();

  build() {
    Column() {
      Button('showDialog')
        .onClick(() => {
          this.promptAction.showDialog({
            title: 'Title Info',
            message: 'Message Info',
            buttons: [
              {
                text: 'button1',
                color: '#000000'
              },
              {
                text: 'button2',
                color: '#000000'
              }
            ],
          })
            .then(data => {
              console.info('showDialog success, click button: ' + data.index);
            })
            .catch((err: Error) => {
              console.error('showDialog error: ' + err);
            })
        })
    }.height('100%').width('100%').justifyContent(FlexAlign.Center)
  }
}
```

### showActionMenu<sup>11+</sup>

showActionMenu(options: promptAction.ActionMenuOptions, callback: AsyncCallback&lt;[promptAction.ActionMenuSuccessResponse](js-apis-promptAction.md#actionmenusuccessresponse)&gt;): void

创建并显示操作菜单，菜单响应结果异步返回。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明               |
| -------- | ------------------------------------------------------------ | ---- | ------------------ |
| options  | [promptAction.ActionMenuOptions](js-apis-promptAction.md#actionmenuoptions) | 是   | 操作菜单选项。     |
| callback | AsyncCallback&lt;[promptAction.ActionMenuSuccessResponse](js-apis-promptAction.md#actionmenusuccessresponse)&gt; | 是   | 菜单响应结果回调。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.promptAction(弹窗)](errorcode-promptAction.md)错误码。

| 错误码ID | 错误信息                           |
| -------- | ---------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001   | Internal error. |

**示例：**

```ts
import { PromptAction, promptAction } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  promptAction: PromptAction = this.getUIContext().getPromptAction();

  build() {
    Column() {
      Button('showActionMenu')
        .onClick(() => {
          try {
            this.promptAction.showActionMenu({
              title: 'Title Info',
              buttons: [
                {
                  text: 'item1',
                  color: '#666666'
                },
                {
                  text: 'item2',
                  color: '#000000'
                }
              ]
            }, (err: BusinessError, data: promptAction.ActionMenuSuccessResponse) => {
              if (err) {
                console.error('showDialog err: ' + err);
                return;
              }
              console.info('showDialog success callback, click button: ' + data.index);
            });
          } catch (error) {
            let message = (error as BusinessError).message;
            let code = (error as BusinessError).code;
            console.error(`showActionMenu args error code is ${code}, message is ${message}`);
          };
        })
    }.height('100%').width('100%').justifyContent(FlexAlign.Center)
  }
}
```

### showActionMenu<sup>(deprecated)</sup>

showActionMenu(options: promptAction.ActionMenuOptions, callback: [promptAction.ActionMenuSuccessResponse](js-apis-promptAction.md#actionmenusuccessresponse)): void

创建并显示操作菜单，菜单响应结果异步返回。

从API version11开始不再维护，建议使用[showActionMenu](#showactionmenu11)。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full。

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明               |
| -------- | ------------------------------------------------------------ | ---- | ------------------ |
| options  | [promptAction.ActionMenuOptions](js-apis-promptAction.md#actionmenuoptions) | 是   | 操作菜单选项。     |
| callback | [promptAction.ActionMenuSuccessResponse](js-apis-promptAction.md#actionmenusuccessresponse) | 是   | 菜单响应结果回调。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.promptAction(弹窗)](errorcode-promptAction.md)错误码。

| 错误码ID  | 错误信息                               |
| ------ | ---------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001 | Internal error. |

**示例：**

```ts
import { PromptAction } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  promptAction: PromptAction = this.getUIContext().getPromptAction();

  build() {
    Column() {
      Button('showActionMenu')
        .onClick(() => {
          try {
            this.promptAction.showActionMenu({
              title: 'Title Info',
              buttons: [
                {
                  text: 'item1',
                  color: '#666666'
                },
                {
                  text: 'item2',
                  color: '#000000'
                }
              ]
            }, { index:0 });
          } catch (error) {
            let message = (error as BusinessError).message;
            let code = (error as BusinessError).code;
            console.error(`showActionMenu args error code is ${code}, message is ${message}`);
          };
        })
    }.height('100%').width('100%').justifyContent(FlexAlign.Center)
  }
}
```

### showActionMenu

showActionMenu(options: promptAction.ActionMenuOptions): Promise&lt;promptAction.ActionMenuSuccessResponse&gt;

创建并显示操作菜单，通过Promise获取菜单响应结果。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名     | 类型                                       | 必填   | 说明      |
| ------- | ---------------------------------------- | ---- | ------- |
| options | [promptAction.ActionMenuOptions](js-apis-promptAction.md#actionmenuoptions) | 是    | 操作菜单选项。 |

**返回值：**

| 类型                                       | 说明      |
| ---------------------------------------- | ------- |
| Promise&lt;[promptAction.ActionMenuSuccessResponse](js-apis-promptAction.md#actionmenusuccessresponse)&gt; | 菜单响应结果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.promptAction(弹窗)](errorcode-promptAction.md)错误码。

| 错误码ID  | 错误信息                               |
| ------ | ---------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001 | Internal error. |

**示例：**

该示例通过调用showActionMenu接口，展示了弹出操作菜单以及通过Promise获取菜单响应结果的功能。

```ts
import { PromptAction } from '@kit.ArkUI';
@Entry
@Component
struct Index {
  promptAction: PromptAction = this.getUIContext().getPromptAction();

  build() {
    Column() {
      Button('showActionMenu')
        .onClick(() => {
          this.promptAction.showActionMenu({
            title: 'showActionMenu Title Info',
            buttons: [
              {
                text: 'item1',
                color: '#666666'
              },
              {
                text: 'item2',
                color: '#000000'
              },
            ]
          })
            .then(data => {
              console.info('showActionMenu success, click button: ' + data.index);
            })
            .catch((err: Error) => {
              console.error('showActionMenu error: ' + err);
            })
        })
    }.height('100%').width('100%').justifyContent(FlexAlign.Center)
  }
}
```

### openCustomDialog<sup>12+</sup>

openCustomDialog\<T extends Object>(dialogContent: ComponentContent\<T>, options?: promptAction.BaseDialogOptions): Promise&lt;void&gt;

创建并弹出dialogContent对应的自定义弹窗，使用Promise异步回调。通过该接口弹出的弹窗内容样式完全按照dialogContent中设置的样式显示，即相当于customDialog设置customStyle为true时的显示效果。暂不支持[isModal](js-apis-promptAction.md#basedialogoptions11) = true与[showInSubWindow](js-apis-promptAction.md#basedialogoptions11) = true同时使用。如果同时设置为true时，则只生效showInSubWindow = true。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名     | 类型                                       | 必填   | 说明      |
| ------- | ---------------------------------------- | ---- | ------- |
| dialogContent | [ComponentContent\<T>](./js-apis-arkui-ComponentContent.md) | 是 | 自定义弹窗中显示的组件内容。 |
| options | [promptAction.BaseDialogOptions](js-apis-promptAction.md#basedialogoptions11) | 否    |   弹窗样式。 |

**返回值：**

| 类型                                       | 说明      |
| ---------------------------------------- | ------- |
|   Promise&lt;void&gt;           |    返回Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.promptAction(弹窗)](errorcode-promptAction.md)错误码。

| 错误码ID  | 错误信息                               |
| ------ | ---------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 103301 | The ComponentContent is incorrect. |
| 103302 | Dialog content already exists.|

**示例：**

该示例通过监听[系统环境信息](../apis-ability-kit/js-apis-app-ability-configuration.md)（系统语言、深浅色等）的变化，调用[ComponentContent\<T>](./js-apis-arkui-ComponentContent.md) 的[update](../apis-arkui/js-apis-arkui-builderNode.md#update)和[updateConfiguration](../apis-arkui/js-apis-arkui-builderNode.md#updateconfiguration12)实现自定义弹窗的数据更新及节点的全量刷新。
```ts
import { ComponentContent } from '@kit.ArkUI';
import { AbilityConstant, Configuration, EnvironmentCallback, ConfigurationConstant } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { resourceManager } from '@kit.LocalizationKit';

class Params {
  text: string = "";
  colorMode: resourceManager.ColorMode = resourceManager.ColorMode.LIGHT

  constructor(text: string, colorMode: resourceManager.ColorMode) {
    this.text = text
    this.colorMode = colorMode
  }
}

@Builder
function BuilderDialog(params: Params) {
  Column() {
    Text(params.text)
      .fontSize(50)
      .fontWeight(FontWeight.Bold)
      .margin({ bottom: 36 })
  }.backgroundColor(params.colorMode == resourceManager.ColorMode.LIGHT ? "#D5D5D5" : "#004AAF")
}

@Entry
@Component
struct Index {
  @State message: string = "hello";
  contentNode: ComponentContent<Params> | null = null;
  callbackId: number | undefined = 0;

  aboutToAppear(): void {
    let environmentCallback: EnvironmentCallback = {
      onMemoryLevel: (level: AbilityConstant.MemoryLevel): void => {
      },
      onConfigurationUpdated: (config: Configuration): void => {
        console.log("onConfigurationUpdated " + JSON.stringify(config));
        this.getUIContext().getHostContext()?.getApplicationContext().resourceManager.getConfiguration((err,
          config) => {
          // 调用ComponentContent的update更新colorMode信息
          this.contentNode?.update(new Params(this.message, config.colorMode))
          setTimeout(() => {
            // 调用ComponentContent的updateConfiguration，触发节点的全量更新
            this.contentNode?.updateConfiguration()
          })
        })
      }
    }
    // 注册监听系统环境变化监听器
    this.callbackId =
      this.getUIContext().getHostContext()?.getApplicationContext().on('environment', environmentCallback)
    // 设置应用深浅色跟随系统
    this.getUIContext()
      .getHostContext()?.getApplicationContext().setColorMode(ConfigurationConstant.ColorMode.COLOR_MODE_NOT_SET)
  }

  aboutToDisappear() {
    // 解注册监听系统环境变化的回调
    this.getUIContext().getHostContext()?.getApplicationContext().off('environment', this.callbackId)
    this.contentNode?.dispose()
  }

  build() {
    Row() {
      Column() {
        Button("click me")
          .onClick(() => {
            let uiContext = this.getUIContext();
            let promptAction = uiContext.getPromptAction();
            if (this.contentNode == null && uiContext.getHostContext() != undefined) {
              this.contentNode = new ComponentContent(uiContext, wrapBuilder(BuilderDialog), new Params(this.message,
                uiContext.getHostContext()!!.getApplicationContext().resourceManager.getConfigurationSync().colorMode))
            }
            if (this.contentNode == null) {
              return
            }
            promptAction.closeCustomDialog(this.contentNode)
            promptAction.openCustomDialog(this.contentNode).then(() => {
              console.info("succeeded")
            }).catch((error: BusinessError) => {
              console.error(`OpenCustomDialog args error code is ${error.code}, message is ${error.message}`);
            })
          })
      }
      .width('100%')
      .height('100%')
    }
    .height('100%')
  }
}
```

### openCustomDialogWithController<sup>18+</sup>

openCustomDialogWithController\<T extends Object>(dialogContent: ComponentContent\<T>, controller: promptAction.DialogController, options?: promptAction.BaseDialogOptions): Promise&lt;void&gt;

创建并弹出dialogContent对应的自定义弹窗，使用Promise异步回调。支持传入弹窗控制器与自定义弹窗绑定，后续可以通过控制器控制自定义弹窗。

通过该接口弹出的弹窗内容样式完全按照dialogContent中设置的样式显示，即相当于customDialog设置customStyle为true时的显示效果。

暂不支持[isModal](js-apis-promptAction.md#basedialogoptions11) = true与[showInSubWindow](js-apis-promptAction.md#basedialogoptions11) = true同时使用。如果同时设置为true时，则只生效showInSubWindow = true。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名     | 类型                                       | 必填   | 说明      |
| ------- | ---------------------------------------- | ---- | ------- |
| dialogContent | [ComponentContent\<T>](./js-apis-arkui-ComponentContent.md) | 是 | 自定义弹窗中显示的组件内容。 |
| controller | [promptAction.DialogController](js-apis-promptAction.md#dialogcontroller18) | 是 | 自定义弹窗的控制器。 |
| options | [promptAction.BaseDialogOptions](js-apis-promptAction.md#basedialogoptions11) | 否    | 自定义弹窗的样式。 |

**返回值：**

| 类型                                       | 说明      |
| ---------------------------------------- | ------- |
|   Promise&lt;void&gt;           |    返回Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.promptAction(弹窗)](errorcode-promptAction.md)错误码。

| 错误码ID  | 错误信息                               |
| ------ | ---------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 103301 | The ComponentContent is incorrect. |
| 103302 | Dialog content already exists.|

**示例：**

该示例通过调用openCustomDialog接口，展示了支持传入弹窗控制器与自定义弹窗绑定的功能。

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { ComponentContent, promptAction } from '@kit.ArkUI';

class Params {
  text: string = "";
  dialogController: promptAction.DialogController = new promptAction.DialogController();

  constructor(text: string, dialogController: promptAction.DialogController) {
    this.text = text;
    this.dialogController = dialogController;
  }
}

@Builder
function buildText(params: Params) {
  Column() {
    Text(params.text)
      .fontSize(50)
      .fontWeight(FontWeight.Bold)
      .margin({ bottom: 36 })
    Button('点我关闭弹窗：通过外部传递的DialogController')
      .onClick(() => {
        if (params.dialogController != undefined) {
          params.dialogController.close();
        }
      })
  }.backgroundColor('#FFF0F0F0')
}

@Entry
@ComponentV2
struct Index {
  @Local message: string = "hello";
  private dialogController: promptAction.DialogController = new promptAction.DialogController();

  build() {
    Row() {
      Column() {
        Button("click me")
          .onClick(() => {
            let uiContext = this.getUIContext();
            let promptAction = uiContext.getPromptAction();
            let contentNode = new ComponentContent(uiContext, wrapBuilder(buildText),
              new Params(this.message, this.dialogController));
            promptAction.openCustomDialogWithController(contentNode, this.dialogController)
              .then(() => {
                console.info('succeeded');
              })
              .catch((error: BusinessError) => {
                console.error(`OpenCustomDialogWithController args error code is ${error.code}, message is ${error.message}`);
              })
          })
      }
      .width('100%')
      .height('100%')
    }
    .height('100%')
  }
}
```

### closeCustomDialog<sup>12+</sup>

closeCustomDialog\<T extends Object>(dialogContent: ComponentContent\<T>): Promise&lt;void&gt;

关闭已弹出的dialogContent对应的自定义弹窗，使用Promise异步回调。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名     | 类型                                       | 必填   | 说明      |
| ------- | ---------------------------------------- | ---- | ------- |
| dialogContent | [ComponentContent\<T>](./js-apis-arkui-ComponentContent.md) | 是 | 自定义弹窗中显示的组件内容。 |

**返回值：**

| 类型                                       | 说明      |
| ---------------------------------------- | ------- |
|   Promise&lt;void&gt;           |    返回Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.promptAction(弹窗)](errorcode-promptAction.md)错误码。

| 错误码ID  | 错误信息                               |
| ------ | ---------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 103301 | The ComponentContent is incorrect. |
| 103303 | The ComponentContent cannot be found. |

**示例：**

该示例通过调用closeCustomDialog接口，关闭已弹出的dialogContent对应的自定义弹窗。

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { ComponentContent } from '@kit.ArkUI';

class Params {
  text: string = "";

  constructor(text: string) {
    this.text = text;
  }
}

@Builder
function buildText(params: Params) {
  Column() {
    Text(params.text)
      .fontSize(50)
      .fontWeight(FontWeight.Bold)
      .margin({ bottom: 36 })
  }.backgroundColor('#FFF0F0F0')
}

@Entry
@Component
struct Index {
  @State message: string = "hello";

  build() {
    Row() {
      Column() {
        Button("click me")
          .onClick(() => {
            let uiContext = this.getUIContext();
            let promptAction = uiContext.getPromptAction();
            let contentNode = new ComponentContent(uiContext, wrapBuilder(buildText), new Params(this.message));
            promptAction.openCustomDialog(contentNode)
              .then(() => {
                console.info('succeeded');
              })
              .catch((error: BusinessError) => {
                console.error(`OpenCustomDialog args error code is ${error.code}, message is ${error.message}`);
              })
            setTimeout(() => {
              promptAction.closeCustomDialog(contentNode)
                .then(() => {
                  console.info('succeeded');
                })
                .catch((error: BusinessError) => {
                  console.error(`OpenCustomDialog args error code is ${error.code}, message is ${error.message}`);
                })
            }, 2000); //2秒后自动关闭
          })
      }
      .width('100%')
      .height('100%')
    }
    .height('100%')
  }
}
```

### updateCustomDialog<sup>12+</sup>

updateCustomDialog\<T extends Object>(dialogContent: ComponentContent\<T>, options: promptAction.BaseDialogOptions): Promise&lt;void&gt;

更新已弹出的dialogContent对应的自定义弹窗的样式，使用Promise异步回调。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名     | 类型                                       | 必填   | 说明      |
| ------- | ---------------------------------------- | ---- | ------- |
| dialogContent | [ComponentContent\<T>](./js-apis-arkui-ComponentContent.md) | 是 | 自定义弹窗中显示的组件内容。 |
| options | [promptAction.BaseDialogOptions](js-apis-promptAction.md#basedialogoptions11) | 是    |   弹窗样式，目前仅支持更新alignment、offset、autoCancel、maskColor。 |

**返回值：**

| 类型                                       | 说明      |
| ---------------------------------------- | ------- |
|   Promise&lt;void&gt;           |    返回Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.promptAction(弹窗)](errorcode-promptAction.md)错误码。

| 错误码ID  | 错误信息                               |
| ------ | ---------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 103301 | The ComponentContent is incorrect. |
| 103303 | The ComponentContent cannot be found. |

**示例：**

该示例通过调用updateCustomDialog接口，动态调整已弹出自定义弹窗的位置。

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { ComponentContent } from '@kit.ArkUI';

class Params {
  text: string = "";

  constructor(text: string) {
    this.text = text;
  }
}

@Builder
function buildText(params: Params) {
  Column() {
    Text(params.text)
      .fontSize(50)
      .fontWeight(FontWeight.Bold)
      .margin({ bottom: 36 })
  }.backgroundColor('#FFF0F0F0')
}

@Entry
@Component
struct Index {
  @State message: string = "hello";

  build() {
    Row() {
      Column() {
        Button("click me")
          .onClick(() => {
            let uiContext = this.getUIContext();
            let promptAction = uiContext.getPromptAction();
            let contentNode = new ComponentContent(uiContext, wrapBuilder(buildText), new Params(this.message));
            promptAction.openCustomDialog(contentNode)
              .then(() => {
                console.info('succeeded');
              })
              .catch((error: BusinessError) => {
                console.error(`updateCustomDialog args error code is ${error.code}, message is ${error.message}`);
              })

            setTimeout(() => {
              promptAction.updateCustomDialog(contentNode, { alignment: DialogAlignment.CenterEnd })
                .then(() => {
                  console.info('succeeded');
                })
                .catch((error: BusinessError) => {
                  console.error(`updateCustomDialog args error code is ${error.code}, message is ${error.message}`);
                })
            }, 2000); //2秒后自动更新弹窗位置
          })
      }
      .width('100%')
      .height('100%')
    }
    .height('100%')
  }
}
```

### openCustomDialog<sup>12+</sup>

openCustomDialog(options: promptAction.CustomDialogOptions): Promise\<number>

创建并弹出自定义弹窗。通过Promise异步回调返回供closeCustomDialog使用的对话框id。暂不支持isModal = true与showInSubWindow = true同时使用。如果同时设置为true时，则只生效showInSubWindow = true。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名  | 类型                                                         | 必填 | 说明               |
| ------- | ------------------------------------------------------------ | ---- | ------------------ |
| options | [promptAction.CustomDialogOptions](js-apis-promptAction.md#customdialogoptions11) | 是   | 自定义弹窗的内容。 |

**返回值：**

| 类型                | 说明                                    |
| ------------------- | --------------------------------------- |
| Promise&lt;number&gt; | 返回供closeCustomDialog使用的对话框id。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.promptAction(弹窗)](errorcode-promptAction.md)错误码。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed. |
| 100001   | Internal error.                                              |

### presentCustomDialog<sup>18+</sup>

presentCustomDialog(builder: CustomBuilder \| CustomBuilderWithId, controller?: promptAction.DialogController, options?: promptAction.DialogOptions): Promise\<number>

创建并弹出自定义弹窗。通过Promise异步回调返回供closeCustomDialog使用的对话框id。

支持在自定义弹窗内容中持有弹窗ID进行对应操作。支持传入弹窗控制器与自定义弹窗绑定，后续可以通过控制器控制自定义弹窗。

暂不支持isModal = true与showInSubWindow = true同时使用。如果同时设置为true时，则只生效showInSubWindow = true。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名  | 类型                                                         | 必填 | 说明               |
| ------- | ------------------------------------------------------------ | ---- | ------------------ |
| builder | [CustomBuilder](arkui-ts/ts-types.md#custombuilder8) \| [CustomBuilderWithId](#custombuilderwithid18) | 是   | 自定义弹窗的内容。 |
| controller | [promptAction.DialogController](js-apis-promptAction.md#dialogcontroller18) | 否 | 自定义弹窗的控制器。 |
| options | [promptAction.DialogOptions](js-apis-promptAction.md#dialogoptions18) | 否 | 自定义弹窗的样式。 |

**返回值：**

| 类型                | 说明                                    |
| ------------------- | --------------------------------------- |
| Promise&lt;number&gt; | 返回自定义弹窗ID。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.promptAction(弹窗)](errorcode-promptAction.md)错误码。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed. |
| 100001   | Internal error.                                              |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { PromptAction, promptAction } from '@kit.ArkUI';

@Entry
@ComponentV2
struct Index {
  @Local message: string = "hello";
  private ctx: UIContext = this.getUIContext();
  private promptAction: PromptAction = this.ctx.getPromptAction();
  private dialogController: promptAction.DialogController = new promptAction.DialogController();

  private customDialogComponentId: number = 0;
  @Builder customDialogComponent() {
    Column() {
      Text(this.message).fontSize(30)
      Row({ space: 10 }) {
        Button("通过DialogId关闭").onClick(() => {
          this.promptAction.closeCustomDialog(this.customDialogComponentId);
        })
        Button("通过DialogController关闭").onClick(() => {
          this.dialogController.close();
        })
      }
    }.height(200).padding(5).justifyContent(FlexAlign.SpaceBetween)
  }

  @Builder customDialogComponentWithId(dialogId: number) {
    Column() {
      Text(this.message).fontSize(30)
      Row({ space: 10 }) {
        Button("通过DialogId关闭").onClick(() => {
          this.promptAction.closeCustomDialog(dialogId);
        })
        Button("通过DialogController关闭").onClick(() => {
          this.dialogController.close();
        })
      }
    }.height(200).padding(5).justifyContent(FlexAlign.SpaceBetween)
  }

  build() {
    Row() {
      Column({ space: 10 }) {
        Button('presentCustomDialog')
          .fontSize(20)
          .onClick(() => {
            this.promptAction.presentCustomDialog(() => {
              this.customDialogComponent()
            }, this.dialogController)
              .then((dialogId: number) => {
                this.customDialogComponentId = dialogId;
              })
              .catch((err: BusinessError) => {
                console.error("presentCustomDialog error: " + err.code + " " + err.message);
              })
          })
        Button('presentCustomDialog with id')
          .fontSize(20)
          .onClick(() => {
            this.promptAction.presentCustomDialog((dialogId: number) => {
              this.customDialogComponentWithId(dialogId)
            }, this.dialogController)
              .catch((err: BusinessError) => {
                console.error("presentCustomDialog with id error: " + err.code + " " + err.message);
              })
          })
      }
      .width('100%')
      .height('100%')
    }
    .height('100%')
  }
}
```

### closeCustomDialog<sup>12+</sup>

closeCustomDialog(dialogId: number): void

关闭自定义弹窗。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名   | 类型   | 必填 | 说明                             |
| -------- | ------ | ---- | -------------------------------- |
| dialogId | number | 是   | openCustomDialog返回的对话框id。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.promptAction(弹窗)](errorcode-promptAction.md)错误码。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed. |
| 100001   | Internal error.                                              |

**示例：** 

```ts
import { PromptAction } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  promptAction: PromptAction = this.getUIContext().getPromptAction();
  private customDialogComponentId: number = 0;

  @Builder
  customDialogComponent() {
    Column() {
      Text('弹窗').fontSize(30)
      Row({ space: 50 }) {
        Button("确认").onClick(() => {
          this.promptAction.closeCustomDialog(this.customDialogComponentId);
        })
        Button("取消").onClick(() => {
          this.promptAction.closeCustomDialog(this.customDialogComponentId);
        })
      }
    }.height(200).padding(5).justifyContent(FlexAlign.SpaceBetween)
  }

  build() {
    Row() {
      Column() {
        Button("click me")
          .onClick(() => {
            this.promptAction.openCustomDialog({
              builder: () => {
                this.customDialogComponent()
              },
              onWillDismiss: (dismissDialogAction: DismissDialogAction) => {
                console.info("reason" + JSON.stringify(dismissDialogAction.reason));
                console.log("dialog onWillDismiss");
                if (dismissDialogAction.reason == DismissReason.PRESS_BACK) {
                  dismissDialogAction.dismiss();
                }
                if (dismissDialogAction.reason == DismissReason.TOUCH_OUTSIDE) {
                  dismissDialogAction.dismiss();
                }
              }
            }).then((dialogId: number) => {
              this.customDialogComponentId = dialogId;
            })
          })
      }
      .width('100%')
      .height('100%')
    }
    .height('100%')
  }
}
```

### getTopOrder<sup>18+</sup>

getTopOrder(): LevelOrder

返回最顶层显示的弹窗的顺序。

获取最顶层显示的弹窗的顺序，可以在下一个弹窗时指定期望的顺序。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型                | 说明                                    |
| ------------------- | --------------------------------------- |
| [LevelOrder](js-apis-promptAction.md#levelorder18) | 返回弹窗层级信息。 |

**示例：**

该示例通过调用getTopOrder接口，展示了获取最顶层显示弹窗顺序的功能。

```ts
import { ComponentContent, PromptAction, LevelOrder, promptAction, UIContext } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

class Params {
  text: string = "";
  constructor(text: string) {
    this.text = text;
  }
}

@Builder
function buildText(params: Params) {
  Column({ space: 20 }) {
    Text(params.text)
      .fontSize(50)
      .fontWeight(FontWeight.Bold)
      .margin({ bottom: 36 })
  }.backgroundColor('#FFF0F0F0')
}

@Entry
@Component
struct Index {
  @State message: string = '弹窗';
  private ctx: UIContext = this.getUIContext();
  private promptAction: PromptAction = this.ctx.getPromptAction();
  private contentNode: ComponentContent<Object> =
    new ComponentContent(this.ctx, wrapBuilder(buildText), new Params(this.message));

  private baseDialogOptions: promptAction.BaseDialogOptions = {
    showInSubWindow: false,
    levelOrder: LevelOrder.clamp(30.1),
  };

  build() {
    Row() {
      Column({ space: 10 }) {
        Button('openCustomDialog弹窗')
          .fontSize(20)
          .onClick(() => {
            this.promptAction.openCustomDialog(this.contentNode, this.baseDialogOptions)
              .catch((err: BusinessError) => {
                console.error("openCustomDialog error: " + err.code + " " + err.message);
              })
              .then(() => {
                let topOrder: LevelOrder = this.promptAction.getTopOrder();
                if (topOrder !== undefined) {
                  console.error('topOrder: ' + topOrder.getOrder());
                }
              })
          })
      }.width('100%')
    }.height('100%')
  }
}
```

### getBottomOrder<sup>18+</sup>

getBottomOrder(): LevelOrder

返回最底层显示的弹窗的顺序。

获取最底层显示的弹窗的顺序，可以在下一个弹窗时指定期望的顺序。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型                | 说明                                    |
| ------------------- | --------------------------------------- |
| [LevelOrder](js-apis-promptAction.md#levelorder18) | 返回弹窗层级信息。 |

**示例：**

该示例通过调用getBottomOrder接口，展示了获取最底层显示弹窗顺序的功能。

```ts
import { ComponentContent, PromptAction, LevelOrder, promptAction, UIContext } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

class Params {
  text: string = "";
  constructor(text: string) {
    this.text = text;
  }
}

@Builder
function buildText(params: Params) {
  Column({ space: 20 }) {
    Text(params.text)
      .fontSize(50)
      .fontWeight(FontWeight.Bold)
      .margin({ bottom: 36 })
  }.backgroundColor('#FFF0F0F0')
}

@Entry
@Component
struct Index {
  @State message: string = '弹窗';
  private ctx: UIContext = this.getUIContext();
  private promptAction: PromptAction = this.ctx.getPromptAction();
  private contentNode: ComponentContent<Object> =
    new ComponentContent(this.ctx, wrapBuilder(buildText), new Params(this.message));

  private baseDialogOptions: promptAction.BaseDialogOptions = {
    showInSubWindow: false,
    levelOrder: LevelOrder.clamp(30.1),
  };

  build() {
    Row() {
      Column({ space: 10 }) {
        Button('openCustomDialog弹窗')
          .fontSize(20)
          .onClick(() => {
            this.promptAction.openCustomDialog(this.contentNode, this.baseDialogOptions)
              .catch((err: BusinessError) => {
                console.error("openCustomDialog error: " + err.code + " " + err.message);
              })
              .then(() => {
                let bottomOrder: LevelOrder = this.promptAction.getBottomOrder();
                if (bottomOrder !== undefined) {
                  console.error('bottomOrder: ' + bottomOrder.getOrder());
                }
              })
          })
      }.width('100%')
    }.height('100%')
  }
}
```

### openPopup<sup>18+</sup>

openPopup\<T extends Object>(content: ComponentContent\<T>, target: TargetInfo, options?: PopupCommonOptions): Promise&lt;void&gt;

创建并弹出以content作为内容的Popup弹窗，使用Promise异步回调。

> **说明：**
>
> 1. 使用该接口时，若未传入有效的target，则无法弹出popup弹窗。
>
> 2. 由于[updatePopup](#updatepopup18)和[closePopup](#closepopup18)依赖content去更新或者关闭指定的popup弹窗，开发者需自行维护传入的content。
>
> 3. 如果在wrapBuilder中包含其他组件（例如：[Popup](arkui-ts/ohos-arkui-advanced-Popup.md#popup)、[Chip](arkui-ts/ohos-arkui-advanced-Chip.md#chip)组件），则[ComponentContent](./js-apis-arkui-ComponentContent.md#componentcontent-1)应采用带有四个参数的构造函数constructor，其中options参数应传递{ nestingBuilderSupported: true }。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名     | 类型                                       | 必填   | 说明      |
| ------- | ---------------------------------------- | ---- | ------- |
| content | [ComponentContent\<T>](./js-apis-arkui-ComponentContent.md) | 是 | popup弹窗中显示的组件内容。 |
| target | [TargetInfo](#targetinfo18) | 是 | 需要绑定组件的信息。 |
| options | [PopupCommonOptions](arkui-ts/ts-universal-attributes-popup.md#popupcommonoptions18类型说明) | 否 | popup弹窗样式。 |

**返回值：**

| 类型                                       | 说明      |
| ---------------------------------------- | ------- |
|   Promise&lt;void&gt;           |    返回Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.promptAction(弹窗)](errorcode-promptAction.md)错误码。

| 错误码ID  | 错误信息                               |
| ------ | ---------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 103301 | The ComponentContent is incorrect. |
| 103302 | The ComponentContent already exists. |
| 103304 | The targetId does not exist. |
| 103305 | The node of targetId is not in the component tree. |

**示例：**

该示例通过调用openPopuo、updatePopup和closePopup接口，展示了弹出、更新以及关闭Popup的功能。

```ts
import { ComponentContent, FrameNode } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

interface PopupParam {
  updateFunc?: () => void;
  closeFunc?: () => void;
}

export function showPopup(context: UIContext, uniqueId: number, contentNode: ComponentContent<PopupParam>,
  popupParam: PopupParam) {
  const promptAction = context.getPromptAction();
  let frameNode: FrameNode | null = context.getFrameNodeByUniqueId(uniqueId);
  let targetId = frameNode?.getFirstChild()?.getUniqueId();
  promptAction.openPopup(contentNode, { id: targetId }, {
    radius: 16,
    mask: { color: Color.Pink },
    enableArrow: true,
  })
    .then(() => {
      console.info('openPopup success');
    })
    .catch((err: BusinessError) => {
      console.error('openPopup error: ' + err.code + ' ' + err.message);
    })
  popupParam.updateFunc = () => {
    promptAction.updatePopup(contentNode, {
      enableArrow: false
    }, true)
      .then(() => {
        console.info('updatePopup success');
      })
      .catch((err: BusinessError) => {
        console.error('updatePopup error: ' + err.code + ' ' + err.message);
      })
  }
  popupParam.closeFunc = () => {
    promptAction.closePopup(contentNode)
      .then(() => {
        console.info('closePopup success');
      })
      .catch((err: BusinessError) => {
        console.error('closePopup error: ' + err.code + ' ' + err.message);
      })
  }
}

@Builder
function buildText(param?: PopupParam) {
  Column() {
    Text('popup')
    Button('Update Popup')
      .fontSize(20)
      .onClick(() => {
        param?.updateFunc?.();
      })
    Button('Close Popup')
      .fontSize(20)
      .onClick(() => {
        param?.closeFunc?.();
      })
  }
}

@Entry
@Component
struct Index {
  build() {
    Column() {
      Button('Open Popup')
        .fontSize(20)
        .onClick(() => {
          let context = this.getUIContext();
          const popupParam: PopupParam = {};
          const contentNode = new ComponentContent(context, wrapBuilder(buildText), popupParam);
          showPopup(context, this.getUniqueId(), contentNode, popupParam);
        })
    }
  }
}
```

### updatePopup<sup>18+</sup>

updatePopup\<T extends Object>(content: ComponentContent\<T>, options: PopupCommonOptions, partialUpdate?: boolean ): Promise&lt;void&gt;

更新content对应的Popup弹窗的样式，使用Promise异步回调。

> **说明：**
>
> 不支持更新showInSubWindow、focusable、onStateChange、onWillDismiss、transition。
>

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名     | 类型                                       | 必填   | 说明      |
| ------- | ---------------------------------------- | ---- | ------- |
| content | [ComponentContent\<T>](./js-apis-arkui-ComponentContent.md) | 是 | popup弹窗中显示的组件内容。 |
| options | [PopupCommonOptions](arkui-ts/ts-universal-attributes-popup.md#popupcommonoptions18类型说明) | 是 | popup弹窗样式。<br/>**说明：** <br/>不支持更新showInSubWindow、focusable、onStateChange、onWillDismiss、transition。 |
| partialUpdate | boolean | 否 | popup弹窗更新方式, 默认值为false。<br/>**说明：** <br/>1. true为增量更新，保留当前值，更新options中的指定属性。 <br/>2. false为全量更新，除options中的指定属性，其他属性恢复默认值。 |

**返回值：**

| 类型                                       | 说明      |
| ---------------------------------------- | ------- |
|   Promise&lt;void&gt;           |    返回Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.promptAction(弹窗)](errorcode-promptAction.md)错误码。

| 错误码ID  | 错误信息                               |
| ------ | ---------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 103301 | The ComponentContent is incorrect. |
| 103303 | The ComponentContent cannot be found. |

**示例：**

请参考[openPopup](#openpopup18)示例。

### closePopup<sup>18+</sup>

closePopup\<T extends Object>(content: ComponentContent\<T>): Promise&lt;void&gt;

关闭content对应的Popup弹窗，使用Promise异步回调。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名     | 类型                                       | 必填   | 说明      |
| ------- | ---------------------------------------- | ---- | ------- |
| content | [ComponentContent\<T>](./js-apis-arkui-ComponentContent.md) | 是 | popup弹窗中显示的组件内容。 |

**返回值：**

| 类型                                       | 说明      |
| ---------------------------------------- | ------- |
|   Promise&lt;void&gt;           |    返回Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.promptAction(弹窗)](errorcode-promptAction.md)错误码。

| 错误码ID  | 错误信息                               |
| ------ | ---------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 103301 | The ComponentContent is incorrect. |
| 103303 | The ComponentContent cannot be found. |

**示例：**

请参考[openPopup](#openpopup18)示例。

### openMenu<sup>18+</sup>

openMenu\<T extends Object>(content: ComponentContent\<T>, target: TargetInfo, options?: MenuOptions): Promise&lt;void&gt;

创建并弹出以content作为内容的Menu弹窗。使用Promise异步回调。

> **说明：**
>
> 1. 使用该接口时，若未传入有效的target，则无法弹出menu弹窗。
>
> 2. 由于[updateMenu](#updatemenu18)和[closeMenu](#closemenu18)依赖content去更新或者关闭指定的menu弹窗，开发者需自行维护传入的content。
>
> 3. 如果在wrapBuilder中包含其他组件（例如：[Popup](arkui-ts/ohos-arkui-advanced-Popup.md#popup)、[Chip](arkui-ts/ohos-arkui-advanced-Chip.md#chip)组件），则[ComponentContent](./js-apis-arkui-ComponentContent.md#componentcontent-1)应采用带有四个参数的构造函数constructor，其中options参数应传递{ nestingBuilderSupported: true }。
>
> 4. 子窗弹窗里不能再弹出子窗弹窗，例如[openMenu](#openmenu18)设置了showInSubWindow为true时，则不能再弹出另一个设置了showInSubWindow为true的弹窗。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名     | 类型                                       | 必填   | 说明      |
| ------- | ---------------------------------------- | ---- | ------- |
| content | [ComponentContent\<T>](./js-apis-arkui-ComponentContent.md) | 是 | menu弹窗中显示的组件内容。 |
| target | [TargetInfo](#targetinfo18) | 是 | 需要绑定组件的信息。 |
| options | [MenuOptions](./arkui-ts/ts-universal-attributes-menu.md#menuoptions10) | 否 | menu弹窗样式。<br/>**说明：**<br/>title属性不生效。<br/>preview参数仅支持设置MenuPreviewMode类型。 |

**返回值：**

| 类型                                       | 说明      |
| ---------------------------------------- | ------- |
|   Promise&lt;void&gt;           |    返回Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.promptAction(弹窗)](errorcode-promptAction.md)错误码。

| 错误码ID  | 错误信息                               |
| ------ | ---------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 103301 | The ComponentContent is incorrect. |
| 103302 | The ComponentContent already exists. |
| 103304 | The targetId does not exist. |
| 103305 | The node of targetId is not in the component tree. |

**示例：**

该示例通过调用openMenu接口，展示了弹出Menu的功能。

```ts
import { ComponentContent, FrameNode } from '@kit.ArkUI';

export function doSomething(context: UIContext, uniqueId: number, contentNode: ComponentContent<Object>) {
  showMenu(context, uniqueId, contentNode);
}

@Builder
function MyMenu() {
  Column() {
    Menu() {
      MenuItem({ startIcon: $r("app.media.startIcon"), content: "菜单选项1" })
      MenuItem({ startIcon: $r("app.media.startIcon"), content: "菜单选项2" })
    }
  }
  .width('80%')
  .padding('20lpx')
}

export function showMenu(context: UIContext, uniqueId: number, contentNode: ComponentContent<Object>) {
  const promptAction = context.getPromptAction();
  let frameNode: FrameNode | null = context.getFrameNodeByUniqueId(uniqueId);
  let frameNodeTarget = frameNode?.getFirstChild();
  frameNodeTarget = frameNodeTarget?.getChild(0);
  let targetId = frameNodeTarget?.getUniqueId();
  promptAction.openMenu(contentNode, { id: targetId }, {
    enableArrow: true,
  });
}

@Entry
@Component
struct Index {
  build() {
    Column() {
      Button('OpenMenu', { type: ButtonType.Normal, stateEffect: true })
        .borderRadius('16lpx')
        .width('80%')
        .margin(10)
        .onClick(() => {
          let context = this.getUIContext();
          const contentNode = new ComponentContent(context, wrapBuilder(MyMenu));
          doSomething(context, this.getUniqueId(), contentNode);
        })
    }
  }
}
```

### updateMenu<sup>18+</sup>

updateMenu\<T extends Object>(content: ComponentContent\<T>, options: MenuOptions, partialUpdate?: boolean ): Promise&lt;void&gt;

更新content对应的Menu弹窗的样式。使用Promise异步回调。

> **说明：**
>
> 不支持更新showInSubWindow、preview、previewAnimationOptions、transition、onAppear、aboutToAppear、onDisappear、aboutToDisappear。
>

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名     | 类型                                       | 必填   | 说明      |
| ------- | ---------------------------------------- | ---- | ------- |
| content | [ComponentContent\<T>](./js-apis-arkui-ComponentContent.md) | 是 | menu弹窗中显示的组件内容。 |
| options | [MenuOptions](./arkui-ts/ts-universal-attributes-menu.md#menuoptions10) | 是 | menu弹窗样式。<br/>**说明：** <br/>不支持更新showInSubWindow、preview、previewAnimationOptions、transition、onAppear、aboutToAppear、onDisappear、aboutToDisappear。 |
| partialUpdate | boolean | 否 | menu弹窗更新方式，默认值为false。<br/>**说明：** <br/>1. true为增量更新，保留当前值，更新options中的指定属性。 <br/>2. false为全量更新，除options中的指定属性，其他属性恢复默认值。 |

**返回值：**

| 类型                                       | 说明      |
| ---------------------------------------- | ------- |
|   Promise&lt;void&gt;           |    返回Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.promptAction(弹窗)](errorcode-promptAction.md)错误码。

| 错误码ID  | 错误信息                               |
| ------ | ---------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 103301 | The ComponentContent is incorrect. |
| 103303 | The ComponentContent cannot be found. |

**示例：**

该示例通过调用updateMenu接口，展示了更新Menu箭头样式的功能。

```ts
import { ComponentContent, FrameNode } from '@kit.ArkUI';

export function doSomething(context: UIContext, uniqueId: number, contentNode: ComponentContent<Object>) {
  showMenu(context, uniqueId, contentNode);
}

@Builder
function MyMenu() {
  Column() {
    Menu() {
      MenuItem({ startIcon: $r("app.media.startIcon"), content: "菜单选项1" })
      MenuItem({ startIcon: $r("app.media.startIcon"), content: "菜单选项2" })
    }
  }
  .width('80%')
  .padding('20lpx')
}

export function showMenu(context: UIContext, uniqueId: number, contentNode: ComponentContent<Object>) {
  const promptAction = context.getPromptAction();
  let frameNode: FrameNode | null = context.getFrameNodeByUniqueId(uniqueId);
  let frameNodeTarget = frameNode?.getFirstChild();
  frameNodeTarget = frameNodeTarget?.getChild(0);
  let targetId = frameNodeTarget?.getUniqueId();
  promptAction.openMenu(contentNode, { id: targetId }, {
    enableArrow: true,
  });
  setTimeout(() => {
    promptAction.updateMenu(contentNode, {
      enableArrow: false,
    });
  }, 2000);
}

@Entry
@Component
struct Index {
  build() {
    Column() {
      Button('OpenMenu', { type: ButtonType.Normal, stateEffect: true })
        .borderRadius('16lpx')
        .width('80%')
        .margin(10)
        .onClick(() => {
          let context = this.getUIContext();
          const contentNode = new ComponentContent(context, wrapBuilder(MyMenu));
          doSomething(context, this.getUniqueId(), contentNode);
        })
    }
  }
}
```

### closeMenu<sup>18+</sup>

closeMenu\<T extends Object>(content: ComponentContent\<T>): Promise&lt;void&gt;

关闭content对应的Menu弹窗。使用Promise异步回调。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名     | 类型                                       | 必填   | 说明      |
| ------- | ---------------------------------------- | ---- | ------- |
| content | [ComponentContent\<T>](./js-apis-arkui-ComponentContent.md) | 是 | menu弹窗中显示的组件内容。 |

**返回值：**

| 类型                                       | 说明      |
| ---------------------------------------- | ------- |
|   Promise&lt;void&gt;           |    返回Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[ohos.promptAction(弹窗)](errorcode-promptAction.md)错误码。

| 错误码ID  | 错误信息                               |
| ------ | ---------------------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 103301 | The ComponentContent is incorrect. |
| 103303 | The ComponentContent cannot be found. |

**示例：**

该示例通过调用closeMenu接口，展示了关闭Menu的功能。

```ts
import { ComponentContent, FrameNode } from '@kit.ArkUI';

export function doSomething(context: UIContext, uniqueId: number, contentNode: ComponentContent<Object>) {
  showMenu(context, uniqueId, contentNode);
}

@Builder
function MyMenu() {
  Column() {
    Menu() {
      MenuItem({ startIcon: $r("app.media.startIcon"), content: "菜单选项1" })
      MenuItem({ startIcon: $r("app.media.startIcon"), content: "菜单选项2" })
    }
  }
  .width('80%')
  .padding('20lpx')
}

export function showMenu(context: UIContext, uniqueId: number, contentNode: ComponentContent<Object>) {
  const promptAction = context.getPromptAction();
  let frameNode: FrameNode | null = context.getFrameNodeByUniqueId(uniqueId);
  let frameNodeTarget = frameNode?.getFirstChild();
  frameNodeTarget = frameNodeTarget?.getChild(0);
  let targetId = frameNodeTarget?.getUniqueId();
  promptAction.openMenu(contentNode, { id: targetId }, {
    enableArrow: true,
  });
  setTimeout(() => {
    promptAction.closeMenu(contentNode);
  }, 2000);
}

@Entry
@Component
struct Index {
  build() {
    Column() {
      Button('OpenMenu', { type: ButtonType.Normal, stateEffect: true })
        .borderRadius('16lpx')
        .width('80%')
        .margin(10)
        .onClick(() => {
          let context = this.getUIContext();
          const contentNode = new ComponentContent(context, wrapBuilder(MyMenu));
          doSomething(context, this.getUniqueId(), contentNode);
        })
    }
  }
}
```

## DragController<sup>11+</sup>
以下API需先使用UIContext中的[getDragController()](js-apis-arkui-UIContext.md#getdragcontroller11)方法获取DragController实例，再通过此实例调用对应方法。

### executeDrag<sup>11+</sup>

executeDrag(custom: CustomBuilder | DragItemInfo, dragInfo: dragController.DragInfo, callback: AsyncCallback&lt;dragController.DragEventParam&gt;): void

主动发起拖拽能力，传入拖拽发起后跟手效果所拖拽的对象以及携带拖拽信息。通过回调返回拖拽事件结果。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| custom   | [CustomBuilder](arkui-ts/ts-types.md#custombuilder8) \| [DragItemInfo](arkui-ts/ts-universal-events-drag-drop.md#dragiteminfo) | 是   | 拖拽发起后跟手效果所拖拽的对象。 <br/> **说明：** <br/>不支持全局builder。如果builder中使用了[Image](arkui-ts/ts-basic-components-image.md)组件，应尽量开启同步加载，即配置Image的[syncLoad](arkui-ts/ts-basic-components-image.md#syncload8)为true。该builder只用于生成当次拖拽中显示的图片。builder的根组件宽高为0时，无法生成拖拽显示的图片导致拖拽失败。builder的修改不会同步到当前正在拖拽的图片，对builder的修改需要在下一次拖拽时生效。 |
| dragInfo | [dragController.DragInfo](js-apis-arkui-dragController.md#draginfo) | 是   | 拖拽信息。                                                   |
| callback | [AsyncCallback](../apis-basic-services-kit/js-apis-base.md#asynccallback)&lt;[dragController.DragEventParam](js-apis-arkui-dragController.md#drageventparam12)&gt; | 是   | 拖拽结束返回结果的回调<br/>- event：拖拽事件信息，仅包括拖拽结果。<br/>- extraParams：拖拽事件额外信息。 |

**错误码：** 
以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)错误码。

| 错误码ID | 错误信息      |
| -------- | ------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed. |
| 100001   | Internal handling failed. |

**示例：**

```ts
import { dragController } from '@kit.ArkUI';
import { unifiedDataChannel } from '@kit.ArkData';

@Entry
@Component
struct DragControllerPage {
  @Builder DraggingBuilder() {
    Column() {
      Text("DraggingBuilder")
    }
    .width(100)
    .height(100)
    .backgroundColor(Color.Blue)
  }

  build() {
    Column() {
      Button('touch to execute drag')
        .onTouch((event?: TouchEvent) => {
          if (event) {
            if (event.type == TouchType.Down) {
              let text = new unifiedDataChannel.Text();
              let unifiedData = new unifiedDataChannel.UnifiedData(text);

              let dragInfo: dragController.DragInfo = {
                pointerId: 0,
                data: unifiedData,
                extraParams: ''
              };
              class tmp {
                event: DragEvent | undefined = undefined;
                extraParams: string = '';
              }
              let eve: tmp = new tmp();
              this.getUIContext().getDragController().executeDrag(() => { this.DraggingBuilder() }, dragInfo, (err, eve) => {
                if (eve.event) {
                  if (eve.event.getResult() == DragResult.DRAG_SUCCESSFUL) {
                    // ...
                  } else if (eve.event.getResult() == DragResult.DRAG_FAILED) {
                    // ...
                  }
                }
              })
            }
          }
        })
    }
  }
}
```

### executeDrag<sup>11+</sup>

executeDrag(custom: CustomBuilder | DragItemInfo, dragInfo: dragController.DragInfo): Promise&lt;dragController.DragEventParam&gt;

主动发起拖拽能力，传入拖拽发起后跟手效果所拖拽的对象以及携带拖拽信息。通过Promise返回拖拽事件结果。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                             |
| -------- | ------------------------------------------------------------ | ---- | -------------------------------- |
| custom   | [CustomBuilder](arkui-ts/ts-types.md#custombuilder8) \| [DragItemInfo](arkui-ts/ts-universal-events-drag-drop.md#dragiteminfo) | 是   | 拖拽发起后跟手效果所拖拽的对象。 |
| dragInfo | [dragController.DragInfo](js-apis-arkui-dragController.md#draginfo)                                        | 是   | 拖拽信息。                       |

**返回值：**

| 类型                                                         | 说明                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| Promise&lt;[dragController.DragEventParam](js-apis-arkui-dragController.md#drageventparam12)&gt; | 拖拽结束返回结果的回调<br/>- event：拖拽事件信息，仅包括拖拽结果。<br/>- extraParams：拖拽事件额外信息。 |

**错误码：**
以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)错误码。

| 错误码ID | 错误信息      |
| -------- | ------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed. |
| 100001   | Internal handling failed. |

**示例：**

```ts
import { dragController } from '@kit.ArkUI';
import { image } from '@kit.ImageKit';
import { unifiedDataChannel } from '@kit.ArkData';

@Entry
@Component
struct DragControllerPage {
  @State pixmap: image.PixelMap | null = null;

  @Builder DraggingBuilder() {
    Column() {
      Text("DraggingBuilder")
    }
    .width(100)
    .height(100)
    .backgroundColor(Color.Blue)
  }

  @Builder PixmapBuilder() {
    Column() {
      Text("PixmapBuilder")
    }
    .width(100)
    .height(100)
    .backgroundColor(Color.Blue)
  }

  build() {
    Column() {
      Button('touch to execute drag')
        .onTouch((event?: TouchEvent) => {
          if (event) {
            if (event.type == TouchType.Down) {
              let text = new unifiedDataChannel.Text();
              let unifiedData = new unifiedDataChannel.UnifiedData(text);

              let dragInfo: dragController.DragInfo = {
                pointerId: 0,
                data: unifiedData,
                extraParams: ''
              };
              let pb: CustomBuilder = (): void => { this.PixmapBuilder() };
              this.getUIContext().getComponentSnapshot().createFromBuilder(pb).then((pix: image.PixelMap) => {
                this.pixmap = pix;
                let dragItemInfo: DragItemInfo = {
                  pixelMap: this.pixmap,
                  builder: () => { this.DraggingBuilder() },
                  extraInfo: "DragItemInfoTest"
                };

                class tmp {
                  event: DragResult | undefined = undefined;
                  extraParams: string = '';
                }
                let eve: tmp = new tmp();
                this.getUIContext().getDragController().executeDrag(dragItemInfo, dragInfo)
                  .then((eve) => {
                    if (eve.event.getResult() == DragResult.DRAG_SUCCESSFUL) {
                      // ...
                    } else if (eve.event.getResult() == DragResult.DRAG_FAILED) {
                      // ...
                    }
                  })
                  .catch((err: Error) => {
                  })
              })
            }
          }
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

### createDragAction<sup>11+</sup>

createDragAction(customArray: Array&lt;CustomBuilder \| DragItemInfo&gt;, dragInfo: dragController.DragInfo): dragController.DragAction

创建拖拽的Action对象，需要显式指定拖拽背板图(可多个)，以及拖拽的数据，跟手点等信息；当通过一个已创建的 Action 对象发起的拖拽未结束时，无法再次创建新的 Action 对象，接口会抛出异常；当Action对象的生命周期结束后，注册在该对象上的回调函数会失效，因此需要在一个尽量长的作用域下持有该对象，并在每次发起拖拽前通过createDragAction返回新的对象覆盖旧值。

**说明：** 建议控制传递的拖拽背板数量，传递过多容易导致拖起的效率问题。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                             |
| --------      | ------------------------------------------------------------ | ---- | -------------------------------- |
| customArray  | Array&lt;[CustomBuilder](arkui-ts/ts-types.md#custombuilder8) \| [DragItemInfo](arkui-ts/ts-universal-events-drag-drop.md#dragiteminfo)&gt; | 是   | 拖拽发起后跟手效果所拖拽的对象。 |
| dragInfo | [dragController.DragInfo](js-apis-arkui-dragController.md#draginfo)                                | 是   | 拖拽信息。                       |

**返回值：**

| 类型                                                   | 说明               |
| ------------------------------------------------------ | ------------------ |
| [dragController.DragAction](js-apis-arkui-dragController.md#dragaction11)| 创建拖拽Action对象，主要用于后面实现注册监听拖拽状态改变事件和启动拖拽服务。 |

**错误码：**
以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)错误码。

| 错误码ID | 错误信息      |
| -------- | ------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed. |
| 100001   | Internal handling failed. |

**示例：**
1.在EntryAbility.ets中获取UI上下文并保存至LocalStorage中。
```ts
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { window, UIContext } from '@kit.ArkUI';

let uiContext: UIContext;
let localStorage: LocalStorage = new LocalStorage('uiContext');

export default class EntryAbility extends UIAbility {
  storage: LocalStorage = localStorage;
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onCreate');
  }

  onDestroy(): void {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onDestroy');
  }

  onWindowStageCreate(windowStage: window.WindowStage): void {
    // Main window is created, set main page for this ability
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onWindowStageCreate');

    windowStage.loadContent('pages/Index', this.storage, (err, data) => {
      if (err.code) {
        hilog.error(0x0000, 'testTag', 'Failed to load the content. Cause: %{public}s', JSON.stringify(err) ?? '');
        return;
      }
      hilog.info(0x0000, 'testTag', 'Succeeded in loading the content. Data: %{public}s', JSON.stringify(data) ?? '');
      windowStage.getMainWindow((err, data) =>
      {
        if (err.code) {
          console.error('Failed to abtain the main window. Cause:' + err.message);
          return;
        }
        let windowClass: window.Window = data;
        uiContext = windowClass.getUIContext();
        this.storage.setOrCreate<UIContext>('uiContext', uiContext);
        // 获取UIContext实例
      });
    });
  }

  onWindowStageDestroy(): void {
    // Main window is destroyed, release UI related resources
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onWindowStageDestroy');
  }

  onForeground(): void {
    // Ability has brought to foreground
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onForeground');
  }

  onBackground(): void {
    // Ability has back to background
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onBackground');
  }
}
```
2.通过this.getUIContext().getSharedLocalStorage()获取上下文，进而获取DragController对象实施后续操作。
```ts
import { dragController, componentSnapshot, UIContext, DragController } from '@kit.ArkUI';
import { image } from '@kit.ImageKit';
import { unifiedDataChannel } from '@kit.ArkData';

@Entry()
@Component
struct DragControllerPage {
  @State pixmap: image.PixelMap | null = null;
  private dragAction: dragController.DragAction | null = null;
  customBuilders: Array<CustomBuilder | DragItemInfo> = new Array<CustomBuilder | DragItemInfo>();
  storages = this.getUIContext().getSharedLocalStorage();

  @Builder DraggingBuilder() {
    Column() {
      Text("DraggingBuilder")
    }
    .width(100)
    .height(100)
    .backgroundColor(Color.Blue)
  }

  build() {
    Column() {

      Column() {
        Text("测试")
      }
      .width(100)
      .height(100)
      .backgroundColor(Color.Red)

      Button('多对象dragAction customBuilder拖拽').onTouch((event?: TouchEvent) => {
        if (event) {
          if (event.type == TouchType.Down) {
            console.info("muti drag Down by listener");
            this.customBuilders.push(() => { this.DraggingBuilder() });
            this.customBuilders.push(() => { this.DraggingBuilder() });
            this.customBuilders.push(() => { this.DraggingBuilder() });
            let text = new unifiedDataChannel.Text();
            let unifiedData = new unifiedDataChannel.UnifiedData(text);
            let dragInfo: dragController.DragInfo = {
              pointerId: 0,
              data: unifiedData,
              extraParams: ''
            };
            try{
              let uiContext: UIContext = this.storages?.get<UIContext>('uiContext') as UIContext;
              this.dragAction = uiContext.getDragController().createDragAction(this.customBuilders, dragInfo);
              if (!this.dragAction) {
                console.info("listener dragAction is null");
                return;
              }
              this.dragAction.on('statusChange', (dragAndDropInfo) => {
                if (dragAndDropInfo.status == dragController.DragStatus.STARTED) {
                  console.info("drag has start");
                } else if (dragAndDropInfo.status == dragController.DragStatus.ENDED) {
                  console.info("drag has end");
                  if (!this.dragAction) {
                    return;
                  }
                  this.customBuilders.splice(0, this.customBuilders.length);
                  this.dragAction.off('statusChange');
                }
              })
              this.dragAction.startDrag().then(() => {}).catch((err: Error) => {
                console.error("start drag Error:" + err.message);
              })
            } catch(err) {
              console.error("create dragAction Error:" + err.message);
            }
          }
        }
      }).margin({ top: 20 })
    }
  }
}
```

### getDragPreview<sup>11+</sup>

getDragPreview(): dragController.DragPreview

返回一个代表拖拽背板的对象。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：** 

| 类型                                                         | 说明                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| [dragController.DragPreview](js-apis-arkui-dragController.md#dragpreview11) | 一个代表拖拽背板的对象，提供背板样式设置的接口，在OnDrop和OnDragEnd回调中使用不生效。 |

**错误码：** 通用错误码请参考[通用错误码说明文档](../errorcode-universal.md)。

**示例：**

请参考[animate](js-apis-arkui-dragController.md#animate11)

### setDragEventStrictReportingEnabled<sup>12+</sup>

setDragEventStrictReportingEnabled(enable: boolean): void

当目标从父组件拖拽到子组件时，通过该方法设置是否会触发父组件的onDragLeave的回调。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** : SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型    | 必填 | 说明                                                         |
| ------ | ------- | ---- | ------------------------------------------------------------ |
| enable | boolean | 是   | 将目标从父组件拖拽到子组件时，是否会触发父组件的onDragLeave的回调。true表示触发父组件的onDragLeave的回调，false表示不触发。 |

**示例：**

```ts
import { UIAbility } from '@kit.AbilityKit';
import { window, UIContext } from '@kit.ArkUI';

 export default class EntryAbility extends UIAbility {
   onWindowStageCreate(windowStage: window.WindowStage): void {
       windowStage.loadContent('pages/Index', (err, data) => {
         if (err.code) {
         return;
       }
       windowStage.getMainWindow((err, data) => {
         if (err.code) {
           return;
         }
         let windowClass: window.Window = data;
         let uiContext: UIContext = windowClass.getUIContext();
         uiContext.getDragController().setDragEventStrictReportingEnabled(true);
     });
   });
 }
}
```

### cancelDataLoading<sup>15+</sup>

cancelDataLoading(key: string): void

当使用[startDataLoading](arkui-ts/ts-universal-events-drag-drop.md#dragevent7)获取拖拽数据时，可调用该接口取消数据传输。

**原子化服务API：** 从API version 15开始，该接口支持在原子化服务中使用。

**系统能力：** : SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型    | 必填 | 说明                                                         |
| ------ | ------- | ---- | ------------------------------------------------------------ |
| key | string | 是   | 拖拽数据的标识，用于区分每次拖拽。key可通过startDataLoading接口获取。 |

**错误码：** 

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[拖拽事件错误码](./errorcode-drag-event.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error. |
| 190004      | Operation failed. |

**示例：**

请参考[拖拽异步获取数据](./arkui-ts/ts-universal-events-drag-drop.md#示例3拖拽异步获取数据)。

### notifyDragStartRequest<sup>18+</sup>

notifyDragStartRequest(requestStatus: dragController.DragStartRequestStatus): void

控制应用是否可以发起拖拽。

**原子化服务API**: 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力**: SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型   | 必填| 说明                                                        |
| ------ | ------- | ---- | ------------------------------------------------------------ |
| requestStatus  | [dragController.DragStartRequestStatus](js-apis-arkui-dragController.md#dragstartrequeststatus18)    | 是  |定义应用是否可以发起拖拽。|

**示例：**

```ts
import { unifiedDataChannel } from '@kit.ArkData';
import { image } from '@kit.ImageKit';
import { dragController } from '@kit.ArkUI';

// xxx.ets
@Entry
@Component
struct NormalEts {
  @State finished: boolean = false;
  @State timeout1: number = 1;
  @State pixmap: image.PixelMap | undefined = undefined;
  @State unifiedData1: unifiedDataChannel.UnifiedData | undefined = undefined;
  @State previewData: DragItemInfo | undefined = undefined;

  loadData() {
    let timeout = setTimeout(() => {
      this.getUIContext().getComponentSnapshot().get("image1", (error: Error, pixmap: image.PixelMap) => {
        this.pixmap = pixmap;
        this.previewData = {
          pixelMap: this.pixmap
        };
      });

      let data: unifiedDataChannel.Image = new unifiedDataChannel.Image();
      data.imageUri = "app.media.startIcon";
      let unifiedData = new unifiedDataChannel.UnifiedData(data);
      this.unifiedData1 = unifiedData;

      this.getUIContext().getDragController().notifyDragStartRequest(dragController.DragStartRequestStatus.READY);
    }, 4000);
    this.timeout1 = timeout;
  }


    build() {
      Column({space: 20}) {
        Image($r("app.media.startIcon"))
          .width(300)
          .height(200)
          .id("image1")
          .draggable(true)
          .dragPreview(this.previewData)
          .onPreDrag((status: PreDragStatus) => {
            if (status == PreDragStatus.PREPARING_FOR_DRAG_DETECTION) {
              this.loadData();
            } else {
              clearTimeout(this.timeout1);
            }
          })
          .onDragStart((event: DragEvent) => {
            if (this.finished == false) {
              this.getUIContext().getDragController().notifyDragStartRequest(dragController.DragStartRequestStatus.WAITING);
            } else {
              event.setData(this.unifiedData1);
            }
          })
          .onDragEnd(() => {
            this.finished = false;
          })
      }
      .height(400)
      .backgroundColor(Color.Pink)
    }
}
```

## OverlayManager<sup>12+</sup>

以下API需先使用UIContext中的[getOverlayManager()](#getoverlaymanager12)方法获取到OverlayManager对象，再通过该对象调用对应方法。
> **说明：**
>
> OverlayManager上节点的层级在Page页面层级之上，在Dialog、Popup、Menu、BindSheet、BindContentCover和Toast等之下。
>
> OverlayManager上节点安全区域内外的绘制方式与Page一致，键盘避让方式与Page一致。
>
> 与OverlayManager相关的属性推荐采用AppStorage来进行应用全局存储，以免切换页面后属性值发生变化从而导致业务错误。

### addComponentContent<sup>12+</sup>

addComponentContent(content: ComponentContent, index?: number): void

在OverlayManager上新增指定节点。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名     | 类型                                       | 必填   | 说明          |
| ------- | ---------------------------------------- | ---- | ----------- |
| content | [ComponentContent](js-apis-arkui-ComponentContent.md) | 是    | 在OverlayManager上新增指定节点上添加此content。 <br>**说明：** <br/> 新增的节点默认处于页面居中，按层级堆叠。|
| index | number | 否    | 新增节点在OverlayManager上的层级位置。<br>**说明：** <br/> 当index ≥ 0时，越大，ComponentContent的层级越高；若多个ComponentContent的index相同，ComponentContent添加的时间越晚层级越高。<br/> 当index < 0、index = null或index = undefined时，ComponentContent默认添加至最高层。<br/>当同一个ComponentContent被添加多次时，只保留最后一次添加的ComponentContent。

**示例：**

```ts
import { ComponentContent, OverlayManager } from '@kit.ArkUI';

class Params {
  text: string = "";
  offset: Position;

  constructor(text: string, offset: Position) {
    this.text = text;
    this.offset = offset;
  }
}

@Builder
function builderText(params: Params) {
  Column() {
    Text(params.text)
      .fontSize(30)
      .fontWeight(FontWeight.Bold)
  }.offset(params.offset)
}

@Entry
@Component
struct OverlayExample {
  @State message: string = 'ComponentContent';
  private uiContext: UIContext = this.getUIContext();
  private overlayNode: OverlayManager = this.uiContext.getOverlayManager();
  @StorageLink('contentArray') contentArray: ComponentContent<Params>[] = [];
  @StorageLink('componentContentIndex') componentContentIndex: number = 0;
  @StorageLink('arrayIndex') arrayIndex: number = 0;
  @StorageLink("componentOffset") componentOffset: Position = { x: 0, y: 80 };

  build() {
    Column() {
      Button("++componentContentIndex: " + this.componentContentIndex).onClick(() => {
        ++this.componentContentIndex;
      })
      Button("--componentContentIndex: " + this.componentContentIndex).onClick(() => {
        --this.componentContentIndex;
      })
      Button("增加ComponentContent" + this.contentArray.length).onClick(() => {
        let componentContent = new ComponentContent(
          this.uiContext, wrapBuilder<[Params]>(builderText),
          new Params(this.message + (this.contentArray.length), this.componentOffset)
        );
        this.contentArray.push(componentContent);
        this.overlayNode.addComponentContent(componentContent, this.componentContentIndex);
      })
      Button("++arrayIndex: " + this.arrayIndex).onClick(() => {
        ++this.arrayIndex;
      })
      Button("--arrayIndex: " + this.arrayIndex).onClick(() => {
        --this.arrayIndex;
      })
      Button("删除ComponentContent" + this.arrayIndex).onClick(() => {
        if (this.arrayIndex >= 0 && this.arrayIndex < this.contentArray.length) {
          let componentContent = this.contentArray.splice(this.arrayIndex, 1);
          this.overlayNode.removeComponentContent(componentContent.pop());
        } else {
          console.info("arrayIndex有误");
        }
      })
      Button("显示ComponentContent" + this.arrayIndex).onClick(() => {
        if (this.arrayIndex >= 0 && this.arrayIndex < this.contentArray.length) {
          let componentContent = this.contentArray[this.arrayIndex];
          this.overlayNode.showComponentContent(componentContent);
        } else {
          console.info("arrayIndex有误");
        }
      })
      Button("隐藏ComponentContent" + this.arrayIndex).onClick(() => {
        if (this.arrayIndex >= 0 && this.arrayIndex < this.contentArray.length) {
          let componentContent = this.contentArray[this.arrayIndex];
          this.overlayNode.hideComponentContent(componentContent);
        } else {
          console.info("arrayIndex有误");
        }
      })
      Button("显示所有ComponentContent").onClick(() => {
        this.overlayNode.showAllComponentContents();
      })
      Button("隐藏所有ComponentContent").onClick(() => {
        this.overlayNode.hideAllComponentContents();
      })

      Button("跳转页面").onClick(() => {
        this.getUIContext().getRouter().pushUrl({
          url: 'pages/Second'
        });
      })
    }
    .width('100%')
    .height('100%')
  }
}
```

### addComponentContentWithOrder<sup>18+</sup>

addComponentContentWithOrder(content: ComponentContent, levelOrder?: LevelOrder): void

创建浮层节点时，指定显示顺序。

支持在浮层节点创建时指定显示的顺序。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名     | 类型                                       | 必填   | 说明          |
| ------- | ---------------------------------------- | ---- | ----------- |
| content | [ComponentContent](js-apis-arkui-ComponentContent.md) | 是    | 在OverlayManager上新增指定节点上添加此content。 <br>**说明：** <br/> 新增的节点默认处于页面居中位置，按层级堆叠。|
| levelOrder | [LevelOrder](js-apis-promptAction.md#levelorder18) | 否    | 新增浮层节点的显示顺序。<br />**说明：**<br />- 默认值：LevelOrder.clamp(0)。|

**示例：**

该示例通过调用addComponentContentWithOrder接口，实现了按照指定显示顺序创建浮层节点的功能。

```ts
import { ComponentContent, PromptAction, LevelOrder, UIContext, OverlayManager } from '@kit.ArkUI';

class Params {
  text: string = "";
  offset: Position;
  constructor(text: string, offset: Position) {
    this.text = text;
    this.offset = offset;
  }
}
@Builder
function builderText(params: Params) {
  Column() {
    Text(params.text)
      .fontSize(30)
      .fontWeight(FontWeight.Bold)
  }.offset(params.offset)
}

@Entry
@Component
struct Index {
  @State message: string = '弹窗';
  private ctx: UIContext = this.getUIContext();
  private promptAction: PromptAction = this.ctx.getPromptAction();
  private overlayNode: OverlayManager = this.ctx.getOverlayManager();
  @StorageLink('contentArray') contentArray: ComponentContent<Params>[] = [];
  @StorageLink('componentContentIndex') componentContentIndex: number = 0;
  @StorageLink('arrayIndex') arrayIndex: number = 0;
  @StorageLink("componentOffset") componentOffset: Position = { x: 0, y: 80 };

  build() {
    Row() {
      Column({ space: 10 }) {
        Button('OverlayManager下面弹窗')
          .fontSize(20)
          .onClick(() => {
            let componentContent = new ComponentContent(
              this.ctx, wrapBuilder<[Params]>(builderText),
              new Params(this.message + (this.contentArray.length), this.componentOffset)
            );
            this.contentArray.push(componentContent);
            this.overlayNode.addComponentContentWithOrder(componentContent, LevelOrder.clamp(100.1));
            let topOrder: LevelOrder = this.promptAction.getTopOrder();
            if (topOrder !== undefined) {
              console.error('topOrder: ' + topOrder.getOrder());
            }
            let bottomOrder: LevelOrder = this.promptAction.getBottomOrder();
            if (bottomOrder !== undefined) {
              console.error('bottomOrder: ' + bottomOrder.getOrder());
            }
          })
        Button('OverlayManager上面弹窗')
          .fontSize(20)
          .onClick(() => {
            let componentContent = new ComponentContent(
              this.ctx, wrapBuilder<[Params]>(builderText),
              new Params(this.message + (this.contentArray.length), this.componentOffset)
            );
            this.contentArray.push(componentContent);
            this.overlayNode.addComponentContentWithOrder(componentContent, LevelOrder.clamp(100.2));
            let topOrder: LevelOrder = this.promptAction.getTopOrder();
            if (topOrder !== undefined) {
              console.error('topOrder: ' + topOrder.getOrder());
            }
            let bottomOrder: LevelOrder = this.promptAction.getBottomOrder();
            if (bottomOrder !== undefined) {
              console.error('bottomOrder: ' + bottomOrder.getOrder());
            }
          })
      }.width('100%')
    }.height('100%')
  }
}
```

### removeComponentContent<sup>12+</sup>

removeComponentContent(content: ComponentContent): void

删除overlay上的指定节点。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名     | 类型                                       | 必填   | 说明          |
| ------- | ---------------------------------------- | ---- | ----------- |
| content | [ComponentContent](js-apis-arkui-ComponentContent.md) | 是    | 在OverlayManager上删除此content。 |

**示例：**

请参考[addComponentContent示例](#addcomponentcontent12)

### showComponentContent<sup>12+</sup>

showComponentContent(content: ComponentContent): void

在OverlayManager上显示指定节点。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名     | 类型                                       | 必填   | 说明          |
| ------- | ---------------------------------------- | ---- | ----------- |
| content | [ComponentContent](js-apis-arkui-ComponentContent.md) | 是    | 在OverlayManager上显示此content。|

**示例：**

请参考[addComponentContent示例](#addcomponentcontent12)

### hideComponentContent<sup>12+</sup>

hideComponentContent(content: ComponentContent): void

隐藏OverlayManager上的指定节点。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名     | 类型                                       | 必填   | 说明          |
| ------- | ---------------------------------------- | ---- | ----------- |
| content | [ComponentContent](js-apis-arkui-ComponentContent.md) | 是    | 在OverlayManager上隐藏此content。 |

**示例：**

请参考[addComponentContent示例](#addcomponentcontent12)

### showAllComponentContents<sup>12+</sup>

showAllComponentContents(): void

显示OverlayManager上所有的ComponentContent。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

请参考[addComponentContent示例](#addcomponentcontent12)

### hideAllComponentContents<sup>12+</sup>

hideAllComponentContents(): void

隐藏OverlayManager上的所有ComponentContent。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

请参考[addComponentContent示例](#addcomponentcontent12)

## OverlayManagerOptions<sup>15+</sup>

初始化[OverlayManager](#overlaymanager12)时所用参数。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称             | 类型                | 必填     | 说明                     |
| --------------- | ---------------------- | ------------ | --------------------- |
| renderRootOverlay   | boolean | 否 | 是否渲染overlay根节点，true表示渲染overlay根节点，false表示不渲染overlay根节点，默认值为true。<br/>**原子化服务API：** 从API version 15开始，该接口支持在原子化服务中使用。|
| enableBackPressedEvent<sup>19+</sup>   | boolean | 否 | 是否支持通过侧滑手势关闭OverlayManager下的ComponentContent，true表示可以通过侧滑关闭，false表示不可以通过侧滑关闭，默认值为false。 <br/>**原子化服务API：** 从API version 19开始，该接口支持在原子化服务中使用。|

## AtomicServiceBar<sup>11+</sup>

以下接口需要先使用UIContext中的[getAtomicServiceBar](#getatomicservicebar11)方法获取到AtomicServiceBar对象，再通过该对象调用对应方法。
> **说明：**
>
> 从API version 12开始原子化服务menuBar样式变更，以下接口将失效。

### setVisible<sup>11+</sup>

setVisible(visible: boolean): void

通过该方法设置原子化服务menuBar是否可见。
> **说明：**
>
> 从API version 12开始原子化服务menuBar样式变更，menuBar默认隐藏，变为悬浮按钮，通过该接口无法改变menuBar的可见性。

**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------- | ------- | ------- | ------- |
| visible | boolean | 是 | 原子化服务menuBar是否可见。true表示设置menuBar可见，false表示设置menuBar不可见。|


**示例：**

```ts
import { UIAbility } from '@kit.AbilityKit';
import { UIContext, AtomicServiceBar, window } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    // Main window is created, set main page for this ability
    hilog.info(0x0000, 'testTag', 'Ability onWindowStageCreate');
    windowStage.loadContent('pages/Index', (err, data) => {
      let uiContext: UIContext = windowStage.getMainWindowSync().getUIContext();
      let atomicServiceBar: Nullable<AtomicServiceBar> = uiContext.getAtomicServiceBar();
      if (atomicServiceBar != undefined) {
        hilog.info(0x0000, 'testTag', 'Get AtomServiceBar Successfully.');
        atomicServiceBar.setVisible(false);
      } else {
        hilog.info(0x0000, 'testTag', 'Get AtomicServiceBar failed.');
      }
    });
  }
}
```

### setBackgroundColor<sup>11+</sup>

setBackgroundColor(color:Nullable<Color | number | string>): void

通过该方法设置原子化服务menuBar的背景颜色。
> **说明：**
>
> 从API version 12开始原子化服务menuBar样式变更，menuBar的背景默认隐藏，通过该接口无法改变menuBar的背景颜色。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：**  SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ------ | ------ | ------ |
| color | Nullable\<[Color](arkui-ts/ts-appendix-enums.md#color) \| number \| string> | 是 | 通过该方法设置原子化服务menuBar的背景颜色，undefined代表使用默认颜色。number为HEX格式颜色，支持rgb或者argb，示例：0xffffff。string为rgb或者argb格式颜色，示例：'#ffffff'。|

**示例：**

```ts
import { UIAbility } from '@kit.AbilityKit';
import { UIContext, AtomicServiceBar, window } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';

export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    // Main window is created, set main page for this ability
    hilog.info(0x0000, 'testTag', 'Ability onWindowStageCreate');
    windowStage.loadContent('pages/Index', (err, data) => {
      let uiContext: UIContext = windowStage.getMainWindowSync().getUIContext();
      let atomicServiceBar: Nullable<AtomicServiceBar> = uiContext.getAtomicServiceBar();
      if (atomicServiceBar != undefined) {
        hilog.info(0x0000, 'testTag', 'Get AtomServiceBar Successfully.');
        atomicServiceBar.setBackgroundColor(0x88888888);
      } else {
        hilog.error(0x0000, 'testTag', 'Get AtomicServiceBar failed.');
      }
    });
  }
}
```

### setTitleContent<sup>11+</sup>

setTitleContent(content:string): void

通过该方法设置原子化服务menuBar的标题内容。
> **说明：**
>
> 从API version 12开始原子化服务menuBar样式变更，menuBar的标题默认隐藏，通过该接口无法改变menuBar的标题内容。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：**  SystemCapability.ArkUI.ArkUI.Full

**参数：**

|参数名|类型|必填|说明 |
| ------- | ------- | ------- | ------- |
| content | string | 是 | 原子化服务menuBar中的标题内容。|

**示例：**

```ts
import { UIAbility } from '@kit.AbilityKit';
import { UIContext, AtomicServiceBar, window } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';
export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    // Main window is created, set main page for this ability
    hilog.info(0x0000, 'testTag', 'Ability onWindowStageCreate');
    windowStage.loadContent('pages/Index', (err, data) => {
      let uiContext: UIContext = windowStage.getMainWindowSync().getUIContext();
      let atomicServiceBar: Nullable<AtomicServiceBar> = uiContext.getAtomicServiceBar();
      if (atomicServiceBar != undefined) {
        hilog.info(0x0000, 'testTag', 'Get AtomServiceBar Successfully.');
        atomicServiceBar.setTitleContent('text2');
      } else {
        hilog.info(0x0000, 'testTag', 'Get AtomicServiceBar failed.');
      }
    });
  }
}
```

### setTitleFontStyle<sup>11+</sup>

setTitleFontStyle(font:FontStyle):void

通过该方法设置原子化服务menuBar的字体样式。
> **说明：**
>
> 从API version 12开始原子化服务menuBar样式变更，menuBar的标题默认隐藏，通过该接口无法改变menuBar的字体样式。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------ | ------ | ------ | ------ |
| font | [FontStyle](arkui-ts/ts-appendix-enums.md#fontstyle) | 是 | 原子化服务menuBar中的字体样式。 |

**示例：**

```ts
import { UIAbility } from '@kit.AbilityKit';
import { UIContext, AtomicServiceBar, window } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';
export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    // Main window is created, set main page for this ability
    hilog.info(0x0000, 'testTag', 'Ability onWindowStageCreate');
    windowStage.loadContent('pages/Index', (err, data) => {
      let uiContext: UIContext = windowStage.getMainWindowSync().getUIContext();
      let atomicServiceBar: Nullable<AtomicServiceBar> = uiContext.getAtomicServiceBar();
      if (atomicServiceBar != undefined) {
        hilog.info(0x0000, 'testTag', 'Get AtomServiceBar Successfully.');
        atomicServiceBar.setTitleFontStyle(FontStyle.Normal);
      } else {
        hilog.info(0x0000, 'testTag', 'Get AtomicServiceBar failed.');
      }
    });
  }
}
```

### setIconColor<sup>11+</sup>

setIconColor(color:Nullable<Color | number | string>): void

通过该方法设置原子化服务图标的颜色。
> **说明：**
>
> 从API version 12开始原子化服务menuBar样式变更，menuBar默认隐藏，悬浮按钮图标不予用户设置，通过该接口无法改变menuBar的图标颜色。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------- | ------- | ------- | ------- |
| color | Nullable\<[Color](arkui-ts/ts-appendix-enums.md#color) \| number \| string> | 是 | 原子化服务图标的颜色，undefined代表使用默认颜色。number为HEX格式颜色，支持rgb或者argb，示例：0xffffff。string为rgb或者argb格式颜色，示例：'#ffffff'。 |


**示例：**

```ts
import { UIAbility } from '@kit.AbilityKit';
import { UIContext, AtomicServiceBar, window } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';
export default class EntryAbility extends UIAbility {
  onWindowStageCreate(windowStage: window.WindowStage) {
    // Main window is created, set main page for this ability
    hilog.info(0x0000, 'testTag', 'Ability onWindowStageCreate');
    windowStage.loadContent('pages/Index', (err, data) => {
      let uiContext: UIContext = windowStage.getMainWindowSync().getUIContext();
      let atomicServiceBar: Nullable<AtomicServiceBar> = uiContext.getAtomicServiceBar();
      if (atomicServiceBar != undefined) {
        hilog.info(0x0000, 'testTag', 'Get AtomServiceBar Successfully.');
        atomicServiceBar.setIconColor(0x12345678);
      } else {
        hilog.info(0x0000, 'testTag', 'Get AtomicServiceBar failed.');
      }
    });
  }
}
```

### getBarRect<sup>15+</sup>

getBarRect(): Frame

获取原子化服务menuBar相对窗口的布局信息。
> **说明：**
>
> 布局信息包含了原子化服务menuBar的左右margin。

**原子化服务API：** 从API version 15开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型                | 说明            |
| ----------------- | ------------- |
| [Frame](./js-apis-arkui-graphics.md#frame) | 原子化服务menuBar的大小和位置。 |

**示例：**

```ts
import { AtomicServiceBar } from '@kit.ArkUI';
import { hilog } from '@kit.PerformanceAnalysisKit';
@Entry
@Component
struct Index {
  build() {
    Button("getBarRect")
      .onClick(() => {
        let uiContext: UIContext = this.getUIContext();
        let currentBar: Nullable<AtomicServiceBar> = uiContext.getAtomicServiceBar();
        if (currentBar != undefined) {
          let rect = currentBar.getBarRect();
          hilog.info(0x0000, 'testTag', 'Get AtomServiceBar Successfully. x:' +
            rect.x + ' y:' + rect.y + ' width:' + rect.width + ' height:' + rect.height);
        } else {
          hilog.info(0x0000, 'testTag', 'Get AtomServiceBar failed.');
        }
      })
  }
}
```

## KeyboardAvoidMode<sup>11+</sup>

配置键盘避让时页面的避让模式。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 名称   | 值   | 说明       |
| ------ | ---- | ---------- |
| OFFSET | 0    | 上抬模式。 <br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。|
| RESIZE | 1    | 压缩模式。 <br/>**原子化服务API：** 从API version 11开始，该接口支持在原子化服务中使用。|
| OFFSET_WITH_CARET<sup>14+</sup>  | 2 | 上抬模式，输入框光标位置发生变化时候也会触发避让。<br/>**原子化服务API：** 从API version 14开始，该接口支持在原子化服务中使用。|
| RESIZE_WITH_CARET<sup>14+</sup>  | 3 | 压缩模式，输入框光标位置发生变化时候也会触发避让。<br/>**原子化服务API：** 从API version 14开始，该接口支持在原子化服务中使用。|
| NONE<sup>14+</sup>  | 4 | 不避让键盘。<br/>**原子化服务API：** 从API version 14开始，该接口支持在原子化服务中使用。|


## FocusController<sup>12+</sup>
以下API需先使用UIContext中的[getFocusController()](js-apis-arkui-UIContext.md#getfocuscontroller12)方法获取FocusController实例，再通过该实例调用对应方法。

### clearFocus<sup>12+</sup>

clearFocus(): void

清除焦点，将焦点强制转移到页面根容器节点，焦点链路上其他节点失焦。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**

```ts
@Entry
@Component
struct ClearFocusExample {
  @State inputValue: string = '';
  @State btColor: Color = Color.Blue;

  build() {
    Column({ space: 20 }) {
      Column({ space: 5 }) {
        Button('button1')
          .width(200)
          .height(70)
          .fontColor(Color.White)
          .focusOnTouch(true)
          .backgroundColor(Color.Blue)
        Button('button2')
          .width(200)
          .height(70)
          .fontColor(Color.White)
          .focusOnTouch(true)
          .backgroundColor(this.btColor)
          .defaultFocus(true)
          .onFocus(() => {
            this.btColor = Color.Red;
          })
          .onBlur(() => {
            this.btColor = Color.Blue;
          })
        Button('clearFocus')
          .width(200)
          .height(70)
          .fontColor(Color.White)
          .backgroundColor(Color.Blue)
          .onClick(() => {
            this.getUIContext().getFocusController().clearFocus();
          })
      }
    }
    .width('100%')
    .height('100%')
  }
}
```

### requestFocus<sup>12+</sup>

requestFocus(key: string): void

通过组件的id将焦点转移到组件树对应的实体节点，当前帧生效。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------- | ------- | ------- | ------- |
| key | string | 是 | 节点对应的[组件标识](arkui-ts/ts-universal-attributes-component-id.md)。|

**错误码：**

以下错误码的详细介绍请参见[焦点错误码](errorcode-focus.md)。

| 错误码ID | 错误信息                                        |
| -------- | ----------------------------------------------- |
| 150001   | the component cannot be focused.                |
| 150002   | This component has an unfocusable ancestor.     |
| 150003   | the component is not on tree or does not exist. |

**示例：**

```ts
@Entry
@Component
struct RequestExample {
  @State btColor: Color = Color.Blue;

  build() {
    Column({ space: 20 }) {
      Column({ space: 5 }) {
        Button('Button')
          .width(200)
          .height(70)
          .fontColor(Color.White)
          .focusOnTouch(true)
          .backgroundColor(this.btColor)
          .onFocus(() => {
            this.btColor = Color.Red;
          })
          .onBlur(() => {
            this.btColor = Color.Blue;
          })
          .id("testButton")

        Divider()
          .vertical(false)
          .width("80%")
          .backgroundColor(Color.Black)
          .height(10)

        Button('requestFocus')
          .width(200)
          .height(70)
          .onClick(() => {
            this.getUIContext().getFocusController().requestFocus("testButton");
          })

        Button('requestFocus fail')
          .width(200)
          .height(70)
          .onClick(() => {
            try {
              this.getUIContext().getFocusController().requestFocus("eee");
            } catch (error) {
              console.error('requestFocus failed code is ' + error.code + ' message is ' + error.message);
            }
          })
      }
    }
    .width('100%')
    .height('100%')
  }
}
```

### activate<sup>14+</sup>

activate(isActive: boolean, autoInactive?: boolean): void

设置当前界面的[焦点激活态](../../ui/arkts-common-events-focus-event.md)。

**原子化服务API：** 从API version 14开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------- | ------- | ------- | ------- |
| isActive| boolean| 是 | 设置是否进入/退出焦点激活态。<br/>true表示设置进入焦点激活态，false表示设置退出焦点激活态。 |
| autoInactive | boolean | 否 | 设置焦点激活态退出逻辑。<br/>为true时，会自动在触摸事件、鼠标事件触发时退出，为false时，仅受开发者API控制。<br/>默认值：true |

```ts
// 该示例表示在页面加载完成时进入焦点激活态，可按方向键在button间走焦
@Entry
@Component
struct ActivateExample {
  aboutToAppear() {
    this.getUIContext().getFocusController().activate(true, false);
  }

  aboutToDisappear() {
    this.getUIContext().getFocusController().activate(false);
  }

  build() {
    Row() {
      Button('Button1')
        .width(200)
        .height(70)
        .defaultFocus(true)

      Button('Button2')
        .width(200)
        .height(70)

      Button('Button3')
        .width(200)
        .height(70)
    }
    .padding(10)
    .justifyContent(FlexAlign.SpaceBetween)
    .width(800)
  }
}
```

### setAutoFocusTransfer<sup>14+</sup>

setAutoFocusTransfer(isAutoFocusTransfer: boolean): void

设置页面切换时，新的页面是否需要主动获取焦点。

**原子化服务API：** 从API version 14开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------- | ------- | ------- | ------- |
| isAutoFocusTransfer | boolean| 是 | 设置页面切换时，新的页面是否需要主动获取焦点，例如[Router](js-apis-router.md#routerpushurldeprecated)、[Navigation](arkui-ts/ts-basic-components-navigation.md#navigation)、[Menu](arkui-ts/ts-basic-components-menu.md#menu)、[Dialog](arkui-ts/ohos-arkui-advanced-Dialog.md)、[Popup](arkui-ts/ohos-arkui-advanced-Popup.md#popup)等。true表示需要主动获取焦点，false表示不需要主动获取焦点。默认值为true。 |

```ts
@CustomDialog
struct CustomDialogExample {
  controller?: CustomDialogController;
  build() {
    Column() {
      Text('这是自定义弹窗')
        .fontSize(30)
        .height(100)
      Text('弹窗不能主动获取焦点')
        .fontSize(20)
        .height(100)
      Button('点我关闭弹窗')
        .onClick(() => {
          if (this.controller != undefined) {
            this.getUIContext().getFocusController().setAutoFocusTransfer(true);
            this.controller.close();
          }
        })
        .margin(20)
    }
  }
}
@Entry
@Component
struct CustomDialogUser {
  dialogController: CustomDialogController | null = new CustomDialogController({
    builder: CustomDialogExample({
    }),
  });
  aboutToDisappear() {
    this.dialogController = null;
  }

  build() {
    Column() {
      Button('click me')
        .onClick(() => {
          if (this.dialogController != null) {
            this.getUIContext().getFocusController().setAutoFocusTransfer(false);
            this.dialogController.open();
          }
        }).backgroundColor(0x317aff)
    }.width('100%').margin({ top: 5 })
  }
}
```

### setKeyProcessingMode<sup>15+</sup>

setKeyProcessingMode(mode: KeyProcessingMode): void

设置按键事件处理的优先级。

**原子化服务API：** 从API version 15开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| ------- | ------- | ------- | ------- |
| mode | [KeyProcessingMode](./arkui-ts/ts-universal-attributes-focus.md#keyprocessingmode15)| 是 | 按键处理模式。 |

```ts

// 该示例演示了在页面加载完成后设置走焦类型的实现方式。
@Entry
@Component
struct Index {

  aboutToAppear() {
    this.getUIContext().getFocusController().setKeyProcessingMode(KeyProcessingMode.ANCESTOR_EVENT);
  }

  build() {
    Row() {
      Row() {
        Button('Button1').id('Button1').onKeyEvent((event) => {
          console.log("Button1");
          return true;
        })
        Button('Button2').id('Button2').onKeyEvent((event) => {
          console.log("Button2");
          return true;
        })
      }
      .width('100%')
      .height('100%')
      .id('Row1')
      .onKeyEventDispatch((event) => {
        let context = this.getUIContext();
        context.getFocusController().requestFocus('Button1');
        return context.dispatchKeyEvent('Button1', event);
      })
    }
    .height('100%')
    .width('100%')
    .onKeyEventDispatch((event) => {
      if (event.type == KeyType.Down) {
        let context = this.getUIContext();
        context.getFocusController().requestFocus('Row1');
        return context.dispatchKeyEvent('Row1', event);
      }
      return true;
    })
  }
}
```

## PointerStyle<sup>12+</sup>

type PointerStyle = pointer.PointerStyle

光标样式。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.MultimodalInput.Input.Pointer

|类型|说明|
| -- | -- |
|[pointer.PointerStyle](../apis-input-kit/js-apis-pointer.md#pointerstyle) |光标样式。|

## CursorController<sup>12+</sup>
以下API需先使用UIContext中的[getCursorController()](js-apis-arkui-UIContext.md#getcursorcontroller12)方法获取CursorController实例，再通过此实例调用对应方法。

### restoreDefault<sup>12+</sup>

restoreDefault(): void

恢复默认的光标样式

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**
当光标移出绿框时，通过CursorController的restoreDefault方法恢复默认光标样式

```ts
import { pointer } from '@kit.InputKit';
import { UIContext, CursorController } from '@kit.ArkUI';

@Entry
@Component
struct CursorControlExample {
  @State text: string = '';
  cursorCustom: CursorController = this.getUIContext().getCursorController();

  build() {
    Column() {
      Row().height(200).width(200).backgroundColor(Color.Green).position({x: 150 ,y:70})
        .onHover((flag) => {
          if (flag) {
            this.cursorCustom.setCursor(pointer.PointerStyle.EAST);
          } else {
            console.info("restoreDefault");
            this.cursorCustom.restoreDefault();
          }
        })
    }.width('100%')
  }
}
```
![cursor-restoreDefault](figures/cursor-restoreDefault.gif)

### setCursor<sup>12+</sup>

setCursor(value: PointerStyle): void

更改当前的鼠标光标样式

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名     | 类型                                       | 必填   | 说明      |
| ------- | ---------------------------------------- | ---- | ------- |
| value | [PointerStyle](#pointerstyle12) | 是    | 光标样式 |

**示例：**
当光标进入蓝框时，通过CursorController的setCursor方法修改光标样式为PointerStyle.WEST

```ts
import { pointer } from '@kit.InputKit';
import { UIContext, CursorController } from '@kit.ArkUI';

@Entry
@Component
struct CursorControlExample {
  @State text: string = '';
  cursorCustom: CursorController = this.getUIContext().getCursorController();

  build() {
    Column() {
      Row().height(200).width(200).backgroundColor(Color.Blue).position({x: 100 ,y:70})
        .onHover((flag) => {
          if (flag) {
            this.cursorCustom.setCursor(pointer.PointerStyle.WEST);
          } else {
            this.cursorCustom.restoreDefault();
          }
        })
    }.width('100%')
  }
}
```
![cursor-setCursor](figures/cursor-setCursor.gif)

## ContextMenuController<sup>12+</sup>
以下API需先使用UIContext中的[getContextMenuController()](js-apis-arkui-UIContext.md#getcontextmenucontroller12)方法获取ContextMenuController实例，再通过此实例调用对应方法。

### close<sup>12+</sup>

close(): void

关闭菜单

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**示例：**
通过定时器触发，调用ContextMenuController的close方法关闭菜单

```ts
import { ContextMenuController } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  menu: ContextMenuController = this.getUIContext().getContextMenuController();

  @Builder MenuBuilder() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Button('Test ContextMenu1 Close')
      Divider().strokeWidth(2).margin(5).color(Color.Black)
      Button('Test ContextMenu2')
      Divider().strokeWidth(2).margin(5).color(Color.Black)
      Button('Test ContextMenu3')
    }
    .width(200)
    .height(160)
  }

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Button("启动定时器").onClick(()=>
      {
        setTimeout(() => {
          this.menu.close();
        }, 10000);
      })

      Column() {
        Text("Test ContextMenu close")
          .fontSize(20)
          .width('100%')
          .height(500)
          .backgroundColor(0xAFEEEE)
          .textAlign(TextAlign.Center)
      }
      .bindContextMenu(this.MenuBuilder, ResponseType.LongPress)
    }
    .width('100%')
    .height('100%')
  }
}
```

![contextMenuController_close](figures/contextMenuController_close.gif)

## MeasureUtils<sup>12+</sup>

以下API需先使用UIContext中的[getMeasureUtils()](js-apis-arkui-UIContext.md#getmeasureutils12)方法获取MeasureUtils实例，再通过此实例调用对应方法。

> **说明：**
>
>
> 如需更多测算文本参数，建议使用图形对应测算接口[Paragraph](../apis-arkgraphics2d/js-apis-graphics-text.md#paragraph)接口。
>
> 调用文本计算接口时，不推荐同时用[ApplicationContext.setFontSizeScale](../apis-ability-kit/js-apis-inner-application-applicationContext.md#applicationcontextsetfontsizescale13)设置应用字体大小缩放比例。为了确保时序正确性，建议开发者自行监听字体缩放变化，以保证测算结果的准确性。
>
> 在测算裁剪后的文本时，由于某些Unicode字符（如emoji）的码位长度大于1，直接按字符串长度裁剪会导致不准确的结果。建议基于Unicode码点进行迭代处理，避免错误截断字符，确保测算结果准确。

### measureText<sup>12+</sup>

measureText(options: MeasureOptions): number

计算指定文本单行布局下的宽度。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名     | 类型                              | 必填   | 说明        |
| ------- | ------------------------------- | ---- | --------- |
| options | [MeasureOptions](js-apis-measure.md#measureoptions) | 是    | 被计算文本描述信息。 |

**返回值：**

| 类型          | 说明       |
| ------------  | --------- |
| number        | 文本宽度。<br/>**说明:**<br/>浮点数会向上取整。<br/>单位：px |


**示例：**
通过MeasureUtils的measureText方法获取"Hello World"文字的宽度。

```ts
import { MeasureUtils } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State uiContext: UIContext = this.getUIContext();
  @State uiContextMeasure: MeasureUtils = this.uiContext.getMeasureUtils();
  @State textWidth: number = this.uiContextMeasure.measureText({
    textContent: "Hello World",
    fontSize: '50px'
  });

  build() {
    Row() {
      Column() {
        Text(`The width of 'Hello World': ${this.textWidth}`)
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### measureTextSize<sup>12+</sup>

measureTextSize(options: MeasureOptions): SizeOptions

计算指定文本单行布局下的宽度和高度。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名     | 类型                              | 必填   | 说明        |
| ------- | ------------------------------- | ---- | --------- |
| options | [MeasureOptions](js-apis-measure.md#measureoptions) | 是    | 被计算文本描述信息。 |

**返回值：**

| 类型          | 说明       |
| ------------  | --------- |
| [SizeOptions](arkui-ts/ts-types.md#sizeoptions)   | 返回文本所占布局宽度和高度。<br/>**说明:**<br/>没有传参constraintWidth的情况下，文本宽度返回值浮点数会向上取整。<br/>文本宽度以及高度返回值单位均为px。 |


**示例：**
通过MeasureUtils的measureTextSize方法获取"Hello World"文字的宽度和高度。

```ts
import { MeasureUtils } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State uiContext: UIContext = this.getUIContext();
  @State uiContextMeasure: MeasureUtils = this.uiContext.getMeasureUtils();
  textSize: SizeOptions = this.uiContextMeasure.measureTextSize({
    textContent: "Hello World",
    fontSize: '50px'
  });
  build() {
    Row() {
      Column() {
        Text(`The width of 'Hello World': ${this.textSize.width}`)
        Text(`The height of 'Hello World': ${this.textSize.height}`)
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

## ComponentSnapshot<sup>12+</sup>

以下API需先使用UIContext中的[getComponentSnapshot()](js-apis-arkui-UIContext.md#getcomponentsnapshot12)方法获取ComponentSnapshot对象，再通过此实例调用对应方法。

缩放、平移、旋转等图形变换属性只对被截图组件的子组件生效；对目标组件本身应用图形变换属性不生效，显示的是还是图形变换前的效果。

### get<sup>12+</sup>

get(id: string, callback: AsyncCallback<image.PixelMap>, options?: componentSnapshot.SnapshotOptions): void

获取已加载的组件的截图，传入组件的[组件标识](arkui-ts/ts-universal-attributes-component-id.md#组件标识)，找到对应组件进行截图。通过回调返回结果。

> **说明：** 
>
> 截图会获取最近一帧的绘制内容。如果在组件触发更新的同时调用截图，更新的渲染内容不会被截取到，截图会返回上一帧的绘制内容。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| id       | string                                                       | 是   | 目标组件的[组件标识](arkui-ts/ts-universal-attributes-component-id.md#组件标识)。<br/>**说明：** 不支持未挂树组件，当传入的组件标识是离屏或缓存未挂树的节点时，系统不会对其进行截图。 |
| callback | [AsyncCallback](../apis-basic-services-kit/js-apis-base.md#asynccallback)&lt;image.[PixelMap](../apis-image-kit/js-apis-image.md#pixelmap7)&gt; | 是   | 截图返回结果的回调。                                         |
| options<sup>12+</sup>       | [componentSnapshot.SnapshotOptions](js-apis-arkui-componentSnapshot.md#snapshotoptions12)            | 否    | 截图相关的自定义参数。 |

**错误码：** 

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)错误码和[截图错误码](errorcode-snapshot.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed. |
| 100001   | Invalid ID.                                                  |

**示例：** 

```ts
import { image } from '@kit.ImageKit';
import { UIContext } from '@kit.ArkUI';

@Entry
@Component
struct SnapshotExample {
  @State pixmap: image.PixelMap | undefined = undefined;
  uiContext: UIContext = this.getUIContext();
  build() {
    Column() {
      Row() {
        Image(this.pixmap).width(150).height(150).border({ color: Color.Black, width: 2 }).margin(5)
        Image($r('app.media.img')).autoResize(true).width(150).height(150).margin(5).id("root")
      }
      Button("click to generate UI snapshot")
        .onClick(() => {
          this.uiContext.getComponentSnapshot().get("root", (error: Error, pixmap: image.PixelMap) => {
            if (error) {
              console.error("error: " + JSON.stringify(error));
              return;
            }
            this.pixmap = pixmap;
          }, { scale: 2, waitUntilRenderFinished: true });
        }).margin(10)
    }
    .width('100%')
    .height('100%')
    .alignItems(HorizontalAlign.Center)
  }
}
```

### get<sup>12+</sup>

get(id: string, options?: componentSnapshot.SnapshotOptions): Promise<image.PixelMap>

获取已加载的组件的截图，传入组件的[组件标识](arkui-ts/ts-universal-attributes-component-id.md#组件标识)，找到对应组件进行截图。通过Promise返回结果。

> **说明：**
>
> 截图会获取最近一帧的绘制内容。如果在组件触发更新的同时调用截图，更新的渲染内容不会被截取到，截图会返回上一帧的绘制内容。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型   | 必填 | 说明                                                         |
| ------ | ------ | ---- | ------------------------------------------------------------ |
| id     | string | 是   | 目标组件的[组件标识](arkui-ts/ts-universal-attributes-component-id.md#组件标识)。<br/>**说明：** 不支持未挂树组件，当传入的组件标识是离屏或缓存未挂树的节点时，系统不会对其进行截图。 |
| options<sup>12+</sup>       | [componentSnapshot.SnapshotOptions](js-apis-arkui-componentSnapshot.md#snapshotoptions12)            | 否    | 截图相关的自定义参数。 |

**返回值：**

| 类型                                                         | 说明             |
| ------------------------------------------------------------ | ---------------- |
| Promise&lt;image.[PixelMap](../apis-image-kit/js-apis-image.md#pixelmap7)&gt; | 截图返回的结果。 |

**错误码：** 

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)错误码和[截图错误码](errorcode-snapshot.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed. |
| 100001   | Invalid ID.                                                  |

**示例：** 

```ts
import { image } from '@kit.ImageKit';
import { UIContext } from '@kit.ArkUI';

@Entry
@Component
struct SnapshotExample {
  @State pixmap: image.PixelMap | undefined = undefined;
  uiContext: UIContext = this.getUIContext();

  build() {
    Column() {
      Row() {
        Image(this.pixmap).width(150).height(150).border({ color: Color.Black, width: 2 }).margin(5)
        Image($r('app.media.icon')).autoResize(true).width(150).height(150).margin(5).id("root")
      }
      Button("click to generate UI snapshot")
        .onClick(() => {
          this.uiContext.getComponentSnapshot()
            .get("root", { scale: 2, waitUntilRenderFinished: true })
            .then((pixmap: image.PixelMap) => {
              this.pixmap = pixmap;
            })
            .catch((err: Error) => {
              console.error("error: " + err);
            })
        }).margin(10)
    }
    .width('100%')
    .height('100%')
    .alignItems(HorizontalAlign.Center)
  }
}
```

### createFromBuilder<sup>12+</sup>

createFromBuilder(builder: CustomBuilder, callback: AsyncCallback<image.PixelMap>, delay?: number, checkImageStatus?: boolean, options?: componentSnapshot.SnapshotOptions): void

传入[CustomBuilder](arkui-ts/ts-types.md#custombuilder8)自定义组件，系统对其进行离屏构建后进行截图，并通过回调返回结果。
> **说明：** 
>
> 由于需要等待组件构建、渲染成功，离屏截图的回调有500ms以内的延迟，不适宜使用在对性能敏感的场景。
>
> 部分执行耗时任务的组件可能无法及时在截图前加载完成，因此会截取不到加载成功后的图像。例如：加载网络图片的[Image](arkui-ts/ts-basic-components-image.md)组件、[Web](../apis-arkweb/ts-basic-components-web.md)组件。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| builder  | [CustomBuilder](arkui-ts/ts-types.md#custombuilder8)         | 是   | 自定义组件构建函数。<br/>**说明：** 不支持全局builder。<br/>builder的根组件宽高为0时，截图操作会失败并抛出100001错误码。      |
| callback | [AsyncCallback](../apis-basic-services-kit/js-apis-base.md#asynccallback)&lt;image.[PixelMap](../apis-image-kit/js-apis-image.md#pixelmap7)&gt; | 是   | 截图返回结果的回调。支持在回调中获取离屏组件绘制区域坐标和大小。 |
| delay<sup>12+</sup>   | number | 否    | 指定触发截图指令的延迟时间。当布局中使用了图片组件时，需要指定延迟时间，以便系统解码图片资源。资源越大，解码需要的时间越长，建议尽量使用不需要解码的PixelMap资源。<br/> 当使用PixelMap资源或对Image组件设置syncload为true时，可以配置delay为0，强制不等待触发截图。该延迟时间并非指接口从调用到返回的时间，由于系统需要对传入的builder进行临时离屏构建，因此返回的时间通常要比该延迟时间长。<br/>**说明：** 截图接口传入的builder中，不应使用状态变量控制子组件的构建，如果必须要使用，在调用截图接口时，也不应再有变化，以避免出现截图不符合预期的情况。<br/> 默认值：300 <br/> 单位：毫秒 <br/> 取值范围：[0, +∞)，小于0时按默认值处理。 |
| checkImageStatus<sup>12+</sup>  | boolean | 否    | 指定是否允许在截图之前，校验图片解码状态。如果为true，则会在截图之前检查所有Image组件是否已经解码完成，如果没有完成检查，则会放弃截图并返回异常。<br/>默认值：false|
| options<sup>12+</sup>       | [componentSnapshot.SnapshotOptions](js-apis-arkui-componentSnapshot.md#snapshotoptions12) | 否    | 截图相关的自定义参数。 |

**错误码：** 

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)错误码和[截图错误码](errorcode-snapshot.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed. |
| 100001   | The builder is not a valid build function.                   |
| 160001   | An image component in builder is not ready for taking a snapshot. The check for the ready state is required when the checkImageStatus option is enabled. |

**示例：** 

```ts
import { image } from '@kit.ImageKit';
import { UIContext } from '@kit.ArkUI';

@Entry
@Component
struct ComponentSnapshotExample {
  @State pixmap: image.PixelMap | undefined = undefined;
  uiContext: UIContext = this.getUIContext();
  @Builder
  RandomBuilder() {
    Flex({ direction: FlexDirection.Column, justifyContent: FlexAlign.Center, alignItems: ItemAlign.Center }) {
      Text('Test menu item 1')
        .fontSize(20)
        .width(100)
        .height(50)
        .textAlign(TextAlign.Center)
      Divider().height(10)
      Text('Test menu item 2')
        .fontSize(20)
        .width(100)
        .height(50)
        .textAlign(TextAlign.Center)
    }
    .width(100)
    .id("builder")
  }

  build() {
    Column() {
      Button("click to generate UI snapshot")
        .onClick(() => {
          this.uiContext.getComponentSnapshot().createFromBuilder(() => {
            this.RandomBuilder()
          },
            (error: Error, pixmap: image.PixelMap) => {
              if (error) {
                console.error("error: " + JSON.stringify(error));
                return;
              }
              this.pixmap = pixmap;
            }, 320, true, { scale: 2, waitUntilRenderFinished: true });
        })
      Image(this.pixmap)
        .margin(10)
        .height(200)
        .width(200)
        .border({ color: Color.Black, width: 2 })
    }.width('100%').margin({ left: 10, top: 5, bottom: 5 }).height(300)
  }
}
```

### createFromBuilder<sup>12+</sup>

createFromBuilder(builder: CustomBuilder, delay?: number, checkImageStatus?: boolean, options?: componentSnapshot.SnapshotOptions): Promise<image.PixelMap>

传入[CustomBuilder](arkui-ts/ts-types.md#custombuilder8)自定义组件，系统对其进行离屏构建后进行截图，并通过回调返回结果。

> **说明：** 
>
> 由于需要等待组件构建、渲染成功，离屏截图的回调有500ms以内的延迟，不适宜使用在对性能敏感的场景。
>
> 部分执行耗时任务的组件可能无法及时在截图前加载完成，因此会截取不到加载成功后的图像。例如：加载网络图片的[Image](arkui-ts/ts-basic-components-image.md)组件、[Web](../apis-arkweb/ts-basic-components-web.md)组件。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名  | 类型                                                 | 必填 | 说明                                                    |
| ------- | ---------------------------------------------------- | ---- | ------------------------------------------------------- |
| builder | [CustomBuilder](arkui-ts/ts-types.md#custombuilder8) | 是   | 自定义组件构建函数。<br/>**说明：** 不支持全局builder。<br/>builder的根组件宽高为0时，截图操作会失败并抛出100001错误码。 |
| delay<sup>12+</sup>   | number | 否    | 指定触发截图指令的延迟时间。当布局中使用了图片组件时，需要指定延迟时间，以便系统解码图片资源。资源越大，解码需要的时间越长，建议尽量使用不需要解码的PixelMap资源。<br/> 当使用PixelMap资源或对Image组件设置syncload为true时，可以配置delay为0，强制不等待触发截图。该延迟时间并非指接口从调用到返回的时间，由于系统需要对传入的builder进行临时离屏构建，因此返回的时间通常要比该延迟时间长。<br/>**说明：** 截图接口传入的builder中，不应使用状态变量控制子组件的构建，如果必须要使用，在调用截图接口时，也不应再有变化，以避免出现截图不符合预期的情况。<br/> 默认值：300 <br/> 单位：毫秒<br/> 取值范围：[0, +∞)，小于0时按默认值处理。|
| checkImageStatus<sup>12+</sup>  | boolean | 否    | 指定是否允许在截图之前，校验图片解码状态。如果为true，则会在截图之前检查所有Image组件是否已经解码完成，如果没有完成检查，则会放弃截图并返回异常。<br/>默认值：false|
| options<sup>12+</sup>       | [componentSnapshot.SnapshotOptions](js-apis-arkui-componentSnapshot.md#snapshotoptions12)           | 否    | 截图相关的自定义参数。 |

**返回值：**

| 类型                                                         | 说明             |
| ------------------------------------------------------------ | ---------------- |
| Promise&lt;image.[PixelMap](../apis-image-kit/js-apis-image.md#pixelmap7)&gt; | 截图返回的结果。 |

**错误码：** 

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)错误码和[截图错误码](errorcode-snapshot.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed. |
| 100001   | The builder is not a valid build function.                   |
| 160001   | An image component in builder is not ready for taking a snapshot. The check for the ready state is required when the checkImageStatus option is enabled. |

**示例：** 

```ts
import { image } from '@kit.ImageKit';
import { UIContext } from '@kit.ArkUI';

@Entry
@Component
struct ComponentSnapshotExample {
  @State pixmap: image.PixelMap | undefined = undefined;
  uiContext: UIContext = this.getUIContext();
  @Builder
  RandomBuilder() {
    Flex({ direction: FlexDirection.Column, justifyContent: FlexAlign.Center, alignItems: ItemAlign.Center }) {
      Text('Test menu item 1')
        .fontSize(20)
        .width(100)
        .height(50)
        .textAlign(TextAlign.Center)
      Divider().height(10)
      Text('Test menu item 2')
        .fontSize(20)
        .width(100)
        .height(50)
        .textAlign(TextAlign.Center)
    }
    .width(100)
    .id("builder")
  }
  build() {
    Column() {
      Button("click to generate UI snapshot")
        .onClick(() => {
          this.uiContext.getComponentSnapshot()
            .createFromBuilder(() => {
              this.RandomBuilder()
            }, 320, true, { scale: 2, waitUntilRenderFinished: true })
            .then((pixmap: image.PixelMap) => {
              this.pixmap = pixmap;
            })
            .catch((err: Error) => {
              console.error("error: " + err);
            })
        })
      Image(this.pixmap)
        .margin(10)
        .height(200)
        .width(200)
        .border({ color: Color.Black, width: 2 })
    }.width('100%').margin({ left: 10, top: 5, bottom: 5 }).height(300)
  }
}
```

### getSync<sup>12+</sup>

getSync(id: string, options?: componentSnapshot.SnapshotOptions): image.PixelMap

获取已加载的组件的截图，传入组件的[组件标识](arkui-ts/ts-universal-attributes-component-id.md#组件标识)，找到对应组件进行截图。同步等待截图完成返回[PixelMap](../apis-image-kit/js-apis-image.md#pixelmap7)。

> **说明：**
>
> 截图会获取最近一帧的绘制内容。如果在组件触发更新的同时调用截图，更新的渲染内容不会被截取到，截图会返回上一帧的绘制内容。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名  | 类型     | 必填   | 说明                                       |
| ---- | ------ | ---- | ---------------------------------------- |
| id   | string | 是    | 目标组件的[组件标识](arkui-ts/ts-universal-attributes-component-id.md#组件标识)。 <br/>**说明：** 不支持未挂树组件，当传入的组件标识是离屏或缓存未挂树的节点时，系统不会对其进行截图。|
| options       | [componentSnapshot.SnapshotOptions](js-apis-arkui-componentSnapshot.md#snapshotoptions12)            | 否    | 截图相关的自定义参数。 |

**返回值：**

| 类型                            | 说明       |
| ----------------------------- | -------- |
| image.[PixelMap](../apis-image-kit/js-apis-image.md#pixelmap7) | 截图返回的结果。 |

**错误码：** 

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)错误码和[截图错误码](errorcode-snapshot.md)。

| 错误码ID  | 错误信息                |
| ------ | ------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001 | Invalid ID. |
| 160002 | Timeout. |

**示例：**

```ts
import { image } from '@kit.ImageKit';
import { UIContext } from '@kit.ArkUI';

@Entry
@Component
struct SnapshotExample {
  @State pixmap: image.PixelMap | undefined = undefined;

  build() {
    Column() {
      Row() {
        Image(this.pixmap).width(200).height(200).border({ color: Color.Black, width: 2 }).margin(5)
        Image($r('app.media.img')).autoResize(true).width(200).height(200).margin(5).id("root")
      }
      Button("click to generate UI snapshot")
        .onClick(() => {
          try {
            let pixelmap = this.getUIContext().getComponentSnapshot().getSync("root", { scale: 2, waitUntilRenderFinished: true });
            this.pixmap = pixelmap;
          } catch (error) {
            console.error("getSync errorCode: " + error.code + " message: " + error.message);
          }
        }).margin(10)
    }
    .width('100%')
    .height('100%')
    .alignItems(HorizontalAlign.Center)
  }
}
```

### getWithUniqueId<sup>15+</sup>

getWithUniqueId(uniqueId: number, options?: componentSnapshot.SnapshotOptions): Promise<image.PixelMap>

获取已加载的组件的截图，传入组件的[uniqueId](js-apis-arkui-frameNode.md#getuniqueid12)，找到对应组件进行截图。通过Promise返回结果。

> **说明：**
>
> 截图会获取最近一帧的绘制内容。如果在组件触发更新的同时调用截图，更新的渲染内容不会被截取到，截图会返回上一帧的绘制内容。

**原子化服务API：** 从API version 15开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名  | 类型     | 必填   | 说明                                       |
| ---- | ------ | ---- | ---------------------------------------- |
| uniqueId   | number | 是    | 目标组件的[uniqueId](js-apis-arkui-frameNode.md#getuniqueid12) <br/>**说明：** 不支持未挂树组件，当传入的组件标识是离屏或缓存未挂树的节点时，系统不会对其进行截图。|
| options       | [componentSnapshot.SnapshotOptions](js-apis-arkui-componentSnapshot.md#snapshotoptions12)            | 否    | 截图相关的自定义参数。 |

**返回值：**

| 类型                                                         | 说明             |
| ------------------------------------------------------------ | ---------------- |
| Promise&lt;image.[PixelMap](../apis-image-kit/js-apis-image.md#pixelmap7)&gt; | 截图返回的结果。 |

**错误码：** 

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)错误码和[截图错误码](errorcode-snapshot.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed. |
| 100001   | Invalid ID.                                                  |

**示例：**

```ts
import { NodeController, FrameNode, typeNode } from '@kit.ArkUI';
import { image } from '@kit.ImageKit';
import { UIContext } from '@kit.ArkUI';

class MyNodeController extends NodeController {
  public node: FrameNode | null = null;

  public imageNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.node = new FrameNode(uiContext);
    this.node.commonAttribute.width('100%').height('100%');

    let image = typeNode.createNode(uiContext, 'Image');
    image.initialize($r('app.media.img')).width('100%').height('100%').autoResize(true);
    this.imageNode = image;

    this.node.appendChild(image);
    return this.node;
  }
}

@Entry
@Component
struct SnapshotExample {
  private myNodeController: MyNodeController = new MyNodeController();

  @State pixmap: image.PixelMap | undefined = undefined;

  build() {
    Column() {
      Row() {
        Image(this.pixmap).width(200).height(200).border({ color: Color.Black, width: 2 }).margin(5)
        NodeContainer(this.myNodeController).width(200).height(200).margin(5)
      }
      Button("UniqueId get snapshot")
        .onClick(() => {
          try {
            this.getUIContext()
              .getComponentSnapshot()
              .getWithUniqueId(this.myNodeController.imageNode?.getUniqueId(), { scale: 2, waitUntilRenderFinished: true })
              .then((pixmap: image.PixelMap) => {
                this.pixmap = pixmap;
              })
              .catch((err: Error) => {
                console.log("error: " + err);
              })
          } catch (error) {
            console.error("UniqueId get snapshot Error: " + JSON.stringify(error));
          }
        }).margin(10)
    }
    .width('100%')
    .height('100%')
    .alignItems(HorizontalAlign.Center)
  }
}
```

### getSyncWithUniqueId<sup>15+</sup>

getSyncWithUniqueId(uniqueId: number, options?: componentSnapshot.SnapshotOptions): image.PixelMap

获取已加载的组件的截图，传入组件的[uniqueId](js-apis-arkui-frameNode.md#getuniqueid12)，找到对应组件进行截图。同步等待截图完成返回[PixelMap](../apis-image-kit/js-apis-image.md#pixelmap7)。

> **说明：**
>
> 截图会获取最近一帧的绘制内容。如果在组件触发更新的同时调用截图，更新的渲染内容不会被截取到，截图会返回上一帧的绘制内容。

**原子化服务API：** 从API version 15开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名  | 类型     | 必填   | 说明                                       |
| ---- | ------ | ---- | ---------------------------------------- |
| uniqueId   | number | 是    | 目标组件的[uniqueId](js-apis-arkui-frameNode.md#getuniqueid12)。<br/>**说明：** 不支持未挂树组件，当传入的组件标识是离屏或缓存未挂树的节点时，系统不会对其进行截图。|
| options       | [componentSnapshot.SnapshotOptions](js-apis-arkui-componentSnapshot.md#snapshotoptions12)            | 否    | 截图相关的自定义参数。 |

**返回值：**

| 类型                            | 说明       |
| ----------------------------- | -------- |
| image.[PixelMap](../apis-image-kit/js-apis-image.md#pixelmap7) | 截图返回的结果。 |

**错误码：** 

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)错误码和[截图错误码](errorcode-snapshot.md)。

| 错误码ID  | 错误信息                |
| ------ | ------------------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100001 | Invalid ID. |
| 160002 | Timeout. |

**示例：**

```ts
import { NodeController, FrameNode, typeNode } from '@kit.ArkUI';
import { image } from '@kit.ImageKit';
import { UIContext } from '@kit.ArkUI';

class MyNodeController extends NodeController {
  public node: FrameNode | null = null;

  public imageNode: FrameNode | null = null;

  makeNode(uiContext: UIContext): FrameNode | null {
    this.node = new FrameNode(uiContext);
    this.node.commonAttribute.width('100%').height('100%');

    let image = typeNode.createNode(uiContext, 'Image');
    image.initialize($r('app.media.img')).width('100%').height('100%').autoResize(true);
    this.imageNode = image;

    this.node.appendChild(image);
    return this.node;
  }
}

@Entry
@Component
struct SnapshotExample {
  private myNodeController: MyNodeController = new MyNodeController();

  @State pixmap: image.PixelMap | undefined = undefined;

  build() {
    Column() {
      Row() {
        Image(this.pixmap).width(200).height(200).border({ color: Color.Black, width: 2 }).margin(5)
        NodeContainer(this.myNodeController).width(200).height(200).margin(5)
      }
      Button("UniqueId getSync snapshot")
        .onClick(() => {
          try {
            this.pixmap = this.getUIContext()
              .getComponentSnapshot()
              .getSyncWithUniqueId(this.myNodeController.imageNode?.getUniqueId(), { scale: 2, waitUntilRenderFinished: true });
          } catch (error) {
            console.error("UniqueId getSync snapshot Error: " + JSON.stringify(error));
          }
        }).margin(10)
    }
    .width('100%')
    .height('100%')
    .alignItems(HorizontalAlign.Center)
  }
}
```

### createFromComponent<sup>18+</sup>

createFromComponent\<T extends Object>(content: ComponentContent\<T>, delay?: number, checkImageStatus?: boolean, options?: componentSnapshot.SnapshotOptions): Promise<image.PixelMap>

将传入的content对象进行截图，并通过Promise返回结果。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名   | 类型                                                         | 必填 | 说明                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| content  | [ComponentContent\<T>](./js-apis-arkui-ComponentContent.md)         | 是   | 当前UIContext显示的组件内容。      |
| delay   | number | 否    | 指定触发截图指令的延迟时间。当布局中使用了图片组件时，需要指定延迟时间，以便系统解码图片资源。资源越大，解码需要的时间越长，建议尽量使用不需要解码的PixelMap资源。<br/> 当使用PixelMap资源或对Image组件设置syncload为true时，可以配置delay为0，强制不等待触发截图。该延迟时间并非指接口从调用到返回的时间，由于系统需要对传入的builder进行临时离屏构建，因此返回的时间通常要比该延迟时间长。<br/>**说明：** 截图接口传入的builder中，不应使用状态变量控制子组件的构建，如果必须要使用，在调用截图接口时，也不应再有变化，以避免出现截图不符合预期的情况。<br/> 取值范围：[0,+∞) ，小于0时按默认值处理。<br/>默认值：300 <br/> 单位：毫秒|
| checkImageStatus  | boolean | 否    | 指定是否允许在截图之前，校验图片解码状态。如果为true，则会在截图之前检查所有Image组件是否已经解码完成，如果没有完成检查，则会放弃截图并返回异常。<br/>默认值：false|
| options       | [componentSnapshot.SnapshotOptions](js-apis-arkui-componentSnapshot.md#snapshotoptions12) | 否    | 截图相关的自定义参数。可以指定截图时图形侧绘制pixelmap的缩放比例与是否强制等待系统执行截图指令前所有绘制指令都执行完成之后再截图。 |

**返回值：**

| 类型                            | 说明       |
| ----------------------------- | -------- |
| Promise<image.[PixelMap](../apis-image-kit/js-apis-image.md#pixelmap7)>  | 截图返回的结果。 |

**错误码：** 

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)错误码和[截图错误码](errorcode-snapshot.md)。

| 错误码ID | 错误信息                                                     |
| -------- | ------------------------------------------------------------ |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed. |
| 100001   | The builder is not a valid build function.                   |
| 160001   | An image component in builder is not ready for taking a snapshot. The check for the ready state is required when the checkImageStatus option is enabled. |

**示例：** 

```ts
import { image } from '@kit.ImageKit';
import { ComponentContent } from '@kit.ArkUI';

class Params {
  text: string | undefined | null  = "";

  constructor(text: string | undefined | null ) {
    this.text = text;
  }
}

@Builder
function buildText(params: Params) {
  ReusableChildComponent({ text: params.text })
}

@Component
struct ReusableChildComponent {
  @Prop text: string | undefined | null  = "";

  aboutToReuse(params: Record<string, object>) {
    console.log("ReusableChildComponent Reusable " + JSON.stringify(params));
  }

  aboutToRecycle(): void {
    console.log("ReusableChildComponent aboutToRecycle " + this.text);
  }

  build() {
    Column() {
      Text(this.text)
        .fontSize(90)
        .fontWeight(FontWeight.Bold)
        .margin({ bottom: 36 })
        .width('100%')
        .height('100%')
    }.backgroundColor('#FFF0F0F0')
  }
}

@Entry
@Component
struct Index {
  @State pixmap: image.PixelMap | undefined = undefined;
  @State message: string | undefined | null = "hello";
  uiContext: UIContext = this.getUIContext();

  build() {
    Row() {
      Column() {
        Button("点击生成组件截图")
          .onClick(() => {
            let uiContext = this.getUIContext();
            let contentNode = new ComponentContent(uiContext, wrapBuilder(buildText), new Params(this.message));
            this.uiContext.getComponentSnapshot()
              .createFromComponent(contentNode
                , 320, true, { scale: 2, waitUntilRenderFinished: true })
              .then((pixmap: image.PixelMap) => {
                this.pixmap = pixmap;
              })
              .catch((err: Error) => {
                console.error("error: " + err);
              })
          })
        Image(this.pixmap)
          .margin(10)
          .height(200)
          .width(200)
          .border({ color: Color.Black, width: 2 })
      }.width('100%').margin({ left: 10, top: 5, bottom: 5 }).height(300)
    }
    .width('100%')
    .height('100%')
  }
}
```

## FrameCallback<sup>12+</sup>

用于设置下一帧渲染时需要执行的任务。需要配合[UIContext](#uicontext)中的[postFrameCallback](#postframecallback12)和[postDelayedFrameCallback](#postdelayedframecallback12)使用。开发者需要继承该类并重写[onFrame](#onframe12)或[onIdle](#onidle12)方法，实现具体的业务逻辑。

### onFrame<sup>12+</sup>

onFrame(frameTimeInNano: number): void

在下一帧进行渲染时，该方法将被执行。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名  | 类型                                                 | 必填 | 说明                                                    |
| ------- | ---------------------------------------------------- | ---- | ------------------------------------------------------- |
| frameTimeInNano | number | 是   | 下一帧渲染开始执行的时间，以纳秒为单位。<br/>取值范围：[0, +∞) |

**示例：**

```ts
import { FrameCallback } from '@kit.ArkUI';

class MyFrameCallback extends FrameCallback {
  private tag: string;

  constructor(tag: string) {
    super();
    this.tag = tag;
  }

  onFrame(frameTimeNanos: number) {
    console.info('MyFrameCallback ' + this.tag + ' ' + frameTimeNanos.toString());
  }
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('点击触发postFrameCallback')
          .onClick(() => {
            this.getUIContext().postFrameCallback(new MyFrameCallback("normTask"));
          })
        Button('点击触发postDelayedFrameCallback')
          .onClick(() => {
            this.getUIContext().postDelayedFrameCallback(new MyFrameCallback("delayTask"), 5);
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

### onIdle<sup>12+</sup>

onIdle(timeLeftInNano: number): void

在下一帧渲染结束时，如果距离下一个Vsync信号到来还有1ms以上的剩余时间，该方法将被执行，否则将顺延至后面的帧。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名  | 类型                                                 | 必填 | 说明                                                    |
| ------- | ---------------------------------------------------- | ---- | ------------------------------------------------------- |
| timeLeftInNano | number | 是   | 这一帧剩余的空闲时间，以纳秒为单位。<br/>取值范围：[0, +∞) |

**示例：**

```ts
import { FrameCallback } from '@ohos.arkui.UIContext';

class MyIdleCallback extends FrameCallback {
  private tag: string;

  constructor(tag: string) {
    super();
    this.tag = tag;
  }

  onIdle(timeLeftInNano: number) {
    console.info('MyIdleCallback ' + this.tag + ' ' + timeLeftInNano.toString());
  }
}

@Entry
@Component
struct Index {
  build() {
    Row() {
      Column() {
        Button('点击触发postFrameCallback')
          .onClick(() => {
            this.getUIContext().postFrameCallback(new MyIdleCallback("normTask"));
          })
        Button('点击触发postDelayedFrameCallback')
          .onClick(() => {
            this.getUIContext().postDelayedFrameCallback(new MyIdleCallback("delayTask"), 5);
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

## DynamicSyncScene<sup>12+</sup>

以下接口需先使用UIContext中的requireDynamicSyncScene()方法获取DynamicSyncScene对象，再通过此实例调用对应方法。

### setFrameRateRange<sup>12+</sup>

setFrameRateRange(range: ExpectedFrameRateRange): void

设置期望帧率范围。

最终结果不一定是设置的帧率，会由系统能力做综合决策，尽量满足开发者的设置帧率。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：**  SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名      | 类型         | 必填   | 说明   |
| -------- | ---------- | ---- | ---- |
| range | [ExpectedFrameRateRange](../apis-arkui/arkui-ts/ts-explicit-animation.md#expectedframeraterange11)| 是    | 设置期望的帧率范围。<br />默认值:{min:0, max:120, expected: 120} |

**示例：**

```ts
import { SwiperDynamicSyncSceneType, SwiperDynamicSyncScene } from '@kit.ArkUI';

@Entry
@Component
struct Frame {
  @State ANIMATION: ExpectedFrameRateRange = { min: 0, max: 120, expected: 90 };
  @State GESTURE: ExpectedFrameRateRange = { min: 0, max: 120, expected: 30};
  private scenes: SwiperDynamicSyncScene[] = [];

  build() {
    Column() {
      Text("动画"+ JSON.stringify(this.ANIMATION))
      Text("跟手"+ JSON.stringify(this.GESTURE))
      Row(){
        Swiper() {
          Text("one")
          Text("two")
          Text("three")
        }
        .width('100%')
        .height('300vp')
        .id("dynamicSwiper")
        .backgroundColor(Color.Blue)
        .autoPlay(true)
        .onAppear(()=>{
          this.scenes = this.getUIContext().requireDynamicSyncScene("dynamicSwiper") as SwiperDynamicSyncScene[];
        })
      }

      Button("set frame")
        .onClick(() => {
          this.scenes.forEach((scenes: SwiperDynamicSyncScene) => {

            if (scenes.type == SwiperDynamicSyncSceneType.ANIMATION) {
              scenes.setFrameRateRange(this.ANIMATION);
            }

            if (scenes.type == SwiperDynamicSyncSceneType.GESTURE) {
              scenes.setFrameRateRange(this.GESTURE);
            }
          });
        })
    }
  }
}
```

### getFrameRateRange<sup>12+</sup>

getFrameRateRange(): ExpectedFrameRateRange

获取期望帧率范围。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：**  SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型                  | 说明      |
| ------------------- | ------- |
| [ExpectedFrameRateRange](../apis-arkui/arkui-ts/ts-explicit-animation.md#expectedframeraterange11) | 期望帧率范围。|

**示例：**

```ts
import { SwiperDynamicSyncSceneType, SwiperDynamicSyncScene } from '@kit.ArkUI';

@Entry
@Component
struct Frame {
  @State ANIMATION: ExpectedFrameRateRange = { min: 0, max: 120, expected: 90 };
  @State GESTURE: ExpectedFrameRateRange = { min: 0, max: 120, expected: 30 };
  private scenes: SwiperDynamicSyncScene[] = [];

  build() {
    Column() {
      Text("动画"+ JSON.stringify(this.ANIMATION))
      Text("跟手"+ JSON.stringify(this.GESTURE))
      Row(){
        Swiper() {
          Text("one")
          Text("two")
          Text("three")
        }
        .width('100%')
        .height('300vp')
        .id("dynamicSwiper")
        .backgroundColor(Color.Blue)
        .autoPlay(true)
        .onAppear(() => {
          this.scenes = this.getUIContext().requireDynamicSyncScene("dynamicSwiper") as SwiperDynamicSyncScene[];
        })
      }

      Button("set frame")
        .onClick(() => {
          this.scenes.forEach((scenes: SwiperDynamicSyncScene) => {

            if (scenes.type == SwiperDynamicSyncSceneType.ANIMATION) {
              scenes.setFrameRateRange(this.ANIMATION);
              scenes.getFrameRateRange();
            }

            if (scenes.type == SwiperDynamicSyncSceneType.GESTURE) {
              scenes.setFrameRateRange(this.GESTURE);
              scenes.getFrameRateRange();
            }
          });
        })
      }
  }
}
```
## SwiperDynamicSyncScene<sup>12+</sup>

SwiperDynamicSyncScene继承自[DynamicSyncScene](#dynamicsyncscene12)，对应Swiper的动态帧率场景。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：**  SystemCapability.ArkUI.ArkUI.Full

| 名称       | 类型                                                      | 只读 | 可选 | 说明                                |
| --------- | --------------------------------------------------------- | ---- | ---- | ---------------------------------- |
| type      | [SwiperDynamicSyncSceneType](#swiperdynamicsyncscenetype12) | 是   | 否   | Swiper的动态帧率场景。             |

## SwiperDynamicSyncSceneType<sup>12+</sup>

枚举值，表示动态帧率场景的类型。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：**  SystemCapability.ArkUI.ArkUI.Full

| 名称     | 值   | 说明                   |
| -------- | ---- | ---------------------- |
| GESTURE | 0   | 手势操作场景。 |
| ANIMATION | 1   | 动画过渡场景。 |

## MarqueeDynamicSyncScene<sup>14+</sup>

MarqueeDynamicSyncScene继承自[DynamicSyncScene](#dynamicsyncscene12)，对应[Marquee](arkui-ts/ts-basic-components-marquee.md)的动态帧率场景。

**原子化服务API：** 从API version 14开始，该接口支持在原子化服务中使用。

**系统能力：**  SystemCapability.ArkUI.ArkUI.Full

| 名称       | 类型                                                      | 只读 | 可选 | 说明                                |
| --------- | --------------------------------------------------------- | ---- | ---- | ---------------------------------- |
| type      | [MarqueeDynamicSyncSceneType](#marqueedynamicsyncscenetype14) | 是   | 否   | Marquee的动态帧率场景。             |

## MarqueeDynamicSyncSceneType<sup>14+</sup>

枚举值，表示Marquee的动态帧率场景的类型。

**原子化服务API：** 从API version 14开始，该接口支持在原子化服务中使用。

**系统能力：**  SystemCapability.ArkUI.ArkUI.Full

| 名称     | 值   | 说明                   |
| -------- | ---- | ---------------------- |
| ANIMATION | 1   | 动画过度场景 |

**示例：**

```ts
import { MarqueeDynamicSyncSceneType, MarqueeDynamicSyncScene } from '@kit.ArkUI';

@Entry
@Component
struct MarqueeExample {
  @State start: boolean = false;
  @State src: string = '';
  @State marqueeText: string = 'Running Marquee';
  private fromStart: boolean = true;
  private step: number = 10;
  private loop: number = Number.POSITIVE_INFINITY;
  controller: TextClockController = new TextClockController();
  convert2time(value: number): string {
    let date = new Date(Number(value+'000'));
    let hours = date.getHours().toString().padStart(2, '0');
    let minutes = date.getMinutes().toString().padStart(2, '0');
    let seconds = date.getSeconds().toString().padStart(2, '0');
    return hours+ ":" + minutes + ":" + seconds;
  }
  @State ANIMATION: ExpectedFrameRateRange = { min: 0, max: 120, expected: 30 };
  private scenes: MarqueeDynamicSyncScene[] = [];

  build() {
    Flex({ direction: FlexDirection.Column, alignItems: ItemAlign.Center, justifyContent: FlexAlign.Center }) {
      Marquee({
        start: this.start,
        step: this.step,
        loop: this.loop,
        fromStart: this.fromStart,
        src: this.marqueeText + this.src
      })
        .marqueeUpdateStrategy(MarqueeUpdateStrategy.PRESERVE_POSITION)
        .width(300)
        .height(80)
        .fontColor('#FFFFFF')
        .fontSize(48)
        .fontWeight(700)
        .backgroundColor('#182431')
        .margin({ bottom: 40 })
        .id('dynamicMarquee')
        .onAppear(()=>{
          this.scenes = this.getUIContext().requireDynamicSyncScene('dynamicMarquee') as MarqueeDynamicSyncScene[];
        })
      Button('Start')
        .onClick(() => {
          this.start = true;
          this.controller.start();
          this.scenes.forEach((scenes: MarqueeDynamicSyncScene) => {
            if (scenes.type == MarqueeDynamicSyncSceneType.ANIMATION) {
              scenes.setFrameRateRange(this.ANIMATION);
            }
          });
        })
        .width(120)
        .height(40)
        .fontSize(16)
        .fontWeight(500)
        .backgroundColor('#007DFF')
      TextClock({ timeZoneOffset: -8, controller: this.controller })
        .format('hms')
        .onDateChange((value: number) => {
          this.src = this.convert2time(value);
        })
        .margin(20)
        .fontSize(30)
    }
    .width('100%')
    .height('100%')
  }
}
```
## TextMenuController<sup>16+</sup>
以下API需先使用UIContext中的[getTextMenuController()](js-apis-arkui-UIContext.md#gettextmenucontroller16)方法获取TextMenuController实例，再通过此实例调用对应方法。

### setMenuOptions<sup>16+</sup>

setMenuOptions(options: TextMenuOptions): void

设置菜单选项。

**原子化服务API：** 从API version 16开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名      | 类型         | 必填   | 说明   |
| -------- | ---------- | ---- | ---- |
| options | [TextMenuOptions](../apis-arkui/arkui-ts/ts-text-common.md#textmenuoptions16对象说明)| 是    | 设置菜单选项。<br />默认值:{showMode: TextMenuShowMode.DEFAULT} |

**示例：**

```ts
// xxx.ets
@Entry
@Component
struct Index {
  aboutToAppear(): void {
    // 设置在对应的UIContext下优先使用独立窗口显示文本选择菜单
    this.getUIContext()
      .getTextMenuController()
      .setMenuOptions(
        {
          showMode: TextMenuShowMode.PREFER_WINDOW
        }
      );
  }

  build() {
    Row() {
      Column() {
        TextInput({ text: "这是一个TextInput，长按弹出文本选择菜单" })
          .height(60)
          .fontStyle(FontStyle.Italic)
          .fontWeight(FontWeight.Bold)
          .textAlign(TextAlign.Center)
          .caretStyle({ width: '4vp' })

        Text("这是一个Text，长按弹出文本选择菜单")
          .height(60)
          .copyOption(CopyOptions.InApp)
          .fontStyle(FontStyle.Italic)
          .fontWeight(FontWeight.Bold)
          .textAlign(TextAlign.Center)
      }.width('100%')
    }
    .height('100%')
  }
}
```