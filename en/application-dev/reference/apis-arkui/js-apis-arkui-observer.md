# @ohos.arkui.observer (Observer)

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @piggyguy; @lushi871202; @CCFFWW-->
<!--Designer: @piggyguy; @lushi871202; @CCFFWW-->
<!--Tester: @fredyuan912-->
<!--Adviser: @Brilliantry_Rui-->

Provides APIs for listening for UI component behavior changes. [UIObserver](./arkts-apis-uicontext-uiobserver.md) is recommended for component observation.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - UIObserver can only listen for relevant information within the current process and does not support obtaining information in cross-process scenarios<!--Del--> such as [UIExtensionComponent](../../reference/apis-arkui/arkui-ts/ts-container-ui-extension-component-sys.md)<!--DelEnd-->.


## Modules to Import

```ts
import { uiObserver } from '@kit.ArkUI';
```

## NavDestinationState

Describes the state of the **NavDestination** component.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name     | Value | Description                    |
| --------- | --- | ------------------------ |
| ON_SHOWN  | 0   | The **NavDestination** component is displayed.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| ON_HIDDEN | 1   | The **NavDestination** component is hidden.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| ON_APPEAR<sup>12+</sup> | 2   | The **NavDestination** component is attached to the component tree.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| ON_DISAPPEAR<sup>12+</sup> | 3   | The **NavDestination** component is detached from the component tree.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| ON_WILL_SHOW<sup>12+</sup> | 4   | The **NavDestination** component is about to be displayed.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| ON_WILL_HIDE<sup>12+</sup> | 5   | The **NavDestination** component is about to be hidden.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| ON_WILL_APPEAR<sup>12+</sup>| 6   | The **NavDestination** component is about to be mounted to the component tree.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| ON_WILL_DISAPPEAR<sup>12+</sup>| 7   | The **NavDestination** component is about to be unmounted from the component tree.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| ON_ACTIVE<sup>17+</sup> | 8 | The **NavDestination** component is active.<br>**Atomic service API**: This API can be used in atomic services since API version 17.|
| ON_INACTIVE<sup>17+</sup> | 9 | The **NavDestination** component is inactive.<br>**Atomic service API**: This API can be used in atomic services since API version 17.|
| ON_BACKPRESS<sup>12+</sup> | 100   | The back button is pressed on the **NavDestination** component.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|

## ScrollEventType<sup>12+</sup>

Enumerates the scroll event types.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name     | Value | Description                    |
| --------- | --- | ------------------------ |
| SCROLL_START  | 0   | The scroll event starts.|
| SCROLL_STOP   | 1   | The scroll event ends.|

## RouterPageState

