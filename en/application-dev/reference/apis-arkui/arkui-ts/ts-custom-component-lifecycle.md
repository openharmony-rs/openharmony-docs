# Custom Component Lifecycle

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @seaside_wu1; @xin11112-->
<!--Designer: @zhangboren-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=ca610c3b31eac2a84ffac21a107ce522b473feb1 translatedAt=2026-08-28T01:24:39.152Z pushedAt=2026-08-28T09:08:50.403Z -->

The lifecycle callbacks of a custom component are used to notify users of the lifecycle of the component. These callbacks are private and are invoked by the development framework at a specified time during runtime. They cannot be actively called from an app. Through these callbacks, developers can initialize data and state variables when a component is created, release resources when the component is destroyed, update the page state, refresh data, or pause and resume tasks when the page is shown or hidden, and pass parameters and update the state when the component is reused, thereby implementing fine-grained management of the component. Do not reuse the same custom component node across multiple windows, as its lifecycle may become disordered.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - Promise and asynchronous callback functions are allowed in lifecycle functions, for example, for network resource acquisition and timer setting.

## build

build(): void

The **build()** function is used to define the declarative UI description of a custom component. Every custom component must define a **build()** function.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

## aboutToAppear

aboutToAppear?(): void

Invoked after a new instance of the custom component is created and before its **build()** function is executed. You can change [state variables](../../../ui/state-management/arkts-state-management-glossary.md#state-variable) in the **aboutToAppear** function, and the changes will take effect in the subsequent execution of the **build()** function. The **aboutToAppear** lifecycle of a custom component that implements [custom layout](./ts-custom-component-layout.md) is triggered during the layout process. For details about how to use it, see [Custom Component Lifecycle](../../../ui/state-management/arkts-page-custom-components-lifecycle.md).

> **NOTE**
>
> * In this callback function, it is recommended that you only perform initialization logic for the current node component. Avoid high-time-consuming operations that may block the main thread. For high-time-consuming operations, consider caching or asynchronous solutions. For best practices, see [Optimizing Performance of UI Components: Avoiding Time-Consuming Operations During the Lifecycle of Custom Components](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-ui-component-performance-optimization#section18755173594714).
> * In scenarios where components need to be frequently created and destroyed, this callback will be called frequently. For best practices, see [Optimizing Time-Consuming Operations in the Main Thread: Component Lifecycle Callback](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-time-optimization-of-the-main-thread#section418843713435).

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

## onDidBuild<sup>12+</sup>

onDidBuild?(): void

Invoked after the **build()** function of the custom component is executed. You can use this callback for actions that do not directly affect the UI, such as tracking data reporting. For details, see [Custom Component Lifecycle](../../../ui/state-management/arkts-page-custom-components-lifecycle.md).

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

## aboutToDisappear

aboutToDisappear?(): void

Executed when the custom component is destructed and destroyed. Do not change state variables in the **aboutToDisappear** function. In particular, modifying the \@Link variable may cause unstable app behavior. For details about how to use it, see [Custom Component Lifecycle](../../../ui/state-management/arkts-page-custom-components-lifecycle.md). It is not recommended to trigger logic such as [creating a custom dialog box](./ts-methods-custom-dialog-box.md#open) after the **aboutToDisappear** function is called, because this may cause abnormal app behavior due to the loss of component tree information, for example, [\@Consume](../../../ui/state-management/arkts-provide-and-consume.md) cannot find the corresponding [\@Provide](../../../ui/state-management/arkts-provide-and-consume.md), or the dialog box displays a blank screen without components.

> **NOTE**
>
> In scenarios where components need to be frequently created and destroyed, this callback will be called frequently. For best practices, see [Optimizing Time-Consuming Operations in the Main Thread: Component Lifecycle Callback](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-time-optimization-of-the-main-thread#section418843713435).

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

## onPageShow

onPageShow?(): void

Invoked each time a router-managed page (a custom component decorated with [\@Entry](../../../../application-dev/ui/state-management/arkts-create-custom-components.md#entry)) is displayed, including scenarios such as route redirection and the app entering the foreground. It is recommended that you avoid performing time-consuming operations that block the main thread in this callback function, so as not to affect page display performance.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

## onPageHide

onPageHide?(): void

Invoked each time a router-managed page (a custom component decorated with [\@Entry](../../../../application-dev/ui/state-management/arkts-create-custom-components.md#entry)) is hidden, including scenarios such as route navigation and the application moving to the background.

> **NOTE**
>
> To ensure smooth UI responsiveness, avoid executing time-consuming operations within the callback function that may block the main thread. For resource-intensive tasks such as camera resource deallocation, consider implementing asynchronous solutions. For best practices, see [Reducing Application Latency: Postponing Resource Release](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-application-latency-optimization-cases#section8783201923819).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

## onBackPress

onBackPress?(): void | boolean

Takes effect on a router-managed page (a custom component decorated with [\@Entry](../../../../application-dev/ui/state-management/arkts-create-custom-components.md#entry)) and is triggered when the user clicks the back button. The value **true** indicates that the page handles the back logic by itself and does not perform page routing; the value **false** indicates that the default routing back logic is used. If no return value is set, it is processed as **false**. Typical use cases include: blocking the back action to prompt the user to save when the page has unsaved edits, and popping up a custom confirmation dialog box to replace the default system back behavior.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type               | Description       |
| ------------------- | --------- |
| void \| boolean | Action of the back button. The value **true** indicates that the page handles the back logic by itself without page routing, and **false** indicates that the default routing back logic is used. If no value is returned, **false** is used. |

``` TypeScript
// xxx.ets
@Entry
@Component
struct IndexComponent {
  @State textColor: Color = Color.Black;

  onPageShow() {
    // Set textColor to Blue when onPageShow is triggered.
    this.textColor = Color.Blue;
    console.info('IndexComponent onPageShow');
  }

  onPageHide() {
    // Set textColor to Transparent when onPageHide is triggered.
    this.textColor = Color.Transparent;
    console.info('IndexComponent onPageHide');
  }

  onBackPress() {
    // Set textColor to Red when onBackPress is triggered by pressing the back key.
    this.textColor = Color.Red;
    console.info('IndexComponent onBackPress');
  }

  build() {
    Column() {
      Text('Hello World')
        .fontColor(this.textColor)
        .fontSize(30)
        .margin(30)
    }.width('100%')
  }
}
```

![en-us_image_lifecycle](figures/image-lifecycle.gif)

## onNewParam<sup>19+</sup>

onNewParam?(param: ESObject): void

Invoked when a page in the routing stack is moved to the top of the stack in the singleton mode of [RouterMode](../js-apis-router.md#routermode9). This callback takes effect only for custom components decorated with [\@Entry](../../../../application-dev/ui/state-management/arkts-create-custom-components.md#entry) within the [router](../js-apis-router.md) page stack.

**Atomic service API**: This API can be used in atomic services since API version 19.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type    | Mandatory    |             Description        |
|-------|----------|----------|---------------------------|
| param | ESObject | Yes | Data passed to the target page during routing. It is consistent with the data passed by the **params** field in **router.pushUrl()**, and its structure is defined by the developer. |

``` TypeScript
// pages/Index.ets
import { router } from '@kit.ArkUI';

export class RouterParam {
  msg: string = '__NA__';

  constructor(msg: string) {
    this.msg = msg;
  }
}

@Entry
@Component
struct Index {
  aboutToAppear(): void {
    console.info('onNewParam', 'Index aboutToAppear');
  }

  onNewParam(param: ESObject) {
    console.info('onNewParam', 'Index onNewParam, param: ' + JSON.stringify(param));
  }

  build() {
    Column() {
      Button('push pageOne Standard')
        .margin(10)
        .onClick(() => {
          this.getUIContext().getRouter().pushUrl({
            url: 'pages/PageOne',
            params: new RouterParam('push pageOne Standard')
          }, router.RouterMode.Standard);
        })
      // In Single mode, if PageOne is already in the stack, it is reused and PageOne.onNewParam is triggered.
      Button('push pageOne Single')
        .margin(10)
        .onClick(() => {
          this.getUIContext().getRouter().pushUrl({
            url: 'pages/PageOne',
            params: new RouterParam('push pageOne Single')
          }, router.RouterMode.Single);
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

<!--code_no_check-->

``` TypeScript
// pages/PageOne.ets
import { router } from '@kit.ArkUI';
import { RouterParam } from './Index';

@Entry
@Component
struct PageOne {
  aboutToAppear(): void {
    console.info('onNewParam', 'PageOne aboutToAppear');
  }

  onNewParam(param: ESObject) {
    console.info('onNewParam', 'PageOne onNewParam, param: ' + JSON.stringify(param));
  }

  build() {
    Column() {
      Button('push Index Standard')
        .margin(10)
        .onClick(() => {
          this.getUIContext().getRouter().pushUrl({
            url: 'pages/Index',
            params: new RouterParam('push Index Standard')
          }, router.RouterMode.Standard);
        })
      // In Single mode, if Index is already in the stack, it is reused and Index.onNewParam is triggered.
      Button('push Index Single')
        .margin(10)
        .onClick(() => {
          this.getUIContext().getRouter().pushUrl({
            url: 'pages/Index',
            params: new RouterParam('push Index Single')
          }, router.RouterMode.Single);
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

## aboutToReuse<sup>10+</sup>

aboutToReuse?(params: Record\<string, Object | undefined | null>): void

When a reusable custom component is re-added to the node tree from the reuse cache, the **aboutToReuse** lifecycle callback is triggered, and the construction parameters of the component are passed to this callback.

> **NOTE**
>
> * Avoid repeatedly assigning values to state variables that are automatically updated, such as **@Link**/**@ObjectLink**/**@Prop**, in **aboutToReuse()**.
> * In sliding scenarios, component reuse usually requires this callback function to update the state variables of the component. Therefore, avoid time-consuming operations in this callback function, otherwise frame loss and lag may occur. For best practices, see [Optimizing Time-Consuming Operations in the Main Thread - Component Reuse Callback](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-time-optimization-of-the-main-thread#section20815336174316).

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                                     | Mandatory| Description               |
|--------|-------------------------------------------|-----|---------------------|
| params | Record\<string, Object \| undefined \| null> | Mandatory | Construction parameters of the custom component. The key is the name of the component member variable passed in from outside during reuse, and the value is the corresponding parameter value passed in from outside during reuse. |

``` TypeScript
// xxx.ets
export class Message {
  value: string | undefined;

  constructor(value: string) {
    this.value = value;
  }
}

@Entry
@Component
struct Index {
  @State isShown: boolean = true;

  build() {
    Column() {
      // Click Button to toggle isShown, controlling Child being removed from or re-added to the component tree.
      Button('Hello World')
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
        .onClick(() => {
          this.isShown = !this.isShown;
        })
      if (this.isShown) {
        Child({ message: new Message('Child') })
      }
    }
    .height('100%')
    .width('100%')
  }
}

@Reusable
@Component
struct Child {
  @State message: Message = new Message('AboutToReuse');

  aboutToReuse(params: Record<string, ESObject>) {
    console.info('Reuse Child');
    this.message = params.message as Message;
  }

  build() {
    Column() {
      Text(this.message.value)
        .fontSize(20)
    }
    .borderWidth(2)
    .height(100)
  }
}
```

## aboutToReuse<sup>18+</sup>

aboutToReuse?(): void

When a reusable custom component of state management V2 is re-added to the node tree from the reuse cache, the **aboutToReuse** lifecycle callback is triggered. In frequently invoked scenarios, avoid performing time-consuming operations in it, otherwise frame loss and lag may occur.

For details, see [\@ReusableV2](../../../ui/state-management/arkts-new-reusableV2.md).

**Atomic service API**: This API can be used in atomic services since API version 18.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

``` TypeScript
@Entry
@ComponentV2
struct Index {
  @Local condition: boolean = true;
  build() {
    Column() {
      Button('Recycle/Reuse').onClick(() => { this.condition = !this.condition; }) // Tap to toggle the recycle/reuse state.
      if (this.condition) {
        ReusableV2Component()
      }
    }
  }
}
@ReusableV2
@ComponentV2
struct ReusableV2Component {
  @Local message: string = 'Hello World';
  aboutToReuse() {
    console.info('ReusableV2Component aboutToReuse'); // Called when the component is reused.
  }
  build() {
    Column() {
      Text(this.message)
    }
  }
}
```

## aboutToRecycle<sup>10+</sup>

aboutToRecycle?(): void

Invoked before a reusable component is added to the reuse cache from the node tree. When the component is subsequently reused from the reuse cache, the [aboutToReuse](#abouttoreuse10) lifecycle callback is triggered. In frequently invoked scenarios, avoid performing time-consuming operations in it, otherwise frame loss and lag may occur.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

``` TypeScript
// xxx.ets
export class Message {
  value: string | undefined;

  constructor(value: string) {
    this.value = value;
  }
}

@Entry
@Component
struct Index {
  @State isShown: boolean = true;

  build() {
    Column() {
      Button('Hello World')
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
        .onClick(() => {
          this.isShown = !this.isShown;
        })
      if (this.isShown) {
        Child({ message: new Message('Child') })
      }
    }
    .height('100%')
    .width('100%')
  }
}

@Reusable
@Component
struct Child {
  @State message: Message = new Message('AboutToReuse');

  aboutToReuse(params: Record<string, ESObject>) {
    console.info('Reuse Child');
    this.message = params.message as Message;
  }

  aboutToRecycle() {
    // This is where you can release memory-intensive content or other non-essential resource references to avoid continuous memory usage that could lead to memory leaks.
    console.info('Recycle Child, child enters the reuse pool');
  }

  build() {
    Column() {
      Text(this.message.value)
        .fontSize(20)
    }
    .borderWidth(2)
    .height(100)
  }
}
```

## onWillApplyTheme<sup>12+</sup>

onWillApplyTheme?(theme: Theme): void

Obtains the **Theme** object of the current component context. It is executed after a new instance of the custom component is created and before its **build()** function is executed. Unlike **aboutToAppear**, **onWillApplyTheme** is used to initialize state variables based on the **Theme** object, while **aboutToAppear** is used for general initialization logic. You can change state variables in the **onWillApplyTheme** function, and the changes will take effect in the subsequent execution of the **build()** function.

> **NOTE**
>
> Since API version 18, this API is supported in the components of V2.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name   | Type                                      | Mandatory   | Description        |
|--------|------------------------------------------|------------|-------------------------|
| theme | [Theme](#theme12) | Yes | **Theme** object currently in effect for the custom component. In the callback, you can use this object to obtain resources such as theme colors to update the style variables of the component. |

## Theme<sup>12+</sup>

type Theme = import('../api/@ohos.arkui.theme').Theme

Defines the **Theme** object.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Type                                                     | Description                   |
| --------------------------------------------------------- | ----------------------- |
| import('../api/@ohos.arkui.theme').[Theme](../js-apis-arkui-theme.md#theme) | The **Theme** object currently in effect for the custom component. |

V1:

``` TypeScript
// xxx.ets
import { CustomTheme, CustomColors, Theme, ThemeControl } from '@kit.ArkUI';

class BlueColors implements CustomColors {
  fontPrimary = Color.White;
  backgroundPrimary = Color.Blue;
  brand = Color.Blue; // Brand color
}

class PageCustomTheme implements CustomTheme {
  colors?: CustomColors;

  constructor(colors: CustomColors) {
    this.colors = colors;
  }
}
const blueColorsTheme = new PageCustomTheme(new BlueColors());
// setDefaultTheme should be called on the application entry page or in an ability.
ThemeControl.setDefaultTheme(blueColorsTheme);

@Entry
@Component
struct IndexComponent {
  @State textColor: ResourceColor = $r('sys.color.font_primary');
  @State columnBgColor: ResourceColor = $r('sys.color.background_primary');

  // In onWillApplyTheme, the Theme object of the current component context can be obtained. Here, in onWillApplyTheme, assign the state variables textColor and columnBgColor to the colors in the currently used Theme object (blueColorsTheme).
  onWillApplyTheme(theme: Theme) {
    this.textColor = theme.colors.fontPrimary;
    this.columnBgColor = theme.colors.backgroundPrimary;
    console.info('IndexComponent onWillApplyTheme');
  }

  build() {
    Column() {
      // Initial color style of the component
      Column() {
        Text('Hello World')
          .fontColor($r('sys.color.font_primary'))
          .fontSize(30)
      }
      .width('100%')
      .height('25%')
      .borderRadius('10vp')
      .backgroundColor($r('sys.color.background_primary'))

      // The color style configured in onWillApplyTheme is applied.
      Column() {
        Text('onWillApplyTheme')
          .fontColor(this.textColor)
          .fontSize(30)
        Text('Hello World')
          .fontColor(this.textColor)
          .fontSize(30)
      }
      .width('100%')
      .height('25%')
      .borderRadius('10vp')
      .backgroundColor(this.columnBgColor)
    }
    .padding('16vp')
    .backgroundColor('#dcdcdc')
    .width('100%')
    .height('100%')
  }
}
```

![onWillApplyThemePage](figures/onWillApplyTheme.png)

V2:

``` TypeScript
import { CustomTheme, CustomColors, Theme, ThemeControl } from '@kit.ArkUI';

class BlueColors implements CustomColors {
  fontPrimary = Color.White;
  backgroundPrimary = Color.Blue;
  brand = Color.Blue; // Brand color
}

class PageCustomTheme implements CustomTheme {
  colors?: CustomColors;

  constructor(colors: CustomColors) {
    this.colors = colors;
  }
}

const blueColorsTheme = new PageCustomTheme(new BlueColors());
// setDefaultTheme should be called on the application entry page or in an ability.
ThemeControl.setDefaultTheme(blueColorsTheme);

@Entry
@ComponentV2
struct IndexComponent {
  @Local textColor: ResourceColor = $r('sys.color.font_primary');
  @Local columnBgColor: ResourceColor = $r('sys.color.background_primary');

  // In onWillApplyTheme, you can obtain the Theme object of the current component context. Here, the state variables textColor and columnBgColor are assigned the colors from the currently used Theme object (blueColorsTheme).
  onWillApplyTheme(theme: Theme) {
    this.textColor = theme.colors.fontPrimary;
    this.columnBgColor = theme.colors.backgroundPrimary;
    console.info('IndexComponent onWillApplyTheme');
  }

  build() {
    Column() {
      // Initial color style of the component
      Column() {
        Text('Hello World')
          .fontColor($r('sys.color.font_primary'))
          .fontSize(30)
      }
      .width('100%')
      .height('25%')
      .borderRadius('10vp')
      .backgroundColor($r('sys.color.background_primary'))

      // The color style configured in onWillApplyTheme is applied.
      Column() {
        Text('onWillApplyTheme')
          .fontColor(this.textColor)
          .fontSize(30)
        Text('Hello World')
          .fontColor(this.textColor)
          .fontSize(30)
      }
      .width('100%')
      .height('25%')
      .borderRadius('10vp')
      .backgroundColor(this.columnBgColor)
    }
    .padding('16vp')
    .backgroundColor('#dcdcdc')
    .width('100%')
    .height('100%')
  }
}
```

![onWillApplyTheme_V2](figures/onWillApplyTheme_V2.png)

## pageTransition<sup>9+</sup>

pageTransition?(): void

Defines the transition animations for page entry and page exit.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

## onFormRecycle<sup>11+</sup>

onFormRecycle?(): string

Invoked when the widget is recycled. The widget provider can return the data to be saved by the widget manager. This data is passed back to the widget provider using the [onFormRecover](#onformrecover11) API when the widget is recovered.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Widget capability**: This API can be used in ArkTS widgets since API version 11.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type               | Description       |
| ------------------- | ---------   |
| string | Data that the widget provider requests the widget manager to save.|

**Example**

``` TypeScript
@Entry
@Component
struct WidgetCard {
  readonly title: string = 'Hello World';
  readonly actionType: string = 'router';
  readonly abilityName: string = 'EntryAbility';
  readonly message: string = 'add detail';
  readonly fullWidthPercent: string = '100%';
  readonly fullHeightPercent: string = '100%';

  onFormRecycle(): string {
    let formId: string = '1859635745';
    // Trigger the callback when the widget is recycled.
    console.info('card is recycled, formID: ' + formId);
    return formId;
  }

  onFormRecover(statusData: string): void {
    console.info('card has been restored, formID: ' + statusData);
  }

  build() {
    Row() {
      Column() {
        Text(this.title)
          .fontSize($r('app.float.font_size'))
          .fontWeight(FontWeight.Medium)
          .fontColor($r('sys.color.font'))
      }
      .width(this.fullWidthPercent)
    }
    .height(this.fullHeightPercent)
    .backgroundColor($r('sys.color.comp_background_primary'))
    .onClick(() => {
      postCardAction(this, {
        action: this.actionType,
        abilityName: this.abilityName,
        params: {
          message: this.message
        }
      });
    })
  }
}
```

## onFormRecover<sup>11+</sup>

onFormRecover?(statusData: string): void

Invoked when the widget is recovered. The widget provider can obtain the data saved by the widget manager during widget recycling. This data can be saved to the widget manager using the [onFormRecycle](#onformrecycle11) callback.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Widget capability**: This API can be used in ArkTS widgets since API version 11.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name   | Type                                      | Mandatory   | Description        |
|--------|------------------------------------------|------------|-------------------------|
| statusData | string | Yes    | Data saved by the widget manager during widget recycling.|

**Example**

``` TypeScript
@Entry
@Component
struct WidgetCard {
  readonly title: string = 'Hello World';
  readonly actionType: string = 'router';
  readonly abilityName: string = 'EntryAbility';
  readonly message: string = 'add detail';
  readonly fullWidthPercent: string = '100%';
  readonly fullHeightPercent: string = '100%';

  onFormRecycle(): string {
    let formId: string = '1859635745';
    console.info('card is recycled, formID: ' + formId);
    return formId;
  }

  onFormRecover(statusData: string): void {
    // Trigger the callback when the widget is restored.
    console.info('card has been restored, formID: ' + statusData);
  }

  build() {
    Row() {
      Column() {
        Text(this.title)
          .fontSize($r('app.float.font_size'))
          .fontWeight(FontWeight.Medium)
          .fontColor($r('sys.color.font'))
      }
      .width(this.fullWidthPercent)
    }
    .height(this.fullHeightPercent)
    .backgroundColor($r('sys.color.comp_background_primary'))
    .onClick(() => {
      postCardAction(this, {
        action: this.actionType,
        abilityName: this.abilityName,
        params: {
          message: this.message
        }
      });
    })
  }
}
```