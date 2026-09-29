# FloatViewLimits

```TypeScript
interface FloatViewLimits
```

Provides the limits of the float view.

**Since:** 26.0.0

<!--Device-floatView-interface FloatViewLimits--><!--Device-floatView-interface FloatViewLimits-End-->

**System capability:** SystemCapability.Window.SessionManager

## Modules to Import

```TypeScript
import { floatView } from '@kit.ArkUI';
```

## maxSize

```TypeScript
maxSize: window.Size
```

Maximum size of the float view.

**Type:** [window.Size](arkts-arkui-window-size-i.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-FloatViewLimits-maxSize: window.Size--><!--Device-FloatViewLimits-maxSize: window.Size-End-->

**System capability:** SystemCapability.Window.SessionManager

## minSize

```TypeScript
minSize: window.Size
```

Minimum size of the float view.

**Type:** [window.Size](arkts-arkui-window-size-i.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-FloatViewLimits-minSize: window.Size--><!--Device-FloatViewLimits-minSize: window.Size-End-->

**System capability:** SystemCapability.Window.SessionManager

## ratioLimits

```TypeScript
ratioLimits: Array<RatioLimit>
```

Aspect ratio range of the float view.

**Type:** Array&lt;[RatioLimit](arkts-arkui-floatview-ratiolimit-i.md)&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-FloatViewLimits-ratioLimits: Array<RatioLimit>--><!--Device-FloatViewLimits-ratioLimits: Array<RatioLimit>-End-->

**System capability:** SystemCapability.Window.SessionManager