Enumerates the states of a page during routing. **RouterPageState** is used in [RouterPageInfo](#routerpageinfo) as the callback parameter for passive observation via [routerPageUpdate](#uiobserveronrouterpageupdate11).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name             | Value | Description                   |
| ----------------- | --- | ----------------------- |
| ABOUT_TO_APPEAR       | 0   | The page is about to be displayed.           |
| ABOUT_TO_DISAPPEAR    | 1   | The page is about to be destroyed.        |
| ON_PAGE_SHOW          | 2   | The page is displayed.               |
| ON_PAGE_HIDE          | 3   | The page is hidden.               |
| ON_BACK_PRESS         | 4   | The page is returned.             |

## TabContentState<sup>12+</sup>

Enumerates the **TabContent** component states.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name             | Value | Description                   |
| ----------------- | --- | ----------------------- |
| ON_SHOW           | 0   | The **TabContent** component is displayed.   |
| ON_HIDE           | 1   | The **TabContent** component is hidden.   |

## NavDestinationInfo

Information about the **NavDestination** component, returned by the system to developers.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name        | Type                                              | Read-Only| Optional| Description                                        |
| ------------ | -------------------------------------------------  | --- | -----|--------------------------------------------- |
| navigationId | [ResourceStr](arkui-ts/ts-types.md#resourcestr) | No| No| ID of the **Navigation** component that contains the target **NavDestination** component.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| name         | [ResourceStr](arkui-ts/ts-types.md#resourcestr) | No| No| Name of the **NavDestination** component.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| state        | [NavDestinationState](#navdestinationstate)     | No| No| State of the **NavDestination** component.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| index<sup>12+</sup>        | number   | No | No  | Index of the **NavDestination** component in the navigation stack.<br>**Atomic service API**: This API can be used in atomic services since API version 12.<br> Value range: [0, +∞)     |
| param<sup>12+</sup>        | Object   | No| Yes  | Parameters of the **NavDestination** component.<br>**Atomic service API**: This API can be used in atomic services since API version 12.              |
| navDestinationId<sup>12+</sup>        | string    | No | No | Unique ID of the **NavDestination** component.<br>**Atomic service API**: This API can be used in atomic services since API version 12.           |
| mode<sup>15+</sup>        | [NavDestinationMode](arkui-ts/ts-basic-components-navdestination.md#navdestinationmode11)   | No | Yes  | Mode of the **NavDestination** component.<br>**Atomic service API**: This API can be used in atomic services since API version 15.              |
| uniqueId<sup>15+</sup>        | number     | No| Yes| Unique ID of the **NavDestination** component.<br>**Atomic service API**: This API can be used in atomic services since API version 15.            |
| size<sup>23+</sup>        | [Size](./js-apis-arkui-graphics.md#size)     | No| Yes| Size of the **NavDestination** component, in vp.<br>**Atomic service API**: This API can be used in atomic services since API version 23.            |

## NavigationInfo<sup>12+</sup>

Provides information about the **Navigation** component.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name        | Type                                        | Read-Only  | Optional| Description                                        |
| ------------ | ---------------------------------------------| ----- | ---- | -------------------------------------------- |
| navigationId | string | No| No  | ID of the **Navigation** component.<br> **Atomic service API**: This API can be used in atomic services since API version 12.|
| pathStack         | [NavPathStack](arkui-ts/ts-basic-components-navigation.md#navpathstack10) | No| No  | Navigation controller of the **Navigation** component.<br> **Atomic service API**: This API can be used in atomic services since API version 12.                  |
| uniqueId<sup>20+</sup>         | number | No| Yes  | Unique ID of the **Navigation** component, which can be obtained through [queryNavigationInfo](arkui-ts/ts-custom-component-api.md#querynavigationinfo12).<br> **Atomic service API**: This API can be used in atomic services since API version 20.                 |

## ScrollEventInfo<sup>12+</sup>

Provides the scroll event information.


**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name        | Type                                              | Read-Only| Optional| Description                                        |
| ------------ | -------------------------------------------------- | ---- | ---- | -------------------------------------------- |
| id           | string                                             | No| No| ID of the scrollable component.<br> **Atomic service API**: This API can be used in atomic services since API version 12.|
| uniqueId           | number                                             | No| No| Unique ID of the scrollable component.<br> **Atomic service API**: This API can be used in atomic services since API version 12.|
| scrollEvent    | [ScrollEventType](#scrolleventtype12)                | No| No| Enumerates the scroll event types.<br> **Atomic service API**: This API can be used in atomic services since API version 12.|
| offset       | number                                             | No| No| Current offset of the scrollable component.<br> **Atomic service API**: This API can be used in atomic services since API version 12.|
| axis<sup>20+</sup>         | [Axis](arkui-ts/ts-appendix-enums.md#axis)         | No| Yes| Scroll direction of the scrollable component.<br> **Atomic service API**: This API can be used in atomic services since API version 20.|

## ObserverOptions<sup>12+</sup>

Describes the observer options.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name        | Type                                              | Read-Only| Optional| Description                                        |
| ------------ | -------------------------------------------------- | ---- | ---- | -------------------------------------------- |
| id           | string                                             | No  | No| Component ID.                              |

## RouterPageInfo

Provides the information contained in **RouterPageInfo**, returned by the system to developers.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name                | Type                                                  | Read-Only  | Optional| Description                                          |
| -------------------- | -------------------------------------------------------| ----- | ---- | ---------------------------------------------- |
| context              | [UIAbilityContext](../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md) \| [UIContext](./arkts-apis-uicontext-uicontext.md) | No| No  | Context of the router page that invokes the lifecycle callback.<br> **Atomic service API**: This API can be used in atomic services since API version 12.|
| index                | number                                                  | No  | No  | Position of the router page that invokes the lifecycle callback, in the navigation stack.<br> Value range: [0, +∞)<br> **Atomic service API**: This API can be used in atomic services since API version 12.        |
| name                 | string                                                  | No  | No  | Name of the page that invokes the lifecycle callback.<br> **Atomic service API**: This API can be used in atomic services since API version 12.          |
| path                 | string                                                  | No  | No  | Path of the page that invokes the lifecycle callback.<br> **Atomic service API**: This API can be used in atomic services since API version 12.          |
| state                | [RouterPageState](#routerpagestate)                     | No  | No  | State of the router page that invokes the lifecycle callback.<br> **Atomic service API**: This API can be used in atomic services since API version 12.          |
| pageId<sup>12+</sup> | string                                                  | No  | No  | Unique ID of the router page that invokes the lifecycle callback.<br> **Atomic service API**: This API can be used in atomic services since API version 12.      |
| size<sup>23+</sup> | [Size](./js-apis-arkui-graphics.md#size) | No| Yes| Size of the router page, in vp.<br> **Atomic service API**: This API can be used in atomic services since API version 23.|

## DensityInfo<sup>12+</sup>

Provides the information contained in the callback when the screen pixel density changes.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name   | Type                                     | Read-Only| Optional| Description                                  |
| ------- | ----------------------------------------- | ---- | ---- | -------------------------------------- |
| context | [UIContext](./arkts-apis-uicontext-uicontext.md) | No  | No | Context corresponding to the page when the screen pixel density changes.|
| density | number                                    | No  | No  | Screen pixel density after the change.<br>Value range: [0, +∞)                |

## NavDestinationSwitchInfo<sup>12+</sup>

Provides the information about page switching of the **Navigation** component.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name        | Type                                        | Read-Only  | Optional| Description                                         |
| ------------ | -------------------------------------------- | ------ | ---- | -------------------------------------------- |
| context      | [UIAbilityContext](../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md) \| [UIContext](./arkts-apis-uicontext-uicontext.md) | No| No  | Context information corresponding to **Navigation** component that triggers page switching.|
| from         | [NavDestinationInfo](#navdestinationinfo) \| [NavBar](./arkui-ts/ts-basic-components-navigation.md#navbar12) | No| No  | Source page for page switching.        |
| to           | [NavDestinationInfo](#navdestinationinfo) \| [NavBar](./arkui-ts/ts-basic-components-navigation.md#navbar12) | No| No  | Destination page for page switching.        |
| operation    | [NavigationOperation](./arkui-ts/ts-basic-components-navigation.md#navigationoperation11)| No| No  | Page switching operation type.        |

## NavDestinationSwitchObserverOptions<sup>12+</sup>

Provides the observer options for the page switching event of the **Navigation** component.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name        | Type                                         | Read-Only | Optional| Description                                         |
| ------------ | --------------------------------------------- | ----- | ---- | -------------------------------------------- |
| navigationId | [ResourceStr](arkui-ts/ts-types.md#resourcestr) | No| No  | ID of the target **Navigation** component.|

## TextChangeEventInfo<sup>22+</sup>
Provides information about text changes in input fields.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name        | Type                                        | Read-Only | Optional| Description                                         |
| ------------ | -------------------------------------------- | ---- | ---- | -------------------------------------------- |
| id           | string                                       | No  | No  | ID of the text input component.|
| uniqueId     | number                                       | No  | No  | Unique ID of the text input component.|
| content        | string                                       | No  | No  | Text content after the change.|

## TabContentInfo<sup>12+</sup>

Provides the **TabContent** switching information.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name        | Type                                        | Read-Only | Optional| Description                                         |
| ------------ | -------------------------------------------- | ---- | ---- | -------------------------------------------- |
| tabContentId | string                                       | No  | No  | ID of the **TabContent** component.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                        |
| tabContentUniqueId | number                                 | No  | No  | Unique ID of the **TabContent** component.<br>**Atomic service API**: This API can be used in atomic services since API version 12.               |
| state        | [TabContentState](#tabcontentstate12)        | No  | No  | Enumerates the **TabContent** component states.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                   |
| index        | number                                       | No  | No  | Index of the **TabContent** component. The index is zero-based.<br>**Atomic service API**: This API can be used in atomic services since API version 12.      |
| id           | string                                       | No  | No  | ID of the **Tabs** component.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                        |
| uniqueId     | number                                       | No  | No  | Unique ID of the **Tabs** component.<br>**Atomic service API**: This API can be used in atomic services since API version 12.                     |
| lastIndex<sup>22+</sup>    | number                                       | No  | Yes  | Index of the previously focused **TabContent** component. The index is zero-based. This parameter is available only in the callback of [on('tabChange')](./arkts-apis-uicontext-uiobserver.md#ontabchange22).<br>**Atomic service API**: This API can be used in atomic services since API version 22.  |

## WindowSizeLayoutBreakpointInfo<sup>22+</sup>

Provides information about window size layout breakpoint changes.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name                | Type                                                  | Read-Only  | Optional| Description                                          |
| -------------------- | -------------------------------------------------------| ----- | ---- | ---------------------------------------------- |
| widthBreakpoint      | [WidthBreakpoint](./arkui-ts/ts-appendix-enums.md#widthbreakpoint13)  | Yes  | No  | Layout breakpoint for window width.       |
| heightBreakpoint     | [HeightBreakpoint](./arkui-ts/ts-appendix-enums.md#heightbreakpoint13)| Yes  | No  | Layout breakpoint for window height.       |


## uiObserver.on('navDestinationUpdate')

on(type: 'navDestinationUpdate', callback: Callback\<NavDestinationInfo\>): void

Subscribes to status changes of the **NavDestination** component.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                                                 | Mandatory| Description                                                                    |
| -------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------------------ |
| type     | string                                                | Yes  | Event type. Set to **'navDestinationUpdate'** for **NavDestination** component status change events.|
| callback | Callback\<[NavDestinationInfo](#navdestinationinfo)\> | Yes  | Callback used to return the result. It provides the current state of the **NavDestination** component.                            |

**Example**

```ts
// Index.ets
// Example usage of uiObserver.on('navDestinationUpdate', callback)
// uiObserver.off('navDestinationUpdate', callback)
import { uiObserver } from '@kit.ArkUI';

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
    uiObserver.on('navDestinationUpdate', (info) => {
      console.info(`NavDestination state update ${JSON.stringify(info)}`);
    });
  }

  aboutToDisappear() {
    uiObserver.off('navDestinationUpdate');
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

## uiObserver.off('navDestinationUpdate')

off(type: 'navDestinationUpdate', callback?: Callback\<NavDestinationInfo\>): void

Unsubscribes from status changes of the **NavDestination** component.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                                                 | Mandatory| Description                                                                    |
| -------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------------------ |
| type     | string                                                | Yes  | Event type. Set to **'navDestinationUpdate'** for **NavDestination** component status change events.|
| callback | Callback\<[NavDestinationInfo](#navdestinationinfo)\> | No  | Callback used to return the result. It provides the current state of the **NavDestination** component.                            |

**Example**

See the example for [uiObserver.on('navDestinationUpdate')](#uiobserveronnavdestinationupdate).

## uiObserver.on('navDestinationUpdate')

on(type: 'navDestinationUpdate', options: { navigationId: ResourceStr }, callback: Callback\<NavDestinationInfo\>): void

Subscribes to status changes of the **NavDestination** component. Compared with [uiObserver.on](#uiobserveronnavdestinationupdate), this API supports the **options** parameter, which enables you to specify the ID of the target **Navigation** component to observe.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                                                                | Mandatory| Description                                                                    |
| -------- | -------------------------------------------------------------------- | ---- | ------------------------------------------------------------------------ |
| type     | string                                                               | Yes  | Event type. Set to **'navDestinationUpdate'** for **NavDestination** component status change events.|
| options  | { navigationId: [ResourceStr](arkui-ts/ts-types.md#resourcestr) } | Yes  | ID of the target **Navigation** component.                                              |
| callback | Callback\<[NavDestinationInfo](#navdestinationinfo)\>                | Yes  | Callback used to return the result. It provides the current state of the **NavDestination** component.                            |

**Example**

```ts
// Index.ets
// Example usage of uiObserver.on('navDestinationUpdate', navigationId, callback)
// uiObserver.off('navDestinationUpdate', navigationId, callback)
import { uiObserver } from '@kit.ArkUI';

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
    uiObserver.on('navDestinationUpdate', { navigationId: "testId" }, (info) => {
      console.info(`NavDestination state update ${JSON.stringify(info)}`);
    });
  }

  aboutToDisappear() {
    uiObserver.off('navDestinationUpdate', { navigationId: "testId" });
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

## uiObserver.off('navDestinationUpdate')

off(type: 'navDestinationUpdate', options: { navigationId: ResourceStr }, callback?: Callback\<NavDestinationInfo\>): void

Unsubscribes from status changes of the **NavDestination** component. Compared with [uiObserver.off](#uiobserveroffnavdestinationupdate), this API supports the **options** parameter, which enables you to specify the ID of the target **Navigation** component to observe.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                                                                | Mandatory| Description                                                                    |
| -------- | -------------------------------------------------------------------- | ---- | ------------------------------------------------------------------------ |
| type     | string                                                               | Yes  | Event type. Set to **'navDestinationUpdate'** for **NavDestination** component status change events.|
| options  | { navigationId: [ResourceStr](arkui-ts/ts-types.md#resourcestr) } | Yes  | ID of the target **Navigation** component.                                              |
| callback | Callback\<[NavDestinationInfo](#navdestinationinfo)\>                | No  | Callback used to return the result. It provides the current state of the **NavDestination** component.                            |

**Example**

See the example for [uiObserver.on('navDestinationUpdate')](#uiobserveronnavdestinationupdate-1).

## uiObserver.on('scrollEvent')<sup>12+</sup>

on(type: 'scrollEvent', callback: Callback\<ScrollEventInfo\>): void

Listens for the start and end of scroll events of all scrollable components. Supported components include [List](./arkui-ts/ts-container-list.md), [Grid](./arkui-ts/ts-container-grid.md), [Scroll](./arkui-ts/ts-container-scroll.md), [WaterFlow](./arkui-ts/ts-container-waterflow.md), and [ArcList](./arkui-ts/ts-container-arclist.md).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                                                 | Mandatory| Description                                                                    |
| -------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------------------ |
| type     | string                                                | Yes  | Event type. The value **'scrollEvent'** indicates the start and end of a scroll event.                  |
| callback | Callback\<[ScrollEventInfo](#scrolleventinfo12)\>       | Yes  | Callback used to return the result. It returns the information about the scroll event.                                          |

**Example**

See the example for [uiObserver.off('scrollEvent')](#uiobserveroffscrollevent12-1).

## uiObserver.off('scrollEvent')<sup>12+</sup>

off(type: 'scrollEvent', callback?: Callback\<ScrollEventInfo\>): void

Unregisters the listener for the start and end of scroll events of all scrollable components. Supported components include [List](./arkui-ts/ts-container-list.md), [Grid](./arkui-ts/ts-container-grid.md), [Scroll](./arkui-ts/ts-container-scroll.md), [WaterFlow](./arkui-ts/ts-container-waterflow.md), and [ArcList](./arkui-ts/ts-container-arclist.md).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                                                 | Mandatory| Description                                                                    |
| -------- | ----------------------------------------------------- | ---- | ------------------------------------------------------------------------ |
| type     | string                                                | Yes  | Event type. The value **'scrollEvent'** indicates the start and end of a scroll event.                  |
| callback | Callback\<[ScrollEventInfo](#scrolleventinfo12)\>       | No  | Callback used to return the result. It returns the information about the scroll event.                                          |

**Example**

See the example for [uiObserver.off('scrollEvent')](#uiobserveroffscrollevent12-1).

## uiObserver.on('scrollEvent')<sup>12+</sup>

on(type: 'scrollEvent', options: ObserverOptions, callback: Callback\<ScrollEventInfo\>): void

Listens for the start and end of scroll events of a specific scrollable component identified by its ID. Supported components include [List](./arkui-ts/ts-container-list.md), [Grid](./arkui-ts/ts-container-grid.md), [Scroll](./arkui-ts/ts-container-scroll.md), [WaterFlow](./arkui-ts/ts-container-waterflow.md), and [ArcList](./arkui-ts/ts-container-arclist.md).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                                                                | Mandatory| Description                                                                    |
| -------- | -------------------------------------------------------------------- | ---- | ------------------------------------------------------------------------ |
| type     | string                                                               | Yes  | Event type. The value **'scrollEvent'** indicates the start and end of a scroll event.                  |
| options  | [ObserverOptions](#observeroptions12)                                  | Yes  | ID of the target scrollable component.                                                |
| callback | Callback\<[ScrollEventInfo](#scrolleventinfo12)\>                      | Yes  | Callback used to return the result. It returns the information about the scroll event.                                           |

**Example**

See the example for [uiObserver.off('scrollEvent')](#uiobserveroffscrollevent12-1).

## uiObserver.off('scrollEvent')<sup>12+</sup>

off(type: 'scrollEvent', options: ObserverOptions, callback?: Callback\<ScrollEventInfo\>): void

Unregisters the listener for the start and end of scroll events of a specific scrollable component identified by its ID. Supported components include [List](./arkui-ts/ts-container-list.md), [Grid](./arkui-ts/ts-container-grid.md), [Scroll](./arkui-ts/ts-container-scroll.md), [WaterFlow](./arkui-ts/ts-container-waterflow.md), and [ArcList](./arkui-ts/ts-container-arclist.md).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                                                                | Mandatory| Description                                                                    |
| -------- | -------------------------------------------------------------------- | ---- | ------------------------------------------------------------------------ |
| type     | string                                                               | Yes  | Event type. The value **'scrollEvent'** indicates the start and end of a scroll event.                  |
| options  | [ObserverOptions](#observeroptions12)                                  | Yes  | ID of the target scrollable component.                                                |
| callback | Callback\<[ScrollEventInfo](#scrolleventinfo12)\>                      | No  | Callback used to return the result. It returns the information about the scroll event.                                           |

**Example**

```ts
import { uiObserver } from '@kit.ArkUI'

@Entry
@Component
struct Index {
  scroller: Scroller = new Scroller();
  options: uiObserver.ObserverOptions = { id: 'testId' };
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7]

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
            uiObserver.on('scrollEvent', (info) => {
              console.info(`scrollEventInfo ${JSON.stringify(info)}`);
            });
          })
        Button('UIObserver off')
          .onClick(() => {
            uiObserver.off('scrollEvent');
          })
      }

      Row() {
        Button('UIObserverWithId on')
          .onClick(() => {
            uiObserver.on('scrollEvent', this.options, (info) => {
              console.info(`scrollEventInfo ${JSON.stringify(info)}`);
            });
          })
        Button('UIObserverWithId off')
          .onClick(() => {
            uiObserver.off('scrollEvent',this.options);
          })
      }
    }
    .height('100%')
  }
}
```

## uiObserver.on('routerPageUpdate')<sup>11+</sup>

on(type: 'routerPageUpdate', context: UIAbilityContext | UIContext, callback: Callback\<RouterPageInfo\>): void

Subscribes to state changes of the page during routing.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Event type. The value is fixed at **'routerPageUpdate'**, which indicates the state change event of the page during routing.|
| context  | [UIAbilityContext](../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md) \| [UIContext](./arkts-apis-uicontext-uicontext.md) | Yes  | Context information, which is used to specify the target page scope.|
| callback | Callback\<[RouterPageInfo](#routerpageinfo)\>        | Yes  | Callback used to return the result. If **pageInfo** is passed, the current page state is returned.                |

**Example**

```ts
// used in UIAbility
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { UIContext, window, uiObserver } from '@kit.ArkUI';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  private uiContext: UIContext | null = null;

  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    // Subscribe to the target events within the scope of the page under the ability context.
    uiObserver.on('routerPageUpdate', this.context, (info: uiObserver.RouterPageInfo) => {
      console.info(`[uiObserver][abilityContext] got info: ${JSON.stringify(info)}`)
    })
  }

  onWindowStageCreate(windowStage: window.WindowStage): void {
    windowStage.loadContent('pages/Index', (err) => {
      windowStage.getMainWindow((err: BusinessError, data) => {
        let windowInfo: window.Window = data;
        // Obtain a UIContext instance.
        this.uiContext = windowInfo.getUIContext();
        // Subscribe to the target events within the scope of the page under the UI context.
        uiObserver.on('routerPageUpdate', this.uiContext, (info: uiObserver.RouterPageInfo)=>{
          console.info(`[uiObserver][uiContext] got info: ${JSON.stringify(info)}`)
        })
      })
    });
  }

  // ... other function in EntryAbility
}
```

## uiObserver.off('routerPageUpdate')<sup>11+</sup>

off(type: 'routerPageUpdate', context: UIAbilityContext | UIContext, callback?: Callback\<RouterPageInfo\>): void

Unsubscribes from state changes of the page during routing.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Event type. The value is fixed at **'routerPageUpdate'**, which indicates the state change event of the page during routing.|
| context  | [UIAbilityContext](../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md) \| [UIContext](./arkts-apis-uicontext-uicontext.md) | Yes  | Context information, which is used to specify the target page scope.|
| callback | Callback\<[RouterPageInfo](#routerpageinfo)\>        | No  | Target listener to unregister.                |

**Example**

```ts
// used in UIAbility
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { uiObserver, UIContext } from '@kit.ArkUI';

export default class EntryAbility extends UIAbility {
  // Before actual use, uiContext must be assigned a value. For details, see the example for uiObserver.on('routerPageUpdate').
  private uiContext: UIContext | null = null;

  onDestroy(): void {
    // Unregister all callbacks for the routerPageUpdate event under the current ability context.
    uiObserver.off('routerPageUpdate', this.context)
  }

  onWindowStageDestroy(): void {
    // Unregister all callbacks for the routerPageUpdate event under the UI context.
    if (this.uiContext) {
      uiObserver.off('routerPageUpdate', this.uiContext);
    }
  }

  // ... other function in EntryAbility
}
```

## uiObserver.on('densityUpdate')<sup>12+</sup>

on(type: 'densityUpdate', context: UIContext, callback: Callback\<DensityInfo\>): void

Listens for screen pixel density changes.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Event type. Set to **'densityUpdate'** for screen pixel density change events.|
| context  | [UIContext](./arkts-apis-uicontext-uicontext.md) | Yes  | Context information, which is used to specify the target page scope.|
| callback | Callback\<[DensityInfo](#densityinfo12)\>        | Yes  | Callback used to return the result. It provides information about the screen pixel density after the change.                |

**Example**

```ts
import { uiObserver } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State density: number = 0;
  @State message: string = 'Listener not registered';

  densityUpdateCallback = (info: uiObserver.DensityInfo) => {
    this.density = info.density;
    this.message = 'DPI after change:' + this.density.toString();
  }

  build() {
    Column() {
      Text(this.message)
        .fontSize(24)
        .fontWeight(FontWeight.Bold)
      Button('Subscribe to Screen Pixel Density Changes')
        .onClick(() => {
          this.message = 'Listener registered'
          uiObserver.on('densityUpdate', this.getUIContext(), this.densityUpdateCallback);
        })
    }
  }
}
```

## uiObserver.off('densityUpdate')<sup>12+</sup>

off(type: 'densityUpdate', context: UIContext, callback?: Callback\<DensityInfo\>): void

Unregisters the listener for screen pixel density changes.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                                     | Mandatory| Description                                                                                          |
| -------- | ----------------------------------------- | ---- | ---------------------------------------------------------------------------------------------- |
| type     | string                                    | Yes  | Event type. Set to **'densityUpdate'** for screen pixel density change events.                                         |
| context  | [UIContext](./arkts-apis-uicontext-uicontext.md) | Yes  | Context information, which is used to specify the target page scope.                                                            |
| callback | Callback\<[DensityInfo](#densityinfo12)\> | No  | Target listener to unregister. If no parameter is provided, all listeners for the **densityUpdate** event under the current UI context are unregistered.|

```ts
import { uiObserver, UIContext } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State density: number = 0;
  @State message: string = 'Listener not registered'

  densityUpdateCallback = (info: uiObserver.DensityInfo) => {
    this.density = info.density;
    this.message = 'DPI after change:' + this.density.toString();
  }

  build() {
    Column() {
      Text(this.message)
        .fontSize(24)
        .fontWeight(FontWeight.Bold)
      Button('Subscribe to Screen Pixel Density Changes')
        .margin({ bottom: 10 })
        .onClick(() => {
          this.message = 'Listener registered'
          uiObserver.on('densityUpdate', this.getUIContext(), this.densityUpdateCallback);
        })
      Button('Unsubscribe from Screen Pixel Density Changes')
        .onClick(() => {
          this.message = 'Listener not registered'
          uiObserver.off('densityUpdate', this.getUIContext(), this.densityUpdateCallback);
        })
    }
  }
}
```

## uiObserver.on('willDraw')<sup>12+</sup>

on(type: 'willDraw', context: UIContext, callback: Callback\<void\>): void

Listens for drawing instruction dispatch in each frame.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Event event. The value **'willDraw'** indicates whether drawing is about to occur.|
| context  | [UIContext](./arkts-apis-uicontext-uicontext.md) | Yes  | Context information, which is used to specify the target page scope.|
| callback | Callback\<void\>        | Yes  | Callback used to return the result.                |

**Example**

```ts
import { uiObserver } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  willDrawCallback = () => {
    console.info("willDraw instruction dispatched.");
  }
  build() {
    Column() {
      Button('Listen for Drawing Instruction Dispatch')
        .onClick(() => {
          uiObserver.on('willDraw', this.getUIContext(), this.willDrawCallback);
        })
    }
  }
}
```

## uiObserver.off('willDraw')<sup>12+</sup>

off(type: 'willDraw', context: UIContext, callback?: Callback\<void\>): void

Unregisters the listener for drawing instruction dispatch in each frame.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                                     | Mandatory| Description                                                 |
| -------- | ----------------------------------------- | ---- | ----------------------------------------------------- |
| type     | string                                    | Yes  | Event event. The value **'willDraw'** indicates whether drawing is about to occur.|
| context  | [UIContext](./arkts-apis-uicontext-uicontext.md) | Yes  | Context information, which is used to specify the target page scope.                   |
| callback | Callback\<void\>   | No  | Target listener to unregister.                               |

```ts
import { uiObserver } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  willDrawCallback = () => {
    console.info("willDraw instruction dispatched.")
  }

  build() {
    Column() {
      Button('Listen for Drawing Instruction Dispatch')
        .margin({ bottom: 10 })
        .onClick(() => {
          uiObserver.on('willDraw', this.getUIContext(), this.willDrawCallback);
        })
      Button('Unregister Drawing Instruction Dispatch Listener')
        .onClick(() => {
          uiObserver.off('willDraw', this.getUIContext(), this.willDrawCallback);
        })
    }
  }
}
```

## uiObserver.on('didLayout')<sup>12+</sup>

on(type: 'didLayout', context: UIContext, callback: Callback\<void\>): void

Listens for layout completion status in each frame.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Event type. The value **'didLayout'** indicates whether the layout has been completed.|
| context  | [UIContext](./arkts-apis-uicontext-uicontext.md) | Yes  | Context information, which is used to specify the target page scope.|
| callback | Callback\<void\>        | Yes  | Callback used to return the result.                |

**Example**

```ts
import { uiObserver } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  didLayoutCallback = () => {
    console.info("Layout completed.");
  }
  build() {
    Column() {
      Button('Listen for Layout Completion')
        .onClick(() => {
          uiObserver.on('didLayout', this.getUIContext(), this.didLayoutCallback);
        })
    }
  }
}
```

## uiObserver.off('didLayout')<sup>12+</sup>

off(type: 'didLayout', context: UIContext, callback?: Callback\<void\>): void

Unregisters the listener for layout completion status in each frame.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                                     | Mandatory| Description                                                 |
| -------- | ----------------------------------------- | ---- | ----------------------------------------------------- |
| type     | string                                    | Yes  | Event type. The value **'didLayout'** indicates whether the layout has been completed.|
| context  | [UIContext](./arkts-apis-uicontext-uicontext.md) | Yes  | Context information, which is used to specify the target page scope.                   |
| callback | Callback\<void\>   | No  | Target listener to unregister.                               |

```ts
import { uiObserver } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  didLayoutCallback = () => {
    console.info("Layout completed.")
  }

  build() {
    Column() {
      Button('Listen for Layout Completion')
        .margin({ bottom: 10 })
        .onClick(() => {
          uiObserver.on('didLayout', this.getUIContext(), this.didLayoutCallback);
        })
      Button('Unsubscribe from Layout Completion')
        .onClick(() => {
          uiObserver.off('didLayout', this.getUIContext(), this.didLayoutCallback);
        })
    }
  }
}
```

## uiObserver.on('navDestinationSwitch')<sup>12+</sup>

on(type: 'navDestinationSwitch', context: UIAbilityContext | UIContext, callback: Callback\<NavDestinationSwitchInfo\>): void

Subscribes to **Navigation** component page switching events.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Event type. Set to **'navDestinationSwitch'** for **Navigation** component page switching events.|
| context  | [UIAbilityContext](../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md) \| [UIContext](./arkts-apis-uicontext-uicontext.md) | Yes  | Context information, which is used to specify the target scope for page switching events.|
| callback | Callback\<[NavDestinationSwitchInfo](#navdestinationswitchinfo12)\>        | Yes  | Callback used to return the result. It provides page switching event information through **NavDestinationSwitchInfo**.                |

**Example**

```ts
// EntryAbility.ets
// Example usage of uiObserver.on('navDestinationSwitch', UIAbilityContext, callback)
// uiObserver.off('navDestinationSwitch', UIAbilityContext, callback)
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { uiObserver, window } from '@kit.ArkUI';
import { hilog } from "@kit.PerformanceAnalysisKit";

function callbackFunc(info: uiObserver.NavDestinationSwitchInfo) {
  console.info(`testTag navDestinationSwitch from: ${JSON.stringify(info.from)} to: ${JSON.stringify(info.to)}`)
}

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onCreate');
    uiObserver.on('navDestinationSwitch', this.context, callbackFunc);
  }

  onDestroy(): void {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onDestroy');
    uiObserver.off('navDestinationSwitch', this.context, callbackFunc);
  }

  onWindowStageCreate(windowStage: window.WindowStage): void {
    // Main window is created, set main page for this ability
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onWindowStageCreate');

    windowStage.loadContent('pages/Index', (err, data) => {
      if (err.code) {
        hilog.error(0x0000, 'testTag', 'Failed to load the content. Cause: %{public}s', JSON.stringify(err) ?? '');
        return;
      }
      hilog.info(0x0000, 'testTag', 'Succeeded in loading the content. Data: %{public}s', JSON.stringify(data) ?? '');
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

```ts
// Index.ets
// Example usage of uiObserver.on('navDestinationSwitch', UIContext, callback)
// uiObserver.off('navDestinationSwitch', UIContext, callback)
import { uiObserver } from '@kit.ArkUI';

@Component
struct PageOne {
  build() {
    NavDestination() {
      Text("pageOne")
    }.title("pageOne")
  }
}

function callbackFunc(info: uiObserver.NavDestinationSwitchInfo) {
  console.info(`testTag navDestinationSwitch from: ${JSON.stringify(info.from)} to: ${JSON.stringify(info.to)}`)
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
    uiObserver.on('navDestinationSwitch', this.getUIContext(), callbackFunc)
  }

  aboutToDisappear() {
    uiObserver.off('navDestinationSwitch', this.getUIContext(), callbackFunc)
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

## uiObserver.off('navDestinationSwitch')<sup>12+</sup>

off(type: 'navDestinationSwitch', context: UIAbilityContext | UIContext, callback?: Callback\<NavDestinationSwitchInfo\>): void

Unsubscribes from **Navigation** component page switching events.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Event type. Set to **'navDestinationSwitch'** for **Navigation** component page switching events.|
| context  | [UIAbilityContext](../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md) \| [UIContext](./arkts-apis-uicontext-uicontext.md) | Yes  | Context information, which is used to specify the target scope for page switching events.|
| callback | Callback\<[NavDestinationSwitchInfo](#navdestinationswitchinfo12)\>        | No  | Target listener to unregister.                |

**Example**

See the example for [uiObserver.on('navDestinationSwitch')](#uiobserveronnavdestinationswitch12).

## uiObserver.on('navDestinationSwitch')<sup>12+</sup>

on(type: 'navDestinationSwitch', context: UIAbilityContext | UIContext, observerOptions: NavDestinationSwitchObserverOptions, callback: Callback\<NavDestinationSwitchInfo\>): void

Subscribes to **Navigation** component page switching events. Compared with [uiObserver.on](#uiobserveronnavdestinationswitch12), this API supports the **observerOptions** parameter, which enables you to configure observation options.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Event type. Set to **'navDestinationSwitch'** for **Navigation** component page switching events.|
| context  | [UIAbilityContext](../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md) \| [UIContext](./arkts-apis-uicontext-uicontext.md) | Yes  | Context information, which is used to specify the target scope for page switching events.|
| observerOptions | [NavDestinationSwitchObserverOptions](#navdestinationswitchobserveroptions12)        | Yes  | Observer configuration options.  |
| callback | Callback\<[NavDestinationSwitchInfo](#navdestinationswitchinfo12)\>        | Yes  | Callback used to return the result. It provides page switching event information through **NavDestinationSwitchInfo**.                |

**Example**

```ts
// EntryAbility.ets
// Example usage of uiObserver.on('navDestinationSwitch', UIAbilityContext, NavDestinationSwitchObserverOptions, callback)
// uiObserver.off('navDestinationSwitch', UIAbilityContext, NavDestinationSwitchObserverOptions, callback)
import { AbilityConstant, UIAbility, Want } from '@kit.AbilityKit';
import { uiObserver, window } from '@kit.ArkUI';
import { hilog } from "@kit.PerformanceAnalysisKit"

function callbackFunc(info: uiObserver.NavDestinationSwitchInfo) {
  console.info(`testTag navDestinationSwitch from: ${JSON.stringify(info.from)} to: ${JSON.stringify(info.to)}`)
}

export default class EntryAbility extends UIAbility {
  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onCreate');
    uiObserver.on('navDestinationSwitch', this.context, {
      navigationId: "myNavId"
    }, callbackFunc);
  }

  onDestroy(): void {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onDestroy');
    uiObserver.off('navDestinationSwitch', this.context, {
      navigationId: "myNavId"
    }, callbackFunc);
  }

  onWindowStageCreate(windowStage: window.WindowStage): void {
    // Main window is created, set main page for this ability
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onWindowStageCreate');

    windowStage.loadContent('pages/Index', (err, data) => {
      if (err.code) {
        hilog.error(0x0000, 'testTag', 'Failed to load the content. Cause: %{public}s', JSON.stringify(err) ?? '');
        return;
      }
      hilog.info(0x0000, 'testTag', 'Succeeded in loading the content. Data: %{public}s', JSON.stringify(data) ?? '');
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

```ts
// Index.ets
// Example usage of uiObserver.on('navDestinationSwitch', UIContext, NavDestinationSwitchObserverOptions, callback)
// uiObserver.off('navDestinationSwitch', UIContext, NavDestinationSwitchObserverOptions, callback)
import { uiObserver } from '@kit.ArkUI';

@Component
struct PageOne {
  build() {
    NavDestination() {
      Text("pageOne")
    }.title("pageOne")
  }
}

function callbackFunc(info: uiObserver.NavDestinationSwitchInfo) {
  console.info(`testTag navDestinationSwitch from: ${JSON.stringify(info.from)} to: ${JSON.stringify(info.to)}`)
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
    uiObserver.on('navDestinationSwitch', this.getUIContext(), { navigationId: "myNavId" }, callbackFunc)
  }

  aboutToDisappear() {
    uiObserver.off('navDestinationSwitch', this.getUIContext(), { navigationId: "myNavId" }, callbackFunc)
  }

  build() {
    Column() {
      Navigation(this.stack) {
        Button("push").onClick(() => {
          this.stack.pushPath({ name: "pageOne" });
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

## uiObserver.off('navDestinationSwitch')<sup>12+</sup>

off(type: 'navDestinationSwitch', context: UIAbilityContext | UIContext, observerOptions: NavDestinationSwitchObserverOptions, callback?: Callback\<NavDestinationSwitchInfo\>): void

Unsubscribes from **Navigation** component page switching events. Compared with [uiObserver.off](#uiobserveroffnavdestinationswitch12), this API supports the **observerOptions** parameter, which enables you to configure observation options.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Event type. Set to **'navDestinationSwitch'** for **Navigation** component page switching events.|
| context  | [UIAbilityContext](../apis-ability-kit/js-apis-inner-application-uiAbilityContext.md) \| [UIContext](./arkts-apis-uicontext-uicontext.md) | Yes  | Context information, which is used to specify the target scope for page switching events.|
| observerOptions | [NavDestinationSwitchObserverOptions](#navdestinationswitchobserveroptions12)        | Yes  | Observer configuration options.  |
| callback | Callback\<[NavDestinationSwitchInfo](#navdestinationswitchinfo12)\>        | No  | Target listener to unregister.                |

**Example**

See the example for [uiObserver.on('navDestinationSwitch')](#uiobserveronnavdestinationswitch12-1).

## uiObserver.on('tabContentUpdate')<sup>12+</sup>

on(type: 'tabContentUpdate', callback: Callback\<TabContentInfo\>): void

Subscribes to **TabContent** switch events. Unlike [on('tabChange')](./arkts-apis-uicontext-uiobserver.md#ontabchange22), this API does not support listening for the initial tab display event when the **Tabs** component is initialized.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Event type. Set to **'tabContentUpdate'** for **TabContent** page switching events.|
| callback | Callback\<[TabContentInfo](#tabcontentinfo12)\>              | Yes  | Callback used to return the result. It provides information about **TabContent** switch events through **TabContentInfo**.|

**Example**

```ts
import { uiObserver } from '@kit.ArkUI';

function callbackFunc(info: uiObserver.TabContentInfo) {
  console.info(`tabContentUpdate ${JSON.stringify(info)}`);
}

@Entry
@Component
struct TabsExample {

  aboutToAppear(): void {
    uiObserver.on('tabContentUpdate', callbackFunc);
  }

  aboutToDisappear(): void {
    uiObserver.off('tabContentUpdate', callbackFunc);
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

## uiObserver.off('tabContentUpdate')<sup>12+</sup>

off(type: 'tabContentUpdate', callback?: Callback\<TabContentInfo\>): void

Unsubscribes from the **TabContent** switching event.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Event type. Set to **'tabContentUpdate'** for **TabContent** page switching events.|
| callback | Callback\<[TabContentInfo](#tabcontentinfo12)\>              | No  | Target listener to unregister.|

**Example**

See the example for [uiObserver.on('tabContentUpdate')](#uiobserverontabcontentupdate12).

## uiObserver.on('tabContentUpdate')<sup>12+</sup>

on(type: 'tabContentUpdate', options: ObserverOptions, callback: Callback\<TabContentInfo\>): void

Subscribes to **TabContent** page switching events for the specified **Tabs** component identified by its ID. Unlike [on('tabChange')](./arkts-apis-uicontext-uiobserver.md#ontabchange22), this API does not support listening for the initial tab display event when the **Tabs** component is initialized.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Event type. Set to **'tabContentUpdate'** for **TabContent** page switching events.|
| options  | [ObserverOptions](#observeroptions12)                        | Yes  | ID of the target **Tabs** component.|
| callback | Callback\<[TabContentInfo](#tabcontentinfo12)\>              | Yes  | Callback used to return the result. It provides information about **TabContent** switch events through **TabContentInfo**.|

**Example**

```ts
import { uiObserver } from '@kit.ArkUI';

function callbackFunc(info: uiObserver.TabContentInfo) {
  console.info(`tabContentUpdate ${JSON.stringify(info)}`);
}

@Entry
@Component
struct TabsExample {

  aboutToAppear(): void {
    uiObserver.on('tabContentUpdate', { id: 'tabsId' }, callbackFunc);
  }

  aboutToDisappear(): void {
    uiObserver.off('tabContentUpdate', { id: 'tabsId' }, callbackFunc);
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

## uiObserver.off('tabContentUpdate')<sup>12+</sup>

off(type: 'tabContentUpdate', options: ObserverOptions, callback?: Callback\<TabContentInfo\>): void

Unsubscribes from **TabContent** page switching events for the specified **Tabs** component identified by its ID.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                                                        | Mandatory| Description                                                        |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| type     | string                                                       | Yes  | Event type. Set to **'tabContentUpdate'** for **TabContent** page switching events.|
| options  | [ObserverOptions](#observeroptions12)                        | Yes  | ID of the target **Tabs** component.|
| callback | Callback\<[TabContentInfo](#tabcontentinfo12)\>              | No  | Target listener to unregister.|

**Example**

See the example for [uiObserver.on('tabContentUpdate')](#uiobserverontabcontentupdate12-1).
