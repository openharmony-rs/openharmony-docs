# SystemAdaptiveOptions

```TypeScript
declare interface SystemAdaptiveOptions
```

Provides parameters for system adaptive adjustments. By default, the system performs adaptive adjustments based on chip performance.

**Since:** 19

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## disableSystemAdaptation

```TypeScript
disableSystemAdaptation?: boolean
```

Whether to disable system adaptive adjustment. Whenever possible, do not include this parameter. This parameter only affects low-computing-power devices, the definition of which is determined by the device manufacturer. On low- computing-power devices, the system automatically decides whether to adjust effects (such as blur) to lower- computing-power alternatives based on conditions including computing power and load. To disable this feature, set this parameter to **true**.

Default value: **false**

**Type:** boolean

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**Widget capability:** This API can be used in ArkTS widgets since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
