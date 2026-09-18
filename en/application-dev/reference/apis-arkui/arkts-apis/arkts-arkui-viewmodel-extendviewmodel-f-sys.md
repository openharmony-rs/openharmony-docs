# extendViewModel (System API)

## extendViewModel

```TypeScript
export declare function extendViewModel<T extends ViewModel, Data>(
  options: CombinedOptions<T, Data>
): ViewModel & Data
```

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [CombinedOptions](arkts-arkui-combinedoptions-t-sys.md)&lt;T, Data&gt; | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| [ViewModel](arkts-arkui-viewmodel-viewmodel-i.md) & Data |  |
