# TemplateStatusCallback (System API)

```TypeScript
type TemplateStatusCallback = (templateStatusList: TemplateStatus[]) => void
```

Defines the callback triggered for receiving notifications of template status changes. When the template status changes (for example, the template is added, deleted, or its validity changes), the system notifies the application through this callback.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.UserIAM.UserAuth.CompanionDeviceAuth

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| templateStatusList | [TemplateStatus](arkts-userauthentication-companiondeviceauth-templatestatus-i-sys.md)[] | Yes | Template status list. The list contains the status information of all registered templates of the current user. The application can determine whether a template is valid based on the **isValid** field and whether the data is real-time data based on the **isConfirmed** field. |
