# @ohos.arkui.componentUtils (componentUtils)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->

The **componentUtils** module provides API for obtaining the coordinates and size of the drawing area of a component.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The functionality of this module depends on UI context. This means that the APIs of this module cannot be used where [the UI context is ambiguous](../../ui/arkts-global-interface.md#ambiguous-ui-context). For details, see [UIContext](arkts-apis-uicontext-uicontext.md).

## Modules to Import

```ts
import { componentUtils } from '@kit.ArkUI';
```
## componentUtils.getRectangleById<sup>(deprecated)</sup>

getRectangleById(id: string): ComponentInfo

Obtains a **ComponentInfo** object based on the component ID and synchronously returns the geometric properties of the component.

> **NOTE**
>
> - This API is supported since API version 10 and deprecated since API version 18. You are advised to use [getRectangleById](arkts-apis-uicontext-componentutils.md#getrectanglebyid) instead. Before calling this API, you need to obtain the [ComponentUtils](arkts-apis-uicontext-componentutils.md) object using the [getComponentUtils](arkts-apis-uicontext-uicontext.md#getcomponentutils) method in [UIContext](arkts-apis-uicontext-uicontext.md).
>
> - Since API version 10, you can use the [getComponentUtils](arkts-apis-uicontext-uicontext.md#getcomponentutils) API in [UIContext](arkts-apis-uicontext-uicontext.md) to obtain the [ComponentUtils](arkts-apis-uicontext-componentutils.md) object associated with the current UI context. This API provides access to component coordinates and size information after the target component completes layout. It is recommended that you invoke this API within [layout completion callbacks](./js-apis-arkui-inspector.md). Note that dynamically created components must be mounted to the component tree before this API can obtain their information, as unmounted components are not measured or laid out by the UI framework. Always ensure that component mounting precedes information retrieval attempts.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description      |
| ------ | ------ | ---- | ---------- |
| id     | string | Yes  | Component ID.|

**Return value**

| Type  | Description      |
| ------ | ---------- |
| [ComponentInfo](#componentinfo) | **ComponentInfo** object, which provides the size, position, translation, scaling, rotation, and affine matrix information of the component.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID | Error Message               |
| ------ | ------------------- |
| 100001 | UI execution context not found. |

**Example**

```ts
import { componentUtils } from '@kit.ArkUI';
let modePosition:componentUtils.ComponentInfo = componentUtils.getRectangleById("onClick");
```

## ComponentInfo

Implements a **ComponentInfo** object, which provides the size, position, translation, scaling, rotation, and affine matrix information of the component.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name          | Type            | Read-Only   | Optional          | Description                        |
| ---------------|------------| --------------- | -----------------------------| -----------------------------|
| size           | [Size](#size) | No      | No    | Component size.                   |
| localOffset    | [Offset](#offset) | No      | No   | Offset of the component relative to the parent component.        |
| windowOffset   | [Offset](#offset) | No      | No   | Offset of the component relative to the window.          |
| screenOffset   | [Offset](#offset) | No      | No   | Offset of the component relative to the screen.          |
| translate      | [TranslateResult](#translateresult)| No      | No    | Translation of the component.               |
| scale          | [ScaleResult](#scaleresult) | No      | No    | Scaling of the component.               |
| rotate         | [RotateResult](#rotateresult) | No      | No    | Rotation of the component.               |
| transform      | [Matrix4Result](#matrix4result) | No      | No    | Affine matrix of the component, which is a 4x4 matrix object created based on the input parameter. |

### Size 

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Type | Read-Only   | Optional   | Description                              |
| -------- | ---- | -------------------------| ------------------------| ----------------------------------|
| width    | number | No      | No    | Component width.<br>Unit: px                     |
| height   | number | No      | No    | Component height.<br>Unit: px                     |

### Offset

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Type | Read-Only   | Optional    | Description                              |
| --------| ---- | --------------| ------------------------------------| -----------------------------------|
| x       | number| No      | No    | X-coordinate.<br>Unit: px                          |
| y       | number| No      | No    | Y-coordinate.<br>Unit: px                          |

### TranslateResult

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Type| Read-Only   | Optional    | Description                              |
| --------| ---- | -------------------| -------------------------------| -----------------------------------|
| x       | number | No      | No   | Translation distance along the x-axis.<br>Unit: px                      |
| y       | number | No      | No   | Translation distance along the y-axis.<br>Unit: px                      |
| z       | number | No      | No    | Translation distance along the z-axis.<br>Unit: px                      |

### ScaleResult

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Type| Read-Only   | Optional  | Description                              |
| --------| ---- | ---- |-----------------------------------| -----------------------------------|
| x       | number | No      | No| Scale factor along the x-axis.<br>Unit: px                      |
| y       | number | No      | No | Scale factor along the y-axis.<br>Unit: px                      |
| z       | number | No      | No| Scale factor along the z-axis.<br>Unit: px                      |
| centerX | number | No      | No| X-coordinate of the center point.<br>Unit: px                 |
| centerY | number | No      | No | Y-coordinate of the center point.<br>Unit: px               |

### RotateResult

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Type | Read-Only   | Optional    | Description                              |
| --------| ---- | -----------------| ---------------------------------| -----------------------------------|
| x       | number | No      | No | X-coordinate of the rotation vector.<br>Unit: px                  |
| y       | number | No      | No | Y-coordinate of the rotation vector.<br>Unit: px                  |
| z       | number | No      | No | Z coordinate of the rotation vector.<br>Unit: px                  |
| angle   | number | No      | No | Rotation angle.<br>Unit: px                         |
| centerX | number | No      | No | X-coordinate of the center point.<br>Unit: px                |
| centerY | number | No      | No | Y-coordinate of the center point.<br>Unit: px                |

### Matrix4Result

type Matrix4Result = [number,number,number,number,number,number,number,number,number,number,number,number,number,number,number,number]

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Type| Description                              |
| --------| -----------------------------------|
| [number,number,number,number,<br>number,number,number,number,<br>number,number,number,number,<br>number,number,number,number] | A number array whose length is 16 (4 x 4). For details, see **4 x 4 matrix description**.<br>Unit: px |

**4 x 4 matrix description**

| Name| Type  | Mandatory| Description                                |
| ------ | ------ | ---- | ------------------------------------ |
| m00    | number | Yes  | Scale factor along the x-axis. Defaults to **1** for the identity matrix.        |
| m01    | number | Yes  | The second value, which is affected by the rotation of the x, y, and z axes.    |
| m02    | number | Yes  | The third value, which is affected by the rotation of the x, y, and z axes.    |
| m03    | number | Yes  | Meaningless value.                        |
| m10    | number | Yes  | The fifth value, which is affected by the rotation of the x, y, and z axes.    |
| m11    | number | Yes  | Scale factor along the y-axis. Defaults to **1** for the identity matrix.        |
| m12    | number | Yes  | The seventh value, which is affected by the rotation of the x, y, and z axes.    |
| m13    | number | Yes  | Meaningless value.                        |
| m20    | number | Yes  | The ninth value, which is affected by the rotation of the x, y, and z axes.    |
| m21    | number | Yes  | The tenth value, which is affected by the rotation of the x, y, and z axes.   |
| m22    | number | Yes  | Scale factor along the z-axis. Defaults to **1** for the identity matrix.        |
| m23    | number | Yes  | Meaningless value.                        |
| m30    | number | Yes  | Translation value of the x-axis, in px. The default value is **0** for the identity matrix.|
| m31    | number | Yes  | Translation value of the y-axis, in px. The default value is **0** for the identity matrix.|
| m32    | number | Yes  | Translation value of the z-axis, in px. The default value is **0** for the identity matrix.|
| m33    | number | Yes  | Valid in homogeneous coordinates, presenting the perspective projection effect.  |

**Example**

> **NOTE**
>
> You are advised to use [getComponentUtils](./arkts-apis-uicontext-uicontext.md#getcomponentutils) to obtain the **ComponentUtils** object associated with the current UI context.

```ts
import { matrix4, componentUtils } from '@kit.ArkUI';

@Entry
@Component
struct Utils {
  @State x: number = 120;
  @State y: number = 10;
  @State z: number = 100;
  @State value: string = '';
  private matrix1 = matrix4.identity().translate({ x: this.x, y: this.y, z: this.z });

  build() {
    Column() {
      // Replace $r("app.media.img") with the image resource file you use.
      Image($r("app.media.img"))
        .transform(this.matrix1)
        .translate({ x: 20, y: 20, z: 20 })
        .scale({ x: 0.5, y: 0.5, z: 1 })
        .rotate({
          x: 1,
          y: 1,
          z: 1,
          centerX: '50%',
          centerY: '50%',
          angle: 300
        })
        .width(300)
        .height(100)
        .key("image_01")
      Button('getRectangleById')
      .onClick(() => {
        this.value = JSON.stringify(this.getUIContext().getComponentUtils().getRectangleById("image_01")) // You are advised to use this.getUIContext().getComponentUtils().
      }).margin(10).id('onClick')
      Text(this.value)
        .margin(20)
        .width(300)
        .height(300)
        .borderWidth(2)
    }.margin({left: 50})
  }
}
```

![componentget](figures/getRectangleById.gif) 
