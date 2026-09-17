# CombinedOptions (System API)

```TypeScript
type CombinedOptions<T extends ViewModel, Data> = object &
  Options<T, Data> &
  ThisType<T & ViewModel & Data>
```

Used for ide.

@typedef { object & Options&lt;T, Data&gt; & ThisType&lt;T & ViewModel & Data&gt; } CombinedOptions&lt;T extends ViewModel, Data&gt;

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

**System API:** This is a system API.

**Type:** object & [Options](arkts-arkui-viewmodel-options-i.md)&lt;T, Data&gt; & ThisType&lt;T & [ViewModel](arkts-arkui-viewmodel-viewmodel-i.md) & Data&gt;
