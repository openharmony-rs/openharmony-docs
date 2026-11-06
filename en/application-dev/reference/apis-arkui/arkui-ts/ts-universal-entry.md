# @Entry: Page Entry Declaration

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiyujia926-->
<!--Designer: @s10021109-->
<!--Tester: @TerryTsao-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=9689435a9fceea46345907d3b6295f9ad081616f translatedAt=2026-09-02T12:22:23.686Z -->

A custom component decorated by @Entry serves as the entry to a UI page and is identified by the framework as the root component of the page. It is suitable for building standalone UI pages.

> **NOTE**
>
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## @Entry

In a single UI page, only one custom component decorated by @Entry is allowed as the page entry.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Example**

```ts
// The custom component decorated by @Entry serves as the entry of the UI page.
@Entry
@Component
struct Index {
  build() {
    Text('@Entry Test')
  }
}
```

## EntryOptions<sup>10+</sup>

Page entry configuration options, used to configure parameters such as the route name, state storage, and shared storage when decorating a page with @Entry.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name                        | Type                                                        | Read-Only| Optional| Description                                                        |
| ------------------------------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| routeName                      | string                                                       | No  | Yes | Name of the page as a named route. When the page needs to be navigated to through a named route, set this parameter as the route name. If this parameter is not passed, the page is not registered as a named route page and cannot be accessed through named route navigation; it is loaded only as the default entry page.<br>**Card capability:** Since API version 10, this API is supported in ArkTS widgets.<br>**Atomic service API:** Since API version 11, this API is supported in atomic services. |
| storage                        | [LocalStorage](../../../ui/state-management/arkts-localstorage.md) | No | Yes  | Page-level UI state storage. Pass this parameter when you need to create and manage UI state outside the page in advance, or when you need to bind an existing LocalStorage instance to this page for state sharing. If this parameter is not passed, the framework creates a new LocalStorage instance as the default value. When useSharedStorage is set to true and storage is assigned, the value of useSharedStorage takes precedence.<br>**Card capability:** Since API version 10, this API is supported in ArkTS widgets.<br>**Atomic service API:** Since API version 11, this API is supported in atomic services. |
| useSharedStorage<sup>12+</sup> | boolean                                                      | No  | Yes | Whether to use the LocalStorage instance passed in by [loadContent](../arkts-apis-window-WindowStage.md#loadcontent9). The default value is false. true: uses the shared LocalStorage instance (prerequisite: ensure that the loadContent API has passed in a LocalStorage instance; if not, a new LocalStorage instance is created). false: does not use the shared LocalStorage instance. When useSharedStorage is set to true and storage is assigned, the value of useSharedStorage takes precedence.<br>**Card capability:** Since API version 12, this API is supported in ArkTS widgets.<br>**Atomic service API:** Since API version 12, this API is supported in atomic services. |

**Example**

```ts
// Set the route page name to myPage.
@Entry({ routeName: 'myPage' })
@Component
struct Index {
  build() {
    Text('Index')
  }
}
```

