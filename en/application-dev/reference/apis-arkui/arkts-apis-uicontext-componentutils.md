# Class (ComponentUtils)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->

Provides the capability to obtain attribute information of a component's drawing area, including coordinates, size, translation, scaling, rotation, and affine matrix. This is suitable for scenarios where you need to query component drawing area information, helping you access component layout results.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 10.
>
> - The APIs of this module can be used only in the stage model.
>
> - In the following API examples, you must first use [getComponentUtils()](./arkts-apis-uicontext-uicontext.md#getcomponentutils) in **UIContext** to obtain a **ComponentUtils** instance, and then call the APIs using the obtained instance.

## getRectangleById

getRectangleById(id: string): componentUtils.ComponentInfo

Obtains the size, position, translation, scaling, rotation, and affine matrix information of the specified component.

> **NOTE**
>
> This API should be called after the target component layout is complete to obtain its area size information. It is recommended to use this API in the [layout callback](./js-apis-arkui-inspector.md). If a component is dynamically created but not yet attached to the component tree, its measurement and layout information cannot be accessed through this API since this component has not undergone measurement and layout by the UI framework. Ensure the component is attached to the component tree before attempting to retrieve component information.
>
> The component position returned by this API is the layout position. Some property calculations are not supported, such as position-setting properties like [offset](./arkui-ts/ts-universal-attributes-location.md#offset), [markAnchor](./arkui-ts/ts-universal-attributes-location.md#markanchor), [Edges](./arkui-ts/ts-types.md#edges12), [position](./arkui-ts/ts-universal-attributes-location.md#position) of the [LocalizedEdges](./arkui-ts/ts-types.md#localizededges12) type, and graphics transformation properties like [rotate](./arkui-ts/ts-universal-attributes-transformation.md#rotate), [translate](./arkui-ts/ts-universal-attributes-transformation.md#translate), [scale](./arkui-ts/ts-universal-attributes-transformation.md#scale), and [transform](./arkui-ts/ts-universal-attributes-transformation.md#transform). For an alternative, you can use [getPositionToWindowWithTransform](./js-apis-arkui-frameNode.md#getpositiontowindowwithtransform12) to obtain the component's position offset relative to the window, including drawing attributes.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type    | Mandatory  | Description       |
| ---- | ------ | ---- | --------- |
| id   | string | Yes   | Unique ID of a component. Ensure that the component corresponding to the ID has been mounted to the component tree and the layout has been completed.|

**Return value**

| Type                                                        | Description                                            |
| ------------------------------------------------------------ | ------------------------------------------------ |
| [componentUtils.ComponentInfo](./js-apis-arkui-componentUtils.md#componentinfo) | **ComponentInfo** object, which provides the size, position, translation, scaling, rotation, and affine matrix information of the component.|

**Error codes**

For details about the error codes, see [API Call Error Codes](errorcode-internal.md).

| ID | Error Message               |
| ------ | ------------------- |
| 100001 | UI execution context not found. |

**Example**

<!--code_no_check-->
```ts
import { ComponentUtils } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

  build() {
    RelativeContainer() {
      Text(this.message)
        .id('HelloWorld')
        .fontSize($r('app.float.page_text_font_size'))
        .fontWeight(FontWeight.Bold)
        .alignRules({
          center: { anchor: '__container__', align: VerticalAlign.Center },
          middle: { anchor: '__container__', align: HorizontalAlign.Center }
        })
        .onClick(() => {
          this.message = 'Welcome';
          let componentUtils: ComponentUtils = this.getUIContext().getComponentUtils();
          let componentInfo = componentUtils.getRectangleById("HelloWorld");
          let width = componentInfo.size.width; // Obtain the component width.
          let height = componentInfo.size.height; // Obtain the component height.
          let localOffsetX = componentInfo.localOffset.x; // Obtain the x-axis offset of the component relative to its parent component.
          let localOffsetY = componentInfo.localOffset.y; // Obtain the y-axis offset of the component relative to its parent component.
          console.info(`width: ${width}, height: ${height}, localOffsetX: ${localOffsetX}, localOffsetY: ${localOffsetY}`);
        })
    }
    .height('100%')
    .width('100%')
  }
}
```
