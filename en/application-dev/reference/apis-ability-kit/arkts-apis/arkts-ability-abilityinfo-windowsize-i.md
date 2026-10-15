# WindowSize

```TypeScript
export interface WindowSize
```

Describes the window size.

**Since:** 9

<!--Device-unnamed-export interface WindowSize--><!--Device-unnamed-export interface WindowSize-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## maxWindowHeight

```TypeScript
readonly maxWindowHeight: number
```

Maximum height of the window in free window mode. The unit is vp.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-WindowSize-readonly maxWindowHeight: long--><!--Device-WindowSize-readonly maxWindowHeight: long-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## maxWindowRatio

```TypeScript
readonly maxWindowRatio: number
```

Indicates the maximum aspect ratio (width/height) of the window in free-form window state.

Value range: [0, 1]. For example, 0.62 indicates that the maximum window width is 0.62 times the height. This attribute is used to limit the display ratio of the window.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-WindowSize-readonly maxWindowRatio: double--><!--Device-WindowSize-readonly maxWindowRatio: double-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## maxWindowWidth

```TypeScript
readonly maxWindowWidth: number
```

Maximum width of the window in free window mode. The unit is vp.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-WindowSize-readonly maxWindowWidth: long--><!--Device-WindowSize-readonly maxWindowWidth: long-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## minWindowHeight

```TypeScript
readonly minWindowHeight: number
```

Minimum height of the window in free window mode. The unit is vp.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-WindowSize-readonly minWindowHeight: long--><!--Device-WindowSize-readonly minWindowHeight: long-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## minWindowRatio

```TypeScript
readonly minWindowRatio: number
```

Indicates the minimum aspect ratio (width/height) of the window in free-form window state.

Value range: [0, 1]. For example, 0.12 indicates that the minimum window width is 0.12 times the height. This attribute is used to limit the display ratio of the window.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-WindowSize-readonly minWindowRatio: double--><!--Device-WindowSize-readonly minWindowRatio: double-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## minWindowWidth

```TypeScript
readonly minWindowWidth: number
```

Minimum width of the window in free window mode. The unit is vp.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-WindowSize-readonly minWindowWidth: long--><!--Device-WindowSize-readonly minWindowWidth: long-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core
