# Distributed Migration Identifier
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @wangyang2022-->
<!--Designer: @wangyang2022-->
<!--Tester: @sally__-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=10a20f217ecf0e77e23c0c78c466ce20e1033d43 translatedAt=2026-09-02T12:06:00.186Z -->

The distributed migration identifier of a component is used to identify the component in distributed migration scenarios and restore the component to a specific state on the remote device. It helps users retain the original component position or scrolling state after switching devices, improving the continuity of cross-device use.

>  **NOTE**
>
>  The initial APIs of this module are supported since API version 8. Updates will be marked with a superscript to indicate their earliest API version.

## restoreId

restoreId(value: number): T

Marks the component ID that supports distributed migration. The system matches the corresponding components on both devices through this ID and restores the specific state of the component accordingly. The migration effect and restrictions vary by component: the ScrollBar position of Grid cannot be migrated; for Scroll, the migration effect is affected when the display specifications on the two devices differ or when layout inconsistency is caused by differences in layout parameters; for WaterFlow, the offset of the top FlowItem relative to the main axis of WaterFlow (in vp) is also migrated.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                                                        |
| ------ | ------ | ---- | ------------------------------------------------------------ |
| value  | number | required   | ID of the component that supports distributed migration, used for pairing components on the two devices. The value is an integer, and the specific range is subject to the interface implementation constraints. The IDs of all components that support distributed migration in the same application must be different; otherwise, the components on the two devices may fail to pair correctly, affecting state restoration during distributed migration. |

**Return value**

| Type| Description|
| -------- | -------- |
| T | Current component.|

## Components with Hopping Support

| Name     | Initial API Version| Description                                    |
| --------- | ---- | ---------------------------------------- |
| [List](./ts-container-list.md)      | 8    | Migrates the index value of the ListItem displayed at the top of the current device. After migration, the ListItem corresponding to the index value is displayed at the top of the List on the peer device. |
| [Grid](./ts-container-grid.md)      | 9    | Migrates the index value of the GridItem displayed at the top of the current device. After migration, the GridItem corresponding to the index value is displayed at the top of the Grid on the peer device. The ScrollBar position cannot be migrated. |
| [Scroll](./ts-container-scroll.md)    | 9    | Migrates the absolute distance from the scroll position to the top (in vp). Layout inconsistency caused by different display specifications of the two devices may affect the migration effect. |
| [WaterFlow](./ts-container-waterflow.md) | 11   | Migrates the index value of the FlowItem displayed at the top of the current device. After migration, the FlowItem corresponding to the index value is displayed at the top of the WaterFlow on the peer device. The main-axis offset of the top FlowItem relative to the WaterFlow (in vp) is also migrated. |

## Example

This example demonstrates how to use **restoreId** to set the ID of the **List** component for device matching during hopping.

```ts
// xxx.ets
@Entry
@Component
struct RestoreIdExample {
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
  build() {
    Column() {
      List({ space: 20 }) {
        ForEach(this.arr, (item:number) => {
          ListItem() {
            Text('' + item)
              .width('100%')
              .height(100)
              .fontSize(16)
              .textAlign(TextAlign.Center)
              .borderRadius(10)
              .backgroundColor(Color.Pink)
          }
        }, (item:number) => (item.toString()))
      }
      .restoreId(1);
    }
  }
}
```
