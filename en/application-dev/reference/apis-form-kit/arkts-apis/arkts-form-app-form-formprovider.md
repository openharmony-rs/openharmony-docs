# @ohos.app.form.formProvider

The **formProvider** module provides APIs to obtain widget information, update widgets, and set the update time.

**Since:** 9

**System capability:** SystemCapability.Ability.Form

## Modules to Import

```TypeScript
import { formProvider } from '@kit.FormKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [cancelOverflow](arkts-form-formprovider-canceloverflow-f.md) | Cancels an animation. This API takes effect only for [scene-based widgets](../../../form/arkts-ui-widget-configuration.md#sceneanimationparams-field). This API uses a promise to return the result. |
| [closeFormEditAbility](arkts-form-formprovider-closeformeditability-f.md) | Closes the widget editing page. |
| [getFormRect](arkts-form-formprovider-getformrect-f.md) | Obtains the position and dimension of a widget. This API uses a promise to return the result. |
| [getFormsInfo](arkts-form-formprovider-getformsinfo-f.md) | Obtains the application's widget information that meets a filter criterion on the device. This API uses an asynchronous callback to return the result. |
| [getFormsInfo](arkts-form-formprovider-getformsinfo-f.md) | Obtains the application's widget information on the device. This API uses an asynchronous callback to return the result. |
| [getFormsInfo](arkts-form-formprovider-getformsinfo-f.md) | Obtains information about widgets that meet the criteria of the current application. This API uses a promise to return the result. |
| [getPublishedFormInfoById](arkts-form-formprovider-getpublishedforminfobyid-f.md) | Obtains the information of the widget that has been added to the home screen on the device. This API uses a promise to return the result. |
| [getPublishedFormInfos](arkts-form-formprovider-getpublishedforminfos-f.md) | Obtains the information of all widgets that have been added to the home screen on the device. This API uses a promise to return the result. |
| [getPublishedRunningFormInfoById](arkts-form-formprovider-getpublishedrunningforminfobyid-f.md) | Obtains the information of a specified widget that has been added to the home screen. This API uses a promise to return the result. |
| [getPublishedRunningFormInfos](arkts-form-formprovider-getpublishedrunningforminfos-f.md) | Obtains information about all widgets that have been added to the home screen. This API uses a promise to return the result. |
| [openFormEditAbility](arkts-form-formprovider-openformeditability-f.md) | Opens the widget editing page. |
| [openFormManager](arkts-form-formprovider-openformmanager-f.md) | Opens the Widget Manager page of the current application. |
| [reloadAllForms](arkts-form-formprovider-reloadallforms-f.md) | Reloads all widgets. Invoked in the main process of the application, this API notifies the FormExtension process to perform batch updates of all widgets added to the current application. It can only be called within a [UIAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiability-uiability-c.md) and uses a promise to return the result. |
| [reloadForms](arkts-form-formprovider-reloadforms-f.md) | Reloads widgets. For widgets with the same **moduleName**, **abilityName**, and **formName** of the current application, each widget has a different widget ID after being added to the home screen for multiple times. Widget providers can use this API to batch update widgets that have different IDs but share the same **moduleName**, **abilityName**, and **formName**. Invoked in the main process of the application, this API notifies the FormExtension process to perform batch updates. It can only be called within a [UIAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiability-uiability-c.md) and uses a promise to return the result. |
| [requestOverflow](arkts-form-formprovider-requestoverflow-f.md) | Requests an animation. This API takes effect only for [scene-based widgets](../../../form/arkts-ui-widget-configuration.md#sceneanimationparams-field). This API uses a promise to return the result. |
| [setFormNextRefreshTime](arkts-form-formprovider-setformnextrefreshtime-f.md) | Sets the next refresh time for a widget. This API uses an asynchronous callback to return the result. |
| [setFormNextRefreshTime](arkts-form-formprovider-setformnextrefreshtime-f.md) | Sets the next refresh time for a widget. This API uses a promise to return the result. |
| [updateForm](arkts-form-formprovider-updateform-f.md) | Updates a widget. This API uses an asynchronous callback to return the result. |
| [updateForm](arkts-form-formprovider-updateform-f.md) | Updates a widget. This API uses a promise to return the result. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [activateSceneAnimation](arkts-form-formprovider-activatesceneanimation-f-sys.md) | Requests to activate a widget. This API takes effect only for [scene-based widgets](../../../form/arkts-ui-widget-configuration.md#sceneanimationparams-field). This API uses a promise to return the result. An interactive widget can be in the active or inactive state. In the inactive state, the widget is the same as a common widget. In the active state, the widget can start the **LiveFormExtensionAbility** process developed by the widget host to implement animations. |
| [deactivateSceneAnimation](arkts-form-formprovider-deactivatesceneanimation-f-sys.md) | Requests to deactivate a widget. This API takes effect only for [scene-based widgets](../../../form/arkts-ui-widget-configuration.md#sceneanimationparams-field). This API uses a promise to return the result. An interactive widget can be in the active or inactive state. In the inactive state, the widget is the same as a common widget. In the active state, the widget can start the **LiveFormExtensionAbility** process developed by the widget host to implement animations. |
| [isRequestPublishFormSupported](arkts-form-formprovider-isrequestpublishformsupported-f-sys.md) | Checks whether a widget can be added to the widget host. This API uses an asynchronous callback to return the result. |
| [isRequestPublishFormSupported](arkts-form-formprovider-isrequestpublishformsupported-f-sys.md) | Checks whether a widget can be added to the widget host. This API uses a promise to return the result. |
| [offPublishFormCrossBundleControl](arkts-form-formprovider-offpublishformcrossbundlecontrol-f-sys.md) | Unsubscribes from controls on cross-bundle widget addition to the home screen. This API uses an asynchronous callback to return the result. |
| [onPublishFormCrossBundleControl](arkts-form-formprovider-onpublishformcrossbundlecontrol-f-sys.md) | Subscribes to controls on cross-bundle widget addition to the home screen. This API uses an asynchronous callback to return the result. |
| [openFormManagerCrossBundle](arkts-form-formprovider-openformmanagercrossbundle-f-sys.md) | Open the view of forms belonging to the specified bundle. Client to communication with FormManagerService. |
| [requestPublishForm](arkts-form-formprovider-requestpublishform-f-sys.md) | Requests to publish a widget to the widget host (usually the home screen). This API uses an asynchronous callback to return the result. |
| [requestPublishForm](arkts-form-formprovider-requestpublishform-f-sys.md) | Requests to publish a widget to the widget host (usually the home screen). This API uses an asynchronous callback to return the result. |
| [requestPublishForm](arkts-form-formprovider-requestpublishform-f-sys.md) | Requests to publish a widget to the widget host (usually the home screen). This API uses a promise to return the result. |
| [updateTemplateFormDetailInfo](arkts-form-formprovider-updatetemplateformdetailinfo-f-sys.md) | Updates the static configuration information of a specified template widget on the current device. This API uses a promise to return the result. |
<!--DelEnd-->
