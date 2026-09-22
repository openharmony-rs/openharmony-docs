# Stack properties/events

```TypeScript
declare class StackAttribute extends CommonMethod<StackAttribute>
```

In addition to the [universal attributes](arkts-arkui-common-comp-commonmethod-c.md), the following attributes are supported.

The [universal events](arkts-arkui-common-comp-commonmethod-c.md) are supported.

**Inheritance/Implementation:** StackAttribute extends CommonMethod<StackAttribute>

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## alignContent

```TypeScript
alignContent(value: Alignment)
```

Sets the alignment of child components in the container. When both this attribute and [align](arkts-arkui-common-comp-commonmethod-c.md#align) are set, whichever is set last takes effect. When both this attribute and the constructor input parameter are set, the value set by the attribute takes effect, regardless of the setting order.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Alignment](../arkts-apis/arkts-arkui-alignment-e.md) | Yes | Alignment of all child components in the container.<br>Default value: **Alignment.Center** <br>Invalid value: the default value is used. |

## syncLoad

```TypeScript
syncLoad(enable: boolean)
```

Sets whether to synchronously load all child components in the stack container. During synchronous loading, all child components complete layout calculation and rendering within the current frame. During asynchronous loading, the system dynamically adjusts the layout timing of child components based on the layout duration of the current frame to avoid blocking the main thread.

> **NOTE:** 
> 
> When this parameter is set to **false**, in the first display scenario, if the layout of the current frame
> takes more than 50 ms, the child components in the Stack area that have not been laid out are deferred to the
> next frame for layout.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether to synchronously load all child components in the Stack area.<br>The value **true** means synchronous loading, and **false** means asynchronous loading. <br>Default value: **true** |
