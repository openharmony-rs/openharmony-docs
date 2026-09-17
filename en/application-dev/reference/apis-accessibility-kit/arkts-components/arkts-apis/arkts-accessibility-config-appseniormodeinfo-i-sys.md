# AppSeniorModeInfo (System API)

Senior mode state information of an app.

**Since:** 26.0.0

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { config } from '@kit.AccessibilityKit';
```

## appIndex

```TypeScript
appIndex?: number
```

Clone index of the app bundle. The value is an integer greater than or equal to 0. If not specified, the default value is **0**.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## bundleName

```TypeScript
bundleName: string
```

Bundle name of the app, used to identify the app, in the format of **'com.example.myapplication'**.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.

## seniorModeState

```TypeScript
seniorModeState: boolean
```

Senior mode enabled state of the app. The value **true** indicates enabled, and **false** indicates disabled.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BarrierFree.Accessibility.Core

**System API:** This is a system API.
