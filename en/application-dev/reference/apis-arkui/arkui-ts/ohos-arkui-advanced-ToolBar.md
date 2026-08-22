# ToolBar

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangrunsen-->
<!--Designer: @YanSanzo-->
<!--Tester: @ybhou1993-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=4c495f520711bb7a7c0f878dd925391606600e97 translatedAt=2026-07-29T03:09:32.937Z pushedAt=2026-08-04T02:47:34.355Z -->

The **Toolbar** component is used to display operation options for the current interface content, shown at the bottom of the interface. It is suitable for scenarios where quick action entry points need to be provided for users, such as copy, paste, and share operations on an editing page. A maximum of 5 entries are displayed at the bottom. Any excess entries are collapsed into a "More" item, displayed on the far right.

> **NOTE**
>
> - This component is supported since API version 10. Updates will be marked with a superscript to indicate their earliest API version.
>
> - This component can be used only in the stage model.
>
> - If the **ToolBar** component has [universal attributes](ts-component-general-attributes.md) and [universal events](ts-component-general-events.md) configured, the compiler toolchain automatically generates an additional \_\_Common\_\_ node and mounts the universal attributes and universal events on this node rather than the **ToolBar** component itself. As a result, the configured universal attributes and universal events may fail to take effect or behave as intended. For this reason, avoid using universal attributes and events with the **ToolBar** component.

## Modules to Import

```ts
import { SymbolGlyphModifier, DividerModifier, ToolBar, ToolBarOptions, ToolBarModifier, ItemState, LengthMetrics } from '@kit.ArkUI';
```

## Child Components

Not supported

## ToolBar

ToolBar({toolBarList: ToolBarOptions, activateIndex?: number, controller: TabsController, dividerModifier?: DividerModifier, toolBarModifier?: ToolBarModifier})

The **Toolbar** component is designed to present a set of action options related to the current screen, displayed at the bottom of the screen. It can display up to five child components. If there are six or more child components, the first four are shown directly, and the additional ones are grouped under a **More** item on the rightmost side of the toolbar.

**Decorator**: @Component

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

| Name                         | Type                                                        | Mandatory| Decorator | Description                                                                                                                                                            |
| ----------------------------- | ------------------------------------------------------------ | ---- | ----------- |----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| toolBarList                   | [ToolBarOptions](#toolbaroptions)                            | Yes  | @ObjectLink | Toolbar list.<br>**Atomic service API**: This API can be used in atomic services since API version 11.                                                                                                    |
| activateIndex                 | number                                                       | No   | @Prop       | Index of the active item.<br/>Default value: **-1**, indicating no active item. Values less than -1 are treated as no active item.<br/>**Atomic service API:** This API can be used in atomic services since API version 11.                                           |
| controller                    | [TabsController](ts-container-tabs.md#tabscontroller)        | Yes   | -           | Toolbar controller used to associate with **Tabs** component page switching. It does not support controlling toolbar items.<br/>**NOTE**<br/>According to the [usage restrictions](../../../ui/state-management/arkts-custom-components-access-restrictions.md#constraints) of custom component member attribute access qualifiers, this API is a regular member variable. It can be initialized by passing parameters, or left uninitialized. When not passed, it is initialized with the component's preset value: **new TabsController()**.<br/>**Atomic service API:** This API can be used in atomic services since API version 11.                            |
| dividerModifier<sup>13+</sup> | [DividerModifier](ts-universal-attributes-attribute-modifier.md#custom-modifier) | No  | @Prop       | Modifier for the toolbar header divider, which can be used to customize the divider's height, color, and other attributes.<br>Default value: system default value<br>**Atomic service API**: This API can be used in atomic services since API version 13.                                                                   |
| toolBarModifier<sup>13+</sup> | [ToolBarModifier](#toolbarmodifier13)                        | No  | @Prop       | Modifier for the toolbar, which can be used to set the toolbar's height, background color, padding (which only takes effect when there are fewer than five toolbar items), and whether to display the pressed state.<br>Default value:<br>Height of the toolbar: **56vp**<br>Background color: **ohos_id_toolbar_bg**<br>Padding: **24vp**<br>Whether to display the pressed state: yes<br>**Atomic service API**: This API can be used in atomic services since API version 13.|

## ToolBarOptions

Inherits from Array<[ToolBarOption](#toolbaroption)>.

**Decorator Type**: \@Observed

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

## ToolBarOption

Defines the content and attributes of a toolbar.

**Decorator Type**: \@Observed

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

| Name                                    | Type                                                       | Read-Only| Optional| Description                                                                                                                                                                                                                                                    |
|----------------------------------------|-----------------------------------------------------------|---|---|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| content                                | [ResourceStr](ts-types.md#resourcestr)                    | No| No| Text of the toolbar item.<br>**Atomic service API**: This API can be used in atomic services since API version 11.                                                                                                                                                                                         |
| action                                 | ()&nbsp;=&gt;&nbsp;void                                   | No | Yes | Tap event of the toolbar item. If not passed in, tapping the item does not trigger any action.<br/>**Atomic service API:** This API can be used in atomic services since API version 11.                                                                                                                                                                                         |
| icon                                   | [Resource](ts-types.md#resource)                          | No | Yes | Icon of the toolbar item.<br/>By default, if not set or set to **undefined**, the icon is not displayed.<br/>When the **toolBarSymbolOptions** attribute is set, the icon attribute does not take effect.<br/>**Atomic service API:** This API can be used in atomic services since API version 11.                                                                                                                   |
| state                                  | [ItemState](#itemstate)                                   | No| Yes| State of the toolbar item.<br>Default value: **ItemState.ENABLE**<br>**Atomic service API**: This API can be used in atomic services since API version 11.                                                                                                                                                                |
| iconColor<sup>13+</sup>                | [ResourceColor](ts-types.md#resourcecolor)                | No | Yes | Fill color of the toolbar item icon.<br/>Default value: $r('sys.color.icon_primary').<br/>When the toolBarSymbolOptions attribute is set, this parameter does not take effect.<br/>**Atomic service API:** This API can be used in atomic services since API version 13.                                                                                                                                                |
| activatedIconColor<sup>13+</sup>       | [ResourceColor](ts-types.md#resourcecolor)                | No | Yes | Fill color of the toolbar item icon in the activated state.<br/>Default value: **$r('sys.color.icon_emphasize')**.<br/>When the **toolBarSymbolOptions** attribute is set, this parameter does not take effect.<br/>**Atomic service API:** This API can be used in atomic services since API version 13.                                                                                                                                           |
| textColor<sup>13+</sup>                | [ResourceColor](ts-types.md#resourcecolor)                | No| Yes| Font color of the toolbar item.<br>Default value: **$r('sys.color.font_primary')**<br>**Atomic service API**: This API can be used in atomic services since API version 13.                                                                                                                                                 |
| activatedTextColor<sup>13+</sup>       | [ResourceColor](ts-types.md#resourcecolor)                | No| Yes| Font color of the toolbar item in the activated state.<br>Default value: **$r('sys.color.font_emphasize')**<br>**Atomic service API**: This API can be used in atomic services since API version 13.                                                                                                                                            |
| toolBarSymbolOptions<sup>13+</sup>     | [ToolBarSymbolGlyphOptions](#toolbarsymbolglyphoptions13) | No | Yes | Icon attribute of the toolbar item, of the symbol type. After this parameter is set, the **icon** attribute does not take effect.<br/>**Atomic service API:** This API can be used in atomic services since API version 13.                                                                                                                                            |
| accessibilityText<sup>18+</sup>        | [ResourceStr](ts-types.md#resourcestr)                    | No | Yes | Accessibility text attribute of the toolbar item. When the component does not contain a text attribute, the screen reader does not announce it when this component is selected. Developers can set accessibility text for components that do not contain text information, so that the screen reader announces the text content when this component is selected.<br/>Default value: the content of the current item's content attribute.<br/>**Atomic service API:** This API can be used in atomic services since API version 18.                              |
| accessibilityDescription<sup>18+</sup> | [ResourceStr](ts-types.md#resourcestr)                    | No | Yes | Accessibility description of the toolbar item. Used to explain the function and operation consequences of the current component to users in detail, especially when such information cannot be directly obtained from the component text alone. When the component is selected, the content of the text attribute and the accessibility description attribute are announced in sequence.<br/>Default value: "Double-tap with one finger to execute".<br/>**Atomic service API:** This API can be used in atomic services since API version 18.      |
| accessibilityLevel<sup>18+</sup>       | string                                                    | No | Yes | Accessibility level of the toolbar item. Used to control whether the current item can be recognized by accessibility services.<br/>Supported values:<br/>**"auto"**: The current component is converted to **"yes"**.<br/>**"yes"**: The current component can be recognized by accessibility services.<br/>**"no"**: The current component cannot be recognized by accessibility services.<br/>**"no-hide-descendants"**: The current component and all its child components cannot be recognized by accessibility services.<br/>Default value: **"auto"**<br/>**Atomic service API:** This API can be used in atomic services since API version 18. |

## ToolBarModifier<sup>13+</sup>

Provides methods for setting the toolbar height, background color, left and right padding (takes effect only when the number of items is less than 5), and whether to display the pressed state (**stateEffect**).

**Atomic service API**: This API can be used in atomic services since API version 13.

### backgroundColor<sup>13+</sup>

backgroundColor(backgroundColor: ResourceColor): ToolBarModifier

Sets the toolbar background color.

**Atomic service API**: This API can be used in atomic services since API version 13.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

**Parameters**

| Name | Type                                                  | Mandatory| Description                                                              |
| ------- | ------------------------------------------------------ | ---- |------------------------------------------------------------------|
| backgroundColor | [ResourceColor](ts-types.md#resourcecolor) | Yes  | Toolbar background color.<br>Default value: **$r('sys.color.ohos_id_color_toolbar_bg')**|

**Return value**

| Type                                   | Description                                   |
|---------------------------------------|---------------------------------------|
| [ToolBarModifier](#toolbarmodifier13) | Returns the current **ToolBarModifier** object, which supports chained calls. |

### padding<sup>13+</sup>

padding(padding: LengthMetrics): ToolBarModifier

Sets the left and right padding of the toolbar.

**Atomic service API**: This API can be used in atomic services since API version 13.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

**Parameters**

| Name | Type    | Mandatory| Description                                                                                 |
| ------- |--------| ---- |-------------------------------------------------------------------------------------|
| padding | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) | Yes | Left and right padding of the toolbar. Takes effect only when the number of items is less than 5.<br/>By default, the toolbar padding is 24 vp when the number of items is less than 5, and 0 vp when the number of items is 5 or more. |

**Return value**

| Type                                   | Description                                   |
|---------------------------------------|---------------------------------------|
| [ToolBarModifier](#toolbarmodifier13) | Returns the current **ToolBarModifier** object, which supports chained calls. |

### height<sup>13+</sup>

height(height: LengthMetrics): ToolBarModifier

Sets the toolbar height. This height does not include the divider line height.

**Atomic service API**: This API can be used in atomic services since API version 13.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

**Parameters**

| Name | Type                             | Mandatory| Description                                |
| ------- |---------------------------------| ---- |------------------------------------|
| height | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) | Yes  | Height of the toolbar.<br>The default height of the toolbar is 56 vp, which does not include the divider.|

**Return value**

| Type                                   | Description                                   |
|---------------------------------------|---------------------------------------|
| [ToolBarModifier](#toolbarmodifier13) | Returns the current **ToolBarModifier** object, which supports chained calls. |

### stateEffect<sup>13+</sup>

stateEffect(stateEffect: boolean): ToolBarModifier

Sets whether to display the pressed state effect.

**Atomic service API**: This API can be used in atomic services since API version 13.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

**Parameters**

| Name | Type                            | Mandatory| Description                                                      |
| ------- |--------------------------------| ---- |----------------------------------------------------------|
| stateEffect | boolean | Yes  | Whether to display the pressed state effect on the toolbar.<br>The value **true** means to display the pressed state effect on the toolbar, and **false** means the opposite.<br>Default value: **true**|

**Return value**

| Type                                   | Description                                   |
|---------------------------------------|---------------------------------------|
| [ToolBarModifier](#toolbarmodifier13) | Returns the current **ToolBarModifier** object, which supports chained calls. |

## ItemState

Enumerates toolbar item states.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

| Name| Value| Description|
| -------- | -------- | -------- |
| ENABLE | 1 | The toolbar item is enabled.|
| DISABLE | 2 | The toolbar item is disabled.|
| ACTIVATE | 3 | The toolbar item is activated.|

## ToolBarSymbolGlyphOptions<sup>13+</sup>

Defines the icon symbol options.

**Atomic service API**: This API can be used in atomic services since API version 13.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

| Name  | Type      | Read-Only| Optional| Description                                                                                      |
| ------ | ---------- |---|---|------------------------------------------------------------------------------------------|
| normal | [SymbolGlyphModifier](ts-universal-attributes-attribute-symbolglyphmodifier.md#symbolglyphmodifier) | No| Yes| Icon symbol of the toolbar item in normal state.<br>Default value: **fontColor: $r('sys.color.icon_primary'), fontSize: 24vp** |
| activated| [SymbolGlyphModifier](ts-universal-attributes-attribute-symbolglyphmodifier.md#symbolglyphmodifier) | No| Yes| Icon symbol of the toolbar item in activated state.<br>Default value: **fontColor: $r('sys.color.icon_emphasize'), fontSize: 24vp**|

## Events

The [universal events](ts-component-general-events.md) are not supported.

## Example

### Example 1: Setting Toolbar Items to Different States

This example shows the various display effects when the **state** property of toolbar items is set to **ENABLE**, **DISABLE**, or **ACTIVATE**.

```ts
import { ToolBar, ToolBarOptions, ItemState } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State toolbarList: ToolBarOptions = new ToolBarOptions();

  aboutToAppear() {
    this.toolbarList.push({
      content: 'Long long long long long text',
      icon: $r('sys.media.ohos_ic_public_share'),
      action: () => {
      },
    })
    this.toolbarList.push({
      content: 'Copy',
      icon: $r('sys.media.ohos_ic_public_copy'),
      action: () => {
      },
      state: ItemState.DISABLE
    })
    this.toolbarList.push({
      content: 'Paste',
      icon: $r('sys.media.ohos_ic_public_paste'),
      action: () => {
      },
      state: ItemState.ACTIVATE
    })
    this.toolbarList.push({
      content: 'Select all',
      icon: $r('sys.media.ohos_ic_public_select_all'),
      action: () => {
      },
    })
    this.toolbarList.push({
      content: 'Share',
      icon: $r('sys.media.ohos_ic_public_share'),
      action: () => {
      },
    })
    this.toolbarList.push({
      content: 'Share',
      icon: $r('sys.media.ohos_ic_public_share'),
      action: () => {
      },
    })
  }

  build() {
    Row() {
      Stack() {
        Column() {
          ToolBar({
            activateIndex: 2,
            toolBarList: this.toolbarList,
          })
        }
      }
      .align(Alignment.Bottom)
      .width('100%')
      .height('100%')
    }
  }
}
```

![en-us_image_toolbar_example01](figures/image-toolbar-example01.png)

### Example 2: Customizing the Toolbar Style

This example demonstrates how to customize the toolbar's height, background color, and other styles using **ToolBarModifier**. This functionality is supported since API version 13.

```ts
import {
  SymbolGlyphModifier,
  DividerModifier,
  ToolBar,
  ToolBarOptions,
  ToolBarModifier,
  ItemState,
  LengthMetrics,
} from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State toolbarList: ToolBarOptions = new ToolBarOptions();
  // Custom toolbar style
  private toolBarModifier: ToolBarModifier =
    new ToolBarModifier().height(LengthMetrics.vp(52)).backgroundColor(Color.Transparent).stateEffect(false);
  @State dividerModifier: DividerModifier = new DividerModifier().height(0);

  aboutToAppear() {
    // Add toolbar items.
    this.toolbarList.push({
      content: 'Long long long long long long long long text',
      icon: $r('sys.media.ohos_ic_public_share'),
      action: () => {
      },
      state: ItemState.ACTIVATE,
      toolBarSymbolOptions: {
        normal: new SymbolGlyphModifier($r('sys.symbol.ohos_star')).fontColor([Color.Green]), // Symbol icon in the normal state.
        activated: new SymbolGlyphModifier($r('sys.symbol.ohos_star')).fontColor([Color.Red]), // Symbol icon in the activated state.
      },
      activatedTextColor: $r('sys.color.font_primary'),
    })
    this.toolbarList.push({
      content: 'Copy',
      icon: $r('sys.media.ohos_ic_public_copy'),
      action: () => {
      },
      state: ItemState.DISABLE,
      iconColor: '#ff18cb53',
      activatedIconColor: '#ffec5d5d', // Icon fill color of the toolbar item in the activated state.
      activatedTextColor: '#ffec5d5d', // Font color of the toolbar item in the activated state.
    })
    this.toolbarList.push({
      content: 'Paste',
      icon: $r('sys.media.ohos_ic_public_paste'),
      action: () => {
      },
      state: ItemState.ACTIVATE,
      textColor: '#ff18cb53',
    })
    this.toolbarList.push({
      content: 'All',
      icon: $r('sys.media.ohos_ic_public_select_all'),
      action: () => {
      },
      state: ItemState.ACTIVATE,
    })
    this.toolbarList.push({
      content: 'Share',
      icon: $r('sys.media.ohos_ic_public_share'),
      action: () => {
      },
    })
    this.toolbarList.push({
      content: 'Share',
      icon: $r('sys.media.ohos_ic_public_share'),
      action: () => {
      },
    })
  }

  build() {
    Row() {
      Stack() {
        Column() {
          ToolBar({
            toolBarModifier: this.toolBarModifier,
            dividerModifier: this.dividerModifier,
            activateIndex: 0,
            toolBarList: this.toolbarList,
          })
            .height(52)
        }
      }
      .align(Alignment.Bottom)
      .width('100%')
      .height('100%')
    }
  }
}
```

![en-us_image_toolbar_example02](figures/image-toolbar-example02.png)

### Example 3: Implementing Screen Reader Announcement

This example customizes the screen reader announcement text by setting the **accessibilityText**, **accessibilityDescription**, and **accessibilityLevel** properties of the toolbar item. This functionality is supported since API version 18.

```ts
import { ToolBar, ToolBarOptions, ItemState } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State toolbarList: ToolBarOptions = new ToolBarOptions();

  aboutToAppear() {
    // Add toolbar items.
    this.toolbarList.push({
      content: 'Long long long long long text',
      icon: $r('sys.media.ohos_ic_public_share'),
      action: () => {
      },
      accessibilityText: 'Clip', // Screen reader announcement for the item.
      accessibilityDescription: 'Double-tap to clip', // Screen reader announcement for the item.
      accessibilityLevel: 'yes' // Configure this element to be focused by accessibility screen readers.
    })
    this.toolbarList.push({
      content: 'Copy',
      icon: $r('sys.media.ohos_ic_public_copy'),
      action: () => {
      },
      state: ItemState.DISABLE,
      accessibilityLevel: 'no' // Configure this button to be not recognizable by screen readers.
    })
    this.toolbarList.push({
      content: 'Paste',
      icon: $r('sys.media.ohos_ic_public_paste'),
      action: () => {
      },
      state: ItemState.ACTIVATE
    })
    this.toolbarList.push({
      content: 'Select all',
      icon: $r('sys.media.ohos_ic_public_select_all'),
      action: () => {
      },
    })
    this.toolbarList.push({
      content: 'Share',
      icon: $r('sys.media.ohos_ic_public_share'),
      action: () => {
      },
    })
    this.toolbarList.push({
      content: 'Share',
      icon: $r('sys.media.ohos_ic_public_share'),
      action: () => {
      },
    })
  }

  build() {
    Row() {
      Stack() {
        Column() {
          ToolBar({
            activateIndex: 2,
            toolBarList: this.toolbarList,
          })
        }
      }
      .align(Alignment.Bottom)
      .width('100%')
      .height('100%')
    }
  }
}
```

![en-us_image_toolbar_example01](figures/image-toolbar-example01.png)