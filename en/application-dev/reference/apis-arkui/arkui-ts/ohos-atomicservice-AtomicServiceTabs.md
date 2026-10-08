# AtomicServiceTabs

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @qq_36417014-->
<!--Designer: @autojuan-->
<!--Tester: @tinygreyy-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=cd28aee4d9ab08183535dbed788fa24b4fdf5faa translatedAt=2026-08-28T01:34:34.637Z pushedAt=2026-08-28T07:26:02.532Z -->

**AtomicServiceTabs** is an advanced component designed to streamline the attributes of the **Tabs** component that do not need to be exposed to users for customization. It restricts the display to a maximum of five tabs, with fixed styles, positions, and sizes for the tabs.

> **NOTE**
>
> This component is supported since API version 12. Updates will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { AtomicServiceTabs, TabBarOptions, TabBarPosition, OnContentWillChangeCallback } from '@kit.ArkUI';
```

## Child Components

Not supported

## Attributes

The [universal attributes](ts-component-general-attributes.md) are not supported.

## AtomicServiceTabs

```ts
AtomicServiceTabs({
   tabContents?: [ TabContentBuilder?,
                    TabContentBuilder?,
                  TabContentBuilder?,
                  TabContentBuilder?,
                  TabContentBuilder?
                ],
   tabBarOptionsArray: [ TabBarOptions,
                        TabBarOptions,
                        TabBarOptions?,
                        TabBarOptions?,
                        TabBarOptions?
                      ],
   tabBarPosition?: TabBarPosition,
   layoutMode?: LayoutMode,
   barBackgroundColor?: ResourceColor,
   index?: number,
   barOverlap?: boolean,
   controller?: TabsController,
   onChange?: Callback<number>,
   onTabBarClick?: Callback<number>,
   onContentWillChange?: OnContentWillChangeCallback,
})
```

**Decorator**: \@Component

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Decorator| Description|
| --------------- | ------ | ---- | ----|----|
| tabContents | [[TabContentBuilder?](#tabcontentbuilder),[TabContentBuilder?](#tabcontentbuilder), [TabContentBuilder?](#tabcontentbuilder),[TabContentBuilder?](#tabcontentbuilder), [TabContentBuilder?](#tabcontentbuilder)] | No | @BuilderParam | Array of content view containers. A maximum of 5 tabs are supported. Default value: empty. |
| tabBarOptionsArray | [[TabBarOptions](#tabbaroptions),[TabBarOptions](#tabbaroptions), [TabBarOptions?](#tabbaroptions),[TabBarOptions?](#tabbaroptions), [TabBarOptions?](#tabbaroptions)]  | Yes | @Prop | Array of tab bar options. A maximum of 5 tabs are supported. |
| tabBarPosition | [TabBarPosition](#tabbarposition) | No  |@Prop | Position of the tab bar. The default value is **TabBarPosition.BOTTOM**.|
| layoutMode<sup>18+</sup> | [LayoutMode](ts-container-tabcontent.md#layoutmode10) | No   |@Prop | Layout mode of the images and text on the bottom tab. The default value is **LayoutMode.VERTICAL**.<br>**Atomic service API:** This API can be used in atomic services since API version 18. |
| barBackgroundColor | [ResourceColor](ts-types.md#resourcecolor) | No| @Prop | Background color of the tab bar. The default value is transparent.|
| index | number | No | @Prop | Index of the currently displayed tab. The index value starts from 0, ranges from 0 to (number of tabs - 1), and does not exceed 4. Default value: **0**. |
| barOverlap | boolean| No | @Prop | Whether the tab bar background is blurred and overlaid on the TabContent. The value **true** indicates that the tab bar background is blurred and overlaid on the TabContent, and **false** indicates that the tab bar background is not blurred and not overlaid on the TabContent. Default value: **true**. |
| controller|[TabsController](ts-container-tabs.md#tabscontroller) | No | - | Tab controller, which is used to control tab switching. Default value: **new TabsController()**. |
| onChange | Callback\<number\> | No | - | Event triggered after a tab is switched. The callback parameter is the index of the tab after switching, and the index value starts from 0. When the **onContentWillChange** callback returns **false** to intercept the page switching, this event is not triggered. Default value: empty. |
| onTabBarClick | Callback\<number\> | No | - | Event triggered after a tab is clicked. The callback parameter is the index value of the clicked tab, and the index value starts from 0. Default value: empty. |
| onContentWillChange | [OnContentWillChangeCallback](#oncontentwillchangecallback) | No | - | Event for intercepting page switching of Tabs. This callback is triggered when a new page is about to be displayed. When the callback returns **false** to intercept the page switching, the **onChange** event is not triggered. Default value: empty. |

## TabContentBuilder

type TabContentBuilder = () => void

Content view builder, a function used to build the content of the **TabContent** tab.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

## TabBarOptions

Defines the tab options.

### constructor

constructor(icon: ResourceStr | TabBarSymbol, text: ResourceStr, unselectedColor?: ResourceColor, selectedColor?: ResourceColor)

A constructor used to create a **TabBarOptions** instance.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| --------------- | ------ |------ |------ |
| icon | [ResourceStr](ts-types.md#resourcestr) \| [TabBarSymbol](ts-container-tabcontent.md#tabbarsymbol12) | Yes | Icon for the tab. |
| text | [ResourceStr](ts-types.md#resourcestr) | Yes| Text of the tab.|
| unselectedColor | [ResourceColor](ts-types.md#resourcecolor) | No | Color of the tab when it is not selected.<br>Default value: **#99182431** |
| selectedColor | [ResourceColor](ts-types.md#resourcecolor) | No | Color of the tab when it is selected.<br>Default value: **#FF007DFF** |

## TabBarPosition

Sets the position of the tab bar. The default value is **TabBarPosition.BOTTOM**.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Value| Description|
| --------------- | ------ |-----|
| LEFT  | 0 | The tab bar is on the left side of the screen. |
| BOTTOM  | 1 | The tab bar is at the bottom of the screen.|

## OnContentWillChangeCallback

type OnContentWillChangeCallback = (currentIndex: number, comingIndex: number) => boolean

Triggered when the page content is about to change. It is used to intercept page switching, and developers can control whether to allow the switch through the return value.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| --------------- | ------ |------ |------ |
| currentIndex | number | Yes| Index of the current tab.|
| comingIndex | number | Yes| Index of the tab to be switched to.|

**Return value**

| Type| Description|
|--|--|
| boolean | The value **true** indicates that switching to the page to be displayed is allowed, and **false** indicates that switching is not allowed and the current page content is still displayed. |

## Examples

### Example 1: Pure Text Style

```ts
// Index.ets
import { AtomicServiceTabs, TabBarOptions, TabBarPosition, OnContentWillChangeCallback } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State onClickNumber: number = 0;
  @State currentIndex: number = 0;
  @State comingIndex: number = 0;
  onContentWillChangeCallback: OnContentWillChangeCallback = (currentIndex: number, comingIndex: number): boolean => {
    this.currentIndex = currentIndex;
    this.comingIndex = comingIndex;
    console.info('OnContentWillChangeCallback');
    return true;
  }
  onTabClick: Callback<number> = (index: number) => {
    this.onClickNumber++;
    console.info('onTabClick');
  }
  @Builder
  tabContent1() {
    Column().width('100%').height('100%').alignItems(HorizontalAlign.Center).backgroundColor('#00CB87')
  }

  @Builder
  tabContent2() {
    Column().width('100%').height('100%').backgroundColor('#007DFF')
  }

  @Builder
  tabContent3() {
    Column().width('100%').height('100%').backgroundColor('#FFBF00')
  }

  build() {
    Stack() {
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
        new TabBarOptions('', 'Green', Color.Black, Color.Green),
        new TabBarOptions('', 'Blue', Color.Black, Color.Blue),
        new TabBarOptions('', 'Yellow', Color.Black, Color.Yellow),
      ],
      tabBarPosition: TabBarPosition.BOTTOM,
      barBackgroundColor: $r('sys.color.ohos_id_color_bottom_tab_bg'),
      onTabBarClick: this.onTabClick,
      onContentWillChange: this.onContentWillChangeCallback,
    })
    Column() {
      Text('onTabBarClick callback times: ' + this.onClickNumber)
      Text('comingIndex = ' + this.comingIndex + ', currentIndex = ' + this.currentIndex)
    }.margin({top:500})
    }.height('100%')
  }
}
```

![atomicservicetabs](figures/atomicserviceTabs_text.PNG)

### Example 2: Pure Icon Style

```ts
// Index.ets
import { AtomicServiceTabs, TabBarOptions, TabBarPosition, OnContentWillChangeCallback } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State onClickNumber: number = 0;
  @State currentIndex: number = 0;
  @State comingIndex: number = 0;
  onContentWillChangeCallback: OnContentWillChangeCallback = (currentIndex: number, comingIndex: number): boolean => {
    this.currentIndex = currentIndex;
    this.comingIndex = comingIndex;
    console.info('OnContentWillChangeCallback');
    return true;
  }
  onTabClick: Callback<number> = (index: number) => {
    this.onClickNumber++;
    console.info('onTabClick');
  }
  @Builder
  tabContent1() {
    Column().width('100%').height('100%').alignItems(HorizontalAlign.Center).backgroundColor('#00CB87')
  }

  @Builder
  tabContent2() {
    Column().width('100%').height('100%').backgroundColor('#007DFF')
  }

  @Builder
  tabContent3() {
    Column().width('100%').height('100%').backgroundColor('#FFBF00')
  }

  build() {
    Stack() {
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
        new TabBarOptions($r('sys.media.ohos_ic_public_phone'), '', Color.Black, Color.Blue),
        new TabBarOptions($r('sys.media.ohos_ic_public_location'), '', Color.Black, Color.Blue),
        new TabBarOptions($r('sys.media.ohos_ic_public_more'), '', Color.Black, Color.Blue),
      ],
      tabBarPosition: TabBarPosition.BOTTOM,
      barBackgroundColor: $r('sys.color.ohos_id_color_bottom_tab_bg'),
      onTabBarClick: this.onTabClick,
      onContentWillChange: this.onContentWillChangeCallback,
    })
    Column() {
      Text('onTabBarClick callback times: ' + this.onClickNumber)
      Text('comingIndex = ' + this.comingIndex + ', currentIndex = ' + this.currentIndex)
    }.margin({top:500})
    }.height('100%')
  }
}
```

![atomicservicetabs](figures/atomicserviceTabs_icon.PNG)

### Example 3: Custom Layout with Text and Icons

```ts
// Index.ets
import { AtomicServiceTabs, TabBarOptions, TabBarPosition, OnContentWillChangeCallback } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State onClickNumber: number = 0;
  @State currentIndex: number = 0;
  @State comingIndex: number = 0;
  @State layoutMode: LayoutMode = LayoutMode.VERTICAL;
  onContentWillChangeCallback: OnContentWillChangeCallback = (currentIndex: number, comingIndex: number): boolean => {
    this.currentIndex = currentIndex;
    this.comingIndex = comingIndex;
    console.info('OnContentWillChangeCallback');
    return true;
  }
  onTabClick: Callback<number> = (index: number) => {
    this.onClickNumber++;
    console.info('onTabClick');
  }
  onChange: Callback<number> = (index: number) => {
    console.info('onChange');
  }

  @Builder
  tabContent1() {
    Column().width('100%').height('100%').alignItems(HorizontalAlign.Center).backgroundColor('#00CB87')
  }

  @Builder
  tabContent2() {
    Column().width('100%').height('100%').backgroundColor(Color.Blue)
  }

  @Builder
  tabContent3() {
    Column().width('100%').height('100%').backgroundColor('#FFBF00')
  }

  build() {
    Stack() {
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
          },
        ],
        tabBarOptionsArray: [
        new TabBarOptions($r('sys.media.ohos_ic_public_phone'), 'Green', Color.Black, Color.Blue),
        new TabBarOptions($r('sys.media.ohos_ic_public_location'), 'Blue', Color.Black, Color.Blue),
        new TabBarOptions($r('sys.media.ohos_ic_public_more'), 'Yellow', Color.Black, Color.Blue),
        ],
        tabBarPosition: TabBarPosition.BOTTOM,
        barBackgroundColor: $r('sys.color.ohos_id_color_bottom_tab_bg'),
        onTabBarClick: this.onTabClick,
        onContentWillChange: this.onContentWillChangeCallback,
        onChange: this.onChange,
        layoutMode: this.layoutMode,
      })

      Column() {
        Button('Vertical Layout')
          .width('30%')
          .height(50)
          .margin({ top: 5 })
          .onClick((event?: ClickEvent) => {
            this.layoutMode = LayoutMode.VERTICAL;
          })
        Button('Horizontal Layout')
          .width('30%')
          .height(50)
          .margin({ top: 5 })
          .onClick((event?: ClickEvent) => {
            this.layoutMode = LayoutMode.HORIZONTAL;
          })
      }.margin({ top: 10 })
    }.height('100%')
  }
}
```

![atomicservicetabs](figures/atomicservicetabs_layoutMode.gif)