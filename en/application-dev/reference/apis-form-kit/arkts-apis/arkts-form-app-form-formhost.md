# @ohos.app.form.formHost(formHost)

The **formHost** module provides APIs related to the widget host, which is an application that displays the widget content and controls the position where the widget is displayed. You can use the APIs to delete, release, and update widgets installed by the same user, and obtain widget information and status.

**Since:** 9

<!--Device-unnamed-declare namespace formHost--><!--Device-unnamed-declare namespace formHost-End-->

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { formHost } from '@kit.FormKit';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [acquireFormData](arkts-form-formhost-acquireformdata-f-sys.md#acquireformdata1) | Requests data from the widget provider. This API uses an asynchronous callback to return the result. |
| [acquireFormData](arkts-form-formhost-acquireformdata-f-sys.md#acquireformdata2) | Requests data from the widget provider. This API uses a promise to return the result. |
| [acquireFormState](arkts-form-formhost-acquireformstate-f-sys.md#acquireformstate1) | Obtains the widget state. This API uses an asynchronous callback to return the result. |
| [acquireFormState](arkts-form-formhost-acquireformstate-f-sys.md#acquireformstate2) | Obtains the widget state. This API uses a promise to return the result. |
| [addForm](arkts-form-formhost-addform-f-sys.md#addform) | Add a form. |
| [castToNormalForm](arkts-form-formhost-casttonormalform-f-sys.md#casttonormalform1) | Converts a temporary widget to a normal one. This API uses an asynchronous callback to return the result. |
| [castToNormalForm](arkts-form-formhost-casttonormalform-f-sys.md#casttonormalform2) | Converts a temporary widget to a normal one. This API uses a promise to return the result. |
| [clearRouterProxy](arkts-form-formhost-clearrouterproxy-f-sys.md#clearrouterproxy1) | Clears the router proxy set for widgets. This API uses an asynchronous callback to return the result. |
| [clearRouterProxy](arkts-form-formhost-clearrouterproxy-f-sys.md#clearrouterproxy2) | Clears the router proxy set for widgets. This API uses a promise to return the result. |
| [deleteForm](arkts-form-formhost-deleteform-f-sys.md#deleteform1) | Deletes a widget. After this API is called, the application can no longer use the widget, and the Widget Manager will not retain the widget information. This API uses an asynchronous callback to return the result. |
| [deleteForm](arkts-form-formhost-deleteform-f-sys.md#deleteform2) | Deletes a widget. After this API is called, the application can no longer use the widget, and the Widget Manager will not retain the widget information. This API uses a promise to return the result. |
| [deleteInvalidForms](arkts-form-formhost-deleteinvalidforms-f-sys.md#deleteinvalidforms1) | Deletes invalid widgets from the list. This API uses an asynchronous callback to return the result. |
| [deleteInvalidForms](arkts-form-formhost-deleteinvalidforms-f-sys.md#deleteinvalidforms2) | Deletes invalid widgets from the list. This API uses a promise to return the result. |
| [disableFormsUpdate](arkts-form-formhost-disableformsupdate-f-sys.md#disableformsupdate1) | Instructs the widget framework to make a widget not updatable. After this API is called, the widget cannot receive updates from the widget provider. This API uses an asynchronous callback to return the result. |
| [disableFormsUpdate](arkts-form-formhost-disableformsupdate-f-sys.md#disableformsupdate2) | Instructs the widget framework to make a widget not updatable. After this API is called, the widget cannot receive updates from the widget provider. This API uses a promise to return the result. |
| [enableFormsUpdate](arkts-form-formhost-enableformsupdate-f-sys.md#enableformsupdate1) | Instructs the widget framework to make a widget updatable. After this API is called, the widget is in the enabled state and can receive updates from the widget provider. This API uses an asynchronous callback to return the result. |
| [enableFormsUpdate](arkts-form-formhost-enableformsupdate-f-sys.md#enableformsupdate2) | Instructs the widget framework to make a widget updatable. After this API is called, the widget is in the enabled state and can receive updates from the widget provider. This API uses a promise to return the result. |
| [getAllFormsInfo](arkts-form-formhost-getallformsinfo-f-sys.md#getallformsinfo1) | Obtains the widget information provided by all applications on the device (excluding template widgets). This API uses an asynchronous callback to return the result. |
| [getAllFormsInfo](arkts-form-formhost-getallformsinfo-f-sys.md#getallformsinfo2) | Obtains the widget information provided by all applications on the device (excluding template widgets). This API uses a promise to return the result. |
| [getAllTemplateFormsInfo](arkts-form-formhost-getalltemplateformsinfo-f-sys.md#getalltemplateformsinfo) | Obtains the template widget information provided by all applications on the device. This API uses a promise to return the result. |
| [getFormIdsByFormLocation](arkts-form-formhost-getformidsbyformlocation-f-sys.md#getformidsbyformlocation) | Obtains the list of widget IDs at a specified location on the device. This API uses a promise to return the result. |
| [getFormsInfo](arkts-form-formhost-getformsinfo-f-sys.md#getformsinfo1) | Obtains the widget information provided by a specified application on the device (excluding template widgets). This API uses an asynchronous callback to return the result. |
| [getFormsInfo](arkts-form-formhost-getformsinfo-f-sys.md#getformsinfo2) | Obtains the widget information provided by a specified application on the device (excluding template widgets). This API uses an asynchronous callback to return the result. |
| [getFormsInfo](arkts-form-formhost-getformsinfo-f-sys.md#getformsinfo3) | Obtains the widget information provided by a specified application on the device (excluding template widgets). This API uses a promise to return the result. |
| [getFormsInfo](arkts-form-formhost-getformsinfo-f-sys.md#getformsinfo4) | Obtains the widget information provided by a specified application on the device (excluding template widgets). This API uses a promise to return the result. |
| [getTemplateFormsInfo](arkts-form-formhost-gettemplateformsinfo-f-sys.md#gettemplateformsinfo) | Obtains the template widget information provided by a specified application on the device. This API uses a promise to return the result. |
| [isSystemReady](arkts-form-formhost-issystemready-f-sys.md#issystemready1) | Checks whether the system is ready. This API uses an asynchronous callback to return the result. |
| [isSystemReady](arkts-form-formhost-issystemready-f-sys.md#issystemready2) | Checks whether the system is ready. This API uses a promise to return the result. |
| [notifyFormsEnableUpdate](arkts-form-formhost-notifyformsenableupdate-f-sys.md#notifyformsenableupdate1) | Instructs the widgets to enable or disable updates. This API uses an asynchronous callback to return the result. |
| [notifyFormsEnableUpdate](arkts-form-formhost-notifyformsenableupdate-f-sys.md#notifyformsenableupdate2) | Instructs the widgets to enable or disable updates. This API uses a promise to return the result. |
| [notifyFormsPrivacyProtected](arkts-form-formhost-notifyformsprivacyprotected-f-sys.md#notifyformsprivacyprotected1) | Notifies that the privacy protection status of the specified widgets changes. This API uses an asynchronous callback to return the result. |
| [notifyFormsPrivacyProtected](arkts-form-formhost-notifyformsprivacyprotected-f-sys.md#notifyformsprivacyprotected2) | Notifies that the privacy protection status of the specified widgets changes. This API uses a promise to return the result. |
| [notifyFormsVisible](arkts-form-formhost-notifyformsvisible-f-sys.md#notifyformsvisible1) | Instructs the widgets to make themselves visible. This API uses an asynchronous callback to return the result. |
| [notifyFormsVisible](arkts-form-formhost-notifyformsvisible-f-sys.md#notifyformsvisible2) | Instructs the widgets to make themselves visible. This API uses a promise to return the result. |
| [notifyInvisibleForms](arkts-form-formhost-notifyinvisibleforms-f-sys.md#notifyinvisibleforms1) | Instructs the widget framework to make a widget invisible. After this API is called, **onVisibilityChange** is invoked to notify the widget provider. This API uses an asynchronous callback to return the result. |
| [notifyInvisibleForms](arkts-form-formhost-notifyinvisibleforms-f-sys.md#notifyinvisibleforms2) | Instructs the widget framework to make a widget invisible. After this API is called, **onVisibilityChange** is invoked to notify the widget provider. This API uses a promise to return the result. |
| [notifyVisibleForms](arkts-form-formhost-notifyvisibleforms-f-sys.md#notifyvisibleforms1) | Instructs the widget framework to make a widget visible. After this API is called, **onVisibilityChange** is invoked to notify the widget provider. This API uses an asynchronous callback to return the result. |
| [notifyVisibleForms](arkts-form-formhost-notifyvisibleforms-f-sys.md#notifyvisibleforms2) | Instructs the widget framework to make a widget visible. After this API is called, **onVisibilityChange** is invoked to notify the widget provider. This API uses a promise to return the result. |
| [off("formUninstall")](arkts-form-formhost-off-f-sys.md#offformuninstall) | Unsubscribes from widget uninstall events. This API uses an asynchronous callback to return the result. |
| [off('formOverflow')](arkts-form-formhost-off-f-sys.md#offformoverflow) | Unsubscribes from the interactive widget animation request event. This API uses an asynchronous callback to return the result. |
| [off('changeSceneAnimationState')](arkts-form-formhost-off-f-sys.md#offchangesceneanimationstate) | Unsubscribes from the event of switching the interactive widget state. An interactive widget can be in the active or inactive state. In the inactive state, the interactive widget is the same as a common widget. In the active state, the interactive widget can start the **LiveFormExtensionAbility** process developed by the widget host to implement interactive widget animations. This API uses an asynchronous callback to return the result. |
| [off('getFormRect')](arkts-form-formhost-off-f-sys.md#offgetformrect) | Unsubscribes from the event of requesting widget position and dimension. This API uses an asynchronous callback to return the result. |
| [off('getLiveFormStatus')](arkts-form-formhost-off-f-sys.md#offgetliveformstatus) | Cancels Listening to the event of get live form status. |
| [offDeleteFormsCallback](arkts-form-formhost-offdeleteformscallback-f-sys.md#offdeleteformscallback) | Unregister the callback for deleting forms. |
| [offGetWantParamsCallback](arkts-form-formhost-offgetwantparamscallback-f-sys.md#offgetwantparamscallback) | Unregister callback of getting the want parameters of the form. |
| [offTemplateFormDetailInfoChange](arkts-form-formhost-offtemplateformdetailinfochange-f-sys.md#offtemplateformdetailinfochange) | Unsubscribes from changes in the static configuration information of template widgets. This API uses an asynchronous callback to return the result. |
| [offUpdateFormsConfigCallback](arkts-form-formhost-offupdateformsconfigcallback-f-sys.md#offupdateformsconfigcallback) | Unregister the callback for updating form config. |
| [on("formUninstall")](arkts-form-formhost-on-f-sys.md#onformuninstall) | Subscribes to widget uninstall events. This API uses an asynchronous callback to return the result. |
| [on('formOverflow')](arkts-form-formhost-on-f-sys.md#onformoverflow) | Subscribes to the interactive widget animation request event. This API uses an asynchronous callback to return the result. |
| [on('changeSceneAnimationState')](arkts-form-formhost-on-f-sys.md#onchangesceneanimationstate) | Subscribes to the event of switching the interactive widget state. An interactive widget can be in the active or inactive state. In the inactive state, the interactive widget is the same as a common widget. In the active state, the interactive widget can start the **LiveFormExtensionAbility** process developed by the widget host to implement interactive widget animations. This API uses an asynchronous callback to return the result. |
| [on('getFormRect')](arkts-form-formhost-on-f-sys.md#ongetformrect) | Subscribes to the event of requesting widget position and dimension. This API uses an asynchronous callback to return the result. |
| [on('getLiveFormStatus')](arkts-form-formhost-on-f-sys.md#ongetliveformstatus) | Listens to the event of get live form status. |
| [onDeleteFormsCallback](arkts-form-formhost-ondeleteformscallback-f-sys.md#ondeleteformscallback) | Register the callback for deleting forms. |
| [onGetWantParamsCallback](arkts-form-formhost-ongetwantparamscallback-f-sys.md#ongetwantparamscallback) | Register callback of getting the want parameters of the form. |
| [onTemplateFormDetailInfoChange](arkts-form-formhost-ontemplateformdetailinfochange-f-sys.md#ontemplateformdetailinfochange) | Subscribes to changes in the static configuration information of template widgets. This API uses an asynchronous callback to return the result. |
| [onUpdateFormsConfigCallback](arkts-form-formhost-onupdateformsconfigcallback-f-sys.md#onupdateformsconfigcallback) | Register the callback for updating form config. |
| [recoverForms](arkts-form-formhost-recoverforms-f-sys.md#recoverforms1) | Recovers recycled widgets and updates their status to non-recyclable, or updates the status of widgets to non- recyclable if the widgets are not recycled. This API uses a promise to return the result. |
| [recoverForms](arkts-form-formhost-recoverforms-f-sys.md#recoverforms2) | Recovers widgets. This API uses an asynchronous callback to return the result. |
| [recycleForms](arkts-form-formhost-recycleforms-f-sys.md#recycleforms) | Recycles widgets, that is, reclaiming widget memory. This API uses a promise to return the result. |
| [registerFormHostService](arkts-form-formhost-registerformhostservice-f-sys.md#registerformhostservice) | Register the form host service info. |
| [releaseForm](arkts-form-formhost-releaseform-f-sys.md#releaseform1) | Releases a widget. After this API is called, the application can no longer use the widget, but the Widget Manager still retains the widget cache and storage information. This API uses an asynchronous callback to return the result. |
| [releaseForm](arkts-form-formhost-releaseform-f-sys.md#releaseform2) | Releases a widget. After this API is called, the application can no longer use the widget, but the Widget Manager retains the storage information about the widget and retains or releases the cache information based on the setting. This API uses an asynchronous callback to return the result. |
| [releaseForm](arkts-form-formhost-releaseform-f-sys.md#releaseform3) | Releases a widget. After this API is called, the application can no longer use the widget, but the Widget Manager retains the storage information about the widget and retains or releases the cache information based on the setting. This API uses a promise to return the result. |
| [requestForm](arkts-form-formhost-requestform-f-sys.md#requestform1) | Requests a widget update. This API uses an asynchronous callback to return the result. |
| [requestForm](arkts-form-formhost-requestform-f-sys.md#requestform2) | Requests a widget update. This API uses a promise to return the result. |
| [requestFormWithParams](arkts-form-formhost-requestformwithparams-f-sys.md#requestformwithparams) | Carries parameters to request a widget update. This API uses a promise to return the result. |
| [setFormsRecyclable](arkts-form-formhost-setformsrecyclable-f-sys.md#setformsrecyclable1) | Sets widgets to be recyclable. This API uses a promise to return the result. |
| [setFormsRecyclable](arkts-form-formhost-setformsrecyclable-f-sys.md#setformsrecyclable2) | Sets widgets to be recyclable. This API uses an asynchronous callback to return the result. |
| [setPublishFormResult](arkts-form-formhost-setpublishformresult-f-sys.md#setpublishformresult) | Sets the result for the operation of adding a widget to the home screen. |
| [setRouterProxy](arkts-form-formhost-setrouterproxy-f-sys.md#setrouterproxy1) | Sets a router proxy for widgets and obtains the Want information required for redirection. This API uses an asynchronous callback to return the result. |
| [setRouterProxy](arkts-form-formhost-setrouterproxy-f-sys.md#setrouterproxy2) | Sets a router proxy for widgets and obtains the Want information required for redirection. This API uses a promise to return the result. This API uses a promise to return the result. |
| [shareForm](arkts-form-formhost-shareform-f-sys.md#shareform1) | Shares a specified widget with a remote device. This API uses an asynchronous callback to return the result. |
| [shareForm](arkts-form-formhost-shareform-f-sys.md#shareform2) | Shares a specified widget with a remote device. This API uses a promise to return the result. |
| [unregisterFormHostService](arkts-form-formhost-unregisterformhostservice-f-sys.md#unregisterformhostservice) | Unregister the form host service info. |
| [updateFormLocation](arkts-form-formhost-updateformlocation-f-sys.md#updateformlocation) | Updates the widget location. |
| [updateFormLockedState](arkts-form-formhost-updateformlockedstate-f-sys.md#updateformlockedstate) | Notifies the update of the widget lock state. This API uses a promise to return the result. If an application is locked, its widget will also be locked and masked in a locked style. To use the widget, you need to enter the password set for the widget. |
| [updateFormSize](arkts-form-formhost-updateformsize-f-sys.md#updateformsize) | Updates the size of the widget. |
<!--DelEnd-->
