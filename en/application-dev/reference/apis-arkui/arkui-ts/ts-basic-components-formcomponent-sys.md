# FormComponent (System API)
<!--Kit: Form Kit-->
<!--Subsystem: Ability-->
<!--Owner: @Qian-Win-->
<!--Designer: @cx983299475-->
<!--Tester: @mahailong123456-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=92cb4d2f8dca1d59bddc5aa0581a2b5f1a4d54e4 translatedAt=2026-09-03T03:56:41.282Z -->

Provides the card component to display cards.

>  **NOTE**
>
> - This component is supported since API version 7. Updates will be marked with a superscript to indicate their earliest API version.
>
> - This component is the user of the card component. For details about the corresponding provider, see [JS Service Widget UI Component](../js-service-widget-ui/js-service-widget-file.md).
>
> - This component requires a system signature.
>
> - This module is a system API.

## Permissions

ohos.permission.REQUIRE_FORM, ohos.permission.GET_BUNDLE_INFO_PRIVILEGED


## Child Components

None


## API

## FormComponent (value: FormInfo)

Creates a FormComponent to display the provided card.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type                        | Mandatory | Description                                                                |
| --------- | ------------------------------- | ---- | ----------------------------------------------------------------------- |
| value        | [FormInfo](#forminfo12)                 | Yes   | Card information.   |

## FormInfo<sup>12+</sup>

Card information.

> **NOTE**
>
> - The temporary parameter indicates whether the card is a temporary card. For details about the comparison between temporary cards and normal cards, see [Temporary and Normal Widgets](../../../form/widget-host-development-guide-sys.md#temporary-and-normal-widgets).

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Type                        | Read-Only | Optional | Description                                                                |
| --------- | ------------------------------- | ---- |---- |-------|
| id        | number \| string                    | No   | No   | Card ID (set to 0 for a new card).<br/>**Note:**<br>Different users cannot use the same ID.<br/>When the same user uses the same ID, the card added later is displayed.<br>The ID is greater than or equal to 0 and less than 2^32.                                        |
| name      | string                          |  No   | No   | Card name.                                                              |
| bundle    | string                          |  No   | No   | Bundle name of the target card.                                                          |
| ability   | string                          |  No   | No   | Name of the target card ability.                                                   |
| module    | string                          |  No   | No   | Module name of the card.                                                          |
| dimension | [FormDimension](#formdimension) |  No   | Yes   | Card size. Cards of 2 x 2, 4 x 4, and 2 x 4 are supported.<br/>Default value: **Dimension_2_2**. |
| temporary | boolean                         |  No   | Yes   | Whether the card is a temporary card. The value **true** indicates a temporary card, and **false** indicates a normal card.<br/>Default value: **false**. |
| renderingMode | [FormRenderingMode](#formrenderingmode11) |  No   | Yes   | Rendering mode of the card. The value can be one of the following, and the default value is **FULL_COLOR**.<br>- **FULL_COLOR**: full-color mode. The card framework does not modify the card effect, which remains the same as that set by the card developer.<br>- **SINGLE_COLOR**: single-color mode. The card framework sets the card background to transparent. Developers need to set the card style based on best practices.<br>**Note:**<br>If the system does not support the unified rendering mode, the card framework does not set the card background to transparent even in single-color mode. |
| want | [import('../api/@ohos.app.ability.Want').default](../../../reference/apis-ability-kit/js-apis-app-ability-want.md#want) |  No   | Yes   | Carrier for the information transferred by the card. |
| shape  | [FormShape](#formshape12)      | No    | Yes    | Shape of the card. |
| exemptAppLock<sup>20+</sup> |boolean        |  No   | Yes   | Whether the card is exempt from the app lock. The value **true** indicates that when the app to which the card belongs has an app lock, the card is not controlled by the app lock and no app lock mask is displayed. The value **false** indicates that when the app to which the card belongs has an app lock, the card is controlled by the app lock and the app lock mask is displayed normally.<br/>Default value: **false**. |

## FormCallbackInfo<sup>12+</sup>

Parameter for obtaining the formId when a card is queried or uninstalled.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Type                        | Read-Only | Optional | Description              |
| --------- | ------------------------------- | ---- | ---- | ----------------- |
| id        | number                 |   No   |  No   | Card ID.<br/>**Note:**<br/>If the obtained id is -1, the id is greater than or equal to 2^53, and idString must be used to obtain it.                                        |
| idString      | string            |   No   |   No   | Card ID.                             |
| isLocked<sup>22+</sup>      | boolean             |   No   |   No   | Whether the card is locked. The value true indicates that the card is locked, and false indicates that the card is not locked.|

## FormSize<sup>18+</sup>

Card size information.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Type                        | Read-Only | Optional | Description    |
| --------- | ------------------------------- | ---- | ---- |---------|
| width        | number                 | No   | No   | Width of the card, in vp.<br/>**Note:**<br>The value range of width is greater than 0 and less than 2^53. If the value is out of range, the card is not displayed. |
| height      | number            | No   | No   | Height of the card, in vp.<br/>**Note:**<br>The value range of height is greater than 0 and less than 2^53. If the value is out of range, the card is not displayed. |

## ErrorInformation<sup>18+</sup>

Card error information.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Type                        | Read-Only | Optional | Description                     |
| --------- | ------------------------------- | ---- | ---- | ------------------------------ |
| errcode        | number                 | No  | No   | [Error code](../../apis-form-kit/errorcode-form.md).                                        |
| msg      | string            | No       | No   | Error message.                             |

## FormDimension

Enumerates the card sizes.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name                       | Value     | Description     |
| -------------------------- | -------- | -------- |
| Dimension_1_2              | 0 | 1*2 card |
| Dimension_2_2              | 1 | 2*2 card |
| Dimension_2_4              | 2 | 2*4 card |
| Dimension_4_4              | 3 | 4*4 card |
| Dimension_2_1<sup>(deprecated)</sup> | 4 | 2*1 card <br>**Note:** This field is supported since API version 9 and deprecated since API version 20.|
| Dimension_1_1<sup>11+</sup> | 6 | 1*1 card |
| Dimension_6_4<sup>12+</sup> | 7 | 6*4 card |
| Dimension_2_3<sup>18+</sup> | 8 | 2*3 card for wearable devices |
| Dimension_3_3<sup>18+</sup> | 9 | 3*3 card for wearable devices |

## FormRenderingMode<sup>11+</sup>

Enumerates the card rendering modes.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name                       | Value     | Description     |
| -------------------------- | -------- | -------- |
| FULL_COLOR                 | 0 | Full color mode. |
| SINGLE_COLOR               | 1 | Single color mode. |

## FormColorMode<sup>23+</sup>

Enumerates the color modes of the card.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

| Name                       | Value     | Description      |
| -------------------------- | -------- | -------- |
| MODE_AUTO                  | -1 | Follows the system.|
| MODE_DARK                  | 0 | Dark mode.|
| MODE_LIGHT                 | 1 | Light mode.|

## FormShape<sup>12+</sup>

Enumerates the card shapes.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name                       | Value     | Description      |
| -------------------------- | -------- | -------- |
| RECT                  | 1 | Rectangular card.|
| CIRCLE                  | 2 | Circular card.|

## Attributes

### size<sup>18+</sup>

size(formSize: FormSize)

Sets the width and height.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters** 

| Name | Type                                                      | Mandatory | Description       |
| ------ | --------------------------------------------------------- | ---- | ---------- |
| formSize  | [FormSize](#formsize18) | Yes   | Width and height. |

### moduleName

moduleName(value: string)

Sets the card module name.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters** 

| Name | Type   | Mandatory | Description           |
| ------ | ------ | ---- | -------------- |
| value  | string | Yes   | Card module name. |

### dimension

dimension(value: FormDimension)

Sets the card size, supporting cards of types such as 2 * 2, 4 * 4, and 2 * 4.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters** 

| Name | Type                            | Mandatory | Description                                 |
| ------ | ------------------------------- | ---- | ------------------------------------ |
| value  | [FormDimension](#formdimension) | Yes   | Card size.<br/>Default value: Dimension_2_2. |

### allowUpdate

allowUpdate(value: boolean)

Sets whether to allow card updates.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters** 

| Name | Type    | Mandatory | Description                                |
| ------ | ------- | ---- | ----------------------------------- |
| value  | boolean | Yes  | Whether to allow card updates. The value **true** means to allow card updates, and **false** means the opposite.<br/>Default value: **true**. |

### visibility

visibility(value: Visibility)

Sets whether to allow the card to be visible.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters** 

| Name | Type                                          | Mandatory | Description                                   |
| ------ | --------------------------------------------- | ---- | -------------------------------------- |
| value  | [Visibility](ts-appendix-enums.md#visibility) | Yes   | Whether to allow the card to be visible.<br/>Default value: **Visible** |

### colorMode<sup>23+</sup>

colorMode(value: FormColorMode)

Sets the card color mode.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Model restriction**: This API can be used only in the stage model.

**Parameters** 

| Name | Type                                          | Mandatory | Description                                   |
| ------ | --------------------------------------------- | ---- | -------------------------------------- |
| value  | [FormColorMode](#formcolormode23) | Yes   | Card color mode. |

## Events

### onAcquired

onAcquired(callback:&nbsp;Callback<[FormCallbackInfo](#formcallbackinfo12)>)&nbsp;

Called when the card is acquired.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters** 

| Name | Type                                | Mandatory | Description       |
| ------ | ----------------------------------- | ---- | ---------- |
| callback | Callback<[FormCallbackInfo](#formcallbackinfo12)> | Yes   | Callback function used to obtain the FormCallbackInfo object. |

### onError<sup>18+</sup>

onError(callback: Callback\<ErrorInformation\>)

Callback invoked when the card fails to load.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters** 

| Name | Type                                                         | Mandatory | Description                                            |
| ------ | ------------------------------------------------------------ | ---- | ----------------------------------------------- |
| callback   | Callback<[ErrorInformation](#errorinformation18)> | Yes   | errcode:&nbsp;Error code.<br/>msg:&nbsp;Error message. |

### onRouter<sup>18+</sup>

onRouter(callback: Callback\<object\>)

Callback for the card click event.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters** 

| Name  | Type | Mandatory | Description                                                         |
|------| - | ---- | ------------------------------------------------------------ |
| callback | Callback\<object\>  | Yes   | Obtains the [routerEvent](../js-service-widget-ui/js-service-widget-syntax-hml.md#event-binding) object. |

### onUninstall

onUninstall(callback:&nbsp;Callback<[FormCallbackInfo](#formcallbackinfo12)>)&nbsp;

Card uninstall callback.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters** 

| Name      | Type                                | Mandatory | Description       |
|----------| ----------------------------------- | ---- | ---------- |
| callback | Callback<[FormCallbackInfo](#formcallbackinfo12)> | Yes   | Callback function used to obtain the FormCallbackInfo object. |

### onLoad<sup>18+</sup>

onLoad(callback: VoidCallback)

Callback for the card loading event.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name      | Type                                | Mandatory | Description       |
|----------| ----------------------------------- | ---- | ---------- |
| callback | [VoidCallback](ts-types.md#voidcallback12) | Yes   | No return value. |

### onUpdate<sup>18+</sup>

onUpdate(callback:&nbsp;Callback<[FormCallbackInfo](#formcallbackinfo12)>)&nbsp;

Callback invoked when the card content is updated.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name      | Type                                | Mandatory | Description       |
|----------| ----------------------------------- | ---- | ---------- |
| callback | Callback<[FormCallbackInfo](#formcallbackinfo12)> | Yes   | Callback function used to obtain the FormCallbackInfo object. |

## Example

Card example.

This example creates a 2 x 2 card and registers the event callback.
```ts
// card.ets
@Entry
@Component
struct CardExample {
  @State formId:string = '0';
  build() {
    Column() {
      Text('this is a card')
        .fontSize(50)
        .fontWeight(FontWeight.Bold)
      FormComponent({
        id:this.formId,
        name:"Form1",
        bundle:"com.example.cardexample",
        ability:"FormAbility",
        module:"entry",
        dimension:FormDimension.Dimension_2_2,
        temporary:false
      })
        .allowUpdate(true)
        .size({width:360,height:360})
        .visibility(Visibility.Visible)
        .onAcquired((form: FormCallbackInfo)=>{
          console.info(`form info : ${form?.id}`);
          // Invalid form id
          if (form.id == -1) {
            this.formId = form.idString;
          } else {
            this.formId = form.id.toString();
          }
        })
        .onError((error)=>{
          console.error(`fail to add form, error code: ${error?.errcode}, error message: ${error?.msg}`);
        })
        .onUninstall((form: FormCallbackInfo)=>{
          console.info(`uninstall form success : ${form?.id}`);
          // Invalid form id
          if (form.id == -1) {
            this.formId = form.idString;
          } else {
            this.formId = form.id.toString();
          }
        })
        .onUpdate((form: FormCallbackInfo)=>{
          console.info(`form update done : ${form?.id}`);
        })
    }
    .width('100%')
    .height('100%')
  }
}
```

![Form](figures/form.png)