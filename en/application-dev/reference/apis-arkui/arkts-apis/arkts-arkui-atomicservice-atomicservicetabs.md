# @ohos.atomicservice.AtomicServiceTabs(Provides an advanced struct of tabs for atomic services)

## Child Components

Not supported

## Attributes

The [universal attributes](../arkts-components/arkts-arkui-common-comp.md#common) are not supported.

## Modules to Import

```TypeScript
import { AtomicServiceTabs, TabBarOptions, TabBarPosition, TabContentBuilder, OnContentWillChangeCallback } from '@kit.ArkUI';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [TabBarOptions](arkts-arkui-atomicservice-atomicservicetabs-tabbaroptions-c.md) | Array of tab bar container configurations. |

### Structs

| Name | Description |
| --- | --- |
| [AtomicServiceTabs](arkts-arkui-atomicservice-atomicservicetabs-atomicservicetabs-s.md) | **AtomicServiceTabs** is an advanced component designed to streamline the use of the **Tabs** component by limiting customization options. It restricts the display to a maximum of five tabs, with fixed styles, positions, and sizes for the tabs. |

### Enums

| Name | Description |
| --- | --- |
| [TabBarPosition](arkts-arkui-atomicservice-atomicservicetabs-tabbarposition-e.md) | Position of the tab bar. The default value is **TabBarPosition.BOTTOM**. |

### Types

| Name | Description |
| --- | --- |
| [OnContentWillChangeCallback](arkts-arkui-oncontentwillchangecallback-t.md) | Defines the callback function triggered when the page content changes. |
| [TabContentBuilder](arkts-arkui-tabcontentbuilder-t.md) | Defines the content view container. |

## Examples

### Example 1: Pure Text Style



```TypeScript
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

### Example 2: Pure Icon Style



```TypeScript
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

### Example 3: Custom Layout with Text and Icons

```TypeScript
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
