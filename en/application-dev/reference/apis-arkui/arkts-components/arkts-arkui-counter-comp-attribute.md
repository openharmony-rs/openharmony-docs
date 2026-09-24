# Counter properties/events

```TypeScript
declare class CounterAttribute extends CommonMethod<CounterAttribute>
```

In addition to the [universal attributes](../../../reference/apis-arkui/arkui-ts/ts-component-general-attributes.md), the following attributes are supported.

In addition to the [universal events](../../../reference/apis-arkui/arkui-ts/ts-component-general-events.md), the following events are supported.

**Inheritance/Implementation:** CounterAttribute extends CommonMethod<CounterAttribute>

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableDec

```TypeScript
enableDec(value: boolean)
```

Sets whether to enable the decrement button.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to enable the decrement button.<br>Default value: **true**. The value **true** means to enable the decrement button, and the value **false** means the opposite. |

## enableInc

```TypeScript
enableInc(value: boolean)
```

Sets whether to enable the increment button.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to enable the increment button.<br>Default value: **true**. The value **true** means to enable the increment button, and the value **false** means the opposite. |

## onDec

```TypeScript
onDec(event: VoidCallback)
```

Invoked when the value decreases.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [VoidCallback](../arkts-apis/arkts-arkui-voidcallback-t.md) | Yes | Callback invoked when the value decreases.<br>**Since:** 18 |

## onInc

```TypeScript
onInc(event: VoidCallback)
```

Invoked when the value increases.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [VoidCallback](../arkts-apis/arkts-arkui-voidcallback-t.md) | Yes | Callback invoked when the value increases.<br>**Since:** 18 |
