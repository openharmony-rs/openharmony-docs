# Constants

## ANIMATOR_DURATION_SCALE

```TypeScript
const ANIMATOR_DURATION_SCALE: string
```

Indicates the scaling factor for the animation duration.

<p>This affects the start delay and duration of all such animations. If the value is `0`, the animation ends immediately. The default value is `1`.

**Type:** string

**Since:** 7

**Deprecated since:** 21

**System capability:** SystemCapability.Applications.Settings.Core

## AUTO_SCREEN_BRIGHTNESS

```TypeScript
const AUTO_SCREEN_BRIGHTNESS: string
```

Specifies whether automatic screen brightness adjustment is enabled.

<p>If the value is `1`, automatic adjustment is enabled. If the value is `0`, automatic adjustment is disabled.

**Type:** string

**Since:** 7

**System capability:** SystemCapability.Applications.Settings.Core

## AUTO_SCREEN_BRIGHTNESS_MODE

```TypeScript
const AUTO_SCREEN_BRIGHTNESS_MODE: number
```

Indicates the value of `AUTO_SCREEN_BRIGHTNESS` when automatic screen brightness adjustment is used.

**Type:** number

**Since:** 7

**System capability:** SystemCapability.Applications.Settings.Core

## DEFAULT_SCREEN_ROTATION

```TypeScript
const DEFAULT_SCREEN_ROTATION: string
```

Indicates the screen rotation when no other policy is available.

<p>This constant is invalid when auto-rotation is enabled. When auto-rotation is disabled, the following values are available:

&lt;ul&gt; &lt;li&gt;`0` - The screen rotates 0 degrees. &lt;li&gt;`1` - The screen rotates 90 degrees. &lt;li&gt;`2` - The screen rotates 180 degrees. &lt;li&gt;`3` - The screen rotates 270 degrees. &lt;/ul&gt;

**Type:** string

**Since:** 7

**Deprecated since:** 21

**System capability:** SystemCapability.Applications.Settings.Core

## DISPLAY_INVERSION_STATUS

```TypeScript
const DISPLAY_INVERSION_STATUS: string
```

Specifies whether display color inversion is enabled.

<p>If the value is `1`, display color inversion is enabled. If the value is `0`, display color inversion is disabled.

**Type:** string

**Since:** 7

**Deprecated since:** 21

**System capability:** SystemCapability.Applications.Settings.Core

## FONT_SCALE

```TypeScript
const FONT_SCALE: string
```

Indicates the scaling factor of fonts, which is a float number.

**Type:** string

**Since:** 7

**System capability:** SystemCapability.Applications.Settings.Core

## MANUAL_SCREEN_BRIGHTNESS_MODE

```TypeScript
const MANUAL_SCREEN_BRIGHTNESS_MODE: number
```

Indicates the value of `AUTO_SCREEN_BRIGHTNESS` when manual screen brightness adjustment is used.

**Type:** number

**Since:** 7

**System capability:** SystemCapability.Applications.Settings.Core

## SCREEN_BRIGHTNESS_STATUS

```TypeScript
const SCREEN_BRIGHTNESS_STATUS: string
```

Indicates the screen brightness. The value ranges from 0 to 255.

**Type:** string

**Since:** 7

**System capability:** SystemCapability.Applications.Settings.Core

## SCREEN_OFF_TIMEOUT

```TypeScript
const SCREEN_OFF_TIMEOUT: string
```

Indicates the duration that the device waits before going to sleep after a period of inactivity, in milliseconds.

**Type:** string

**Since:** 7

**System capability:** SystemCapability.Applications.Settings.Core

## TRANSITION_ANIMATION_SCALE

```TypeScript
const TRANSITION_ANIMATION_SCALE: string
```

Indicates the scaling factor for transition animations. If the value is `0`, transition animations are disabled.

**Type:** string

**Since:** 7

**Deprecated since:** 21

**System capability:** SystemCapability.Applications.Settings.Core

## WINDOW_ANIMATION_SCALE

```TypeScript
const WINDOW_ANIMATION_SCALE: string
```

Indicates the scaling factor for normal window animations. If the value is `0`, window animations are disabled.

**Type:** string

**Since:** 7

**Deprecated since:** 21

**System capability:** SystemCapability.Applications.Settings.Core
