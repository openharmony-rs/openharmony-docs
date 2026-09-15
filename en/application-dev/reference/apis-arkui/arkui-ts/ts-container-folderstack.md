# FolderStack

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @fenglinbailu; @song-song-song-->
<!--Designer: @fenglinbailu-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=75a7d62c0702c21a06ca0119552a942305a023cc translatedAt=2026-08-21T02:24:09.654Z pushedAt=2026-08-21T07:32:35.990Z -->

**FolderStack** extends the [Stack](ts-container-stack.md) container, adding the <!--RP1-->foldable screen hover<!--RP1End--> capability. By setting child component IDs in the **upperItems** array of the [FolderStackOptions](#folderstackoptions18) configuration, the corresponding child components automatically avoid the fold crease area and move to the upper screen. **FolderStack** is designed for the hover status scenario of dual-fold devices, such as video playback and video conferencing apps, where the video image automatically moves to the upper screen while the control panel remains on the lower screen. This component addresses the adaptation challenges of dual-fold devices, delivering benefits such as improved user experience and simplified layout adaptation for developers.

> **NOTE**
>
> - This component is supported since API version 11. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.
>
> - The hover capability of this component is designed for <!--RP2-->dual-fold<!--RP2End--> devices and takes effect only on dual-fold devices. You can use [FoldStatus](ts-appendix-enums.md#foldstatus11) to determine the fold status of the device.
>
> - When the parent component of this component is an [if/else: conditional rendering](../../../ui/rendering-control/arkts-rendering-control-ifelse.md) node, the foldable screen hover capability becomes invalid.

## Child Components

Multiple child components are supported.

## APIs

FolderStack(options?: FolderStackOptions)

A foldable screen hover layout container that extends [Stack](ts-container-stack.md). It implements the foldable screen hover capability through the **upperItems** configuration. When the device is in hover status, the specified child components automatically move to the upper screen, while other components are stacked on the lower screen.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

**Parameters**

| Name      | Type                                   | Mandatory| Description                                                                |
| ------------ | ------------------------------------------- | ---- |----------------------------------------------------------------------|
| options | [FolderStackOptions](#folderstackoptions18) | No | Configuration options of **FolderStack**, used to set the child components that need to be moved to the upper half screen in hover status. When the foldable screen hover capability is needed, specify child component IDs through the **upperItems** array. If not passed, **FolderStack** is used as a regular **Stack** component without the hover capability enabled, and **upperItems** defaults to an empty array. |

## FolderStackOptions<sup>18+</sup>

Configuration object for the **FolderStack** hover status, which describes the information about child components that need to be moved to the upper screen in hover status.

> **NOTE**
>
> To standardize anonymous object definitions, the element definitions here have been revised in API version 18. While historical version information is preserved for anonymous objects, there may be cases where the outer element's @since version number is higher than inner elements'. This does not affect interface usability.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| upperItems<sup>11+</sup> | Array<string\> | No | Yes | Array of IDs of child components that will be moved to the upper half-screen in hover status.<br>Default value: **[]**<br>When hover is triggered, the child components in the **upperItems** array automatically avoid the foldable screen crease area and move to the upper half-screen, while other components are stacked in the lower half-screen area.<br>**Atomic service API:** This API can be used in atomic services since API version 12. |

## Attributes

> **NOTE**
>
> Setting the **offset** and **margin** attributes may cause the upper and lower screens to obscure the fold crease area. This is not recommended.

In addition to the [universal attributes](ts-component-general-attributes.md), the following attributes are supported.

### alignContent

alignContent(value: Alignment)

Sets the alignment of child components in the container. After this attribute is set, child components are arranged in the container according to the specified alignment. When both this attribute and [align](ts-universal-attributes-location.md#align) are set, whichever is set last takes effect.

>**NOTE**
>
> This API can be called within [attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier) since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

**Parameters**

| Name| Type                                       | Mandatory| Description                                                   |
| ------ | ------------------------------------------- | ---- | ------------------------------------------------------- |
| value  | [Alignment](ts-appendix-enums.md#alignment) | Yes   | Alignment of the child component in the container. The value can be **TopStart**, **Top**, **TopEnd**, **Start**, **Center**, **End**, **BottomStart**, **Bottom**, or **BottomEnd**.<br>Default value: **Alignment.Center**<br>If an illegal value is set, the default value is used. |

### enableAnimation

enableAnimation(value: boolean)

Sets whether to use the default animation effect. After this attribute is set, the default hover animation effect of **FolderStack** is enabled or disabled.

>**NOTE**
>
> This API can be called within [attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier) since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

**Parameters**

| Name| Type                                       | Mandatory| Description                               |
| ------ | ------------------------------------------- | ---- | ----------------------------------- |
| value | boolean | Yes | Whether to use the default animation effect.<br>Default value: **true**, which means the default animation effect is used; **false** means the default animation effect is not used.<br>If an illegal value is set, the default value is used. |

### autoHalfFold

autoHalfFold(value: boolean)

Sets whether to enable auto-rotation for the **FolderStack** component in half-fold status. When the system auto-rotate switch is turned off, this attribute controls whether **FolderStack** performs auto-rotation in half-fold status.<br>Typical usage: When the user has turned off the auto-rotate function in system settings, the app layout orientation can still be automatically adjusted based on the fold status when the foldable device is in half-fold status.

>**NOTE**
>
> This API can be called within [attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier) since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

**Parameters**

| Name| Type   | Mandatory| Description                               |
| ------ | ------- | ---- | ----------------------------------- |
| value | boolean | Yes | Whether to enable auto rotation.<br>Default value: **true**. When set to **true**, **FolderStack** automatically rotates during layout in the half-fold status (see [FoldStatus](ts-appendix-enums.md#foldstatus11)). When set to **false**, FolderStack does not automatically rotate in the half-fold status. This attribute takes effect only when system auto rotation is disabled. When system auto rotation is enabled, this attribute does not take effect, and **FolderStack** follows the system rotation behavior. This parameter takes effect only on dual-fold devices. When the parent component of **FolderStack** is an if/else conditional rendering node, this parameter becomes invalid.<br>Illegal value: processed as the default value. |

## Events

In addition to the [universal events](ts-component-general-events.md), the following events are supported.

### onFolderStateChange

onFolderStateChange(callback: OnFoldStatusChangeCallback)

Triggered when the fold status of the current device changes <!--RP3-->(This callback takes effect only in landscape mode.)<!--RP3End-->.<br>Typical usage: Adjust the app layout based on the fold status, for example, displaying a two-column layout in the expanded state and adjusting the content distribution between the upper and lower screens in the half-fold status.

>**NOTE**
>
> This API can be called within [attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier) since API version 20.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

**Parameters**

| Name    | Type                                           | Mandatory| Description                |
| ---------- | ----------------------------------------------- | ---- | -------------------- |
| callback | [OnFoldStatusChangeCallback](#onfoldstatuschangecallback18) | Yes  | Callback invoked when the fold state of the device changes.|

### onHoverStatusChange<sup>12+</sup>

onHoverStatusChange(handler: OnHoverStatusChangeCallback)

Triggered when the hover status of the current device changes.<br>Typical usage: Adjust the app layout and interaction logic based on the hover status, for example, optimizing the content display on the upper and lower screens in hover mode.

>**NOTE**
>
> This API can be called within [attributeModifier](ts-universal-attributes-attribute-modifier.md#attributemodifier) since API version 20.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

**Parameters**

| Name    | Type                                           | Mandatory| Description                |
| ---------- | ----------------------------------------------- | ---- | -------------------- |
| handler | [OnHoverStatusChangeCallback](#onhoverstatuschangecallback18) | Yes  | Callback invoked when the hover state of the device changes.|

## OnHoverStatusChangeCallback<sup>18+</sup>

type OnHoverStatusChangeCallback = (param: HoverEventParam) => void

Defines the current allback invoked when the hover state of the device changes.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

**Parameters**

| Name    | Type                                           | Mandatory| Description                |
| ---------- | ----------------------------------------------- | ---- | -------------------- |
| param | [HoverEventParam](#hovereventparam12) | Yes  | Parameters related to the hover state of the device, including the fold state, hover state, application orientation, and window mode enumeration of the device.|

## OnFoldStatusChangeCallback<sup>18+</sup>

type OnFoldStatusChangeCallback = (event: OnFoldStatusChangeInfo) => void

Triggered when the fold status changes<!--RP4-->, which takes effect only in landscape mode<!--RP4End-->.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

**Parameters**

| Name    | Type                                           | Mandatory| Description                |
| ---------- | ----------------------------------------------- | ---- | -------------------- |
| event | [OnFoldStatusChangeInfo](#onfoldstatuschangeinfo18) | Yes | Information about the fold status change. This takes effect only in landscape mode. |

## OnFoldStatusChangeInfo<sup>18+</sup>

Defines the information about the fold status change, which takes effect only in landscape mode.

> **NOTE**
>
> To standardize anonymous object definitions, the element definitions here have been revised in API version 18. While historical version information is preserved for anonymous objects, there may be cases where the outer element's @since version number is higher than inner elements'. This does not affect interface usability.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| foldStatus<sup>11+</sup> | [FoldStatus](ts-appendix-enums.md#foldstatus11) | No | No | Fold status of the current device.<br>**Atomic service API:** This API can be used in atomic services since API version 12. |

## HoverEventParam<sup>12+</sup>

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| foldStatus       | [FoldStatus](ts-appendix-enums.md#foldstatus11)             | No| No  | Current fold state of the device.|
| isHoverMode      | boolean                                                     | No| No  | Whether hover mode is enabled. **true**: Hover mode is enabled. **false**: Hover mode is disabled.|
| appRotation      | [AppRotation](ts-appendix-enums.md#approtation12)           | No  | No   | Rotation angle of the current app orientation.    |
| windowStatusType | [WindowStatusType](#windowstatustype12) | No| No  | Window mode.   |

## WindowStatusType<sup>12+</sup>

type WindowStatusType = import('../api/@ohos.window').default.WindowStatusType

Enumerates the window modes.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Device behavior differences**: On wearables, calling this API results in a runtime exception indicating that the API is undefined. On other devices, the API works correctly.

| Type       | Description                |
| ---------- | ---------------------|
| import('../api/@ohos.window').default.[WindowStatusType](../arkts-apis-window-e.md#windowstatustype11)  | Window mode enum. |

## Example

### Example 1: Implementing the Foldable Device Hover Capability with FolderStack

This example implements the foldable device hover capability.

```ts
@Entry
@Component
struct Index {
  build() {
    Column() {
      // Set upperItems to IDs of the child components to be moved to the upper half screen in the hover state. Other components are stacked in the lower half screen.
      FolderStack({ upperItems: ['upperitemsId'] }) {
        // This column is automatically moved up to the upper half screen.
        Column() {
          Text('video zone').height('100%').width('100%').textAlign(TextAlign.Center).fontSize(25)
        }.backgroundColor('rgb(0, 74, 175)').width('100%').height('100%').id('upperitemsId')

        // The following two columns are stacked in the lower half screen.
        Column() {
          Text('video title')
            .width('100%')
            .height(50)
            .textAlign(TextAlign.Center)
            .backgroundColor('rgb(213, 213, 213)')
            .fontSize(25)
        }.width('100%').height('100%').justifyContent(FlexAlign.Start)

        Column() {
          Text('video bar ')
            .width('100%')
            .height(50)
            .textAlign(TextAlign.Center)
            .backgroundColor('rgb(213, 213, 213)')
            .fontSize(25)
        }.width('100%').height('100%').justifyContent(FlexAlign.End)
      }
      .backgroundColor('rgb(39, 135, 217)')
      // Set whether to enable animation.
      .enableAnimation(true)
      // Set whether to enable auto-rotate.
      .autoHalfFold(true)
      // Called when the folding status changes.
      .onFolderStateChange((msg) => {
        if (msg.foldStatus === FoldStatus.FOLD_STATUS_EXPANDED) {
          console.info('The device is currently in the expanded state')
        } else if (msg.foldStatus === FoldStatus.FOLD_STATUS_HALF_FOLDED) {
          console.info('The device is currently in the half folded state')
        } else {
          // ...
        }
      })
      // The hoverStatusChange callback is invoked when the hover status changes.
      .onHoverStatusChange((msg) => {
        console.info('this foldStatus:' + msg.foldStatus);
        console.info('this isHoverMode:' + msg.isHoverMode);
        console.info('this appRotation:' + msg.appRotation);
        console.info('this windowStatusType:' + msg.windowStatusType);
      })
      // If the folderStack component does not occupy the full screen, it is used as a common stack.
      .alignContent(Alignment.Bottom)
      .height('100%')
      .width('100%')

    }
    .height('100%')
    .width('100%')
    .borderWidth(1)
    .borderColor('rgb(213, 213, 213)')
    .backgroundColor('rgb(0, 74, 175)')
    .expandSafeArea([SafeAreaType.SYSTEM], [SafeAreaEdge.BOTTOM])
  }
}
```

**Figure 1** Expanded state in landscape mode<br>
![FolderStack01.png](figures/FolderStack01.png)<br>
**Figure 2** Half-fold state in landscape mode<br>
![FolderStack02.png](figures/FolderStack02.png)

### Example 2: Dynamically Setting Attributes and Methods of the FolderStack Component Using attributeModifier

This example demonstrates how to dynamically set the **onFolderStateChange** and **onHoverStatusChange** methods of the **FolderStack** component using **attributeModifier**.

```ts
// xxx.ets
class MyFolderStackModifier implements AttributeModifier<FolderStackAttribute> {
  applyNormalAttribute(instance: FolderStackAttribute): void {
    // Called when the folding status changes.
    instance.onFolderStateChange((msg) => {
      if (msg.foldStatus === FoldStatus.FOLD_STATUS_EXPANDED) {
        console.info('The device is currently in the expanded state')
      } else if (msg.foldStatus === FoldStatus.FOLD_STATUS_HALF_FOLDED) {
        console.info('The device is currently in the half folded state')
      } else if (msg.foldStatus === FoldStatus.FOLD_STATUS_FOLDED) {
        console.info('The device is currently in the folded state')
      } else {
        // ...
      }
    })
    // The hoverStatusChange callback is invoked when the hover status changes.
    instance.onHoverStatusChange((msg) => {
      console.info('this foldStatus:' + msg.foldStatus);
      console.info('this isHoverMode:' + msg.isHoverMode);
      console.info('this appRotation:' + msg.appRotation);
      console.info('this windowStatusType:' + msg.windowStatusType);
    })
  }
}

@Entry
@Component
struct attributeDemo {
  @State modifier: MyFolderStackModifier = new MyFolderStackModifier()

  build() {
    Column() {
      // Set upperItems to IDs of the child components to be moved to the upper half screen in the hover state. Other components are stacked in the lower half screen.
      FolderStack({ upperItems: ['upperitemsId'] }) {
        // This column is automatically moved up to the upper half screen.
        Column() {
          Text('video zone').height('100%').width('100%').textAlign(TextAlign.Center).fontSize(25)
        }.backgroundColor('rgb(0, 74, 175)').width('100%').height('100%').id('upperitemsId')

        // The following two columns are stacked in the lower half screen.
        Column() {
          Text('video title')
            .width('100%')
            .height(50)
            .textAlign(TextAlign.Center)
            .backgroundColor('rgb(213, 213, 213)')
            .fontSize(25)
        }.width('100%').height('100%').justifyContent(FlexAlign.Start)

        Column() {
          Text('video bar ')
            .width('100%')
            .height(50)
            .textAlign(TextAlign.Center)
            .backgroundColor('rgb(213, 213, 213)')
            .fontSize(25)
        }.width('100%').height('100%').justifyContent(FlexAlign.End)
      }
      .backgroundColor('rgb(39, 135, 217)')
      // Set whether to enable animation.
      .enableAnimation(true)
      // Set whether to enable auto-rotate.
      .autoHalfFold(true)
      .attributeModifier(this.modifier)
      // If the <folderStack> component does not occupy the full screen, it is used as a common stack.
      .alignContent(Alignment.Bottom)
      .height('100%')
      .width('100%')
    }
    .height('100%')
    .width('100%')
    .borderWidth(1)
    .borderColor('rgb(213, 213, 213)')
    .backgroundColor('rgb(0, 74, 175)')
    .expandSafeArea([SafeAreaType.SYSTEM], [SafeAreaEdge.BOTTOM])
  }
}
```

**Figure 1** Expanded state in landscape mode<br>
Expected log:<br>
The device is currently in the expanded state<br>
this foldStatus:1<br>
this isHoverMode:0<br>
this appRotation:3<br>
this windowStatusType:1<br>
![FolderStack03](figures/FolderStack03.png)<br>
**Figure 2** Half-fold state in landscape mode<br>
Expected log:<br>
The device is currently in the half folded state<br>
this foldStatus:3<br>
this isHoverMode:1<br>
this appRotation:3<br>
this windowStatusType:1<br>
![FolderStack04](figures/FolderStack04.png)