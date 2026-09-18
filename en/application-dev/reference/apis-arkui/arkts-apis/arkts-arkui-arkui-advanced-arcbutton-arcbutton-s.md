# ArcButton

The **ArcButton** component offers various button styles, such as emphasized, normal, and warning. It is recommended for devices with circular screens.

> **NOTE:** 

> - This component can be used on phones, PCs, 2-in-1 devices, tablets, TVs, and wearables. In API version 22 and earlier versions, a compilation warning will be reported when this component is used on phones, PCs, 2-in-1devices, tablets, and TVs, but the component can still run properly.

**Since:** 18

**Decorator:** @Component

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## Modules to Import

```TypeScript
import { ArcButton, ArcButtonOptions, ArcButtonProgressConfig, ArcButtonPosition, ArcButtonStyleMode, ArcButtonStatus } from '@kit.ArkUI';
```

## options

```TypeScript
readonly options: ArcButtonOptions
```

Text, background color, shadow, and other parameters of the **ArcButton** component.

**Type:** [ArcButtonOptions](arkts-arkui-arkui-advanced-arcbutton-arcbuttonoptions-c.md)

**Since:** 18

**Decorator:** @Require

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle
