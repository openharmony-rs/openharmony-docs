# WeakRefCallback (System API)

```TypeScript
type WeakRefCallback = (weakRef: WeakRef<object>) => void
```

WeakRef callback function, which if called by system.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-unnamed-type WeakRefCallback = (weakRef: WeakRef<object>) => void--><!--Device-unnamed-type WeakRefCallback = (weakRef: WeakRef<object>) => void-End-->

**System capability:** SystemCapability.HiviewDFX.HiChecker

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| weakRef | [WeakRef](../../apis-default/arkts-apis/arkts-lib-es2021-weakref-weakref-i.md)&lt;object&gt; | Yes | WeakRef of one object. |
