# PasteButton properties/events

```TypeScript
declare class PasteButtonAttribute extends SecurityComponentMethod<PasteButtonAttribute>
```

This component can only inherit the [universal attributes of security components](../arkts-apis/arkts-arkui-security_component.md).

<br>Only the following events are supported.

**Inheritance/Implementation:** PasteButtonAttribute extends SecurityComponentMethod<PasteButtonAttribute>

**Since:** 10

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onClick

```TypeScript
onClick(event: PasteButtonCallback)
```

Triggered when the paste button is clicked, returning the authorization result. Upon successful authorization, the application obtains temporary permission to read clipboard content.

> **NOTE:** 
> - You may want to learn the [restrictions on security component styles](../../../security/AccessToken/security-component-overview.md#constraints)to avoid authorization failures caused by incompliant styles.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [PasteButtonCallback](arkts-arkui-pastebutton-comp-pastebuttoncallback-t.md) | Yes | Callback for the click event, used to handle the authorization result after the paste button is clicked.<br>Starting from API version 18, **PasteButtonCallback** is adopted uniformly, which additionally provides error information.<br>**Since:** 18 |
