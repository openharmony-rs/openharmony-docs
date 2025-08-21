# 自定义组件内置方法
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xiang-shouxing-->
<!--Designer: @xiang-shouxing-->
<!--Tester: @sally__-->
<!--Adviser: @HelloCrease-->

自定义组件内置方法是由ArkUI开发框架提供给应用开发者的，定义在自定义组件基类上的API。应用开发者可以在自定义组件的实例上调用对应的API以获取当前自定义组件实例相关的信息。例如，查询当前自定义组件上下文的UIContext信息。

> **说明：**
>
> 本模块首批接口从API version 11开始支持，后续版本的新增接口，采用上角标单独标记接口的起始版本。
>

## getUIContext

getUIContext(): UIContext

获取UIContext对象。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型                                                      | 说明                    |
| --------------------------------------------------------- | ----------------------- |
| [UIContext](#uicontext) | 返回UIContext实例对象。在异步调用的回调方法中使用该接口，或者该接口的起始调用不在当前页面时，可能导致接口调用发生在自定义组件销毁之后，返回 undefined。 |

## UIContext

type UIContext = UIContext

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 类型                                                      | 说明                    |
| --------------------------------------------------------- | ----------------------- |
| [UIContext](../arkts-apis-uicontext-uicontext.md) | 返回UIContext实例对象。 |

**示例：**

```ts
import { UIContext } from '@kit.ArkUI';

@Entry
@Component
struct MyComponent {
  aboutToAppear() {
    let uiContext: UIContext = this.getUIContext();
  }

  build() {
    // ...
  }
}
```

## getUniqueId<sup>12+</sup>

getUniqueId(): number

获取当前Component的UniqueId。UniqueId为系统为每个组件分配的Id，可保证当前应用中的唯一性。若在组件对应的节点未创建或已销毁时获取，返回无效UniqueId：-1。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型                                                      | 说明                    |
| --------------------------------------------------------- | ----------------------- |
| number | 返回当前Component的UniqueId。 |

**示例：**

```ts
@Entry
@Component
struct MyComponent {
  aboutToAppear() {
    let uniqueId: number = this.getUniqueId();
  }

  build() {
    // ...
  }
}
```

## queryNavDestinationInfo

queryNavDestinationInfo(): NavDestinationInfo | undefined;

查询自定义组件所属的NavDestination信息，仅当自定义组件在NavDestination的内部时才生效。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型                                                                       | 说明      |
| -------------------------------------------------------------------------- | --------- |
| [NavDestinationInfo](#navdestinationinfo) \| undefined | 返回NavDestinationInfo实例对象。 |

**示例：**

```ts
import { uiObserver } from '@kit.ArkUI';

@Component
export struct NavDestinationExample {
  build() {
    NavDestination() {
      MyComponent()
    }
  }
}

@Component
struct MyComponent {
  navDesInfo: uiObserver.NavDestinationInfo | undefined

  aboutToAppear() {
    // this指代MyComponent自定义节点，并从该节点向上查找其最近的一个类型为NavDestination的父亲节点
    this.navDesInfo = this.queryNavDestinationInfo();
    console.log('get navDestinationInfo: ' + JSON.stringify(this.navDesInfo));
  }

  build() {
    // ...
  }
}
```


## queryNavDestinationInfo<sup>18+</sup>

queryNavDestinationInfo(isInner: Optional\<boolean>): NavDestinationInfo | undefined

查询当前自定义组件距离最近的NavDestination（NavPathStack栈中）信息，isInner为true表示向内查找，false表示向外查找。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：** 

| 参数名 | 类型                                          | 必填 | 说明                                          |
| ------ | --------------------------------------------- | ---- | --------------------------------------------- |
| isInner  | [Optional](ts-universal-attributes-custom-property.md#optionalt12)\<boolean> | 是   | true：向内查询最近的，且在栈内的NavDestinationInfo的详细信息。<br/>false：向外查询最近的，且在栈内的NavDestinationInfo的详细信息。|

**返回值：**

| 类型                                                                       | 说明      |
| -------------------------------------------------------------------------- | --------- |
| [NavDestinationInfo](#navdestinationinfo) \| undefined | 返回NavDestinationInfo实例对象。|

**示例：**

```ts
// Index.ets
@Entry
@Component
struct NavigationExample {
  pageInfo: NavPathStack = new NavPathStack();

  build() {
    Navigation(this.pageInfo) {
      Column() {
        Button('pageOne', { stateEffect: true, type: ButtonType.Capsule })
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            this.pageInfo.pushPath({ name: 'pageOne' }); // 将name指定的NavDestination页面信息入栈。
          })
      }
    }.title('NavIndex')
  }
}
```

```ts
// PageOne.ets
import { uiObserver } from '@kit.ArkUI';

@Builder
export function PageOneBuilder() {
  PageOneComponent()
}

@Component
export struct PageOneComponent {
  navDesInfo: uiObserver.NavDestinationInfo | undefined;
  @State text: string = '';
  build() {
    NavDestination() {
      Column() {
        Button('点击向内查找')
          .width('80%')
          .height(40)
          .margin(20)
          .onClick(() => {
            // 向内查询PageOne的NavDestination信息
            this.navDesInfo = this.queryNavDestinationInfo(true);
            this.text = JSON.stringify(this.navDesInfo?.name).toString();
          })
        Text('向内查找的NavDestination是:' + this.text)
          .width('80%')
          .height(50)
          .margin(50)
          .fontSize(20)
        MyComponent()
      }.width('100%').height('100%')
    }
    .title('pageOne')
  }
}

@Component
struct MyComponent {
  navDesInfo: uiObserver.NavDestinationInfo | undefined;
  @State text: string = '';

  build() {
    Column() {
      Button('点击向外查找')
        .width('80%')
        .height(40)
        .margin(20)
        .onClick(() => {
          // 向外查询PageOne的NavDestination信息
          this.navDesInfo = this.queryNavDestinationInfo(false);
          this.text = JSON.stringify(this.navDesInfo?.name).toString();
        })
      Text('向外查找的NavDestination是:' + this.text)
        .width('80%')
        .height(50)
        .margin(50)
        .fontSize(20)
    }
  }
}
```

```ts
//route_map.json
{
  "routerMap": [
    {
      "name": "pageOne",
      "pageSourceFile": "src/main/ets/pages/PageOne.ets",
      "buildFunction": "PageOneBuilder",
      "data": {
        "description": "this is pageOne"
      }
    }
  ]
}
```

## NavDestinationInfo

type NavDestinationInfo = NavDestinationInfo

NavDestinationInfo实例对象。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

| 类型     | 说明       |
| ------ | ---------- |
| [NavDestinationInfo](../js-apis-arkui-observer.md#navdestinationinfo) | 返回NavDestinationInfo实例对象。 |


## queryNavigationInfo<sup>12+</sup>

queryNavigationInfo(): NavigationInfo | undefined

查询自定义组件所属的Navigation信息。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型                                                                       | 说明      |
| -------------------------------------------------------------------------- | --------- |
| [NavigationInfo](#navigationinfo12) \| undefined | 返回NavigationInfo实例对象。 |

**示例：**

```ts
// index.ets
import { uiObserver } from '@kit.ArkUI';

@Entry
@Component
struct MainPage {
  pathStack: NavPathStack = new NavPathStack();

  build() {
    Navigation(this.pathStack) {
      // ...
    }.id("NavigationId")
  }
}


@Component
export struct PageOne {
  pathStack: NavPathStack = new NavPathStack();

  aboutToAppear() {
    // this指代PageOne自定义节点，并从该节点向上查找其最近的一个类型为Navigation的父亲节点
    let navigationInfo: uiObserver.NavigationInfo | undefined = this.queryNavigationInfo();
    console.log('get navigationInfo: ' + JSON.stringify(navigationInfo));
    if (navigationInfo !== undefined) {
      this.pathStack = navigationInfo.pathStack;
    }
  }

  build() {
    NavDestination() {
      // ...
    }.title('PageOne')
  }
}
```

## NavigationInfo<sup>12+</sup>

type NavigationInfo = NavigationInfo

NavigationInfo实例对象。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

| 类型     | 说明       |
| ------ | ---------- |
| [NavigationInfo](../js-apis-arkui-observer.md#navigationinfo12) | 返回NavigationInfo实例对象。 |

## queryRouterPageInfo<sup>12+</sup>

queryRouterPageInfo(): RouterPageInfo | undefined;

获取RouterPageInfo实例对象。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型                                                         | 说明                         |
| ------------------------------------------------------------ | ---------------------------- |
| [RouterPageInfo](#routerpageinfo12) \| undefined | 返回RouterPageInfo实例对象。 |

**示例：**

```ts
import { uiObserver } from '@kit.ArkUI';

@Entry
@Component
struct MyComponent {
  aboutToAppear() {
    let info: uiObserver.RouterPageInfo | undefined = this.queryRouterPageInfo();
  }

  build() {
    // ...
  }
}
```

## RouterPageInfo<sup>12+</sup>

type RouterPageInfo = RouterPageInfo

RouterPageInfo实例对象。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

| 类型     | 说明       |
| ------ | ---------- |
| [RouterPageInfo](../js-apis-arkui-observer.md#routerpageinfo) | 返回RouterPageInfo实例对象。 |

## getDialogController<sup>18+</sup>

getDialogController(): PromptActionDialogController | undefined

获取PromptActionDialogController实例对象。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型                                                         | 说明                         |
| ------------------------------------------------------------ | ---------------------------- |
| [PromptActionDialogController](#promptactiondialogcontroller18) \| undefined | 返回PromptActionDialogController实例对象。 |

**示例：**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { ComponentContent } from '@kit.ArkUI';

class Params {
  text: string = "";
  constructor(text: string) {
    this.text = text;
  }
}

@ComponentV2
struct MyComponent {
  build() {
    Column() {
      Button('Close Dialog')
        .onClick(() => {
          let ctrl: PromptActionDialogController = this.getDialogController();
          if (ctrl != undefined) {
            ctrl.close();
          }
        })
    }
  }
}

@Builder
function buildText(params: Params) {
  Column() {
    Text(params.text)
      .fontSize(50)
      .fontWeight(FontWeight.Bold)
      .margin({ bottom: 36 })
    MyComponent()
  }.backgroundColor('#FFF0F0F0')
}

@Entry
@ComponentV2
struct Index {
  @Local message: string = "hello";

  build() {
    Row() {
      Column({ space: 10 }) {
        Button('click me')
          .fontSize(20)
          .onClick(() => {
            let ctx = this.getUIContext();
            let promptAction = ctx.getPromptAction();
            promptAction.openCustomDialog(new ComponentContent(ctx, wrapBuilder(buildText), new Params(this.message)))
              .catch((err: BusinessError) => {
                console.error("openCustomDialog error: " + err.code + " " + err.message);
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

## PromptActionDialogController<sup>18+</sup>

type PromptActionDialogController = promptAction.DialogController

自定义弹窗控制器，可以控制当前自定义弹窗，具体控制能力包括关闭弹窗等，详见[promptAction.DialogController](../js-apis-promptAction.md#dialogcontroller18)。

**原子化服务API：** 从API version 18开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

| 类型                                                         | 说明                         |
| ------------------------------------------------------------ | ---------------------------- |
| [promptAction.DialogController](../js-apis-promptAction.md#dialogcontroller18) | 表示对象类型为promptAction.DialogController实例对象。 |
