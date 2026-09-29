# KeyEventPolicy

```TypeScript
interface KeyEventPolicy
```

Enumerates key event handling policies. When a key event occurs, only the keys for which the key event handling policy has been delivered are intercepted. For key events where no handling policy has been delivered, the system executes its original response logic.

**Since:** 23

<!--Device-systemManager-interface KeyEventPolicy--><!--Device-systemManager-interface KeyEventPolicy-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## Modules to Import

```TypeScript
import { systemManager } from '@kit.MDMKit';
```

## keyCode

```TypeScript
keyCode: KeyCode
```

Key code.

**Type:** [KeyCode](arkts-mdm-systemmanager-keycode-e.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-KeyEventPolicy-keyCode: KeyCode--><!--Device-KeyEventPolicy-keyCode: KeyCode-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## keyPolicy

```TypeScript
keyPolicy: KeyPolicy
```

Key policy.

**Type:** [KeyPolicy](arkts-mdm-systemmanager-keypolicy-e.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-KeyEventPolicy-keyPolicy: KeyPolicy--><!--Device-KeyEventPolicy-keyPolicy: KeyPolicy-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager
