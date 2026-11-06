# Panel

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @hehongyang3-->
<!--Designer: @hehongyang3-->
<!--Tester: @lxl007-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=39ca26def5c22dc659f3dc0b76ef62a29421e77a translatedAt=2026-08-19T07:02:37.530Z pushedAt=2026-08-20T10:45:03.042Z -->

<!--deprecated_code_no_check-->

The **Panel** component is a slidable panel that presents lightweight content with flexible sizes.

> **NOTE**
>
> Since API version 12, this component is no longer maintained. It is recommended to use the universal attribute [bindSheet](ts-universal-attributes-sheet-transition.md#bindsheet) instead.
>
> This component is supported since API version 7. Newly added content in later versions is marked with a superscript to indicate the version in which it was introduced.

## Child Components

Supported.

>  **NOTE**
>
>  Allowed child component types: built-in and custom components, including rendering control types ([if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md), [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md), and [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)).

## APIs

Panel(show: boolean)

Defines a slidable panel component.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 12. It is recommended to use [bindSheet](./ts-universal-attributes-sheet-transition.md#bindsheet) instead.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| show | boolean | Yes | Whether to show or hide the panel. The value **true** means to show the panel, and **false** means to hide the panel.<br>**NOTE**<br>If this parameter is set to **false**, the panel is hidden without occupying space. When either [Visibility](ts-appendix-enums.md#visibility).None or **show** takes effect, the panel is hidden without occupying space.<br>The **show** attribute has a higher priority than this parameter. When the **show** attribute is set, this parameter may not take effect. |

## Attributes

In addition to the [universal attributes](ts-component-general-attributes.md), the following attributes are supported.

### type

type(value: PanelType)

Sets the type of the slidable panel. The value of the **type** attribute constrains the use of other attributes: when **type** is **Minibar**, **PanelMode.Half** does not take effect; when **type** is **Temporary**, **PanelMode.Mini** does not take effect; when **type** is **CUSTOM**, the size switching effect is not supported and the **customHeight** attribute must be used; when **type** is **Foldable**, all **PanelMode** values are available, and the **fullHeight**, **halfHeight**, and **miniHeight** attributes can be used to set the height of each state.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 12. It is recommended to use **preferType** in [SheetOptions](./ts-universal-attributes-sheet-transition.md#sheetoptions) instead.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                                                        | Mandatory| Description                                                        |
| ------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| value   | [PanelType](#paneltype) | Yes   | Type of the slidable panel.<br>Default value: **PanelType.Foldable** |

### mode

mode(value: PanelMode)

Sets the initial mode of the panel.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 12. Recommended Alternative: **preferType** in [SheetOptions](./ts-universal-attributes-sheet-transition.md#sheetoptions).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                                                        | Mandatory| Description                                                        |
| ------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| value   | [PanelMode](#panelmode) | Yes   | Initial state of the slidable panel.<br>Default value for the Minibar type: **PanelMode.Mini**; default value for other types: **PanelMode.Half**<br>Since API version 10, this attribute supports two-way binding with variables through [$$](../../../ui/state-management/arkts-two-way-sync.md). |

### dragBar

dragBar(value: boolean)

Sets whether to enable a drag bar.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 12. Recommended Alternative: **dragBar** in [SheetOptions](./ts-universal-attributes-sheet-transition.md#sheetoptions).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                                                        | Mandatory| Description                                                        |
| ------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| value   | boolean | Yes   | Whether a control bar exists. The value **true** indicates that the control bar exists, and **false** indicates that it does not.<br>Default value: **true** |

### customHeight<sup>10+</sup>

customHeight(value: Dimension | PanelHeight)

Sets the height in the **PanelType.CUSTOM** state. This attribute only takes effect when [type](#type) is set to **PanelType.CUSTOM**. When **PanelHeight.WRAP_CONTENT** is used, the height adapts to the content; when a **Dimension** value is used, a fixed height is set.

> **NOTE**
>
> This API is supported since API version 10 and deprecated since API version 12. Recommended Alternative: **height** in [SheetOptions](./ts-universal-attributes-sheet-transition.md#sheetoptions).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                                                        | Mandatory| Description                                                        |
| ------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| value   | [Dimension](ts-types.md#dimension10)&nbsp;\|&nbsp;[PanelHeight](#panelheight10) | Yes   | Height in the **PanelType.CUSTOM** state.<br>Default value: **0**<br>**Note:** <br>Percentage is not supported. If a percentage is passed in, it does not take effect. If a negative number is passed in, it does not take effect. |

### fullHeight

fullHeight(value: number | string)

Sets the height in the **PanelMode.Full** state.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 12. Recommended alternative: **height** in [SheetOptions](./ts-universal-attributes-sheet-transition.md#sheetoptions).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                      | Mandatory| Description                                                        |
| ------ | -------------------------- | ---- | ------------------------------------------------------------ |
| value  | number&nbsp;\|&nbsp;string | Yes   | Height in the **PanelMode.Full** state.<br>Default value: the size of the current component's main axis minus an 8 vp blank area<br>Unit: vp<br>**NOTE**<br>Percentage Not Supported. |

### halfHeight

halfHeight(value: number | string)

Sets the height of the panel in **PanelMode.Half** mode.

> **NOTE**
>
> This attribute takes effect only when **type** is **Foldable** or **Temporary**. When **type** is **Minibar**, the **Half** mode does not take effect, and **halfHeight** is invalid.
>
> This API is supported since API version 7 and deprecated since API version 12. Recommended alternative: **height** in [SheetOptions](./ts-universal-attributes-sheet-transition.md#sheetoptions).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                      | Mandatory| Description                                                        |
| ------ | -------------------------- | ---- | ------------------------------------------------------------ |
| value  | number&nbsp;\|&nbsp;string | Yes   | Height in the **PanelMode.Half** state.<br>Default value: half of the size of the current component along the main axis.<br>Unit: vp<br>**Note:** <br>Percentage is not supported. |

### miniHeight

miniHeight(value: number | string)

Sets the height of the panel in the **PanelMode.Mini** mode.

> **NOTE**
>
> This attribute takes effect only when **type** is **Minibar** or **Foldable**. When **type** is **Temporary**, the **Mini** mode does not take effect, and **miniHeight** is invalid.
>
> This API is supported since API version 7 and deprecated since API version 12. Recommended alternative: **height** in [SheetOptions](./ts-universal-attributes-sheet-transition.md#sheetoptions).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                      | Mandatory| Description                                                        |
| ------ | -------------------------- | ---- | ------------------------------------------------------------ |
| value  | number&nbsp;\|&nbsp;string | Yes   | Height of the panel in the **PanelMode.Mini** state.<br>Default value: **48**<br>Unit: vp<br>**Note:** <br>Percentage is not supported. |

### show

show(value: boolean)

Set whether to show the panel.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 12. Recommended alternative: **isShow** in [SheetOptions](./ts-universal-attributes-sheet-transition.md#sheetoptions).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                                                        | Mandatory| Description                                                        |
| ------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| value   | boolean | Yes   | Whether to show the panel. The value **true** means to display the panel, and **false** means not to display the panel. <br>Default value: **true**<br>**Note:** <br>This attribute has a higher priority than the **show** parameter. |

### backgroundMask<sup>9+</sup>

backgroundMask(color: ResourceColor)

Set the background mask of the panel.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12. Recommended alternative: **maskColor** in [SheetOptions](./ts-universal-attributes-sheet-transition.md#sheetoptions).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                                                        | Mandatory| Description                                                        |
| ------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| color   | [ResourceColor](ts-types.md#resourcecolor) | Yes   | Background mask of the panel.<br>Default value: '#08182431' |

### showCloseIcon<sup>10+</sup>

showCloseIcon(value: boolean)

Sets whether to display the close icon.

> **NOTE**
>
> This API is supported since API version 10 and deprecated since API version 12. Recommended alternative: **showClose** in [SheetOptions](./ts-universal-attributes-sheet-transition.md#sheetoptions).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                                                        | Mandatory| Description                                                        |
| ------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| value   | boolean | Yes   | Whether to display the close icon. The value **true** indicates that the icon is displayed, and **false** indicates that it is not displayed.<br>Default value: **false** |

## PanelType

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 12. Recommended alternative: [SheetSize](./ts-universal-attributes-sheet-transition.md#sheetsize).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name | Value | Description |
| -------- | -------- | -------- |
| Minibar | 0 | Provides switching between the minibar and fullscreen-like display. |
| Foldable | 1 | The content is always displayed, with switching among large (fullscreen-like), medium (half-screen-like), and small sizes. |
| Temporary | 2 | The content is displayed temporarily, with switching between large (fullscreen-like) and medium (half-screen-like) sizes. |
| CUSTOM<sup>10+</sup> | 3 | Configures the adaptive content height. Size switching is not supported. |

## PanelMode

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Value| Description|
| -------- | -------- | -------- |
| Mini |0| When the type is **Minibar** or **Foldable**, the panel is in the minimum state. When the type is **Temporary**, this does not take effect. |
| Half | 1 | When the type is **Foldable** or **Temporary**, the panel is in the half-screen-like state. When the type is **Minibar**, this does not take effect. |
| Full |2  | When the type is **Minibar**, **Foldable**, or **Temporary**, the panel is in the full-screen-like state. When the type is **CUSTOM**, this does not take effect. |

## PanelHeight<sup>10+</sup>

> **NOTE**
>
> This API is supported since API version 10 and deprecated since API version 12. Recommended alternative: [SheetSize](./ts-universal-attributes-sheet-transition.md#sheetsize).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name | Value | Description |
| -------- | -------- | -------- |
| WRAP_CONTENT | 'wrapContent' | When the type of [PanelType](#paneltype) is **CUSTOM**, the panel automatically adapts its height to the content. |

## Events

In addition to the [universal events](ts-component-general-events.md), the following events are supported.

### onChange

onChange(event:&nbsp;(width:&nbsp;number,&nbsp;height:&nbsp;number,&nbsp;mode:&nbsp;PanelMode)&nbsp;=&gt;&nbsp;void)

Triggered when the status of the slidable panel changes. Difference from **onHeightChange**: **onChange** is triggered when the panel mode switches, and returns the width, height, and mode information; **onHeightChange** is triggered when the panel height changes, and returns only the height value. Use **onChange** when you need to detect mode switching, and use **onHeightChange** when you only need to detect height changes.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 12. Recommended alternative: **onTypeDidChange** in [SheetOptions](./ts-universal-attributes-sheet-transition.md#sheetoptions).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name   | Type       | Mandatory| Description                                                                                 |
| --------- | ---------  | ---- | ------------------------------------------------------------------------------------ |
| width     | number     | Yes   | Width of the content area, in vp.                                                                     |
| height    | number     | Yes   | Height of the content area, in vp.<br>When the **dragBar** attribute is set to **true**, the height of the panel itself is the sum of the drag bar height and the content area height. |
| mode      | [PanelMode](#panelmode)  | Yes   | State of the panel.                                                                           |

### onHeightChange<sup>9+</sup>

onHeightChange(callback: (value: number) => void)

Triggered when the height of the panel changes.

> **NOTE**
>
> This API is supported since API version 9 and deprecated since API version 12. Recommended alternative: **onHeightDidChange** in [SheetOptions](./ts-universal-attributes-sheet-transition.md#sheetoptions).

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name   | Type                                               | Mandatory| Description      |
| --------- | --------------------------------------------------- | ---- | ---------- |
| value     | number  | Yes   | Height of the content area. The default unit of the return value is px.<br>When the **dragBar** attribute is set to **true**, the height of the Panel itself is the **dragBar** height plus the content area height.<br>For user experience design reasons, the Panel can slide up to **fullHeight** - 8vp at most. |

## Example

```ts
// xxx.ets
@Entry
@Component
struct PanelExample {
  @State show: boolean = false

  build() {
    Column() {
      Text('2021-09-30    Today Calendar: 1.afternoon......Click for details')
        .width('90%')
        .height(50)
        .borderRadius(10)
        .backgroundColor(0xFFFFFF)
        .padding({ left: 20 })
        .onClick(() => {
          this.show = !this.show;
        })
      Panel(this.show) { // Display calendar events.
        Column() {
          Text('Today Calendar')
          Divider()
          Text('1. afternoon 4:00 The project meeting')
        }
      }
      .type(PanelType.Foldable)
      .mode(PanelMode.Half)
      .dragBar(true) // The drag bar is enabled by default.
      .halfHeight(500) // Set the half height to 500. The default value is half of the main axis size of the current component.
      .showCloseIcon(true) // Display the close icon.
      .onChange((width: number, height: number, mode: PanelMode) => {
        console.info(`width:${width},height:${height},mode:${mode}`);
      })
    }.width('100%').height('100%').backgroundColor(0xDCDCDC).padding({ top: 5 })
  }
}
```

![panel](figures/panel.gif)