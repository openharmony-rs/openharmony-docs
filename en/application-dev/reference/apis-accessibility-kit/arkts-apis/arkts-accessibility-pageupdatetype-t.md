# PageUpdateType

```TypeScript
type PageUpdateType = 'pageContentUpdate' | 'pageStateUpdate' | 'pageStatePreUpdate'
```

Enumerates the page update types. A page update event is triggered by the accessibility service when the page content or state changes. The accessibility extension can receive and process the corresponding page update event through the **onAccessibilityEvent** callback.

**Since:** 9

<!--Device-unnamed-type PageUpdateType = 'pageContentUpdate' | 'pageStateUpdate' | 'pageStatePreUpdate'--><!--Device-unnamed-type PageUpdateType = 'pageContentUpdate' | 'pageStateUpdate' | 'pageStatePreUpdate'-End-->

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

| Type | Description |
| --- | --- |
| 'pageContentUpdate' | Page content updated. |
| 'pageStateUpdate' | Page state updated. |
| 'pageStatePreUpdate' | Indicates that the page status is about to be updated.<br>**Since:** 26.2.0 |
