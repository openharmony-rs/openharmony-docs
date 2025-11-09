# Window Subsystem Changelog

## cl.window.1 Window Launch Behavior Changed for Full-Screen and Split Modes on PCs/2-in-1 Devices

**Access Level**

Public API

**Reason for the Change**

On PCs/2-in-1 devices, when configuring **fullscreen** and **split** in the [supportWindowMode](../../../application-dev/quick-start/module-configuration-file.md#abilities) property of **module.json5** or configuring **FULL_SCREEN** and **SPLIT** in the [supportWindowModes](../../../application-dev/reference/apis-ability-kit/js-apis-app-ability-startOptions.md) property of **startOptions**, windows were previously launching in free window mode, which did not match the expected behavior.

**Impact of the Change**

This change requires application adaptation.

Before change: When **fullscreen** and **split** were configured in the **supportWindowMode** property of **module.json5** or **FULL_SCREEN** and **SPLIT** were configured in the **supportWindowModes** property of **startOptions**, windows would launch in free window mode on PCs/2-in-1 devices.

After change: When **fullscreen** and **split** are configured in the **supportWindowMode** property of **module.json5** or **FULL_SCREEN** and **SPLIT** are configured in the **supportWindowModes** property of **startOptions**, windows will now launch in full-screen mode on PCs/2-in-1 devices.

**Start API Level**

API version 9 for the **supportWindowMode** property of **module.json5**

API version 14 for the **supportWindowModes** property of **startOptions**

**Change Since**

OpenHarmony SDK 5.1.0.52

**Key API/Component Changes**

**supportWindowMode** in **module.json5**

**supportWindowModes** property in **@ohos.app.ability.StartOptions**

**Adaptation Guide**

In API version 15 and later versions, if **fullscreen** and **split** are configured in the **supportWindowMode** property of **module.json5** or if **FULL_SCREEN** and **SPLIT** are configured in the **supportWindowModes** property of **startOptions**, windows will now launch in full-screen mode on PCs/2-in-1 devices.

If free window mode is desired, you must add **floating** to **supportWindowMode** in **module.json5** or add **FLOATING** to **supportWindowModes** in **startOptions**.
