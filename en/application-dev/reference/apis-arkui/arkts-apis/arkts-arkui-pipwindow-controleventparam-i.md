# ControlEventParam

Describes the parameters in the callback of the action event of the PiP controller.

**Since:** 12

**System capability:** SystemCapability.Window.SessionManager

## Modules to Import

```TypeScript
import { PiPWindow } from '@kit.ArkUI';
```

## controlType

```TypeScript
controlType: PiPControlType
```

Type of the action event of the PiP controller. The application performs processing based on the component type. For example, if the video play/pause component is touched, the application starts or stops the video.

**Type:** [PiPControlType](arkts-arkui-pipwindow-pipcontroltype-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager

## status

```TypeScript
status?: PiPControlStatus
```

Status of a component that can be switched. For example, for a microphone on/off component group, a camera on/off component group, and a mute/unmute component group, the value **PiPControlStatus.PLAY** means that the component is enabled and **PiPControlStatus.PAUSE** means that the component is disabled. For the hang-up component, the default value is **-1**.

**Type:** [PiPControlStatus](arkts-arkui-pipwindow-pipcontrolstatus-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Window.SessionManager
