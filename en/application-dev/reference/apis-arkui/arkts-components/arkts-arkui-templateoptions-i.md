# TemplateOptions

When **cachedCount** is set to the maximum number of nodes in the display area of the container component for the current template, **Repeat** achieves maximum reuse efficiency. If there are no nodes of the current template in the container component's display area, the cache list is not released, which increases application memory usage. You are advised to set **cachedCount** to the number of nodes within the container component's display area and adjust the value according to the actual situation. Yet, setting **cachedCount** to less than 2 is not recommended, as this may lead to the frequent node creation during rapid scrolling and result in performance degradation.

> **NOTE:** 
> 
> The **.cachedCount()** attribute of the scrollable container component and the **cachedCount** parameter of the
> **.template()** method of **Repeat** are used to balance performance and memory, but their meanings are different.
> 
> - **.cachedCount()** of the scrollable container component: size of the preloading area outside the display area of the container component. The child component nodes in this area are located in the component tree. The scrollable container component renders nodes in these preloading areas, improving the list scrolling performance.
> 
> - cachedCount in .template(): size of the cache pool for each template in the **Repeat** component. When rendering a new child component, **Repeat** checks whether there are available nodes in the cache pool for the corresponding template. If yes, the nodes are reused. If no, new nodes are created.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## cachedCount

```TypeScript
cachedCount?: number
```

Maximum number of child component nodes that can be cached in the cache pool of the current template. The value range is [0, +∞). The default value is the sum of the number of nodes in the display area of the container component and the number of nodes in the preloading area. When this sum increases (during the scrolling, when only part of the height of child components is within the display area), the value of **cachedCount** also increases accordingly. Note that the value of **cachedCount** does not decrease.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
