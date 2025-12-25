# AtomicServiceNavigation

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @qq_36417014-->
<!--Designer: @zhangbeilei-->
<!--Tester: @tinygreyy-->
<!--Adviser: @zengyawen-->

**AtomicServiceNavigation** is a component that serves as the root container of a page. By default, it includes a title bar, content area, and toolbar. The content area switches between the home page content (child components of [NavDestination](ts-basic-components-navdestination.md)) and non-home page content through routing.

> **NOTE**
>
> This component is supported since API version 12. Updates will be marked with a superscript to indicate their earliest API version.

## Modules to Import

``` ts
import { AtomicServiceNavigation } from '@kit.ArkUI';
```

## Child Components

Supported
Since API version 10, you are advised to use [NavPathStack](ts-basic-components-navigation.md#navpathstack10) for page routing.
## AtomicServiceNavigation

``` ts
AtomicServiceNavigation({
    navPathStack?: NavPathStack,
    navigationContent: Callback<void>,
    title?: ResourceStr,
    titleOptions?: TitleOptions,
    gradientBackground?: GradientBackground,
    hideTitleBar?: boolean,
    navBarWidth?: Length,
    mode?: NavigationMode,
    navDestinationBuilder?: NavDestinationBuilder,
    navBarWidthRange?: [Dimension, Dimension],
    minContentWidth?: Dimension,
    sideBarOptions?: sideBarOptions,
    sideBarContent?: Callback<void>,
    menus?: CustomBuilder | Array<NavigationMenuItem>,
    stateChangeCallback?: Callback<boolean>,
    modeChangeCallback?: Callback<NavigationMode>
})
```

**Decorator**: @Component

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Decorator|Description|
| --------------- | ------ | ---- | ----|----------|
| navPathStack | [NavPathStack](ts-basic-components-navigation.md#navpathstack10) | No| @State | Information about the navigation stack.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| navigationContent | Callback\<void\> | No| @BuilderParam | Content of the navigation container.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| title | [ResourceStr](ts-types.md#resourcestr) | No|@Prop | Page title. The default value is an empty string. Title text will be hidden when the **titleBarType** field of **titleOptions** is set to **[TitleBarType](#titlebartype18).ROUND_ICON** or **[TitleBarType](#titlebartype18).SQUARED_ICON** and **titleIcon** is configured.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| titleOptions | [TitleOptions](#titleoptions) | No| @Prop | Title bar options. Title text will be hidden when the **titleBarType** field of **titleBarType** is set to **[TitleBarType](#titlebartype18).ROUND_ICON** or **[TitleBarType](#titlebartype18).SQUARED_ICON** and **titleIcon** is configured.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| gradientBackground<sup>18+</sup> | [GradientBackground](#gradientbackground18) | No| @Prop | Background color options.<br>**Atomic service API**: This API can be used in atomic services since API version 18.|
| hideTitleBar | boolean | No| @Prop | Whether to hide the title bar. The default value is **false**.<br>The value **true** means to hide the title bar, and **false** means the opposite.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| navBarWidth | [Length](ts-types.md#length)| No| @Prop | Width of the navigation bar. The default value is **240vp**.<br>This property takes effect only when the component is in split-column mode.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| mode| [NavigationMode](ts-basic-components-navigation.md#navigationmode9)| No| @Prop |Display mode of the navigation bar.<br>Available options are **Stack**, **Split**, and **Auto**.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| navDestinationBuilder | [NavDestinationBuilder](#navdestinationbuilder) | No| @BuilderParam | Builder data required for creating the [NavDestination](ts-basic-components-navdestination.md) component.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| navBarWidthRange | [[Dimension](ts-types.md#dimension10), [Dimension](ts-types.md#dimension10)] | No| @Prop |Minimum and maximum widths of the navigation bar (effective in dual-column mode). Default value: **240vp** for the minimum value; 40% of the component width (not greater than 432 vp) for the maximum value; if either of the widths is not set, the default value is used for that width. Unit: vp.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| minContentWidth | [Dimension](ts-types.md#dimension10) | No| @Prop | Minimum width of the navigation bar content area (effective in dual-column mode).<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| sideBarOptions<sup>18+</sup> | [SideBarOptions](#sidebaroptions18) | No| @Prop | Sidebar options.<br>**Atomic service API**: This API can be used in atomic services since API version 18.|
| sideBarContent<sup>18+</sup> | Callback\<void\> | No| @BuilderParam | Content of the sidebar.<br>**Atomic service API**: This API can be used in atomic services since API version 18.|
| menus<sup>18+</sup> | [CustomBuilder](ts-types.md#custombuilder8) \| Array\<[NavigationMenuItem](ts-basic-components-navigation.md#navigationmenuitem)\> | No| @BuilderParam | Custom layout styles for wide-screen scenarios. The default value is empty, with no styles displayed. Wide-screen scenarios refer to scenarios where the screen width is greater than or equal to 600 vp.<br>**Atomic service API**: This API can be used in atomic services since API version 18.|
| stateChangeCallback | Callback\<boolean\> | No| - | Callback invoked when the navigation bar visibility status changes. **true** means that the navigation bar visibility status changes.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| modeChangeCallback | Callback\<[NavigationMode](ts-basic-components-navigation.md#navigationmode9)\>| No| - | Callback invoked when the component is displayed for the first time or its display mode switches between single-column and dual-column.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|

## TitleOptions
Title bar options.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| --------------- | ------ | ---- | -- | ---------- |
| backgroundColor | [ResourceColor](ts-types.md#resourcecolor) | No| Yes| Background color of the title bar.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| isBlurEnabled | boolean | No| Yes| Whether the title bar is blurred. Default value: **true**, meaning the title bar is blurred.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| barStyle | [BarStyle](ts-basic-components-navigation.md#barstyle12)  | No| Yes| Style options of the title bar.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| titleBarType<sup>18+</sup> | [TitleBarType](#titlebartype18) | No| Yes| Type of the title bar. <br>Default value: **TitleBarType.ROUND_ICON**<br>**Atomic service API**: This API can be used in atomic services since API version 18.|
| titleIcon<sup>18+</sup> | [Resource](ts-types.md#resource) \| [SymbolGlyphModifier](ts-universal-attributes-attribute-modifier.md) | No| Yes| Icon of the title bar. Default value: **$r('sys.color.ohos_id_color_titlebar_icon')**<br>**Atomic service API**: This API can be used in atomic services since API version 18.|

## GradientBackground<sup>18+</sup>
Provides options for setting gradient colors for branding.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| --------------- | ------ | ---- | -- | ---------- |
| primaryColor | [ResourceColor](ts-types.md#resourcecolor)  | No| No| Color value for single-color gradients and the first color in dual-color gradients.<br> No default value.|
| secondaryColor |[ResourceColor](ts-types.md#resourcecolor)  | No| Yes|Second color in dual-color gradients.<br> No default value.|
| backgroundTheme |[BackgroundTheme](#backgroundtheme18)  | No| Yes|Background theme of the navigation bar. <br>Default value: **DEFAULT**|
| mixMode | [MixMode](#mixmode18)  | No| Yes|How the two colors blend in dual-color gradients. It is effective only when both **primaryColor** and **secondaryColor** are set. Default value: **TOWARDS**.|
| alpha | [GradientAlpha](#gradientalpha18)  | No| Yes|Opacity of the gradient display area. Default value: **OPACITY_20**|

## NavDestinationBuilder

type NavDestinationBuilder = (name: string, param?: Object) => void

Defines the content of the **NavDestination** component.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| --------------- | ------ | ---- | ---------- |
| name | string | Yes| Name of the [NavDestination](ts-basic-components-navdestination.md) page.|
| param | Object | No| Settings of the [NavDestination](ts-basic-components-navdestination.md) page.|

## MixMode<sup>18+</sup>
Provides options for background color blending modes.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Value| Description|
| --------------- | ------ |-----|
| AVERAGE  | 1 | Both colors are evenly mixed. |
| CROSS  | 2 | One color passes through the other.|
| TOWARDS  | 3 | One color gradually blends into the other.|

## TitleBarType<sup>18+</sup>
Enumerates the title bar types. The default type is **ROUND_ICON**.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Value| Description|
| --------------- | ------ |-----|
| SQUARED_ICON  | 1 | Square icon style.|
| ROUND_ICON | 2 | Round icon style.|
| DRAWER | 3 | Drawer style.|

## GradientAlpha<sup>18+</sup>
Enumerates the opacity levels of the navigation bar background.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Value| Description|
| --------------- | ------ |-----|
| OPACITY_20| 1 | 0.2 opacity.|
| OPACITY_60| 2 | 0.6 opacity.|
| OPACITY_80| 3 | 0.8 opacity.|
| OPACITY_100| 4 | 1.0 opacity.|

## BackgroundTheme<sup>18+</sup>
Enumerates the navigation bar background themes.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Value| Description|
| --------------- | ------ |-----|
| DARK  | 1 | Dark theme.|
| LIGHT  | 2 | Light theme.|
| DEFAULT  | 3 | Light gray theme, with the color value of #F1F3F5.|

## SideBarOptions<sup>18+</sup>
Provides sidebar options.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| --------------- | ------ | ---- | -- | ---------- |
| sideBarBackground | [ResourceColor](ts-types.md#resourcecolor) | No| Yes| Background color of the sidebar. <br>Default value: **$r('sys.color.ohos_id_color_sub_background')**|
| onChange | Callback\<boolean\> | No| Yes| Callback triggered when the sidebar is shown or hidden. **true**: The sidebar is shown. **false**: The sidebar is hidden.|
| sideBarIcon | [Resource](ts-types.md#resource) \| [SymbolGlyphModifier](ts-universal-attributes-attribute-modifier.md) | No| Yes| Icon of the sidebar. Default value: **$r('sys.symbol.open_sidebar')**|

## Example

### Example 1: Setting the Layout and Gradient Background
This example demonstrates how to set the basic style of the **AtomicServiceNavigation** component with a gradient background.

```ts
import { AtomicServiceNavigation, MixMode, GradientAlpha, BackgroundTheme } from '@kit.ArkUI';
import { AtomicServiceTabs, TabBarOptions, TabBarPosition } from '@kit.ArkUI';
@Entry
@Component
struct Index {
  @State message: string = 'Title';
  childNavStack: NavPathStack = new NavPathStack();
  @Builder
  tabContent1() {
    Text('first page')
      .onClick(() => {
        this.childNavStack.pushPath({ name: 'page one' })
      })
  }

  @Builder
  tabContent2() {
    Text('second page')
  }

  @Builder
  tabContent3() {
    Text('third page')
  }

  @Builder
  navigationContent() {
    AtomicServiceTabs({
      tabContents: [
        () => {
          this.tabContent1()
        },
        () => {
          this.tabContent2()
        },
        () => {
          this.tabContent3()
        }
      ],
      tabBarOptionsArray: [
        new TabBarOptions($r('sys.media.ohos_ic_public_phone'), 'Feature 1'),
        new TabBarOptions($r('sys.media.ohos_ic_public_location'), 'Feature 2', Color.Green, Color.Red),
        new TabBarOptions($r('sys.media.ohos_ic_public_more'), 'Feature 3')
      ],
      tabBarPosition: TabBarPosition.BOTTOM,
      barBackgroundColor: $r('sys.color.ohos_id_color_bottom_tab_bg'),
      onTabBarClick: (index: Number) => {
        if (index == 0) {
          this.message = 'Feature 1';
        } else if (index == 1) {
          this.message = 'Feature 2';
        } else {
          this.message = 'Feature 3';
        }
      }
    })
  }

  @Builder
  pageMap(name: string) {
    if (name === 'page one') {
      PageOne()
    } else if (name === 'page two') {
      PageTwo()
    }
  }

  build() {
    Row() {
      Column() {
        AtomicServiceNavigation({
          navigationContent: () => {
            this.navigationContent()
          },
          title: this.message,
          titleOptions: {
            isBlurEnabled: false
          },
          gradientBackground: {
            primaryColor: '#FF0000',
            secondaryColor: '#00FF00',
            backgroundTheme: BackgroundTheme.LIGHT,
            mixMode: MixMode.AVERAGE,
            alpha: GradientAlpha.OPACITY_100
          },
          navDestinationBuilder: this.pageMap,
          navPathStack: this.childNavStack,
          mode: NavigationMode.Stack
        })
      }
      .width('100%')
    }
    .height('100%')
  }
}

@Component
export struct PageOne {
  pageInfo: NavPathStack = new NavPathStack();

  build() {
    NavDestination() {
      Button('Next')
        .onClick(() => {
          this.pageInfo.pushPath({ name: 'page two'})
        })
    }
    .title('PageOne')
    .onReady((context: NavDestinationContext) => {
      this.pageInfo = context.pathStack;
    })
  }
}

@Component
export struct PageTwo {
  pageInfo: NavPathStack = new NavPathStack();

  build() {
    NavDestination() {
      Button('End')
    }
    .title('PageTwo')
    .onReady((context: NavDestinationContext) => {
      this.pageInfo = context.pathStack;
    })
  }
}
```

![](figures/AtomicServiceNavigationDemo02.jpg)

### Example 2: Implementing the Drawer Style with Custom Layouts for Wide-Screen Scenarios

This example demonstrates how to implement the drawer style and insert custom layouts into the title bar in wide-screen scenarios (width > 600 vp).

```ts
import { AtomicServiceNavigation, TitleBarType } from '@kit.ArkUI';
import { AtomicServiceTabs, TabBarOptions, TabBarPosition } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';
  childNavStack: NavPathStack = new NavPathStack();

  @Builder
  tabContent1() {
    Text('First page')
      .onClick(() => {
        this.childNavStack.pushPath({ name: 'page one' })
      })
  }

  @Builder
  tabContent2() {
    Text('Second page')
  }

  @Builder
  tabContent3() {
    Text('Third page')
  }

  @Builder
  navigationContent() {
    AtomicServiceTabs({
      tabContents: [
        () => {
          this.tabContent1()
        },
        () => {
          this.tabContent2()
        },
        () => {
          this.tabContent3()
        }
      ],
      tabBarOptionsArray: [
        new TabBarOptions($r('sys.media.ohos_ic_public_phone'), 'Feature 1'),
        new TabBarOptions($r('sys.media.ohos_ic_public_location'), 'Feature 2', Color.Green, Color.Red),
        new TabBarOptions($r('sys.media.ohos_ic_public_more'), 'Feature 3')
      ],
      tabBarPosition: TabBarPosition.BOTTOM,
      barBackgroundColor: $r('sys.color.ohos_id_color_bottom_tab_bg'),
      onTabBarClick: (index: Number) => {
        if (index == 0) {
          this.message = 'Feature 1';
        } else if (index == 1) {
          this.message = 'Feature 2';
        } else {
          this.message = 'Feature 3';
        }
      }
    })
  }

  @Builder
  pageMap(name: string) {
    if (name === 'page one') {
      PageOne()
    } else if (name === 'page two') {
      PageTwo()
    }
  }

  @State showText: string = 'time: ';
  @State time: number = 0;

  @Builder
  insertComp() {
    Text('This is the menu area')
      .fontColor(Color.Red)
      .width(200)
      .height('100%')
  }

  build() {
    Column() {
      AtomicServiceNavigation({
        navigationContent: () => {
          this.navigationContent()
        },
        navDestinationBuilder: this.pageMap,
        navPathStack: this.childNavStack,
        title: this.message,
        titleOptions: {
          titleIcon: $r('app.media.startIcon'),
          backgroundColor: 'rgb(61, 157, 180)',
          titleBarType: TitleBarType.DRAWER
        },
        menus: () => { this.insertComp() },
        mode: NavigationMode.Stack
      })
    }
    .width('100%')
  }
}

@Component
export struct PageOne {
  pageInfo: NavPathStack = new NavPathStack();

  build() {
    NavDestination() {
      Button('Next')
        .onClick(() => {
          this.pageInfo.pushPath({ name: 'page two'})
        })
    }
    .title('PageOne')
    .onReady((context: NavDestinationContext) => {
      this.pageInfo = context.pathStack;
    })
  }
}

@Component
export struct PageTwo {
  pageInfo: NavPathStack = new NavPathStack();

  build() {
    NavDestination() {
      Button('End')
    }
    .title('PageTwo')
    .onReady((context: NavDestinationContext) => {
      this.pageInfo = context.pathStack;
    })
  }
}
```
![](figures/AtomicServiceNavigationDemo03.png)

### Example 3: Configuring the Sidebar

This example demonstrates how to set the sidebar background color and content style.

```ts
import { AtomicServiceNavigation, TitleBarType } from '@kit.ArkUI';
import { AtomicServiceTabs, TabBarOptions, TabBarPosition } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';
  childNavStack: NavPathStack = new NavPathStack();

  @Builder
  tabContent1() {
    Text('first page')
      .onClick(() => {
        this.childNavStack.pushPath({ name: 'page one' })
      })
  }

  @Builder
  tabContent2() {
    Text('second page')
  }

  @Builder
  tabContent3() {
    Text('third page')
  }

  @Builder
  navigationContent() {
    AtomicServiceTabs({
      tabContents: [
        () => {
          this.tabContent1()
        },
        () => {
          this.tabContent2()
        },
        () => {
          this.tabContent3()
        }
      ],
      tabBarOptionsArray: [
        new TabBarOptions($r('sys.media.ohos_ic_public_phone'), 'Feature 1'),
        new TabBarOptions($r('sys.media.ohos_ic_public_location'), 'Feature 2', Color.Green, Color.Red),
        new TabBarOptions($r('sys.media.ohos_ic_public_more'), 'Feature 3')
      ],
      tabBarPosition: TabBarPosition.BOTTOM,
      barBackgroundColor: $r('sys.color.ohos_id_color_bottom_tab_bg'),
      onTabBarClick: (index: Number) => {
        if (index == 0) {
          this.message = 'Feature 1';
        } else if (index == 1) {
          this.message = 'Feature 2';
        } else {
          this.message = 'Feature 3';
        }
      }
    })
  }

  @Builder
  pageMap(name: string) {
    if (name === 'page one') {
      PageOne()
    } else if (name === 'page two') {
      PageTwo()
    }
  }

  @State showText: string = 'time: ';
  @State time: number = 0;

  @Builder
  insertComp() {
    Text('This is menus area')
      .fontColor(Color.Red)
      .width(200)
      .height('100%')
  }

  @Builder
  sideBarContentBuilder() {
    Text('This is sideBar content area')
      .fontSize(20)
  }

  build() {
    Column() {
      AtomicServiceNavigation({
        navigationContent: () => {
          this.navigationContent()
        },
        navDestinationBuilder: this.pageMap,
        navPathStack: this.childNavStack,
        title: this.message,
        titleOptions: {
          titleIcon: $r('app.media.startIcon'),
          backgroundColor: 'rgb(61, 157, 180)',
          titleBarType: TitleBarType.DRAWER
        },
        sideBarOptions: {
          sideBarBackground: '#409EFF'
        },
        sideBarContent: () => { this.sideBarContentBuilder() },
        mode: NavigationMode.Stack
      })
    }
    .width('100%')
  }
}

@Component
export struct PageOne {
  pageInfo: NavPathStack = new NavPathStack();

  build() {
    NavDestination() {
      Button('Next')
        .onClick(() => {
          this.pageInfo.pushPath({ name: 'page two'})
        })
    }
    .title('PageOne')
    .onReady((context: NavDestinationContext) => {
      this.pageInfo = context.pathStack;
    })
  }
}

@Component
export struct PageTwo {
  pageInfo: NavPathStack = new NavPathStack();

  build() {
    NavDestination() {
      Button('End')
    }
    .title('PageTwo')
    .onReady((context: NavDestinationContext) => {
      this.pageInfo = context.pathStack;
    })
  }
}
```
![](figures/AtomicServiceNavigationDemo04.png)
