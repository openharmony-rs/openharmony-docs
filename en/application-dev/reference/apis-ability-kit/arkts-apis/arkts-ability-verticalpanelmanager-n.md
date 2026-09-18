# verticalPanelManager

Defines a vertical domain panel manager.

@namespace verticalPanelManager

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AppExtension.VerticalPanel

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { verticalPanelManager } from '@kit.AbilityKit';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [startVerticalPanel](arkts-ability-verticalpanelmanager-startverticalpanel-f-sys.md) | Starts the vertical domain picker with panel config. If the target ability is visible, you can start the target ability; If the target ability is invisible, you need to apply for permission:ohos.permission.START_INVISIBLE_ABILITY to start target invisible ability. If the caller application is in the background, it is not allowed to call this interface. |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [PanelConfig](arkts-ability-verticalpanelmanager-panelconfig-i-sys.md) | Indicates the panel config |
| [PanelStartCallback](arkts-ability-verticalpanelmanager-panelstartcallback-i-sys.md) | The callback of start vertical panel. |
<!--DelEnd-->

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [VerticalType](arkts-ability-verticalpanelmanager-verticaltype-e-sys.md) | Provides vertical type definition. |
<!--DelEnd-->

<!--Del-->
### Constants(System API)

| Name | Description |
| --- | --- |
| [SOURCE_APP_BUNDLE_NAME](arkts-ability-verticalpanelmanager-con-sys.md#source_app_bundle_name) | export the const string of bundleName and provide it for sourceAppInfo. |
| [SOURCE_APP_MODULE_NAME](arkts-ability-verticalpanelmanager-con-sys.md#source_app_module_name) | export the const string of moduleName and provide it for sourceAppInfo. |
| [SOURCE_APP_ABILITY_NAME](arkts-ability-verticalpanelmanager-con-sys.md#source_app_ability_name) | export the const string of abilityName and provide it for sourceAppInfo. |
| [SOURCE_APP_WINDOW_ID](arkts-ability-verticalpanelmanager-con-sys.md#source_app_window_id) | export the const string of windowId and provide it for sourceAppInfo. |
| [SOURCE_APP_SCREEN_MODE](arkts-ability-verticalpanelmanager-con-sys.md#source_app_screen_mode) | export the const string of screenMode and provide it for sourceAppInfo. |
<!--DelEnd-->
