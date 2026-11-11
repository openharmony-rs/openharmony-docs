# Class (ComponentUtils)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhou-chaobo-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=3b17ae247298f1cf952b1cbdcb60f1ff0e80beac translatedAt=2026-11-02T12:37:37.470Z pushedAt=2026-11-05T07:11:31.735Z nl=1 -->

Provides the capability of obtaining the coordinates, size, translation, scale, rotation, and affine matrix of the drawing area of a component. It applies to scenarios where the drawing area information of a component needs to be queried, helping you obtain the layout result of the component.

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
> This API must be used after the layout of the target component is complete to obtain the area size information of the target component. It is recommended that you use this API in the [layout callback](./js-apis-arkui-inspector.md). If a component is dynamically created but not mounted to the component tree, the component information after measurement and layout cannot be obtained through this API. This is because the component generally has not been measured and laid out by the UI framework. Ensure that the component has been mounted to the component tree before attempting to obtain the component information.
>
> The component position returned by this API is the layout position. Some attributes are not supported for calculation, such as the position-setting attributes [offset](./arkui-ts/ts-universal-attributes-location.md#offset), [markAnchor](./arkui-ts/ts-universal-attributes-location.md#markanchor), and [position](./arkui-ts/ts-universal-attributes-location.md#position) of the [Edges](./arkui-ts/ts-types.md#edges12) and [LocalizedEdges](./arkui-ts/ts-types.md#localizededges12) types, as well as the graphics transformation attributes [rotate](./arkui-ts/ts-universal-attributes-transformation.md#rotate), [translate](./arkui-ts/ts-universal-attributes-transformation.md#translate), [scale](./arkui-ts/ts-universal-attributes-transformation.md#scale), and [transform](./arkui-ts/ts-universal-attributes-transformation.md#transform). You can use the alternative API [getPositionToWindowWithTransform](./js-apis-arkui-frameNode.md#getpositiontowindowwithtransform12) to obtain the position offset of the component relative to the window with the drawing attributes.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type    | Mandatory  | Description       |
| ---- | ------ | ---- | --------- |
| id   | string | Yes    | Unique ID of the component. Ensure that the component corresponding to this ID has been mounted to the component tree and its layout is complete. |

**Return value**

| Type                                                        | Description                                            |
| ------------------------------------------------------------ | ------------------------------------------------ |
| [componentUtils.ComponentInfo](./js-apis-arkui-componentUtils.md#componentinfo) | Size, position, translation, scale, rotation, and affine matrix information of the component. |

**Error codes**

For details about the error codes, see [API Call Error Codes](./errorcode-internal.md).

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
          let width = componentInfo.size.width; // Obtain the width of the component.
          let height = componentInfo.size.height; // Obtain the height of the component.
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
