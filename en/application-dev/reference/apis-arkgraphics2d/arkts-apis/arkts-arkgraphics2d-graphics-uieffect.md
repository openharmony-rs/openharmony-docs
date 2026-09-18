# @ohos.graphics.uiEffect

This module provides basic capabilities for component effects, including blur, brightening, and more. Effects are categorized into the Filter and VisualEffect classes, and effects of the same class can be cascaded under an instance of that effect class. Using this module, you can quickly implement complex visual effects without needing to master underlying image processing algorithms, reducing development complexity and improving user experience. In actual development, blur can be used for background blurring, and brightening can be used for bright screen display, etc.

- [Filter](arkts-arkgraphics2d-uieffect-filter-i.md): Used to add specified Filter effects to a component.  
- [VisualEffect](arkts-arkgraphics2d-uieffect-visualeffect-i-sys.md): Used to add specified VisualEffect effects to a component.

## Modules to Import

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';
```

## Summary

### Namespaces

| Name | Description |
| --- | --- |
| [uiEffect](arkts-arkgraphics2d-uieffect-n.md) | This module provides basic capabilities for component effects, including blur, brightening, and more. Effects are categorized into the Filter and VisualEffect classes, and effects of the same class can be cascaded under an instance of that effect class. Using this module, you can quickly implement complex visual effects without needing to master underlying image processing algorithms, reducing development complexity and improving user experience. In actual development, blur can be used for background blurring, and brightening can be used for bright screen display, etc. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [BrightnessBlenderParam](arkts-arkgraphics2d-graphics-uieffect-brightnessblenderparam-i-sys.md) | Parameter list of BrightnessBlender, used to configure various properties of the brightness effect, including grayscale adjustment coefficients, saturation, and blending ratio parameters. |
<!--DelEnd-->
