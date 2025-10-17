# Custom Property
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @xiang-shouxing-->
<!--Designer: @xiang-shouxing-->
<!--Tester: @sally__-->
<!--Adviser: @HelloCrease-->

You can set custom properties on components. These custom properties can be obtained on their corresponding FrameNodes, allowing for more flexible component management.

>  **NOTE**
>
>  The initial APIs of this module are supported since API version 12. Updates will be marked with a superscript to indicate their earliest API version.

## customProperty

customProperty(name: string, value: Optional\<Object>): T

Sets a custom property for this component. This API does not work for [custom components](../../../ui/state-management/arkts-create-custom-components.md).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                | Mandatory| Description                                                        |
| ------ | ---------------------------------------------------- | ---- | ------------------------------------------------------------ |
| name  | string | Yes  | Name of the custom property.|
| value  | [Optional](#optionalt12)\<Object> | Yes  | Value of the custom property.|

**Return value**

| Type| Description|
| --- | --- |
| T | Current component.|


## Optional\<T><sup>12+</sup>

type Optional\<T> = T | undefined

Defines the Optional type. The value can be **undefined**.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

| Type| Description                      |
| ---- | -------------------------- |
| T \| undefined | Defines the Optional type. The value can be **undefined**.|

## Example

This example shows how to set custom properties on the [Column](ts-container-column.md) component and obtain the set custom properties from its corresponding [FrameNode](../js-apis-arkui-frameNode.md#framenode-1).

```ts
// xxx.ets
import { FrameNode, UIContext } from '@kit.ArkUI';

@Entry
@Component
struct CustomPropertyExample {
  build() {
    Column() {
      Text('text')
      Button('print').onClick(() => {
        // Obtain the frameNode corresponding to the Column and query the set custom properties.
        const uiContext: UIContext = this.getUIContext();
        if (uiContext) {
          const node: FrameNode | null = uiContext.getFrameNodeById("Test_Column") || null;
          if (node) {
            for (let i = 1; i < 4; i++) {
              const key = 'customProperty' + i;
              const property = node.getCustomProperty(key);
              console.info(key, JSON.stringify(property));
            }
          }
        }
      })
    }
    .id('Test_Column')
    // Set custom properties for the Column component.
    .customProperty('customProperty1', {
      'number': 10,
      'string': 'this is a string',
      'bool': true,
      'object': {
        'name': 'name',
        'value': 100
      }
    })
    .customProperty('customProperty2', {})
    .customProperty('customProperty3', undefined)
    .width('100%')
    .height('100%')
  }
}
```
