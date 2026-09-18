# PageUpdateType

```TypeScript
type PageUpdateType = 'pageContentUpdate' | 'pageStateUpdate'
```

Enumerates the page update types. A page update event is triggered by the accessibility service when the page content or state changes. The accessibility extension can receive and process the corresponding page update event through the **onAccessibilityEvent** callback.

**Since:** 9

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

| Type | Description |
| --- | --- |
| 'pageContentUpdate' | Page content updated. |
| 'pageStateUpdate' | Page state updated. |
