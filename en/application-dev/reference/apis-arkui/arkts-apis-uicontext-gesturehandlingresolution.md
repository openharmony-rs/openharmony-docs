# Class (GestureHandlingResolution)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zhou-chaobo-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=9c92183287fa23162e04874223c3b068eb1f8a4d translatedAt=2026-10-29T09:06:19.498Z pushedAt=2026-10-30T01:59:13.583Z nl=1 -->

Declares the smart gesture handling result.

**Since**: 26.0.0

## constructor

constructor(isConsumed: boolean)

Constructor for the smart gesture handling result.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type | Mandatory | Description |
| ---- | ---- | ---- | ---- |
| isConsumed | boolean | Yes | Whether to consume the current smart gesture.<br>The value **true** means to consume the current smart gesture. In this case, if [selectedProposal](#properties) is not set, the system default action handling is used; if [selectedProposal](#properties) is set, custom action handling is used.<br>The value **false** means not to consume, and the system treats this smart gesture as unhandled. |

## Properties

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

| Name | Type | Read-Only | Optional | Description |
| ---- | ---- | ---- | ---- | ---- |
| isConsumed | boolean | No | No | Whether to consume the current smart gesture.<br>The value **true** means to consume the current smart gesture. In this case, if **selectedProposal** is not set, the system default action handling is used; if **selectedProposal** is set, custom action handling is used.<br>The value **false** means not to consume, and the system treats this smart gesture as unhandled. |
| selectedProposal | [BaseGestureHandlingProposal](./arkts-apis-uicontext-basegesturehandlingproposal.md) | No | Yes | Smart gesture handling behavior specified by the user.<br>When **isConsumed** is **true**, if **selectedProposal** is not set, the system default action handling is used; if **selectedProposal** is set, custom action handling is used.<br>When **isConsumed** is **false**, the setting of **selectedProposal** does not take effect. |
