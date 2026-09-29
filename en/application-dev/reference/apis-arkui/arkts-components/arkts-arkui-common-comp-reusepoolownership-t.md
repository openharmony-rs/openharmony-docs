# ReusePoolOwnership

```TypeScript
declare type ReusePoolOwnership = 'shared' | 'perInstance'
```

Defines the ownership type of the global reuse pool.

'shared': All instances of the **@Component** / **@ComponentV2** class share the same reuse pool instance. This is applicable to scenarios where multiple component instances of the same type need to reuse the same resources, maximizing reuse pool utilization and reducing memory usage.'perInstance': Each instance of **@Component** / **@ComponentV2** has an independent reuse pool instance. This is applicable to scenarios where the reuse resources of each component instance need to be isolated, preventing reuse resources of different instances from affecting each other.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-unnamed-declare type ReusePoolOwnership = 'shared' | 'perInstance'--><!--Device-unnamed-declare type ReusePoolOwnership = 'shared' | 'perInstance'-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

| Type | Description |
| --- | --- |
| 'shared' |  |
| 'perInstance' |  |
