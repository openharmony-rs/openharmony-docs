# FloatViewStateChangeInfo

Provides the state change information of the float view.

**Since:** 26.0.0

**System capability:** SystemCapability.Window.SessionManager

## Modules to Import

```TypeScript
import { floatView } from '@kit.ArkUI';
```

## state

```TypeScript
state: FloatViewState
```

State of the float view.

**Type:** [FloatViewState](arkts-arkui-floatview-floatviewstate-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

## stopReason

```TypeScript
stopReason: string
```

Reason why the float view stops. This parameter is valid only when **state** is set to **FloatViewState.STOPPED**. In other states, this parameter is an empty string by default. The stop reasons and their meanings are as follows:

**"APP_STOP"**: The application proactively stops the float view.

**"STOP_IN_SIDEBAR"**: The float view is closed in the sidebar.

**"TITLE_BAR_STOP_CLICK"**: The float view is closed by clicking the close button on the title bar.

**"DUMPSTER_STOP"**: The float view is dragged to the trash can.

**"REPLACE_STOP"**: The float view is occupied by another float view.

**"FLOATING_BALL_STOP"**: The float view stops when the bound floating ball stops.

**"MAIN_WINDOW_DESTROY_STOP"**: The float view stops after the main window associated with the context is destroyed.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager
