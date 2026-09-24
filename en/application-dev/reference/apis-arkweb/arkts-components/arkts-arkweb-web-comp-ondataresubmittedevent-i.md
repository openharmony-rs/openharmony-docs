# OnDataResubmittedEvent

```TypeScript
declare interface OnDataResubmittedEvent
```

Defines the callback information triggered when the web form data can be resubmitted, including the submission handler. It is suitable for scenarios where handling form retry submission is required, improving form interaction reliability and user experience.

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## handler

```TypeScript
handler: DataResubmissionHandler
```

Handler for resubmitting web form data.

**Type:** [DataResubmissionHandler](arkts-arkweb-web-comp-dataresubmissionhandler-c.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core
