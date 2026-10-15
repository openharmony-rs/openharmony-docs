# EmbeddedComponent properties/events

```TypeScript
declare class EmbeddedComponentAttribute extends CommonMethod<EmbeddedComponentAttribute>
```

The [universal attributes](arkts-arkui-common-comp.md) are supported.

> **NOTE:** 

> The default and minimum width and height of the **EmbeddedComponent** are both 10 vp. The following width- and
> height-related attributes are not supported: **constraintSize**, **aspectRatio**, **layoutWeight**,
> **flexBasis**, **flexGrow**, and **flexShrink**.

Event information related to screen coordinates is converted based on the position, width, and height of the **EmbeddedComponent**, before being transferred to the EmbeddedUIExtensionAbility for processing.

Universal events, such as the [click event](arkts-arkui-common-comp.md), are not supported. Only the following events are supported.

**Inheritance/Implementation:** EmbeddedComponentAttribute extends CommonMethod&lt;EmbeddedComponentAttribute&gt;

**Since:** 12

<!--Device-unnamed-declare class EmbeddedComponentAttribute extends CommonMethod<EmbeddedComponentAttribute>--><!--Device-unnamed-declare class EmbeddedComponentAttribute extends CommonMethod<EmbeddedComponentAttribute>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onDrawReady

```TypeScript
onDrawReady(callback: Callback<void>)
```

Triggered when the launched [EmbeddedUIExtensionAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-embeddeduiextensionability-embeddeduiextensionability-c.md) draws its first frame.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EmbeddedComponentAttribute-onDrawReady(callback: Callback<void>): EmbeddedComponentAttribute--><!--Device-EmbeddedComponentAttribute-onDrawReady(callback: Callback<void>): EmbeddedComponentAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;void&gt; | Yes | Callback invoked when the first frame is drawn by the **EmbeddedUIExtensionAbility**. |

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

<!--Device-EmbeddedComponentAttribute-onError(callback: import('../api/@ohos.base').ErrorCallback): EmbeddedComponentAttribute--><!--Device-EmbeddedComponentAttribute-onError(callback: import('../api/@ohos.base').ErrorCallback): EmbeddedComponentAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | import('../api/@ohos.base').ErrorCallback | Yes | Callback used to receive error information. The input parameter type is [BusinessError](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-businesserror-i.md). You can obtain error information through **code**, **name**, and **message** in the parameter and handle it accordingly. |

## onTerminated

```TypeScript
onTerminated(callback: import('../api/@ohos.base').Callback<TerminationInfo>)
```

Triggered when the the launched EmbeddedUIExtensionAbility exits normally by calling [terminateSelfWithResult](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiextensioncontentsession-uiextensioncontentsession-c.md#terminateselfwithresult1) or [terminateSelf](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiextensioncontentsession-uiextensioncontentsession-c.md#terminateself1).

> **NOTE:** 
> 
> This API cannot be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-EmbeddedComponentAttribute-onTerminated(callback: import('../api/@ohos.base').Callback<TerminationInfo>): EmbeddedComponentAttribute--><!--Device-EmbeddedComponentAttribute-onTerminated(callback: import('../api/@ohos.base').Callback<TerminationInfo>): EmbeddedComponentAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | import('../api/@ohos.base').Callback&lt;[TerminationInfo](arkts-arkui-embeddedcomponent-comp-terminationinfo-i.md)&gt; | Yes | Callback used to receive the return result of **EmbeddedUIExtensionAbility**. The input parameter type is [TerminationInfo](arkts-arkui-embeddedcomponent-comp-terminationinfo-i.md). |
