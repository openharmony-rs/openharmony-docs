# @ohos.app.form.formInfo (formInfo) (System API)
<!--Kit: Form Kit-->
<!--Subsystem: Ability-->
<!--Owner: @cx983299475-->
<!--Designer: @xueyulong-->
<!--Tester: @yangyuecheng-->
<!--Adviser: @HelloShuo-->

The **formInfo** module provides types and enums related to the widget information and state.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - This topic describes only system APIs provided by the module. For details about its public APIs, see [@ohos.app.form.formInfo (formInfo)](./js-apis-app-form-formInfo.md).

## Modules to Import

```ts
import { formInfo } from '@kit.FormKit';
```

## FormInfo

Defines the widget information.

**System capability**: SystemCapability.Ability.Form

| Name       | Type                | Read-Only   | Optional   | Description                                                        |
| ----------- | -------- | -------- | -------------------- | ------------------------------------------------------------ |
| previewImages<sup>18+</sup> | Array&lt;number&gt; | Yes| Yes| Resource IDs of the preview images of the widget.<br>**Atomic service API**: This API can be used in atomic services since API version 18.|
| enableBlurBackground<sup>18+</sup>  | boolean               | Yes   | Yes    | Whether the widget uses a blur background.<br>- **true**: A blur background is enabled.<br>- **false**: A blur background is disabled.|
| renderingMode<sup>18+</sup>|[RenderingMode](./js-apis-app-form-formInfo-sys.md#renderingmode18)|Yes|Yes|Widget rendering mode.|
| resizable<sup>20+</sup> | boolean  | Yes   | Yes    | Whether the widget can be resized by dragging. The value must be in the **supportDimensions** configuration list of the widget or the widget with the same **groupId**.<br>- **true**: The widget can be resized.<br>- **false**: The widget cannot be resized.|
| groupId<sup>20+</sup> | string     | Yes   | Yes    | Common ID of a group of widgets. If the values of **groupId** of multiple widgets are the same and the value of **resizable** is **true**, the **supportDimensions** configuration of multiple widgets is shared. For example, if the **groupId** values of widgets A and B are the same and the **resizable** values are **true**, widget A can be adjusted to any size specified by **supportDimensions**.<br>It is recommended that this field be set when multiple widgets with the same functionality need to be resized.|


##  FormParam

Enumerates the widget parameters.

**System capability**: SystemCapability.Ability.Form

| Name       | Value  | Description        |
| ----------- | ---- | ------------ |
| DEVICE_ID_KEY    | 'ohos.extra.param.key.device_id'   | Device ID.<br>**System API**: This is a system API. |
| THEME_KEY    | 'ohos.extra.param.key.form_is_theme'   | Theme ID.<br>**System API**: This is a system API. |

## FormUsageState<sup>11+</sup>

Enumerates the usage statuses of widgets.

**System capability**: SystemCapability.Ability.Form

**System API**: This is a system API.

| Name       |  Value  | Description        |
| ----------- | ---- | ------------ |
| USED | 0   | The widget is in use.|
| UNUSED | 1   | The widget is not in use.|

## RunningFormInfo<sup>10+</sup>

Defines the information about an added widget, which can be either in use or not.

**System capability**: SystemCapability.Ability.Form

**System API**: This is a system API.

| Name       | Type                | Read-Only   | Optional   | Description                                                        |
| ----------- | -------- | -------- | -------------------- | ------------------------------------------------------------ |
| hostBundleName  | string               | Yes   | No    | Name of the bundle to which the widget host belongs.                  |
| visibilityType  | [VisibilityType](js-apis-app-form-formInfo.md#visibilitytype)               | Yes   | No    | Visibility types of the widget.                  |
| formUsageState<sup>11+</sup> | [FormUsageState](#formusagestate11)         | Yes   | No    | Usage status of the widget. The default value is **FormUsageState.USED**.|
| formDescription<sup>11+</sup> | string         | Yes   | No    | Description in the widget configuration file of the provider.  |
| extraData<sup>12+</sup> | Record<string, Object> | Yes   | Yes    | Extra widget data.  |

## formProviderFilter<sup>10+</sup>

Defines the information about the widget provider.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Ability.Form

**System API**: This is a system API.

| Name       | Type                | Read-Only   | Optional   | Description                                                        |
| ----------- | -------- | -------- | -------------------- | ------------------------------------------------------------ |
| bundleName  | string               | No   | No    | Name of the bundle to which the widget provider belongs. |
| formName    | string               | No   | Yes    | Widget name.                    |
| moduleName  | string               | No   | Yes    | Name of the module to which the widget belongs.       |
| abilityName | string               | No   | Yes    | Name of the ability to which the widget belongs.       |
| isUnusedIncluded<sup>11+</sup> | boolean               | No   | Yes    | Whether an unused widget is included.<br>- **true**: An unused widget is included.<br>- **false** (default): There is no unused widget.<br>        |


## FormInfoFilter

Defines the widget information filter. Only the widget information that meets the filter is returned.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.Ability.Form

| Name       | Type  | Mandatory        |Description        |
| ----------- | ---- | ------------ |------------ |
| bundleName<sup>12+</sup>    | string    |No   | Only the widget information in which **bundleName** is the same as the provided value is returned. If this parameter is left unspecified, the widget information is not filtered by **bundleName**.<br>**System API**: This is a system API. |
| supportedDimensions<sup>12+</sup> | Array\<number\> |No   | Only the widget information in which **supportedDimensions** is the same as the provided value is returned. If this parameter is left unspecified, the widget information is not filtered by **supportedDimensions**.<br>**System API**: This is a system API. |
| supportedShapes<sup>12+</sup>  | Array\<number\> |No   | Only the widget information in which **supportedShapes** is the same as the provided value is returned. If this parameter is left unspecified, the widget information is not filtered by **supportedShapes**.<br>**System API**: This is a system API.  |

## FormLocation<sup>12+</sup>

Enumerates the widget locations.

**System capability**: SystemCapability.Ability.Form

| Name                        | Value  | Description                            |
| ---------------------------- | ---- | -------------------------------- |
| OTHER                        | -1   | The widget is not located in any of the following defined positions.          |
| DESKTOP                      | 0    | The widget is located on the home screen.<br>**Atomic service API**: This API can be used in atomic services since API version 20.              |
| FORM_CENTER                  | 1    | The widget is located in the widget center of the home screen.<br>**Atomic service API**: This API can be used in atomic services since API version 20.    |
| FORM_MANAGER                 | 2    | The widget is located in the widget manager of the home screen.<br>**Atomic service API**: This API can be used in atomic services since API version 20.  |
| NEGATIVE_SCREEN              | 3    | The widget is located on the minus 1 screen.<br>**Atomic service API**: This API can be used in atomic services since API version 20.            |
| FORM_CENTER_NEGATIVE_SCREEN  | 4    | The widget is located in the service panel of the minus 1 screen.  |
| FORM_MANAGER_NEGATIVE_SCREEN | 5    | The widget is located in the widget manager of the minus 1 screen.|
| SCREEN_LOCK                  | 6    | The widget is located on the locked screen.<br>**Atomic service API**: This API can be used in atomic services since API version 20.              |
| AI_SUGGESTION                | 7    | The widget is located in the area of AI Suggestions.<br>**Atomic service API**: This API can be used in atomic services since API version 20.    |

## PublishFormResult<sup>12+</sup>

Describes the result for the operation of adding a widget to the home screen.

**System capability**: SystemCapability.Ability.Form

**Model restriction**: This API can be used only in the stage model.

| Name   | Type                                         | Read-Only| Optional| Description                      |
| ------- | --------------------------------------------- | ---- | ---- | -------------------------- |
| code    | [PublishFormErrorCode](#publishformerrorcode12) | No  | No  | Result code of the operation.      |
| message | string                                        | No  | No  | Message returned for the operation.|

## PublishFormErrorCode<sup>12+</sup>

Enumerates the result codes that may be used for the operation of adding a widget to the home screen.

**System capability**: SystemCapability.Ability.Form

**Model restriction**: This API can be used only in the stage model.

| Name          | Value  | Description                            |
| -------------- | ---- | -------------------------------- |
| SUCCESS        | 0    | The widget is added to the home screen.              |
| NO_SPACE       | 1    | There is no space for adding widgets.          |
| PARAM_ERROR    | 2    | Parameter check fails.              |
| INTERNAL_ERROR | 3    | An internal error occurs during widget processing.|

## RenderingMode<sup>18+</sup>

Enumerates the rendering modes supported by the widget.

**System capability**: SystemCapability.Ability.Form

| Name       | Value  | Description        |
| ----------- | ---- | ------------ |
| AUTO_COLOR    | 0    | Auto mode.  |
| FULL_COLOR     | 1   | Full-color mode.  |
| SINGLE_COLOR      | 2   | Single-color mode.  |

## OverflowRequest<sup>20+</sup>

Defines the request for interactive widget animations.

**System capability**: SystemCapability.Ability.Form

**System API**: This is a system API.

| Name| Type| Read-Only| Optional| Description|
|-----|-----|----|----|-----|
| formId       | string  | No | No | Widget ID.|
| isOverflow   | boolean | No | No | Animation request type. The value **true** indicates the interactive widget requests to trigger the animation; the value **false** indicates the interactive widget requests to cancel the animation.|
| overflowInfo | [formInfo.OverflowInfo](js-apis-app-form-formInfo.md#overflowinfo20) | No| Yes| Animation request parameters, including the animation duration (unit: ms) and animation area (the upper left corner of the widget is used as the origin of the animation area, in vp). The default value is empty.|

## ChangeSceneAnimationStateRequest<sup>20+</sup>

Defines the request for switching the status of an interactive widget. An interactive widget can be in the active or inactive state. In the inactive state, the interactive widget is the same as a common widget. In the active state, the interactive widget can start the **LiveFormExtensionAbility** process developed by the widget host to implement interactive widget animations.

**System capability**: SystemCapability.Ability.Form

**System API**: This is a system API.

| Name| Type| Read-Only| Optional| Description|
|-----|-----|-----|-----|----------------------------------------|
| formId | string | No| No| Widget ID.                                 |
| state  | number | No| No| Status switching request type. The value **1** indicates that the switching request is activated, and the value **0** indicates that the switching request is deactivated.|

## FunInteractionParams<sup>20+</sup>

Defines the parameters for a fun-based widget.

**System capability**: SystemCapability.Ability.Form

**System API**: This is a system API.

| Name| Type| Read-Only| Optional| Description                                                                                                                                  |
|-----|-----|----|-----|--------------------------------------------------------------------------------------------------------------------------------------|
| abilityName | string | No | Yes  | ExtensionAbility name of the interaction scenario. This parameter is left empty by default.|
| targetBundleName  | string | No | No  | Bundle name.       |
| subBundleName  | string | No | No  | Sub-bundle name.|
| keepStateDuration  | number | No | Yes  | Duration of the activated state when there is no interaction. The default value is **10000**, in ms. The value should be an integer within the range [0, 10000]. If the value exceeds this range, it defaults to 10000 milliseconds.|

## SceneAnimationParams<sup>20+</sup>

Defines the parameters for a scene-based widget.

**System capability**: SystemCapability.Ability.Form

**System API**: This is a system API.

| Name| Type| Read-Only| Optional| Description                                                                                                                                             |
|-----|-----|------|----|-------------------------------------------------------------------------------------------------------------------------------------------------|
| abilityName | string | No| No | ExtensionAbility name, for example, LiveFormExtensionAbility name of the widget provider.                                    |
| disabledDesktopBehaviors | string | No| Yes | The options are **SWIPE_DESKTOP**, **PULL_DOWN_SEARCH**, **LONG_CLICK**, and **DRAG**. You can select one or more options. Use a vertical bar (\|) in between to concatenate two different operations, for example, SWIPE_DESKTOP\|PULL_DOWN_SEARCH. By default, no operation is disabled.|

## GetFormRectInfoCallback<sup>20+</sup>

### (formId: string): Promise&lt;formInfo.Rect&gt;

Callback for querying the widget position and dimension. It uses a promise to return the result.

**System capability**: SystemCapability.Ability.Form

**System API**: This is a system API.

**Parameters**

| Name| Type| Mandatory| Description|
|-----|-----|------|------------------|
| formId | string | Yes| Widget ID.|

**Returns**

| Type| Description|
| -------- | -------- |
| Promise&lt;[formInfo.Rect](js-apis-app-form-formInfo.md#rect20)&gt; | Promise used to return the position and dimension of the widget relative to the upper left corner of the screen, in vp.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                                                                 |
|-------|-----------------------------------------------------------------------------------------------------------|
| 202   | The application is not a system application.                                                              |

**Example**

```ts
import { formInfo } from '@kit.FormKit';

// The widget host needs to process the request, and calculate and return the widget dimension and position information.
let getFormRectInfoCallback: formInfo.GetFormRectInfoCallback =
  (formId: string): Promise<formInfo.Rect> => {
    return new Promise<formInfo.Rect>((resolve: Function) => {
      console.info(`formId is ${formId}`);
      let formRect: formInfo.Rect = {
        left: 0,
        top: 0,
        width: 0,
        height: 0
      };
      resolve(formRect);
    })
  };
```
