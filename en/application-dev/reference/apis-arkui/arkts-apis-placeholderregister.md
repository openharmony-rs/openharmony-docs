# @ohos.arkui.placeholderRegister (Scrolling Placeholder Registration)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @rongShao-Z; @wind_-->
<!--Designer: @yangcan18-->
<!--Tester: @leiyuqian-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=37a41c7e4764d3e7f831e1f47fc28c3acf56e6c1 translatedAt=2026-11-02T12:36:02.760Z pushedAt=2026-11-03T07:58:43.823Z nl=1 -->

This module provides the capabilities of registering, unregistering, and querying scrolling placeholder templates. In fast scrolling scenarios, when the framework predicts that creating the next list item within the remaining frame budget will cause a frame overrun, a scrollable component (such as [List](arkui-ts/ts-container-list.md)) first displays a placeholder component for that item. The real list item replaces the placeholder after its frame-by-frame creation on the UI thread is complete, thereby reducing frame drops. After a placeholder template is registered through [register](#register), it can be referenced by ID through the [scrollPlaceholder](arkui-ts/ts-container-list.md#scrollplaceholder) attribute of [List](arkui-ts/ts-container-list.md).

> **NOTE**
>
> The APIs of this module can be used only in the stage model.

**Since:** 26.1.0

## Modules to Import

```ts
import { PlaceholderRegister } from '@kit.ArkUI';
```

## PlaceholderRegister

Describes the registry of scrolling placeholder templates, which provides the capabilities of registering, unregistering, and querying placeholder templates. Each UI instance holds an independent registry, and placeholder templates registered in one UI instance are invisible to other UI instances. Do not construct a **PlaceholderRegister** instance by yourself. Instead, obtain the registry of the current UI instance through [getPlaceholderRegister()](./arkts-apis-uicontext-uicontext.md#getplaceholderregister).

> **NOTE**
>
> In the following API examples, you must first use [getPlaceholderRegister()](./arkts-apis-uicontext-uicontext.md#getplaceholderregister) in **UIContext** to obtain a **PlaceholderRegister** object, and then call the APIs using the obtained object.

**Since:** 26.1.0

### register

register(id: string, builder: WrappedBuilder<[]>): void

Registers a scrolling placeholder template by binding the placeholder builder to the specified ID, so that the [scrollPlaceholder](arkui-ts/ts-container-list.md#scrollplaceholder) attribute of a scrollable component can reference the template by ID.

> **NOTE**
>
> - The placeholder template must be a global, parameterless `@Builder({ isPlaceholder: true })` function that performs read-only static rendering only: it must not access reactive state, register gestures, or register service callbacks. The builder passed in must be wrapped by [wrapBuilder](arkui-ts/ts-universal-wrapBuilder.md#wrapbuilder); a bare builder function is not accepted.
> - The framework validates the constrained builder marker carried in the compilation artifact at registration time: a builder that is not marked with `@Builder({ isPlaceholder: true })` at compile time (including a builder passed in dynamically by bypassing compile-time type checking) is rejected, the ID is not registered, and the system default placeholder is used when the provider of [scrollPlaceholder](arkui-ts/ts-container-list.md#scrollplaceholder) matches this ID.
> - When the same ID is registered repeatedly, the new version of the template is atomically published; a dispatched placeholder task is validated against the template version before it is rendered on screen.

**Since:** 26.1.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 26.1.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type | Mandatory | Description |
| ------- | -------------------- | ---- | ------------------------------------------ |
| id | string | Yes | ID of the placeholder template, by which [PlaceholderProvider](#placeholderprovider) of [scrollPlaceholder](arkui-ts/ts-container-list.md#scrollplaceholder) references the template. |
| builder | [WrappedBuilder](arkui-ts/ts-universal-wrapBuilder.md#wrappedbuilder)\<[]\> | Yes | Global, parameterless placeholder builder wrapped by [wrapBuilder](arkui-ts/ts-universal-wrapBuilder.md#wrapbuilder). A bare builder function is not accepted. |

**Error codes**

For details about the error codes, see [Scrollable Component Error Codes](./errorcode-scroll.md).

| ID | Error Message                                                     |
| -------- | ------------------------------------------------------------ |
| 100031   | Registration rejected: the builder is not marked with @Builder({ isPlaceholder: true }). The ID is not registered. |

**Example**

For the complete example, see [Example 1: Registering a Scrolling Placeholder Template and Setting the Scrolling Placeholder](#example-1-registering-a-scrolling-placeholder-template-and-setting-the-scrolling-placeholder).

### unregister

unregister(id: string): void

Unregisters the placeholder template with the specified ID under the current UI instance.

> **NOTE**
>
> - After the template is unregistered, the ID can no longer be matched: when [PlaceholderProvider](#placeholderprovider) of [scrollPlaceholder](arkui-ts/ts-container-list.md#scrollplaceholder) matches this ID, the system default placeholder is used, and placeholder tasks already dispatched for this template will not be rendered on screen.
> - If the ID to be unregistered has not been registered, the operation is handled silently without raising an exception.

**Since:** 26.1.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 26.1.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type   | Mandatory | Description                             |
| ------ | ------ | ---- | -------------------------------- |
| id     | string | Yes   | ID of the placeholder template to unregister.           |

**Example**

For the complete example, see [Example 1: Registering a Scrolling Placeholder Template and Setting the Scrolling Placeholder](#example-1-registering-a-scrolling-placeholder-template-and-setting-the-scrolling-placeholder).

### isRegistered

isRegistered(id: string): boolean

Queries whether a placeholder template with the specified ID has been registered under the current UI instance.

> **NOTE**
>
> This API is a read-only query. It does not change the registration state or affect subsequent placeholder behavior. The registration state of the template remains unchanged regardless of whether the framework currently retains a pre-built placeholder instance for the template.

**Since:** 26.1.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 26.1.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type   | Mandatory | Description                             |
| ------ | ------ | ---- | -------------------------------- |
| id     | string | Yes   | ID of the placeholder template to query.           |

**Return value**

| Type    | Description                                                    |
| ------- | ------------------------------------------------------- |
| boolean | Whether a placeholder template with the specified ID has been registered under the current UI instance. The value **true** indicates that it is registered, and **false** indicates that it is not. |

**Example**

For the complete example, see [Example 1: Registering a Scrolling Placeholder Template and Setting the Scrolling Placeholder](#example-1-registering-a-scrolling-placeholder-template-and-setting-the-scrolling-placeholder).

## PlaceholderOptions

Describes the placeholder information of a single list item in a scrollable component. When a real list item needs to be created frame by frame, the scrollable component first displays the placeholder component of the item.

**Since:** 26.1.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 26.1.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name   | Type                                       | Read-Only | Optional | Description                                       |
| ------ | ------------------------------------------ | ---- | ---- | ------------------------------------------ |
| id     | string                                     | No   | Yes   | ID of the placeholder template. The registry is obtained through [getPlaceholderRegister()](./arkts-apis-uicontext-uicontext.md#getplaceholderregister) of UIContext, and the placeholder builder is registered through its [register](#register) method.<br/>If it is not set, set to an empty string, or not registered, the system default placeholder is used.<br/>Default value: **undefined** |
| size   | [SizeOptions](arkui-ts/ts-types.md#sizeoptions) | No   | Yes   | Recommended size of the placeholder. It affects only the measurement of the placeholder component, not the layout of the real list item. After the real list item is created, it is laid out again according to the normal layout constraints of the list item. The closer the recommended size is to the size of the real list item, the smaller the visual jump during replacement.<br/>Default value: **undefined**. If it is not set, no recommended size is specified, and the placeholder component is measured according to its own estimated size. |

## PlaceholderProvider

type PlaceholderProvider = (index: number) => PlaceholderOptions | undefined

Provider for the placeholder information of a list item, used by the [scrollPlaceholder](arkui-ts/ts-container-list.md#scrollplaceholder) attribute of [List](arkui-ts/ts-container-list.md). This API is called synchronously during UI thread scrolling and must be only for computation; it must not perform time-consuming operations.

**Since:** 26.1.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 26.1.0.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type   | Mandatory | Description                                       |
| ------ | ------ | ---- | ------------------------------------------ |
| index  | number | Yes   | Index of the list item to create.<br>Value range: [0, +∞).                     |

**Return value**

| Type    | Description                                       |
| ------- | ------------------------------------------ |
| [PlaceholderOptions](#placeholderoptions) \| undefined | Placeholder information of the item. Returning **undefined** indicates that the list item does not require a placeholder, and the system default placeholder is used without interrupting scrolling. |

## Example

### Example 1: Registering a Scrolling Placeholder Template and Setting the Scrolling Placeholder

This example shows how to register a placeholder template through the [register](#register) API, query the registration state through the [isRegistered](#isregistered) API, unregister the placeholder template through the [unregister](#unregister) API when the component is destroyed, and set the placeholder provider through the [scrollPlaceholder](arkui-ts/ts-container-list.md#scrollplaceholder) attribute of [List](arkui-ts/ts-container-list.md): during fast scrolling, list items with an insufficient frame budget first display the registered placeholder template, and the real list items replace the placeholder after frame-by-frame creation is completed, thereby reducing frame drops.

Since API version 26.1.0, the **register**, **unregister**, and **isRegistered** APIs as well as the **PlaceholderOptions** and **PlaceholderProvider** types are added.

<!--code_no_check-->
```ts
// xxx.ets
import { PlaceholderOptions } from '@kit.ArkUI';

// The placeholder template must be a global, parameterless, read-only static rendering constrained builder.
@Builder({ isPlaceholder: true })
function ItemPlaceholder() {
  Column() {
    Text('Loading...')
      .fontSize(16)
      .fontColor(0x999999)
  }
  .width('100%')
  .height(100)
  .justifyContent(FlexAlign.Center)
}

class ListDataSource implements IDataSource {
  private list: number[] = [];

  constructor(list: number[]) {
    this.list = list;
  }

  totalCount(): number {
    return this.list.length;
  }

  getData(index: number): number {
    return this.list[index];
  }

  registerDataChangeListener(listener: DataChangeListener): void {
  }

  unregisterDataChangeListener(listener: DataChangeListener): void {
  }
}

@Entry
@Component
struct PlaceholderRegisterExample {
  private arr: ListDataSource = new ListDataSource([]);

  aboutToAppear() {
    // Obtain the placeholder registry of the current UI instance through UIContext. The registration result is invisible to other UI instances.
    let placeholderRegister = this.getUIContext().getPlaceholderRegister();
    // Query whether the placeholder template with this id is registered. If not registered, register the placeholder template. The builder is passed in after being wrapped by wrapBuilder.
    if (!placeholderRegister.isRegistered('itemPlaceholder')) {
      placeholderRegister.register('itemPlaceholder', wrapBuilder(ItemPlaceholder));
    }
    let list: number[] = [];
    for (let i = 0; i < 100; i++) {
      list.push(i);
    }
    this.arr = new ListDataSource(list);
  }

  aboutToDisappear() {
    this.getUIContext().getPlaceholderRegister().unregister('itemPlaceholder');
  }

  build() {
    Column({ space: 5 }) {
      List({ space: 10 }) {
        LazyForEach(this.arr, (item: number, index: number) => {
          ListItem() {
            Text(item.toString())
              .fontSize(16)
              .width('100%')
              .height(100)
              .textAlign(TextAlign.Center)
          }
        }, (item: number) => item.toString())
      }
      .width('90%')
      .height(300)
      // id corresponds to the registered placeholder template. size indicates the recommended size of the placeholder, consistent with the height of the real list item.
      .scrollPlaceholder((index: number): PlaceholderOptions | undefined => {
        return { id: 'itemPlaceholder', size: { height: 100 } };
      })
    }.width('100%').padding({ top: 10 }).backgroundColor('#FFDCDCDC')
  }
}
```
