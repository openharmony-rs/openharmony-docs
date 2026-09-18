# @ohos.app.form.formAgent

The **FormAgent** module provides APIs related to the widget agent. Currently, you can use the APIs to request to publish widgets only.

**Since:** 11

**System capability:** SystemCapability.Ability.Form

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { formAgent } from '@kit.FormKit';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getAvailableFormHostServices](arkts-form-formagent-getavailableformhostservices-f-sys.md) | Get available form host service info list. |
| [requestPublishForm](arkts-form-formagent-requestpublishform-f-sys.md) | Requests to publish a widget to the widget host. This API uses an asynchronous callback to return the result. The widget host is usually the home screen. |
| [requestPublishForm](arkts-form-formagent-requestpublishform-f-sys.md) | Requests to publish a widget to the widget host. This API uses a promise to return the result. The widget host is usually the home screen. |
| [requestPublishFormCrossDevice](arkts-form-formagent-requestpublishformcrossdevice-f-sys.md) | Requests to publish a form to the form host service of the remote device. |
| [updateFormCrossBundle](arkts-form-formagent-updateformcrossbundle-f-sys.md) | Updates a widget by cross bundle. This API uses a promise to return the result. |
<!--DelEnd-->
