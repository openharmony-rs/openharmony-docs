# AutoFillTriggerType

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @hanchen45-->
<!--Designer: @ccllee1-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=e2c3267fc728379ed661f6395560cc18d085c54a translatedAt=2026-09-03T11:47:31.276Z pushedAt=2026-09-05T10:47:30.696Z -->

Enumerates the launch types of the auto-fill service, which are selected based on user gestures.

**Since:** 26.0.0

## Modules to Import

```ts
import { autoFillManager } from '@kit.AbilityKit';
```

## AutoFillTriggerType

Enumerates the trigger types of the auto-fill service, including AUTO_REQUEST, MANUAL_REQUEST, and PASTE_REQUEST. AutoFillTriggerType is the enum type of [FillRequest.triggerType](./js-apis-inner-application-autoFillRequest.md#fillrequest).

**Since:** 26.0.0

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Ability.AbilityRuntime.AbilityCore

**Model restriction:** This API can be used only in the stage model.

| Name           | Value | Description                               |
| -------------- | ----- | --------------------------------- |
| AUTO_REQUEST   | 0 | Automatically launches the auto-fill service. The service can be automatically launched after the [TextInput](../../reference/apis-arkui/arkui-ts/ts-basic-components-textinput.md) component gains focus. |
| MANUAL_REQUEST | 1 | Manually launches the auto-fill service. The service can be launched by long pressing any input component to bring up the secondary menu and selecting auto-fill. |
| PASTE_REQUEST  | 2 | Launches the auto-fill service by pasting. The service is launched only when the user long presses any input component to bring up the secondary menu and selects paste, after having long pressed a username or password in the password vault and selected secure copy. |
