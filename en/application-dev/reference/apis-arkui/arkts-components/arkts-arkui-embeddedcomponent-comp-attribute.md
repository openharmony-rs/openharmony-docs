# EmbeddedComponent properties/events

```TypeScript
declare class EmbeddedComponentAttribute extends CommonMethod<EmbeddedComponentAttribute>
```

The [universal attributes](arkts-arkui-common-comp.md#common) are supported.

Event information related to screen coordinates is converted based on the position, width, and height of the **EmbeddedComponent**, before being transferred to the EmbeddedUIExtensionAbility for processing.

Universal events, such as the [click event](arkts-arkui-common-comp.md#common), are not supported. Only the following events are supported.

**Inheritance/Implementation:** EmbeddedComponentAttribute extends CommonMethod<EmbeddedComponentAttribute>

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onDrawReady

```TypeScript
onDrawReady(callback: Callback<void>)
```

Callback called when the EmbeddedUIExtensionAbility draw the first frame.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;void&gt; | Yes |  |

## onError

```TypeScript
onError(callback: import('../api/@ohos.base').ErrorCallback)
```

Called when an error occurs during the running of the started EmbeddedUIExtensionAbility. Through the **code**, **name**, and **message** in the callback parameters, error information can be obtained and handled. For details about the error codes, see [UIExtension Error Codes](../../../reference/apis-arkui/errorcode-uiextension.md).

> **NOTE:** 
> 
> This API cannot be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | import('../api/@ohos.base').ErrorCallback | Yes | Callback used to return the error information of the [BusinessError](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-businesserror-i.md) type. The error information can be obtained and processed based on the **code**, **name**, and **message** parameters. |

## onTerminated

```TypeScript
onTerminated(callback: import('../api/@ohos.base').Callback<TerminationInfo>)
```

Triggered when the the launched EmbeddedUIExtensionAbility exits normally by calling [terminateSelfWithResult](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiextensioncontentsession-uiextensioncontentsession-c.md#terminateselfwithresult) or [terminateSelf](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiextensioncontentsession-uiextensioncontentsession-c.md#terminateself).

> **NOTE:** 
> 
> This API cannot be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | import('../api/@ohos.base').Callback&lt;[TerminationInfo](arkts-arkui-embeddedcomponent-comp-terminationinfo-i.md)&gt; | Yes | Callback used to return the result from the EmbeddedUIExtensionAbility. |
