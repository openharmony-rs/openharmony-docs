# Counter properties/events

```TypeScript
declare class CounterAttribute extends CommonMethod<CounterAttribute>
```

In addition to the [universal attributes](arkts-arkui-common-comp.md), the following attributes are supported.

**Inheritance/Implementation:** CounterAttribute extends CommonMethod<CounterAttribute>

**Since:** 7

<!--Device-unnamed-declare class CounterAttribute extends CommonMethod<CounterAttribute>--><!--Device-unnamed-declare class CounterAttribute extends CommonMethod<CounterAttribute>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## enableDec

```TypeScript
enableDec(value: boolean)
```

Sets whether to enable the decrement button.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CounterAttribute-enableDec(value: boolean): CounterAttribute--><!--Device-CounterAttribute-enableDec(value: boolean): CounterAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to enable or disable the decrement button.<br>Default value: **true**, which means the decrement button is enabled; **false** means the decrement button is disabled. |

## enableInc

```TypeScript
enableInc(value: boolean)
```

Sets whether to enable the increment button.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-CounterAttribute-enableInc(value: boolean): CounterAttribute--><!--Device-CounterAttribute-enableInc(value: boolean): CounterAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to disable or enable the increment button.<br>Default value: **true**, which means the increment button is enabled; **false** means the button is disabled. |

## onDec

```TypeScript
onDec(event: VoidCallback)
```

Invoked when the value decreases.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-CounterAttribute-onDec(event: VoidCallback): CounterAttribute--><!--Device-CounterAttribute-onDec(event: VoidCallback): CounterAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [VoidCallback](../arkts-apis/arkts-arkui-voidcallback-t.md) | Yes | Callback invoked when the value of the Counter decreases.<br>**Since:** 18 |

## onInc

```TypeScript
onInc(event: VoidCallback)
```

Invoked when the value increases.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-CounterAttribute-onInc(event: VoidCallback): CounterAttribute--><!--Device-CounterAttribute-onInc(event: VoidCallback): CounterAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [VoidCallback](../arkts-apis/arkts-arkui-voidcallback-t.md) | Yes | Callback invoked when the counter value increases.<br>**Since:** 18 |
