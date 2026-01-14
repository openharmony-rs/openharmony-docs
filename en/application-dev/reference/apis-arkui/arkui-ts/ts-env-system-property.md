# \@Env: Environment Variable
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @liwenzhen3-->
<!--Designer: @s10021109-->
<!--Tester: @zhangwenhan12-->
<!--Adviser: @zhang_yixin13-->

> **NOTE**
> 
> The initial APIs of this module are supported since API version 22. Newly added APIs will be marked with a superscript to indicate their earliest API version.

For details about the development, see [\@Env](../../../ui/arkts-env-system-property.md).


## \@Env
Env: EnvDecorator

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

|Name|Type|Description|
| ----- | ----- | ------ |
|Env|[EnvDecorator](#envdecorator)| Environment variable decorator.|

**Example**

```ts
import { uiObserver } from '@kit.ArkUI';

@Entry
@Component
struct Index {
  @Env(SystemProperties.BREAK_POINT) breakpoint: uiObserver.WindowSizeLayoutBreakpointInfo;

  build() {}
}
```

## EnvDecorator
type EnvDecorator = (value: SystemProperties) => PropertyDecorator

Defines the @Env decorator type.

**Model restriction**: This API can be used only in the stage model.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                 | Mandatory| Description         |
| -------- | -------------------- | ---- | --------- |
| value    |      [SystemProperties](./ts-env-system-property.md#systemproperties)          | Yes  |      Name of the environment variable.   |

**Return value**

|Type|Description|
| ----- | ----- |
| PropertyDecorator| Property decorator.|

**Error codes**

| ID| Error Message|
| ------- | -------------------------------- |
|140000|Invalid key for @Env|

## SystemProperties

Defines the enumerated values of the environment variable.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name       | Value  | Description                                      |
| ----------- | ---- | ------------------------------------------------------------ |
|BREAK_POINT|'system.arkui.breakpoint'|[@Env](#env) variable parameter. You can obtain the [WindowSizeLayoutBreakpointInfo](../js-apis-arkui-observer.md#windowsizelayoutbreakpointinfo22) instance through \@Env(SystemProperties.BREAK_POINT).<br>When this decorator is declared in [\@Component](../../../ui/state-management/arkts-create-custom-components.md#component) or [\@ComponentV2](../../../ui/state-management/arkts-create-custom-components.md#componentv2), it is used to obtain the size layout breakpoint information of the window where the current custom component is located.<br>**Atomic service API**: This API can be used in atomic services since API version 22.|
|WINDOW_SIZE<sup>23+</sup>|'system.window.size'|[@Env](#env) variable parameter. You can obtain the [`SizeInVP`](../arkts-apis-window-i.md#sizeinvp23) instance through \@Env(SystemProperties.WINDOW_SIZE).<br>When this decorator is declared in [\@Component](../../../ui/state-management/arkts-create-custom-components.md#component) or [\@ComponentV2](../../../ui/state-management/arkts-create-custom-components.md#componentv2), it is used to obtain the size (in vp) of the window where the current custom component is located.<br>**Model restriction**: This API can be used only in the stage model.|
|WINDOW_SIZE_PX<sup>23+</sup>|'system.window.size.px'|[@Env](#env) variable parameter. You can obtain the [Size](../arkts-apis-window-i.md#size7) instance through \@Env(SystemProperties.WINDOW_SIZE_PX).<br>When this decorator is declared in [\@Component](../../../ui/state-management/arkts-create-custom-components.md#component) or [\@ComponentV2](../../../ui/state-management/arkts-create-custom-components.md#componentv2), it is used to obtain the size (in px) of the window where the current custom component is located.<br>**Model restriction**: This API can be used only in the stage model.|
|WINDOW_AVOID_AREA<sup>23+</sup>|'system.window.avoidarea'|[@Env](#env) variable parameter. You can obtain the [UIEnvWindowAvoidAreaInfoVP](../arkts-apis-window-i.md#uienvwindowavoidareainfovp23) instance through \@Env(SystemProperties.WINDOW_AVOID_AREA).<br>When this decorator is declared in [\@Component](../../../ui/state-management/arkts-create-custom-components.md#component) or [\@ComponentV2](../../../ui/state-management/arkts-create-custom-components.md#componentv2), it is used to obtain the avoid area (in vp) of the window where the current custom component is located.<br>**Model restriction**: This API can be used only in the stage model.|
|WINDOW_AVOID_AREA_PX<sup>23+</sup>|'system.window.avoidarea.px'|[@Env](#env) variable parameter. You can obtain the [UIEnvWindowAvoidAreaInfoPX](../arkts-apis-window-i.md#uienvwindowavoidareainfopx23) instance through \@Env(SystemProperties.WINDOW_AVOID_AREA_PX).<br>When this decorator is declared in [\@Component](../../../ui/state-management/arkts-create-custom-components.md#component) or [\@ComponentV2](../../../ui/state-management/arkts-create-custom-components.md#componentv2), it is used to obtain the avoid area (in px) of the window where the current custom component is located.<br>**Model restriction**: This API can be used only in the stage model.|

<!--no_check-->