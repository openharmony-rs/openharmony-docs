# @ohos.app.form.formInfo(formInfo)

The **formInfo** module provides types and enums related to the widget information and state.

> **NOTE:** 

> - This topic describes only system APIs provided by the module. For details about its public APIs, see [@ohos.app.form.formInfo (formInfo)](arkts-form-app-form-forminfo.md).

**Since:** 9

**System capability:** SystemCapability.Ability.Form

## Modules to Import

```TypeScript
import { formInfo } from '@kit.FormKit';
```

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [FormInfo](arkts-form-forminfo-forminfo-i.md) | Provides information about a form. |
| [FormInfoFilter](arkts-form-forminfo-forminfofilter-i.md) | The optional options used as filters to ask getFormsInfo to return formInfos from only forms that match the options. |
| [FormStateInfo](arkts-form-forminfo-formstateinfo-i.md) | Provides state information about a form. |
| [OverflowInfo](arkts-form-forminfo-overflowinfo-i.md) | Provides OverflowInfo about funInteraction or sceneAnimation form |
| [Rect](arkts-form-forminfo-rect-i.md) | Indicates rectangle, unit is vp. |
| [RunningFormInfo](arkts-form-forminfo-runningforminfo-i.md) | The class of a running form information. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [ChangeSceneAnimationStateRequest](arkts-form-forminfo-changesceneanimationstaterequest-i-sys.md) | [ChangeSceneAnimationStateRequest](arkts-form-forminfo-changesceneanimationstaterequest-i-sys.md) |
| [FormCustomConfig](arkts-form-forminfo-formcustomconfig-i-sys.md) | [FormCustomConfig](arkts-form-forminfo-formcustomconfig-i-sys.md) |
| [FormHostServiceInfo](arkts-form-forminfo-formhostserviceinfo-i-sys.md) | [FormHostServiceInfo](arkts-form-forminfo-formhostserviceinfo-i-sys.md) |
| [FormInfo](arkts-form-forminfo-forminfo-i-sys.md) | Provides information about a form. |
| [FormInfoFilter](arkts-form-forminfo-forminfofilter-i-sys.md) | The optional options used as filters to ask getFormsInfo to return formInfos from only forms that match the options. |
| [FormProviderFilter](arkts-form-forminfo-formproviderfilter-i-sys.md) | Information about a running form. |
| [FunInteractionParams](arkts-form-forminfo-funinteractionparams-i-sys.md) | The fun interaction form params. |
| [OverflowRequest](arkts-form-forminfo-overflowrequest-i-sys.md) | Provides OverflowRequest about request/cancel form's overflow |
| [PeerFormHostServiceInfo](arkts-form-forminfo-peerformhostserviceinfo-i-sys.md) | [PeerFormHostServiceInfo](arkts-form-forminfo-peerformhostserviceinfo-i-sys.md) |
| [PublishFormCrossBundleInfo](arkts-form-forminfo-publishformcrossbundleinfo-i-sys.md) | [PublishFormCrossBundleInfo](arkts-form-forminfo-publishformcrossbundleinfo-i-sys.md) |
| [PublishFormCrossDeviceResult](arkts-form-forminfo-publishformcrossdeviceresult-i-sys.md) | [PublishFormCrossDeviceResult](arkts-form-forminfo-publishformcrossdeviceresult-i-sys.md) |
| [PublishFormResult](arkts-form-forminfo-publishformresult-i-sys.md) | The result of publish form. |
| [RunningFormInfo](arkts-form-forminfo-runningforminfo-i-sys.md) | The class of a running form information. |
| [SceneAnimationParams](arkts-form-forminfo-sceneanimationparams-i-sys.md) | The scene animation form params. |
| [TemplateFormDetailInfo](arkts-form-forminfo-templateformdetailinfo-i-sys.md) | [TemplateFormDetailInfo](arkts-form-forminfo-templateformdetailinfo-i-sys.md) |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [ColorMode](arkts-form-forminfo-colormode-e.md) | Color mode. |
| [FormDimension](arkts-form-forminfo-formdimension-e.md) | Defines the FormDimension enum. |
| [FormLocation](arkts-form-forminfo-formlocation-e.md) | Enumerates the widget locations. |
| [FormParam](arkts-form-forminfo-formparam-e.md) | Enumerates widget parameters. |
| [FormShape](arkts-form-forminfo-formshape-e.md) | Defines the FormShape enum. |
| [FormState](arkts-form-forminfo-formstate-e.md) | Provides state about a form. |
| [FormType](arkts-form-forminfo-formtype-e.md) | Type of form. |
| [FormUpdateReason](arkts-form-forminfo-formupdatereason-e.md) | Form update reason. |
| [LaunchReason](arkts-form-forminfo-launchreason-e.md) | Indicates the launch reason of a form. |
| [VisibilityType](arkts-form-forminfo-visibilitytype-e.md) | The visibility of a form. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [FormLocation](arkts-form-forminfo-formlocation-e-sys.md) | Enumerates the widget locations. |
| [FormParam](arkts-form-forminfo-formparam-e-sys.md) | Enumerates widget parameters. |
| [FormUsageState](arkts-form-forminfo-formusagestate-e-sys.md) | Enumerates the usage statuses of a widget. |
| [PublishFormErrorCode](arkts-form-forminfo-publishformerrorcode-e-sys.md) | Enumerates the result codes that may be used for the operation of adding a widget to the home screen. |
| [RenderingMode](arkts-form-forminfo-renderingmode-e-sys.md) | Enumerates the rendering modes supported by the widget. |
| [SceneAnimationTriggerType](arkts-form-forminfo-sceneanimationtriggertype-e-sys.md) | The trigger type of the scene animation. |
<!--DelEnd-->

<!--Del-->
### Types(System API)

| Name | Description |
| --- | --- |
| [DeleteFormsCallback](arkts-form-forminfo-deleteformscallback-t-sys.md) | callback for deleting the forms. |
| [GetFormRectInfoCallback](arkts-form-forminfo-getformrectinfocallback-t-sys.md) | Get form rect info callback |
| [GetLiveFormStatusCallback](arkts-form-forminfo-getliveformstatuscallback-t-sys.md) | Get live form status info callback |
| [GetWantParamsCallback](arkts-form-forminfo-getwantparamscallback-t-sys.md) | Get want parameters callback. |
| [PublishFormCrossBundleControlCallback](arkts-form-forminfo-publishformcrossbundlecontrolcallback-t-sys.md) | publish form cross bundle control callback. |
| [TemplateFormDetailInfoCallback](arkts-form-forminfo-templateformdetailinfocallback-t-sys.md) | template form detail info callback. |
| [UpdateFormsConfigCallback](arkts-form-forminfo-updateformsconfigcallback-t-sys.md) | Callback for updating the forms. |
<!--DelEnd-->
