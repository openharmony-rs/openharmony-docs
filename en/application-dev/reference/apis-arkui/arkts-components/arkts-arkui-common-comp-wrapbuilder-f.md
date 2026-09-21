# wrapBuilder

## wrapBuilder

```TypeScript
declare function wrapBuilder<Args extends Object[]>(builder: (...args: Args) => void): WrappedBuilder<Args>
```

Defining wrapBuilder function.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| builder | (...args: Args) =&gt; void | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| [WrappedBuilder](arkts-arkui-common-comp-wrappedbuilder-c.md)&lt;Args&gt; |  |
