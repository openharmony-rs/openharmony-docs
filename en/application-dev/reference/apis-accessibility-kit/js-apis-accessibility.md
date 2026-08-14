# @ohos.accessibility (Accessibility)

<!--Kit: Accessibility Kit-->
<!--Subsystem: BarrierFree-->
<!--Owner: @qiiiiiiian-->
<!--Designer: @z7o-->
<!--Tester: @A_qqq-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=16a51cad246d07c6caba5c76444e9d073c5d43d6 translatedAt=2026-08-03T09:47:01.480Z pushedAt=2026-08-07T02:18:42.537Z -->

This module provides accessibility features, including obtaining the accessibility application list, obtaining the accessibility application enabling state, obtaining the captions configuration, sending accessibility events, and listening for accessibility application state changes.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { accessibility } from '@kit.AccessibilityKit';
```

## AbilityState

type AbilityState = 'enable' | 'disable' | 'install'

Enumerates the states of an accessibility application.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

| Type     | Description      |
| ------- | -------- |
| 'enable'  | The accessibility application is enabled.|
| 'disable'  | The accessibility app is disabled. |
| 'install'  | The accessibility app is installed. |

## AbilityType

type AbilityType = 'audible' | 'generic' | 'haptic' | 'spoken' | 'visual' | 'all'

Enumerates the types of accessibility applications.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

| Type              | Description       |
| ---------------- | --------- |
| 'audible'          | The accessibility application provides audible feedback.|
| 'generic'          | The accessibility application provides generic feedback.|
| 'haptic'           | The accessibility application provides haptic feedback.|
| 'spoken'           | The accessibility application provides spoken feedback.|
| 'visual'           | The accessibility application provides visual feedback.|
| 'all'<sup>9+</sup> | All the preceding types.|

## AccessibilityAbilityInfo

Provides information about an accessibility application.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

### Properties

| Name                            | Type                                      | Read-Only  | Optional  | Description              |
| ------------------------------ | ---------------------------------------- | ---- | ---- | ---------------- |
| id                             | string                                   | Yes   | No   | Ability ID.|
| name                           | string                                   | Yes    | No    | Ability name.       |
| bundleName                     | string                                   | Yes   | No   | Bundle name.       |
| targetBundleNames<sup>9+</sup> | Array&lt;string&gt;                      | Yes   | No   | Name of the target bundle.  |
| abilityTypes                   | Array&lt;[AbilityType](#abilitytype)&gt; | Yes   | No   | Accessibility application type.         |
| capabilities                   | Array&lt;[Capability](#capability)&gt;   | Yes   | No   | Capabilities list of the accessibility application.       |
| description                    | string                                   | Yes   | No   | Description of the accessibility application.         |
| eventTypes                     | Array&lt;[EventType](#eventtype)&gt;     | Yes   | No   | List of events that the accessibility application focuses on. |
| needHide<sup>12+</sup>                     | boolean     | Yes   | No   | Whether the auxiliary application is hidden in the list of installed extended services. The value **true** means the auxiliary application is hidden, and the value **false** means the opposite. |
| label<sup>12+</sup>                     | string     | Yes    | No    | Name of the accessibility app in the extended service list.  |

## Action

type Action = 'accessibilityFocus' | 'clearAccessibilityFocus' | 'focus' | 'clearFocus' | 'clearSelection' |
  'click' | 'longClick' | 'cut' | 'copy' | 'paste' | 'select' | 'setText' | 'delete' |
  'scrollForward' | 'scrollBackward' | 'setSelection' | 'setCursorPosition' | 'home' |
  'back' | 'recentTask' | 'notificationCenter' | 'controlCenter' | 'common' | 'injectAction'

Target actions supported by the app. Target actions that require configuration parameters are indicated in the description column of each action in the table below.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

| Type                      | Description                 |
| ----------------------- |--------------------|
| 'click'                   | Click.            |
| 'longClick'               | Long press.            |
| 'scrollForward'           | Scroll forward. The parameter **scrollType** must be configured, with the value **'fullScreen'** or **'halfScreen'**. |
| 'scrollBackward'          | Scroll backward. The parameter **scrollType** must be configured, with the value **'fullScreen'** or **'halfScreen'**. |
| 'focus'                   | Obtain focus. |
| 'clearFocus'              | Clear focus. |
| 'clearSelection'          | Clear selection. This feature is not supported in the current version. |
| 'accessibilityFocus'      | Obtain accessibility focus. The parameter **accessibilityFocusScene** must be configured, with the value being the type of the accessibility focus scene.       |
| 'clearAccessibilityFocus'      | Clear accessibility focus.       |
| 'cut'                     | Cut.   |
| 'copy'                    | Copy.   |
| 'paste'                   | Paste.   |
| 'select'                  | Select.   |
| 'setText'                 | Set text. The parameter **setText** must be configured, with the value being the text content to set. |
| 'delete'                  | Delete. This feature is not supported in the current version.   |
| 'setSelection'            | Set the text selection range. The parameters **selectTextBegin**, **selectTextEnd**, and **selectTextInForWard** must be configured, with the values being the start coordinate, end coordinate, and whether to select forward.   |
| 'common'<sup>12+</sup>            | No specific action, used for scenarios such as active focus and active announcement.   |
| 'home'<sup>12+</sup>                | Return to the home screen.   |
| 'back'<sup>12+</sup>                | Return to the previous level.   |
| 'recentTask'<sup>12+</sup>          | Open recent tasks.   |
| 'notificationCenter'<sup>12+</sup>      | Open the notification panel.   |
| 'controlCenter'<sup>12+</sup>       | Open the control center.   |
| 'setCursorPosition'<sup>12+</sup>     | Set the cursor position. The parameter **offset** must be configured, with the value being the character offset of the cursor.   |
| 'injectAction'    | Inject an action. The parameter **injectActionType** must be configured, with the value being the type of the injected action.<br>**Since:** 26.0.0<br>**Model restriction:** This API can be used only in the stage model.|
| 'executeCustomAction'     | Execute a custom action. The parameter **customAction** must be configured, with the value being the name of the custom action.<br>**Since:** 26.0.0   |

## Capability

type Capability = 'retrieve' | 'touchGuide' | 'keyEventObserver' | 'zoom' | 'gesture'

Enumerates the capabilities of an accessibility application.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

| Type              | Description                   |
| ---------------- |-----------------------|
| 'retrieve'         | Capability to retrieve the window content.         |
| 'touchGuide' | Capability of the touch guide mode. |
| 'keyEventObserver' | Capability to filter key events.         |
| 'zoom'             | Capability to control the display zoom level. Not supported currently.|
| 'gesture'          | Capability to perform gesture actions.         |

## CaptionsFontEdgeType<sup>8+</sup>

type CaptionsFontEdgeType = 'none' | 'raised' | 'depressed' | 'uniform' | 'dropShadow'

Enumerates the font edge types of captions.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Hearing

| Type        | Description   |
| ---------- | ----- |
| 'none'       | No effect. |
| 'raised'     | Raised effect.|
| 'depressed'  | Depressed effect.|
| 'uniform'    | Uniform effect.|
| 'dropShadow' | Drop shadow effect.|

## CaptionsFontFamily<sup>8+</sup>

type CaptionsFontFamily = 'default' | 'monospacedSerif' | 'serif' | 'monospacedSansSerif' |
  'sansSerif' | 'casual' | 'cursive' | 'smallCapitals'

Enumerates the font families of captions.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Hearing

| Type                 | Description               |
| ------------------- | ----------------- |
| 'default'             | Default font family.            |
| 'monospacedSerif'         | Represents a monospaced Serif font.      |
| 'serif'               | Represents a Serif font.         |
| 'monospacedSansSerif'        | Represents a monospaced Sans Serif font. |
| 'sansSerif'           | Represents a Sans Serif font.    |
| 'casual'              | Casual fonts.           |
| 'cursive'             | Cursive fonts.            |
| 'smallCapitals'       | Small caps fonts.        |

## CaptionsStyle<sup>8+</sup>

Describes the style of captions.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Hearing

| Name             | Type                                   | Read-Only  | Optional  | Description         |
| --------------- | ---------------------------------------- | ---- | ---- | ----------- |
| fontFamily      | [CaptionsFontFamily](#captionsfontfamily8) | No   | No   | Font family of captions.    |
| fontScale       | number                                   | No   | No   | Font scale factor of captions, in percentage. The value ranges from 1 to 200.|
| fontColor       | number \| string                         | No    | No    | Describes the caption font color.<br>number: HEX format color, supporting RGB or ARGB.<br>string: supports '#rrggbb', '#rrggbbaa', '#rgb', and '#rgba' formats.<br>Example: opaque red, number: 0xffff0000, string: '#ff0000', '#ff0000ff', '#f00', '#f00f'. |
| fontEdgeType    | [CaptionsFontEdgeType](#captionsfontedgetype8) | No   | No   | Font edge type of captions.  |
| backgroundColor | number \| string                         | No    | No    | Describes the caption background color.<br>number: HEX format color, supporting RGB or ARGB.<br>string: supports '#rrggbb', '#rrggbbaa', '#rgb', and '#rgba' formats.<br>Example: opaque red, number: 0xffff0000, string: '#ff0000', '#ff0000ff', '#f00', '#f00f'.   |
| windowColor     | number \| string                         | No    | No    | Describes the caption window color.<br>number: HEX format color, supporting RGB or ARGB.<br>string: supports '#rrggbb', '#rrggbbaa', '#rgb', and '#rgba' formats.<br>Example: opaque red, number: 0xffff0000, string: '#ff0000', '#ff0000ff', '#f00', '#f00f'.   |

## CaptionsManager<sup>8+</sup>

Manages captions configuration. Before calling any method of **CaptionsManager**, call [accessibility.getCaptionsManager()](#accessibilitygetcaptionsmanagerdeprecated) to obtain a **CaptionsManager** instance.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Hearing

### Properties

| Name     | Type                              | Read-Only  | Optional  | Description         |
| ------- | -------------------------------- | ---- | ---- | ----------- |
| enabled | boolean                          | No   | No   | Whether to enable captions configuration. The value **true** indicates that the caption configuration is enabled, and **false** indicates the opposite.|
| style   | [CaptionsStyle](#captionsstyle8) | No   | No   | Style of captions.    |

### on('enableChange')<sup>(deprecated)</sup>

on(type: 'enableChange', callback: Callback&lt;boolean&gt;): void

Subscribes to the state changes of captions configuration. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> - The callback parameter for registering a listener must use a named function instead of an anonymous function. Otherwise, a new underlying object is created each time the function is called, causing memory leakage.
> - After calling this method, ensure that [off('enableChange')](#offenablechangedeprecated) is used to unsubscribe before the component instance is destroyed (for example, in the **aboutToDisappear** lifecycle callback). Otherwise, a crash may occur.
> - This API is supported since API version 8 and deprecated since API version 12.

**System capability:** SystemCapability.BarrierFree.Accessibility.Hearing

**Parameters**

| Name     | Type                     | Mandatory  | Description                                     |
| -------- | ----------------------- | ---- | --------------------------------------- |
| type     | string                  | Yes   | Event type, which is set to **'enableChange'** in this API.|
| callback | Callback&lt;boolean&gt; | Yes   | Callback used to return the result. When the enabled state changes, the state is notified through this callback. The value **true** indicates that the caption configuration is enabled, and **false** indicates that the caption configuration is disabled.              |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 401  |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: boolean) => void = this.eventCallback;
  eventCallback(data: boolean): void {
    console.info(`subscribe caption manager enable state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    let captionsManager = accessibility.getCaptionsManager();
    captionsManager.on('enableChange', this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

### on('styleChange')<sup>(deprecated)</sup>

on(type: 'styleChange', callback: Callback&lt;CaptionsStyle&gt;): void

Subscribes to captions style changes. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> - The callback parameter for registering a listener must use a named function instead of an anonymous function. Otherwise, a new underlying object is created each time the function is called, causing memory leakage.
> - After calling this method, ensure that [off('styleChange')](#offstylechangedeprecated) is used to unsubscribe before the component instance is destroyed (for example, in the **aboutToDisappear** lifecycle callback). Otherwise, a crash may occur.
> - This API is supported since API version 8 and deprecated since API version 12.

**System capability:** SystemCapability.BarrierFree.Accessibility.Hearing

**Parameters**

| Name     | Type                                      | Mandatory  | Description                                |
| -------- | ---------------------------------------- | ---- | ---------------------------------- |
| type     | string                                   | Yes   | Event type, which is set to **'styleChange'** in this API.|
| callback | Callback&lt;[CaptionsStyle](#captionsstyle8)&gt; | Yes   | Callback invoked when the style of captions changes.           |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 401  |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: accessibility.CaptionsStyle) => void = this.eventCallback;
  eventCallback(data: accessibility.CaptionsStyle): void {
    console.info(`subscribe caption manager style state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    let captionsManager = accessibility.getCaptionsManager();
    captionsManager.on('styleChange', this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

### off('enableChange')<sup>(deprecated)</sup>

off(type: 'enableChange', callback?: Callback&lt;boolean&gt;): void

Unsubscribes from the state changes of captions configuration. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 12.

**System capability:** SystemCapability.BarrierFree.Accessibility.Hearing

**Parameters**

| Name  | Type                   | Mandatory| Description                                                        |
| -------- | ----------------------- | ---- | ------------------------------------------------------------ |
| type     | string                  | Yes  | Event type, which is set to **'enableChange'** in this API.|
| callback | Callback&lt;boolean&gt; | No  | Callback used to unregister. It must be consistent with the callback used in [on('enableChange')](#onenablechangedeprecated). If this parameter is not specified, listening will be disabled for all callbacks corresponding to the specified type.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 401  |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: boolean) => void = this.eventCallback;
  eventCallback(data: boolean): void {
    console.info(`subscribe caption manager enable state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    let captionsManager = accessibility.getCaptionsManager();
    captionsManager.on('enableChange', this.callback);
  }

  aboutToDisappear(): void {
    let captionsManager = accessibility.getCaptionsManager();
    captionsManager.off('enableChange', this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

### off('styleChange')<sup>(deprecated)</sup>

off(type: 'styleChange', callback?: Callback&lt;CaptionsStyle&gt;): void

Unsubscribes from the captions style changes. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 12.

**System capability:** SystemCapability.BarrierFree.Accessibility.Hearing

**Parameters**

| Name  | Type                                            | Mandatory| Description                                                        |
| -------- | ------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                           | Yes  | Event type, which is set to **'styleChange'** in this API. |
| callback | Callback&lt;[CaptionsStyle](#captionsstyle8)&gt; | No  | Callback used to unregister. It must be consistent with the callback used in [on('styleChange')](#onstylechangedeprecated). If this parameter is not specified, listening will be disabled for all callbacks corresponding to the specified type.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 401  |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: accessibility.CaptionsStyle) => void = this.eventCallback;
  eventCallback(data: accessibility.CaptionsStyle): void {
    console.info(`subscribe caption manager style state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    let captionsManager = accessibility.getCaptionsManager();
    captionsManager.on('styleChange', this.callback);
  }

  aboutToDisappear(): void {
    let captionsManager = accessibility.getCaptionsManager();
    captionsManager.off('styleChange', this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## EventInfo

Defines the accessibility event information, which describes UI changes or interaction events. It is used as a parameter of [sendAccessibilityEvent](#accessibilitysendaccessibilityevent9) to define the event type and trigger action. The sent accessibility event will be distributed by the system to registered accessibility applications that match the event type for response. For details, see [sendAccessibilityEvent](#accessibilitysendaccessibilityevent9).

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

### Properties

| Name            | Type                                  | Read-Only| Optional| Description           |
| ---------------- | ------------------------------------- |----- |------|-----------------------|
| type             | [EventType](#eventtype)               | No  | No  | Accessibility event type (mandatory).        |
| windowUpdateType | [WindowUpdateType](#windowupdatetype) | No  | Yes  | Window update type.              |
| bundleName       | string                                | No   | No   | Bundle name of the target app. This parameter is mandatory.           |
| componentType    | string                                | No  | Yes  | It should correspond to the event source component type, and the default value is empty.<br>Example:<br>- Button type - > 'Button'<br>- Image type - > 'Image'  |
| pageId           | number                                | No  | Yes  | ID of the page where the event occurs. The default value is **0**.           |
| description      | string                                | No   | Yes   | Event description, which is customized by the developer based on service requirements. There is no special restriction. The default value is empty.        |
| triggerAction    | [Action](#action)                     | No  | No  | Action that triggers the event (mandatory).   |
| textMoveUnit     | [TextMoveUnit](#textmoveunit)         | No  | Yes  | Text moving granularity. The default value is char.     |
| contents         | Array&lt;string&gt;                   | No  | Yes  | Content list, which is set according to the actual scenario with no special restrictions. The default value is empty.                |
| lastContent      | string                                | No  | Yes  | Latest content, which is set according to the actual scenario with no special restrictions. The default value is empty.                |
| beginIndex       | number                                | No  | Yes  | Start index. The default value is **0**.|
| currentIndex     | number                                | No  | Yes  | Current index. The default value is **0**.     |
| endIndex         | number                                | No  | Yes  | End index. The default value is **0**.|
| itemCount        | number                                | No  | Yes  | Total number of items. The default value is **0**.       |
| elementId<sup>12+</sup>        | number                  | No  | Yes  | Element ID of the component. The default value is **0**.       |
| textAnnouncedForAccessibility<sup>12+</sup>     | string     | No  | Yes  | Content for auto-broadcasting. When the application needs to proactively broadcast, set the broadcast content according to the actual scenario with no special restrictions, and the default value is empty.|
| textResourceAnnouncedForAccessibility<sup>18+</sup>      | Resource   | No   | Yes   | Content for proactive announcement, which supports the Resource type. The Resource can only reference string resources (for example, $r('app.string.xxx')).  |
| customId<sup>12+</sup>        | string                                | No   | Yes   | Component ID for proactive focus. Set this parameter based on the actual scenario when the app needs to proactively focus. The default value is empty.        |

### constructor

constructor(jsonObject: Object)

Constructor, which is used to construct an EventInfo instance using a JSON object.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name       | Type    | Mandatory  | Description                  |
| ---------- | ------ | ---- | -------------------- |
| jsonObject | Object | Yes | JSON object containing three fields: type, bundleName, and triggerAction. For details, see the example. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

let eventInfo = new accessibility.EventInfo({
  type: 'click',
  bundleName: 'com.example.MyApplication',
  triggerAction: 'click',
});
```

### constructor<sup>11+</sup>

constructor(type: EventType, bundleName: string, triggerAction: Action)

Constructor, which is used to construct an EventInfo instance using independent parameters.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name | Type               | Mandatory| Description           |
|------|-------------------|---|---------------|
| type | [EventType](#eventtype)          | Yes| Accessibility event types.     |
| bundleName | string | Yes | Bundle name of the target app.        |
| triggerAction | [Action](#action) | Yes | Action that triggers the event. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

// The parameters are, in order: type, bundleName, triggerAction.
let eventInfo = new accessibility.EventInfo('click', 'com.example.MyApplication', 'click');
```

## EventType

type EventType = 'accessibilityFocus' | 'accessibilityFocusClear' |
'click' | 'longClick' | 'focus' | 'select' | 'hoverEnter' | 'hoverExit' |
'textUpdate' | 'textSelectionUpdate' | 'scroll' | 'requestFocusForAccessibility' |
'announceForAccessibility' | 'requestFocusForAccessibilityNotInterrupt' |
'announceForAccessibilityNotInterrupt' | 'scrolling' | 'pageActive' | 'notificationUpdate'

Accessibility event types.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

| Type                      | Description                     |
| ----------------------- |------------------------|
| 'accessibilityFocus'      | Event indicating that the accessibility focus is obtained.          |
| 'accessibilityFocusClear' | Event indicating that the accessibility focus is cleared.          |
| 'click'                   | Event indicating that a component is clicked.             |
| 'longClick'               | Event indicating that a component is long-pressed.             |
| 'select'                  | Event indicating that a component is selected.    |
| 'hoverEnter'              | Event indicating that the pointer hovers over a component.  |
| 'hoverExit'               | Event indicating that the pointer leaves a component.  |
| 'focus'                   | Event indicating that a component obtains focus. This feature is not supported in the current version.  |
| 'textUpdate'              | Event indicating that the component text has changed. |
| 'textSelectionUpdate'     | Event indicating that the selected text has changed. This feature is not supported in the current version. |
| 'scroll'                  | Event indicating a scroll view event.    |
| 'requestFocusForAccessibility'<sup>12+</sup>     | Event indicating active focus. |
| 'announceForAccessibility'<sup>12+</sup>         | Event indicating active announcement. |
| 'requestFocusForAccessibilityNotInterrupt'<sup>18+</sup> | Event indicating active focus without interruption.|
| 'announceForAccessibilityNotInterrupt'<sup>18+</sup>  | Event indicating active announcement without interruption.|
| 'scrolling'<sup>18+</sup>   | Event indicating that an item in the scroll view is scrolled off the screen.|
| 'pageActive'<sup>23+</sup> | Event indicating a page change. The value is fixed as the string **'pageActive'**. |
| 'notificationUpdate' | Event indicating a notification change. The value is fixed as the string **'notificationUpdate'**.<br>**Since:** 26.0.0 |
| 'focusInvisible' | Event indicating that the focus becomes invisible. The value is fixed as the string **'focusInvisible'**.<br>**Since:** 26.0.0 |

## TextMoveUnit

type TextMoveUnit = 'char' | 'word' | 'line' | 'page' | 'paragraph'

Enumerates the movement units for traversing the node text.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

| Type       | Description             |
| --------- | --------------- |
| 'char'      | The movement unit for traversing the node text is by character.|
| 'word'      | The movement unit for traversing the node text is by word. |
| 'line'      | The movement unit for traversing the node text is by line. |
| 'page'      | The movement unit for traversing the node text is by page. |
| 'paragraph' | The movement unit for traversing the node text is by paragraph.|

## WindowUpdateType

type WindowUpdateType = 'add' | 'remove' | 'bounds' | 'active' | 'focus'

Window update type.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

| Type    | Description                |
| ------ | ------------------ |
| 'add'    | Window adding.      |
| 'remove' | Window deletion.   |
| 'bounds' | Window boundary change.   |
| 'active' | Window activity change.|
| 'focus'  | Window focus change.  |

## accessibility.getAbilityLists<sup>(deprecated)</sup>

getAbilityLists(abilityType: AbilityType, stateType: AbilityState): Promise&lt;Array&lt;AccessibilityAbilityInfo&gt;&gt;

Obtains the accessibility application list. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [accessibility.getAccessibilityExtensionList](#accessibilitygetaccessibilityextensionlist9) instead.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name        | Type                           | Mandatory  | Description      |
| ----------- | ----------------------------- | ---- | -------- |
| abilityType | [AbilityType](#abilitytype)   | Yes   | Accessibility application type.|
| stateType   | [AbilityState](#abilitystate) | Yes   | Accessibility application status.|

**Return value**

| Type                                      | Description                   |
| ---------------------------------------- | --------------------- |
| Promise&lt;Array&lt;[AccessibilityAbilityInfo](#accessibilityabilityinfo)&gt;&gt; | Promise used to return the accessibility application list.|

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let abilityType: accessibility.AbilityType = 'spoken';
let abilityState: accessibility.AbilityState = 'enable';

accessibility.getAbilityLists(abilityType, abilityState).then((data: accessibility.AccessibilityAbilityInfo[]) => {
  console.info(`succeeded in getting accessibility extension list, ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get accessibility extension list. Code: ${err.code}, message: ${err.message}`);
});
```

## accessibility.getAbilityLists<sup>(deprecated)</sup>

getAbilityLists(abilityType: AbilityType, stateType: AbilityState,callback: AsyncCallback&lt;Array&lt;AccessibilityAbilityInfo&gt;&gt;): void

Obtains the accessibility application list. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [accessibility.getAccessibilityExtensionList](#accessibilitygetaccessibilityextensionlist9-1) instead.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name        | Type                                      | Mandatory  | Description              |
| ----------- | ---------------------------------------- | ---- | ---------------- |
| abilityType | [AbilityType](#abilitytype)              | Yes   | Accessibility application type.        |
| stateType   | [AbilityState](#abilitystate)            | Yes   | Accessibility application status.        |
| callback    | AsyncCallback&lt;Array&lt;[AccessibilityAbilityInfo](#accessibilityabilityinfo)&gt;&gt; | Yes    | Callback used to return the result. If the list of accessibility applications is obtained successfully, **err** is **undefined** and **data** is the list of accessibility application information; otherwise, **err** is an error object. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let abilityType: accessibility.AbilityType = 'spoken';
let abilityState: accessibility.AbilityState = 'enable';

accessibility.getAbilityLists(abilityType, abilityState, (err: BusinessError, data: accessibility.AccessibilityAbilityInfo[]) => {
  if (err) {
    console.error(`Failed to get accessibility extension list. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`succeeded in getting accessibility extension list, ${JSON.stringify(data)}`);
});
```

## accessibility.getAccessibilityExtensionList<sup>9+</sup>

getAccessibilityExtensionList(abilityType: AbilityType, stateType: AbilityState): Promise&lt;Array&lt;AccessibilityAbilityInfo&gt;&gt;

Obtains the accessibility application list. This API uses a promise to return the result.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name        | Type                           | Mandatory  | Description      |
| ----------- | ----------------------------- | ---- | -------- |
| abilityType | [AbilityType](#abilitytype)   | Yes   | Accessibility application type.|
| stateType   | [AbilityState](#abilitystate) | Yes   | Accessibility application status.|

**Return value**

| Type                                      | Description                   |
| ---------------------------------------- | --------------------- |
| Promise&lt;Array&lt;[AccessibilityAbilityInfo](#accessibilityabilityinfo)&gt;&gt; | Promise used to return the accessibility application list.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 401  |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Parameter example**

| Accessibility Application Type/State     | enable       | disable |install|
| ------- | -------- |----|----|
| **audible**  | Queries enabled accessibility applications with audible feedback.|Queries disabled accessibility applications with audible feedback.|Queries installed accessibility applications with audible feedback.|
|**generic**| Queries enabled accessibility applications with generic feedback.|Queries disabled accessibility applications with generic feedback.|Queries installed accessibility applications with generic feedback.|
|**haptic**| Queries enabled accessibility applications with haptic feedback.|Queries disabled accessibility applications with haptic feedback.|Queries installed accessibility applications with haptic feedback.|
|**spoken**| Queries enabled accessibility applications with spoken feedback.|Queries disabled accessibility applications with spoken feedback.|Queries installed accessibility applications with spoken feedback.|
|**visual**| Queries enabled accessibility applications with visual feedback.|Queries disabled accessibility applications with visual feedback.|Queries installed accessibility applications with visual feedback.|
|**all**| Queries all enabled accessibility applications.|Queries all disabled accessibility applications.|Queries all installed accessibility applications.|

**Example**

- Query all installed accessibility applications.

  ```ts
  import { accessibility } from '@kit.AccessibilityKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  let abilityType: accessibility.AbilityType = 'all'; // The accessibility app type is all types.
  let abilityState: accessibility.AbilityState = 'install'; // The accessibility app state is installed.

  accessibility.getAccessibilityExtensionList(abilityType, abilityState).then((data: accessibility.AccessibilityAbilityInfo[]) => {
    console.info(`succeeded in getting accessibility extension list, ${JSON.stringify(data)}`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to get accessibility extension list. Code: ${err.code}, message: ${err.message}`);
  });

  // For example, an accessibility app with the package name com.example.myaccessibilityapp is installed in the system.
  // The log output is:
  // [{"id":"com.example.myaccessibilityapp/AccessibilityExtAbility","name":"AccessibilityExtAbility",
  // "bundleName":"com.example.myaccessibilityapp","abilityTypes":[],
  // "capabilities":["retrieve","gesture"],"description":"$string:MainAbility_desc",
  // "eventTypes":["click","longClick","select","focus","textUpdate","hoverEnter","hoverExit","scroll",
  // "textSelectionUpdate","accessibilityFocus","accessibilityFocusClear","requestFocusForAccessibility",
  // "announceForAccessibility","announceForAccessibilityNotInterrupt",
  // "requestFocusForAccessibilityNotInterrupt","scrolling","pageActive"],"targetBundleNames":[],"needHide":false}}]
  ```

- Query all enabled accessibility applications with voice feedback.

  ```ts
  import { accessibility } from '@kit.AccessibilityKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  let abilityType: accessibility.AbilityType = 'spoken'; // The accessibility app type is spoken feedback.
  let abilityState: accessibility.AbilityState = 'enable'; // The accessibility app state is enabled.

  accessibility.getAccessibilityExtensionList(abilityType, abilityState).then((data: accessibility.AccessibilityAbilityInfo[]) => {
    console.info(`succeeded in getting accessibility extension list, ${JSON.stringify(data)}`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to get accessibility extension list. Code: ${err.code}, message: ${err.message}`);
  });
  ```

## accessibility.getAccessibilityExtensionList<sup>9+</sup>

getAccessibilityExtensionList(abilityType: AbilityType, stateType: AbilityState, callback: AsyncCallback&lt;Array&lt;AccessibilityAbilityInfo&gt;&gt;): void

Obtains the accessibility application list. This API uses an asynchronous callback to return the result.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name        | Type                                      | Mandatory  | Description              |
| ----------- | ---------------------------------------- | ---- | ---------------- |
| abilityType | [AbilityType](#abilitytype)              | Yes   | Accessibility application type.        |
| stateType   | [AbilityState](#abilitystate)            | Yes   | Accessibility application status.        |
| callback    | AsyncCallback&lt;Array&lt;[AccessibilityAbilityInfo](#accessibilityabilityinfo)&gt;&gt; | Yes    | Callback used to return the result. If the query of the accessibility app list is successful, **err** is **undefined** and **data** is the accessibility app information list; otherwise, the value is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 401  |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Parameter example**

| Accessibility Application Type/State     | enable       | disable |install|
| ------- | -------- |----|----|
| **audible**  | Queries enabled accessibility applications with audible feedback.|Queries disabled accessibility applications with audible feedback.|Queries installed accessibility applications with audible feedback.|
|**generic**| Queries enabled accessibility applications with generic feedback.|Queries disabled accessibility applications with generic feedback.|Queries installed accessibility applications with generic feedback.|
|**haptic**| Queries enabled accessibility applications with haptic feedback.|Queries disabled accessibility applications with haptic feedback.|Queries installed accessibility applications with haptic feedback.|
|**spoken**| Queries enabled accessibility applications with spoken feedback.|Queries disabled accessibility applications with spoken feedback.|Queries installed accessibility applications with spoken feedback.|
|**visual**| Queries enabled accessibility applications with visual feedback.|Queries disabled accessibility applications with visual feedback.|Queries installed accessibility applications with visual feedback.|
|**all**| Queries all enabled accessibility applications.|Queries all disabled accessibility applications.|Queries all installed accessibility applications.|

**Example**

- Query all installed accessibility applications.

  ```ts
  import { accessibility } from '@kit.AccessibilityKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  let abilityType: accessibility.AbilityType = 'all'; // The accessibility app type is all types.
  let abilityState: accessibility.AbilityState = 'install'; // The accessibility app state is installed.

  accessibility.getAccessibilityExtensionList(abilityType, abilityState, (err: BusinessError, data: accessibility.AccessibilityAbilityInfo[]) => {
    if (err) {
      console.error(`Failed to get accessibility extension list. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`succeeded in getting accessibility extension list, ${JSON.stringify(data)}`);
  });

  // For example, an accessibility app with the bundle name com.example.myaccessibilityapp is installed in the system.
  // The log is printed as follows:
  // [{"id":"com.example.myaccessibilityapp/AccessibilityExtAbility","name":"AccessibilityExtAbility",
  // "bundleName":"com.example.myaccessibilityapp","abilityTypes":[],
  // "capabilities":["retrieve","gesture"],"description":"$string:MainAbility_desc",
  // "eventTypes":["click","longClick","select","focus","textUpdate","hoverEnter","hoverExit","scroll",
  // "textSelectionUpdate","accessibilityFocus","accessibilityFocusClear","requestFocusForAccessibility",
  // "announceForAccessibility","announceForAccessibilityNotInterrupt",
  // "requestFocusForAccessibilityNotInterrupt","scrolling","pageActive"],"targetBundleNames":[],"needHide":false}}]
  ```

- Query all enabled accessibility applications with voice feedback.

  ```ts
  import { accessibility } from '@kit.AccessibilityKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  let abilityType: accessibility.AbilityType = 'spoken'; // The accessibility app type is spoken feedback.
  let abilityState: accessibility.AbilityState = 'enable'; // The accessibility app state is enabled.

  accessibility.getAccessibilityExtensionList(abilityType, abilityState, (err: BusinessError, data: accessibility.AccessibilityAbilityInfo[]) => {
    if (err) {
      console.error(`Failed to get accessibility extension list. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info(`succeeded in getting accessibility extension list, ${JSON.stringify(data)}`);
  });
  ```

## accessibility.getAccessibilityExtensionListSync<sup>12+</sup>

getAccessibilityExtensionListSync(abilityType: AbilityType, stateType: AbilityState): Array&lt;AccessibilityAbilityInfo&gt;

Query the list of accessibility applications in the current system, which can be queried by criteria.

This API is the synchronous version of [accessibility.getAccessibilityExtensionList](#accessibilitygetaccessibilityextensionlist9) (asynchronous version). They have the same functionality. Use this API if you need to obtain the result immediately. Use the asynchronous version if you need to query in non-blocking scenarios.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name        | Type                           | Mandatory  | Description      |
| ----------- | ----------------------------- | ---- | -------- |
| abilityType | [AbilityType](#abilitytype)   | Yes   | Accessibility application type.|
| stateType   | [AbilityState](#abilitystate) | Yes   | Accessibility application status.|

**Return value**

| Type                                      | Description                   |
| ---------------------------------------- | --------------------- |
| Array&lt;[AccessibilityAbilityInfo](#accessibilityabilityinfo)&gt; | Promise used to return the accessibility application list.|

**Parameter example**

| Accessibility Application Type/State     | enable       | disable |install|
| ------- | -------- |----|----|
| **audible**  | Queries enabled accessibility applications with audible feedback.|Queries disabled accessibility applications with audible feedback.|Queries installed accessibility applications with audible feedback.|
|**generic**| Queries enabled accessibility applications with generic feedback.|Queries disabled accessibility applications with generic feedback.|Queries installed accessibility applications with generic feedback.|
|**haptic**| Queries enabled accessibility applications with haptic feedback.|Queries disabled accessibility applications with haptic feedback.|Queries installed accessibility applications with haptic feedback.|
|**spoken**| Queries enabled accessibility applications with spoken feedback.|Queries disabled accessibility applications with spoken feedback.|Queries installed accessibility applications with spoken feedback.|
|**visual**| Queries enabled accessibility applications with visual feedback.|Queries disabled accessibility applications with visual feedback.|Queries installed accessibility applications with visual feedback.|
|**all**| Queries all enabled accessibility applications.|Queries all disabled accessibility applications.|Queries all installed accessibility applications.|

**Example**

- Query all installed accessibility applications.

  ```ts
  import { accessibility } from '@kit.AccessibilityKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  let abilityType: accessibility.AbilityType = 'all'; // The accessibility app type is all.
  let abilityState: accessibility.AbilityState = 'install'; // The accessibility app state is installed.
  let data: accessibility.AccessibilityAbilityInfo[];

  try {
    data = accessibility.getAccessibilityExtensionListSync(abilityType, abilityState);
    console.info(`succeeded in getting accessibility extension list, ${JSON.stringify(data)}`);
  } catch (error) {
    let err = error as BusinessError;
    console.error(`Failed to get accessibility extension list. Code: ${err.code}, message: ${err.message}`);
  }

  // For example, an accessibility app with the bundle name com.example.myaccessibilityapp is installed in the system.
  // The log output is as follows:
  // [{"id":"com.example.myaccessibilityapp/AccessibilityExtAbility","name":"AccessibilityExtAbility",
  // "bundleName":"com.example.myaccessibilityapp","abilityTypes":[],
  // "capabilities":["retrieve","gesture"],"description":"$string:MainAbility_desc",
  // "eventTypes":["click","longClick","select","focus","textUpdate","hoverEnter","hoverExit","scroll",
  // "textSelectionUpdate","accessibilityFocus","accessibilityFocusClear","requestFocusForAccessibility",
  // "announceForAccessibility","announceForAccessibilityNotInterrupt",
  // "requestFocusForAccessibilityNotInterrupt","scrolling","pageActive"],"targetBundleNames":[],"needHide":false}}]
  ```

- Query all enabled accessibility applications with voice feedback.

  ```ts
  import { accessibility } from '@kit.AccessibilityKit';
  import { BusinessError } from '@kit.BasicServicesKit';

  let abilityType: accessibility.AbilityType = 'spoken'; // The accessibility app type is spoken feedback.
  let abilityState: accessibility.AbilityState = 'enable'; // The accessibility app state is enabled.
  let data: accessibility.AccessibilityAbilityInfo[];

  try {
    data = accessibility.getAccessibilityExtensionListSync(abilityType, abilityState);
    console.info(`succeeded in getting accessibility extension list, ${JSON.stringify(data)}`);
  } catch (error) {
    let err = error as BusinessError;
    console.error(`Failed to get accessibility extension list. Code: ${err.code}, message: ${err.message}`);
  }
  ```

<!--RP1-->
<!--RP1End-->

## accessibility.getCaptionsManager<sup>(deprecated)</sup>

getCaptionsManager(): CaptionsManager

Obtains a **CaptionsManager** instance.

> **NOTE**
>
> This API is supported since API version 8 and deprecated since API version 12.

**System capability:** SystemCapability.BarrierFree.Accessibility.Hearing

**Return value**

| Type                                  | Description        |
| ------------------------------------ | ---------- |
| [CaptionsManager](#captionsmanager8) | Captions configuration.|

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

let captionsManager = accessibility.getCaptionsManager();
```

## accessibility.on('accessibilityStateChange')

on(type: 'accessibilityStateChange', callback: Callback&lt;boolean&gt;): void

Subscribes to the state changes of the accessibility application. This API uses an asynchronous callback to return the result.

To obtain information about accessibility applications in the system, you are advised to use [accessibility.getAccessibilityExtensionListSync](#accessibilitygetaccessibilityextensionlistsync12).

> **NOTE**
>
> - The callback parameter for registering a listener must use a named function instead of an anonymous function. Otherwise, a new underlying object is created each time the function is called, causing memory leakage.
> - After calling this method, ensure that [accessibility.off('accessibilityStateChange')](#accessibilityoffaccessibilitystatechange) is used to unsubscribe before the component instance is destroyed (for example, in the **aboutToDisappear** lifecycle callback). Otherwise, a crash may occur.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name  | Type                   | Mandatory| Description                                                        |
| -------- | ----------------------- | ---- | ------------------------------------------------------------ |
| type     | string                  | Yes  | Event type, which is set to **'accessibilityStateChange'** in this API.|
| callback | Callback&lt;boolean&gt; | Yes   | Callback used to return the result. When the accessibility app enabled state changes, the state is notified through this callback. This state is the global accessibility app enabled state. The value **true** indicates that the accessibility app is enabled, and **false** indicates that the accessibility app is disabled. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 401  |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

// When one or more accessibility apps are installed on the system:
// 1. Enabling an accessibility app: When the first accessibility app is enabled, the callback returns **true**.
// 2. Disabling an accessibility app: If one or more accessibility apps are enabled, when the last enabled accessibility app is disabled, the callback returns **false**.
@Entry
@Component
struct Index {
  callback: (data: boolean) => void = this.eventCallback;
  eventCallback(data: boolean): void {
    console.info(`subscribe accessibility state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    accessibility.on('accessibilityStateChange', this.callback);
  }

  aboutToDisappear(): void {
    accessibility.off('accessibilityStateChange', this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

<!--RP2-->
<!--RP2End-->

## accessibility.on('touchGuideStateChange')

on(type: 'touchGuideStateChange', callback: Callback&lt;boolean&gt;): void

Subscribes to the state changes of touch guide mode. This API uses an asynchronous callback to return the result.

To obtain information about accessibility applications in the system, you are advised to use [accessibility.getAccessibilityExtensionListSync](#accessibilitygetaccessibilityextensionlistsync12).

> **NOTE**
>
> - The callback parameter for registering a listener must use a named function instead of an anonymous function. Otherwise, a new underlying object is created each time the function is called, causing memory leakage.
> - After calling this method, ensure that [accessibility.off('touchGuideStateChange')](#accessibilityofftouchguidestatechange) is used to unsubscribe before the component instance is destroyed (for example, in the **aboutToDisappear** lifecycle callback). Otherwise, a crash may occur.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Vision

**Parameters**

| Name     | Type                     | Mandatory  | Description                                      |
| -------- | ----------------------- | ---- | ---------------------------------------- |
| type     | string                  | Yes   | Event type, which is set to **'touchGuideStateChange'** in this API.|
| callback | Callback&lt;boolean&gt; | Yes | Callback invoked when the touch browsing enabled state changes. The value **true** indicates that the touch browsing feature is enabled, and **false** indicates that the touch browsing feature is disabled. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 401  |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

// When one or more accessibility applications with touch guide mode (touchGuide is set in Capability) have been installed in the system:
// 1. Scenario where a touch browsing accessibility app is enabled: When the first touch browsing accessibility app is enabled, the callback returns **true**.
// 2. Scenario where a touch browsing accessibility app is disabled: If one or more touch browsing accessibility apps are enabled, when the last enabled touch browsing accessibility app is disabled, the callback returns **false**.
@Entry
@Component
struct Index {
  callback: (data: boolean) => void = this.eventCallback;
  eventCallback(data: boolean): void {
    console.info(`subscribe touch guide state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    accessibility.on('touchGuideStateChange', this.callback);
  }

  aboutToDisappear(): void {
    accessibility.off('touchGuideStateChange', this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.on('screenReaderStateChange')<sup>18+</sup>

on(type: 'screenReaderStateChange', callback: Callback&lt;boolean&gt;): void

Subscribes to the state changes of screen reader mode. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> - The callback parameter for registering a listener must use a named function instead of an anonymous function. Otherwise, a new underlying object is created each time the function is called, causing memory leakage.
> - After calling this method, ensure that [accessibility.off('screenReaderStateChange')](#accessibilityoffscreenreaderstatechange18) is used to unsubscribe before the component instance is destroyed (for example, in the **aboutToDisappear** lifecycle callback). Otherwise, a crash may occur.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name     | Type                     | Mandatory  | Description                                      |
| -------- | ----------------------- | ---- | ---------------------------------------- |
| type     | string                  | Yes   | Event type, which is set to **'screenReaderStateChange'** in this API.|
| callback | Callback&lt;boolean&gt; | Yes   | Callback used to return the result. The value **true** indicates that the screen reader function is enabled, and **false** indicates that the screen reader function is disabled.           |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 401  |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: boolean) => void = this.eventCallback;
  eventCallback(data: boolean): void {
    console.info(`subscribe screen reader state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    accessibility.on('screenReaderStateChange', this.callback);
  }

  aboutToDisappear(): void {
    accessibility.off('screenReaderStateChange', this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.on('touchModeChange')<sup>20+</sup>

on(type: 'touchModeChange', callback: Callback&lt;string&gt;): void

Subscribes to the single-tap/double-tap operation mode change event in touch guide mode. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> - The callback parameter for registering a listener must use a named function instead of an anonymous function. Otherwise, a new underlying object is created each time the function is called, causing memory leakage.
> - After calling this method, ensure that [accessibility.off('touchModeChange')](#accessibilityofftouchmodechange20) is used to unsubscribe before the component instance is destroyed (for example, in the **aboutToDisappear** lifecycle callback). Otherwise, a crash may occur.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name     | Type                     | Mandatory  | Description                                      |
| -------- | ----------------------- | ---- | ---------------------------------------- |
| type     | string                  | Yes   | Event type, which is set to **'touchModeChange'** in this API.|
| callback | Callback&lt;string&gt; | Yes | Callback invoked when the single-tap/double-tap operation mode changes in touch browsing mode. The value 'singleTouchMode' indicates single-tap operation mode, 'doubleTouchMode' indicates double-tap operation mode, and 'none' indicates that touch browsing is not enabled. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (mode: string) => void = this.eventCallback;
  eventCallback(mode: string): void {
    console.info(`current touch mode: ${JSON.stringify(mode)}`);
  }

  aboutToAppear(): void {
    accessibility.on('touchModeChange', this.callback);
  }

  aboutToDisappear(): void {
    accessibility.off('touchModeChange', this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.onAnimationReduceStateChange<sup>23+</sup>

onAnimationReduceStateChange(callback: Callback&lt;boolean&gt;): void

Subscribes to the state changes of animation reduction mode. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> - The callback parameter for registering a listener must use a named function instead of an anonymous function. Otherwise, a new underlying object is created each time the function is called, causing memory leakage.
> - After calling this method, ensure that [accessibility.offAnimationReduceStateChange](#accessibilityoffanimationreducestatechange23) is used to unsubscribe before the component instance is destroyed (for example, in the **aboutToDisappear** lifecycle callback). Otherwise, a crash may occur.

**Model restriction**: This API can be used only in the stage model.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name  | Type                   | Mandatory| Description                                                        |
| -------- | ----------------------- | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;boolean&gt; | Yes | Callback invoked when the reduced motion mode status changes. The value **true** indicates that the reduced motion mode is enabled, and **false** indicates that the reduced motion mode is disabled. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: boolean) => void = this.eventCallback;
  eventCallback(data: boolean): void {
    console.info(`subscribe animationReduce state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    accessibility.onAnimationReduceStateChange(this.callback);
  }

  aboutToDisappear(): void {
    accessibility.offAnimationReduceStateChange(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.onFlashReminderStateChange<sup>23+</sup>

onFlashReminderStateChange(callback: Callback&lt;boolean&gt;): void

Subscribes to the state changes of flash alerts mode. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> - The callback parameter for registering a listener must use a named function instead of an anonymous function. Otherwise, a new underlying object is created each time the function is called, causing memory leakage.
> - After calling this method, ensure that [accessibility.offFlashReminderStateChange](#accessibilityoffflashreminderstatechange23) is used to unsubscribe before the component instance is destroyed (for example, in the **aboutToDisappear** lifecycle callback). Otherwise, a crash may occur.

**Model restriction**: This API can be used only in the stage model.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name  | Type                   | Mandatory| Description                                                        |
| -------- | ----------------------- | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;boolean&gt; | Yes | Callback used to return the result. It notifies the state when the flashing reminder mode enabled state changes. The value **true** indicates that the flashing reminder mode is enabled, and **false** indicates that the flashing reminder mode is disabled. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: boolean) => void = this.eventCallback;
  eventCallback(data: boolean): void {
    console.info(`subscribe flashReminder state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    accessibility.onFlashReminderStateChange(this.callback);
  }

  aboutToDisappear(): void {
    accessibility.offFlashReminderStateChange(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.onAudioMonoStateChange<sup>23+</sup>

onAudioMonoStateChange(callback: Callback&lt;boolean&gt;): void

Subscribes to the state changes of mono audio mode. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> - The callback parameter for registering a listener must use a named function instead of an anonymous function. Otherwise, a new underlying object is created each time the function is called, causing memory leakage.
> - After calling this method, ensure that [accessibility.offAudioMonoStateChange](#accessibilityoffaudiomonostatechange23) is used to unsubscribe before the component instance is destroyed (for example, in the **aboutToDisappear** lifecycle callback). Otherwise, a crash may occur.

**Model restriction**: This API can be used only in the stage model.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name  | Type                   | Mandatory| Description                                                        |
| -------- | ----------------------- | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;boolean&gt; | Yes | Callback invoked when the mono audio mode enabled state changes. The value **true** indicates that the mono audio mode is enabled, and **false** indicates that the mono audio mode is disabled. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: boolean) => void = this.eventCallback;
  eventCallback(data: boolean): void {
    console.info(`subscribe audioMono state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    accessibility.onAudioMonoStateChange(this.callback);
  }

  aboutToDisappear(): void {
    accessibility.offAudioMonoStateChange(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.onSeniorModeStateChange

onSeniorModeStateChange(callback: Callback&lt;boolean&gt;): void

Subscribes to the state changes of the senior mode. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> - The callback parameter for registering a listener must use a named function instead of an anonymous function. Otherwise, a new underlying object is created each time the function is called, causing memory leakage.
> - After calling this method, ensure that [accessibility.offSeniorModeStateChange](#accessibilityoffseniormodestatechange) is used to unsubscribe before the component instance is destroyed (for example, in the **aboutToDisappear** lifecycle callback). Otherwise, a crash may occur.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name   | Type                    | Mandatory | Description                                                         |
| -------- | ----------------------- | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;boolean&gt; | Yes   | Callback invoked to return the result. The value **true** indicates that the senior mode is enabled, and **false** indicates that the senior mode is disabled. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: boolean) => void = this.eventCallback;
  eventCallback(data: boolean): void {
    console.info(`subscribe senior mode state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    accessibility.onSeniorModeStateChange(this.callback);
  }

  aboutToDisappear(): void {
    accessibility.offSeniorModeStateChange(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.onSeniorModeStateChangeForSelf

onSeniorModeStateChangeForSelf(callback: Callback&lt;boolean&gt;): void

Subscribes to the "senior mode" change event of the app itself. This API uses an asynchronous callback to return the result.

Unlike [accessibility.onSeniorModeStateChange](#accessibilityonseniormodestatechange), which listens for system-level senior mode state changes, this API only monitors the state of the app itself.

> **NOTE**
>
> - The callback parameter for registering a listener must use a named function instead of an anonymous function. Otherwise, a new underlying object is created each time the function is called, causing memory leakage.
> - After calling this method, ensure that [accessibility.offSeniorModeStateChangeForSelf](#accessibilityoffseniormodestatechangeforself) is used to unsubscribe before the component instance is destroyed (for example, in the **aboutToDisappear** lifecycle callback). Otherwise, a crash may occur.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name  | Type                   | Mandatory| Description                                                        |
| -------- | ----------------------- | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;boolean&gt; | Yes | Callback used to return the result. The value **true** indicates that the app's own senior mode is enabled, and **false** indicates that the app's own senior mode is disabled. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: boolean) => void = this.eventCallback;
  eventCallback(data: boolean): void {
    console.info(`subscribe senior mode state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    accessibility.onSeniorModeStateChangeForSelf(this.callback);
  }

  aboutToDisappear(): void {
    accessibility.offSeniorModeStateChangeForSelf(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.off('accessibilityStateChange')

off(type: 'accessibilityStateChange', callback?: Callback&lt;boolean&gt;): void

Unsubscribes from the state changes of the accessibility application. This API uses an asynchronous callback to return the result.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name  | Type                   | Mandatory| Description                                                        |
| -------- | ----------------------- | ---- | ------------------------------------------------------------ |
| type     | string                  | Yes  | Event type, which is set to **'accessibilityStateChange'** in this API.|
| callback | Callback&lt;boolean&gt; | No  | Callback used to unregister. It must be consistent with the callback used in [accessibility.on('accessibilityStateChange')](#accessibilityonaccessibilitystatechange). If this parameter is not specified, listening will be disabled for all callbacks corresponding to the specified type.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 401  |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: boolean) => void = this.eventCallback;
  eventCallback(data: boolean): void {
    console.info(`subscribe accessibility state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    accessibility.on('accessibilityStateChange', this.callback);
  }

  aboutToDisappear(): void {
    accessibility.off('accessibilityStateChange', this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.off('touchGuideStateChange')

off(type: 'touchGuideStateChange', callback?: Callback&lt;boolean&gt;): void

Unsubscribes from the state changes of touch guide mode. This API uses an asynchronous callback to return the result.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name  | Type                   | Mandatory| Description                                                        |
| -------- | ----------------------- | ---- | ------------------------------------------------------------ |
| type     | string                  | Yes  | Event type, which is set to **'touchGuideStateChange'** in this API.|
| callback | Callback&lt;boolean&gt; | No  | Callback used to unregister. It must be consistent with the callback used in [accessibility.on('touchGuideStateChange')](#accessibilityontouchguidestatechange). If this parameter is not specified, listening will be disabled for all callbacks corresponding to the specified type.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 401  |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: boolean) => void = this.eventCallback;
  eventCallback(data: boolean): void {
    console.info(`subscribe touch guide state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    accessibility.on('touchGuideStateChange', this.callback);
  }

  aboutToDisappear(): void {
    accessibility.off('touchGuideStateChange', this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.off('screenReaderStateChange')<sup>18+</sup>

off(type: 'screenReaderStateChange', callback?: Callback&lt;boolean&gt;): void

Unsubscribes from the state changes of screen reader mode. This API uses an asynchronous callback to return the result.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name  | Type                   | Mandatory| Description                                                        |
| -------- | ----------------------- | ---- | ------------------------------------------------------------ |
| type     | string                  | Yes  | Event type, which is set to **'screenReaderStateChange'** in this API.|
| callback | Callback&lt;boolean&gt; | No  | Callback used to unregister. It must be consistent with the callback used in [accessibility.on('screenReaderStateChange')](#accessibilityonscreenreaderstatechange18). If this parameter is not specified, listening will be disabled for all callbacks corresponding to the specified type.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 401  |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: boolean) => void = this.eventCallback;
  eventCallback(data: boolean): void {
    console.info(`subscribe screen reader state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    accessibility.on('screenReaderStateChange', this.callback);
  }

  aboutToDisappear(): void {
    accessibility.off('screenReaderStateChange', this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.off('touchModeChange')<sup>20+</sup>

off(type: 'touchModeChange', callback?: Callback&lt;string&gt;): void

Unsubscribes from the single-tap/double-tap operation mode change event in touch guide mode. This API uses an asynchronous callback to return the result.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name  | Type                   | Mandatory| Description                                                        |
| -------- | ----------------------- | ---- | ------------------------------------------------------------ |
| type     | string                  | Yes  | Event type, which is set to **'touchModeChange'** in this API.|
| callback | Callback&lt;string&gt; | No  | Callback used to unregister. The value must be the same as the value of callback in [accessibility.on('touchModeChange')](#accessibilityontouchmodechange20). If this parameter is not specified, listening will be disabled for all callbacks corresponding to the specified type.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 401  | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (mode: string) => void = this.eventCallback;
  eventCallback(mode: string): void {
    console.info(`current touch mode: ${JSON.stringify(mode)}`);
  }

  aboutToAppear(): void {
    accessibility.on('touchModeChange', this.callback);
  }

  aboutToDisappear(): void {
    accessibility.off('touchModeChange', this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.offAnimationReduceStateChange<sup>23+</sup>

offAnimationReduceStateChange(callback?: Callback&lt;boolean&gt;): void

Unsubscribes from the state changes in animation reduction mode. This API uses an asynchronous callback to return the result.

**Model restriction**: This API can be used only in the stage model.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name  | Type                  | Mandatory| Description                                                        |
| -------- | ---------------------- | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;boolean&gt; | No  | Callback function. Cancels the event response of a specified callback object. The value must be the same as the value of callback in [accessibility.onAnimationReduceStateChange](#accessibilityonanimationreducestatechange23). If this parameter is not specified, listening will be disabled for all callbacks corresponding to the specified type.|

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: boolean) => void = this.eventCallback;
  eventCallback(data: boolean): void {
    console.info(`subscribe animationReduce state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    accessibility.onAnimationReduceStateChange(this.callback);
  }

  aboutToDisappear(): void {
    accessibility.offAnimationReduceStateChange(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.offFlashReminderStateChange<sup>23+</sup>

offFlashReminderStateChange(callback?: Callback&lt;boolean&gt;): void

Unsubscribes from the state changes in flash alerts mode. This API uses an asynchronous callback to return the result.

**Model restriction**: This API can be used only in the stage model.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name  | Type                  | Mandatory| Description                                                        |
| -------- | ---------------------- | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;boolean&gt; | No  | Callback function. Cancels the event response of a specified callback object. The value must be the same as the value of callback in [accessibility.onFlashReminderStateChange](#accessibilityonflashreminderstatechange23). If this parameter is not specified, listening will be disabled for all callbacks corresponding to the specified type.|

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: boolean) => void = this.eventCallback;
  eventCallback(data: boolean): void {
    console.info(`subscribe flashReminder state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    accessibility.onFlashReminderStateChange(this.callback);
  }

  aboutToDisappear(): void {
    accessibility.offFlashReminderStateChange(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.offAudioMonoStateChange<sup>23+</sup>

offAudioMonoStateChange(callback?: Callback&lt;boolean&gt;): void

Unsubscribes from the state changes in mono audio mode. This API uses an asynchronous callback to return the result.

**Model restriction**: This API can be used only in the stage model.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name  | Type                  | Mandatory| Description                                                        |
| -------- | ---------------------- | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;boolean&gt; | No  | Callback function. Cancels the event response of a specified callback object. The value must be the same as the value of callback in [accessibility.onAudioMonoStateChange](#accessibilityonaudiomonostatechange23). If this parameter is not specified, listening will be disabled for all callbacks corresponding to the specified type.|

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: boolean) => void = this.eventCallback;
  eventCallback(data: boolean): void {
    console.info(`subscribe audioMono state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    accessibility.onAudioMonoStateChange(this.callback);
  }

  aboutToDisappear(): void {
    accessibility.offAudioMonoStateChange(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.offSeniorModeStateChange

offSeniorModeStateChange(callback?: Callback&lt;boolean&gt;): void

Unsubscribes from the state changes of the senior mode. This API uses an asynchronous callback to return the result.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name   | Type                   | Mandatory | Description                                                         |
| -------- | ---------------------- | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;boolean&gt; | No   | Callback for the senior mode state change event. It must be the same as the callback used in [accessibility.onSeniorModeStateChange](#accessibilityonseniormodestatechange). If this parameter is not specified, all registered events are unsubscribed. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: boolean) => void = this.eventCallback;
  eventCallback(data: boolean): void {
    console.info(`subscribe senior mode state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    accessibility.onSeniorModeStateChange(this.callback);
  }

  aboutToDisappear(): void {
    accessibility.offSeniorModeStateChange(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.offSeniorModeStateChangeForSelf

offSeniorModeStateChangeForSelf(callback?: Callback&lt;boolean&gt;): void

Unsubscribes from the "senior mode" change event of the app itself. This API uses an asynchronous callback to return the result.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name  | Type                  | Mandatory| Description                                                        |
| -------- | ---------------------- | ---- | ------------------------------------------------------------ |
| callback | Callback&lt;boolean&gt; | No | Callback for the senior mode state change event. It must be the same as the callback in [accessibility.onSeniorModeStateChangeForSelf](#accessibilityonseniormodestatechangeforself). If not specified, all registered events are unregistered. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  callback: (data: boolean) => void = this.eventCallback;
  eventCallback(data: boolean): void {
    console.info(`subscribe senior mode state change, result: ${JSON.stringify(data)}`);
  }

  aboutToAppear(): void {
    accessibility.onSeniorModeStateChangeForSelf(this.callback);
  }

  aboutToDisappear(): void {
    accessibility.offSeniorModeStateChangeForSelf(this.callback);
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.isOpenAccessibility<sup>(deprecated)</sup>

isOpenAccessibility(): Promise&lt;boolean&gt;

Checks whether an accessibility application is enabled. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [accessibility.isOpenAccessibilitySync](#accessibilityisopenaccessibilitysync10) instead.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Return value**

| Type                    | Description                                      |
| ---------------------- | ---------------------------------------- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates the accessibility app is enabled, and **false** indicates the accessibility app is disabled. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

accessibility.isOpenAccessibility().then((data: boolean) => {
  console.info(`success data:isOpenAccessibility : ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to isOpenAccessibility. Code: ${err.code}, message: ${err.message}`);
});
```

## accessibility.isOpenAccessibility<sup>(deprecated)</sup>

isOpenAccessibility(callback: AsyncCallback&lt;boolean&gt;): void

Checks whether an accessibility application is enabled. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [accessibility.isOpenAccessibilitySync](#accessibilityisopenaccessibilitysync10) instead.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name     | Type                          | Mandatory  | Description                                 |
| -------- | ---------------------------- | ---- | ----------------------------------- |
| callback | AsyncCallback&lt;boolean&gt; | Yes | Callback used to return the result. The value **true** indicates the accessibility app is enabled, and **false** indicates the accessibility app is not enabled. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

accessibility.isOpenAccessibility((err: BusinessError, data: boolean) => {
  if (err) {
    console.error(`Failed to isOpenAccessibility. Code:${err.code}, message:${err.message}`);
    return;
  }
  console.info(`success data:isOpenAccessibility : ${JSON.stringify(data)}`);
});
```

## accessibility.isOpenAccessibilitySync<sup>10+</sup>

isOpenAccessibilitySync(): boolean

Checks whether any accessibility application has been enabled in the system.

To obtain information about accessibility applications in the system, you are advised to use [accessibility.getAccessibilityExtensionListSync](#accessibilitygetaccessibilityextensionlistsync12).

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Return value**

<!--RP3-->

| Type       | Description                                 |
| ----------- | ------------------------------------- |
| boolean | Whether any accessibility application has been enabled in the system. Returns **true** if one or more accessibility applications are enabled; returns **false** otherwise.|

<!--RP3End-->

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

// 1. Multiple accessibility apps are installed in the system. If none of them is enabled, false is returned.
// 2. Multiple accessibility apps are installed in the system. If any of them is enabled, true is returned.
let status: boolean = accessibility.isOpenAccessibilitySync();
```

## accessibility.isOpenTouchGuide<sup>(deprecated)</sup>

isOpenTouchGuide(): Promise&lt;boolean&gt;

Checks whether touch guide mode is enabled. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [accessibility.isOpenTouchGuideSync](#accessibilityisopentouchguidesync10) instead.

**System capability:** SystemCapability.BarrierFree.Accessibility.Vision

**Return value**

| Type                    | Description                                      |
| ---------------------- | ---------------------------------------- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that the touch browsing mode is enabled, and **false** indicates that the touch browsing mode is not enabled. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

accessibility.isOpenTouchGuide().then((data: boolean) => {
  console.info(`success data:isOpenTouchGuide : ${JSON.stringify(data)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to isOpenTouchGuide. Code:${err.code}, message:${err.message}`);
});
```

## accessibility.isOpenTouchGuide<sup>(deprecated)</sup>

isOpenTouchGuide(callback: AsyncCallback&lt;boolean&gt;): void

Checks whether touch guide mode is enabled. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 10. You are advised to use [accessibility.isOpenTouchGuideSync](#accessibilityisopentouchguidesync10) instead.

**System capability:** SystemCapability.BarrierFree.Accessibility.Vision

**Parameters**

| Name     | Type                          | Mandatory  | Description                                   |
| -------- | ---------------------------- | ---- | ------------------------------------- |
| callback | AsyncCallback&lt;boolean&gt; | Yes | Callback used to return the result. The value **true** indicates that the touch browsing mode is enabled, and **false** indicates the opposite. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

accessibility.isOpenTouchGuide((err: BusinessError, data: boolean) => {
  if (err) {
    console.error(`Failed to isOpenTouchGuide. Code:${err.code}, message:${err.message}`);
    return;
  }
  console.info(`success data:isOpenTouchGuide : ${JSON.stringify(data)}`);
});
```

## accessibility.isOpenTouchGuideSync<sup>10+</sup>

isOpenTouchGuideSync(): boolean

Checks whether touch guide mode is enabled.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.BarrierFree.Accessibility.Vision

**Return value**

| Type   | Description                                 |
| ------- | ------------------------------------- |
| boolean | Whether touch guide mode is enabled. Returns **true** if touch guide mode is enabled; returns **false** otherwise.|

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

let status: boolean = accessibility.isOpenTouchGuideSync();
```

## accessibility.isScreenReaderOpenSync<sup>18+</sup>

isScreenReaderOpenSync(): boolean

Checks whether screen reader mode is enabled.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Vision

**Return value**

| Type   | Description                                 |
| ------- | ------------------------------------- |
| boolean | Whether the screen reader is enabled. Returns **true** if the screen reader is enabled; returns **false** otherwise.|

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

let status: boolean = accessibility.isScreenReaderOpenSync();
```

## accessibility.isAnimationReduceEnabled<sup>23+</sup>

isAnimationReduceEnabled(): Promise&lt;boolean&gt;

Checks whether animation reduction mode is enabled. This API uses a promise to return the result.

**Model restriction**: This API can be used only in the stage model.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Return value**

| Type                  | Description                                                        |
| ---------------------- | ------------------------------------------------------------ |
| Promise&lt;boolean&gt; | Promise used to return the result. Returns **true** if animation reduction mode is enabled; returns **false** otherwise.|

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  aboutToAppear(): void {
    accessibility.isAnimationReduceEnabled().then((data: boolean) => {
      console.info(`success data:isAnimationReduceEnabled : ${JSON.stringify(data)}`);
    }).catch((err: BusinessError) => {
      console.error(`Failed to isAnimationReduceEnabled. Code: ${err.code}, message: ${err.message}`);
    });
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.isAnimationReduceEnabledSync<sup>23+</sup>

isAnimationReduceEnabledSync(): boolean

Checks whether animation reduction mode is enabled.

This API is the synchronous version of [accessibility.isAnimationReduceEnabled](#accessibilityisanimationreduceenabled23) (asynchronous version). They have the same functionality. Use this API if you need to obtain the result immediately. Use the asynchronous version if you need to query in non-blocking scenarios.

**Model restriction**: This API can be used only in the stage model.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Return value**

| Type   | Description                                                        |
| ------- | ------------------------------------------------------------ |
| boolean | Whether animation reduction mode is enabled. Returns **true** if animation reduction mode is enabled; returns **false** otherwise.|

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  aboutToAppear(): void {
    let status: boolean = accessibility.isAnimationReduceEnabledSync();
    console.info(`status: ${JSON.stringify(status)}`);
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.isFlashReminderEnabled<sup>23+</sup>

isFlashReminderEnabled(): Promise&lt;boolean&gt;

Checks whether flash alerts mode is enabled. This API uses a promise to return the result.

**Model restriction**: This API can be used only in the stage model.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Return value**

| Type                  | Description                                                        |
| ---------------------- | ------------------------------------------------------------ |
| Promise&lt;boolean&gt; | Promise used to return the result. Returns **true** if flash alerts mode is enabled; returns **false** otherwise.|

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  aboutToAppear(): void {
    accessibility.isFlashReminderEnabled().then((data: boolean) => {
      console.info(`success data:isFlashReminderEnabled : ${JSON.stringify(data)}`);
    }).catch((err: BusinessError) => {
      console.error(`Failed to isFlashReminderEnabled. Code:${err.code}, message:${err.message}`);
    });
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.isFlashReminderEnabledSync<sup>23+</sup>

isFlashReminderEnabledSync(): boolean

Checks whether flash alerts mode is enabled.

This API is the synchronous version of [accessibility.isFlashReminderEnabled](#accessibilityisflashreminderenabled23) (asynchronous version). They have the same functionality. Use this API if you need to obtain the result immediately. Use the asynchronous version if you need to query in non-blocking scenarios.

**Model restriction**: This API can be used only in the stage model.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Return value**

| Type   | Description                                                        |
| ------- | ------------------------------------------------------------ |
| boolean | Whether flash alerts mode is enabled. Returns **true** if flash alerts mode is enabled; returns **false** otherwise.|

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  aboutToAppear(): void {
    let status: boolean = accessibility.isFlashReminderEnabledSync();
    console.info(`status: ${JSON.stringify(status)}`);
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.isAudioMonoEnabled<sup>23+</sup>

isAudioMonoEnabled(): Promise&lt;boolean&gt;

Checks whether mono audio mode is enabled. This API uses a promise to return the result.

**Model restriction**: This API can be used only in the stage model.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Return value**

| Type                  | Description                                                        |
| ---------------------- | ------------------------------------------------------------ |
| Promise&lt;boolean&gt; | Promise used to return the result. Returns **true** if mono audio mode is enabled; returns **false** otherwise.|

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  aboutToAppear(): void {
    accessibility.isAudioMonoEnabled().then((data: boolean) => {
      console.info(`success data:isAudioMonoEnabled : ${JSON.stringify(data)}`);
    }).catch((err: BusinessError) => {
      console.error(`Failed to isAudioMonoEnabled. Code:${err.code}, message:${err.message}`);
    });
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.isAudioMonoEnabledSync<sup>23+</sup>

isAudioMonoEnabledSync(): boolean

Checks whether mono audio mode is enabled.

This API is the synchronous version of [accessibility.isAudioMonoEnabled](#accessibilityisaudiomonoenabled23) (asynchronous version). They have the same functionality. Use this API if you need to obtain the result immediately. Use the asynchronous version if you need to query in non-blocking scenarios.

**Model restriction**: This API can be used only in the stage model.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Return value**

| Type   | Description                                                        |
| ------- | ------------------------------------------------------------ |
| boolean | Whether mono audio mode is enabled. Returns **true** if mono audio mode is enabled; returns **false** otherwise.|

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  aboutToAppear(): void {
    let status: boolean = accessibility.isAudioMonoEnabledSync();
    console.info(`status: ${JSON.stringify(status)}`);
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.isSeniorModeEnabled

isSeniorModeEnabled(): Promise&lt;boolean&gt;

Checks whether the senior mode is enabled. This API uses a promise to return the result.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Return value**

| Type                  | Description                                                        |
| ---------------------- | ------------------------------------------------------------ |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that senior mode is enabled, and **false** indicates that senior mode is disabled. |

**Error codes**

For details about the error codes, see [Accessibility Error Codes](errorcode-accessibility.md).

| ID  | Error Message                                    |
| ------- | ---------------------------------------- |
| 9300000 | System abnormality. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  aboutToAppear(): void {
    accessibility.isSeniorModeEnabled().then((data: boolean) => {
      console.info(`success data:isSeniorModeEnabled : ${JSON.stringify(data)}`);
    }).catch((err: BusinessError) => {
      console.error(`Failed to call isSeniorModeEnabled. Code:${err.code}, message:${err.message}`);
    });
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.getSeniorModeStateForSelf

getSeniorModeStateForSelf(): Promise&lt;boolean&gt;

Checks whether the app has "senior mode" enabled. This API uses a promise to return the result.

Unlike [accessibility.isSeniorModeEnabled](#accessibilityisseniormodeenabled), which checks whether the system-level senior mode is enabled, this API only queries the state of the app itself.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Return value**

| Type                   | Description                                                         |
| ---------------------- | ------------------------------------------------------------ |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that the "senior mode" of the app itself is enabled, and **false** indicates that the "senior mode" of the app itself is disabled. |

**Error codes**

For details about the following error codes, see [Accessibility Error Codes](errorcode-accessibility.md).

| ID   | Error Message                                     |
| ------- | ---------------------------------------- |
| 9300000 | System abnormality. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  aboutToAppear(): void {
    accessibility.getSeniorModeStateForSelf().then((data: boolean) => {
      console.info(`Succeeded in getting seniorModeStateForSelf, data: ${data}`);
    }).catch((err: BusinessError) => {
      console.error(`Failed to call getSeniorModeStateForSelf. Code:${err.code}, message:${err.message}`);
    });
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.setSeniorModeStateForSelf

setSeniorModeStateForSelf(state: boolean): Promise&lt;void&gt;

Sets whether the app has "senior mode" enabled. This API uses a promise to return the result.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name      | Type                           | Mandatory   | Description                                    |
| -------- | ---------------------------- | ---- | ------------------------------------- |
| state | boolean | Yes    | Whether to enable "senior mode" for the app. The value **true** indicates that "senior mode" is enabled, and **false** indicates that "senior mode" is disabled. |

**Return value**

| Type                   | Description                                                         |
| ---------------------- | ------------------------------------------------------------ |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the following error codes, see [Accessibility Error Codes](errorcode-accessibility.md).

| ID   | Error Message                                     |
| ------- | ---------------------------------------- |
| 9300000 | System abnormality. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  aboutToAppear(): void {
    accessibility.setSeniorModeStateForSelf(true).then(() => {
      console.info(`Succeeded in setting seniorModeStateForSelf`);
    }).catch((err: BusinessError) => {
      console.error(`Failed to call setSeniorModeStateForSelf. Code:${err.code}, message:${err.message}`);
    });
  }

  build() {
    Column() {
    }
  }
}
```

## accessibility.sendEvent<sup>(deprecated)</sup>

sendEvent(event: EventInfo): Promise&lt;void&gt;

Sends an accessibility event. The event will be distributed to registered accessibility extension applications that match the event type for response. This API uses a promise to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [accessibility.sendAccessibilityEvent](#accessibilitysendaccessibilityevent9) instead.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name  | Type                     | Mandatory  | Description      |
| ----- | ----------------------- | ---- | -------- |
| event | [EventInfo](#eventinfo) | Yes   | Accessibility event.|

**Return value**

| Type                 | Description              |
| ------------------- | ---------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let eventInfo: accessibility.EventInfo = ({
  type: 'click',
  bundleName: 'com.example.MyApplication',
  triggerAction: 'click',
});

accessibility.sendEvent(eventInfo).then(() => {
  console.info(`succeeded in sending event, eventInfo is ${eventInfo}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to sendEvent. Code:${err.code}, message:${err.message}`);
});
```

## accessibility.sendEvent<sup>(deprecated)</sup>

sendEvent(event: EventInfo, callback: AsyncCallback&lt;void&gt;): void

Sends an accessibility event. The event will be distributed to registered accessibility extension applications that match the event type for response. This API uses an asynchronous callback to return the result.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [accessibility.sendAccessibilityEvent](#accessibilitysendaccessibilityevent9-1) instead.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name     | Type                       | Mandatory  | Description                                      |
| -------- | ------------------------- | ---- | ---------------------------------------- |
| event    | [EventInfo](#eventinfo)   | Yes    | Accessibility event object.                                  |
| callback | AsyncCallback&lt;void&gt; | Yes    | Callback used to return the result. If the accessibility event is sent successfully, err is undefined; otherwise, err is an error object. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let eventInfo: accessibility.EventInfo = ({
  type: 'click',
  bundleName: 'com.example.MyApplication',
  triggerAction: 'click',
});

accessibility.sendEvent(eventInfo, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to sendEvent. Code:${err.code}, message:${err.message}`);
    return;
  }
  console.info(`succeeded in sending event, eventInfo is ${eventInfo}`);
});
```

## accessibility.sendAccessibilityEvent<sup>9+</sup>

sendAccessibilityEvent(event: EventInfo): Promise&lt;void&gt;

Sends an accessibility event. The event will be distributed to registered accessibility extension applications that match the event type for response. This API uses a promise to return the result.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name  | Type                     | Mandatory  | Description      |
| ----- | ----------------------- | ---- | -------- |
| event | [EventInfo](#eventinfo) | Yes   | Accessibility event.|

**Return value**

| Type                 | Description              |
| ------------------- | ---------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 401  |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let eventInfo: accessibility.EventInfo = ({
  type: 'click',
  bundleName: 'com.example.MyApplication',
  triggerAction: 'click',
});

accessibility.sendAccessibilityEvent(eventInfo).then(() => {
  console.info(`succeeded in sending event, eventInfo is ${eventInfo}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to send event. Code: ${err.code}, message: ${err.message}`);
});
```

## accessibility.sendAccessibilityEvent<sup>9+</sup>

sendAccessibilityEvent(event: EventInfo, callback: AsyncCallback&lt;void&gt;): void

Sends an accessibility event. The event will be distributed to registered accessibility applications that match the event type for response. This API uses an asynchronous callback to return the result.

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Parameters**

| Name     | Type                       | Mandatory  | Description                                      |
| -------- | ------------------------- | ---- | ---------------------------------------- |
| event    | [EventInfo](#eventinfo)   | Yes    | Accessibility event object.                                  |
| callback | AsyncCallback&lt;void&gt; | Yes    | Callback used to return the result. If the accessibility event is sent successfully, err is undefined; otherwise, err is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 401  |Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let eventInfo: accessibility.EventInfo = ({
  type: 'click',
  bundleName: 'com.example.MyApplication',
  triggerAction: 'click',
});

accessibility.sendAccessibilityEvent(eventInfo, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to send event. Code:${err.code}, message:${err.message}`);
    return;
  }
  console.info(`succeeded in sending event, eventInfo is ${eventInfo}`);
});
```

**Example of auto-focusing:**

```ts
@Entry
@Component
struct Index {

  build() {
    Column() {
      // Add the id attribute to the component to be focused. The uniqueness of the ID is ensured by the user.
      Button('Component to be focused').id('click')
    }
  }
}
```

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let eventInfo: accessibility.EventInfo = ({
  type: 'requestFocusForAccessibility',
  bundleName: 'com.example.MyApplication',
  triggerAction: 'common',
  customId: 'click' // ID attribute value of the component to be focused.
});

accessibility.sendAccessibilityEvent(eventInfo, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to send event. Code:${err.code}, message:${err.message}`);
    return;
  }
  console.info(`succeeded in sending event, eventInfo is ${eventInfo}`);
});
```

**Example of resource-supported auto-broadcasting<sup>18+</sup>:**

```ts
import { accessibility } from '@kit.AccessibilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let eventInfo: accessibility.EventInfo = ({
  type: 'announceForAccessibility',
  bundleName: 'com.example.MyApplication',
  triggerAction: 'common',
  textResourceAnnouncedForAccessibility: $r('app.string.ResourceName'),
});

accessibility.sendAccessibilityEvent(eventInfo, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to send event. Code:${err.code}, message:${err.message}`);
    return;
  }
  console.info(`succeeded in sending event, eventInfo is ${eventInfo}`);
});
```

## accessibility.getTouchModeSync<sup>20+</sup>

getTouchModeSync(): string

Obtains the single-tap/double-tap operation mode in touch guide mode. This can be used to adjust the app's interaction response mode based on the current operation mode (for example, responding directly to taps in single-tap mode, or requiring double-tap confirmation in double-tap mode).

**Widget capability**: This API can be used in ArkTS widgets since API version 23.

**Atomic service API**: This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**Return value**

| Type       | Description                                 |
| ----------- | ------------------------------------- |
| string | Touch mode.<br>- **singleTouchMode**: Single-touch mode.<br>- **doubleTouchMode**: Double-touch mode.<br>- **none**: Touch guide mode is disabled.|

**Example**

```ts
import { accessibility } from '@kit.AccessibilityKit';

@Entry
@Component
struct Index {
  aboutToAppear(): void {
    let touchMode: string = accessibility.getTouchModeSync();
    console.info(`current touch mode: ${JSON.stringify(touchMode)}`);
  }

  build() {
    Column() {
    }
  }
}
```