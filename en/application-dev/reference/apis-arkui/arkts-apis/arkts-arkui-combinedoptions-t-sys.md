# CombinedOptions (System API)

```TypeScript
type CombinedOptions<T extends ViewModel, Data> = object &
  Options<T, Data> &
  ThisType<T & ViewModel & Data>
```

Used for ide.

**Type:** object & [Options](arkts-arkui-viewmodel-options-i.md)&lt;T, Data&gt; & ThisType&lt;T & [ViewModel](arkts-arkui-viewmodel-i.md) & Data&gt;

**Since:** 4

**Model restriction:** This API can be used only in the FA model.

<!--Device-unnamed-type CombinedOptions<T extends ViewModel, Data> = object &  Options<T, Data> &  ThisType<T & ViewModel & Data>--><!--Device-unnamed-type CombinedOptions<T extends ViewModel, Data> = object &  Options<T, Data> &  ThisType<T & ViewModel & Data>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Lite

**System API:** This is a system API.
