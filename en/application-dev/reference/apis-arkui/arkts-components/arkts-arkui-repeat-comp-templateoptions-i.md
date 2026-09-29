# TemplateOptions

```TypeScript
interface TemplateOptions
```

When **cachedCount** is set to the maximum number of nodes in the display area of the container component for the current template, **Repeat** achieves maximum reuse efficiency. If there are no nodes of the current template in the display area of the container component, the cache pool is not released, and the application memory increases. The developer needs to adjust it based on the application's requirements for memory usage and component reuse efficiency. It is recommended to set **cachedCount** to the number of nodes in the display area of the container component. Note that it is not recommended to set **cachedCount** to a value less than 2, because this causes frequent creation of new nodes in fast scrolling scenarios, resulting in performance degradation.

> **NOTE:** 
> 
> The `.cachedCount()` attribute of the scrollable container component and the `cachedCount` parameter of the
> `.template()` method of **Repeat** are both used to balance performance and memory, but they have different
> meanings.
> 
> - `.cachedCount()` of the scrollable container component: indicates the size of the preloading area outside the display area of the container component. The child component nodes in this area are located on the component tree.The scrollable container component additionally renders the nodes in this preloading area to improve list scrolling performance.
> 
> - `cachedCount` in `.template()`: indicates the cache pool size of each template of Repeat. When rendering a new child component, **Repeat** first checks whether there are available nodes in the cache pool of the corresponding template. If yes, it reuses them; otherwise, it creates new nodes.

**Since:** 12

<!--Device-unnamed-interface TemplateOptions--><!--Device-unnamed-interface TemplateOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## cachedCount

```TypeScript
cachedCount?: number
```

Maximum number of child component nodes that can be cached in the cache pool of the current template. The value range is [0, +∞), and the default value is the sum of the number of nodes in the display area and the preloaded area of the container component. When the sum of the number of nodes in the display area and the preloaded nodes of the container component increases (during the scrolling process, only child components of partial height are in the display area), **cachedCount** increases accordingly. Note that the **cachedCount** value does not decrease. When a value outside the value range, such as a negative number, is passed in, the default value is used.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TemplateOptions-cachedCount?: number--><!--Device-TemplateOptions-cachedCount?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
