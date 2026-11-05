# BackupExtensionAbility (System API)

```TypeScript
declare class BackupExtensionAbility
```

Class to be override for backup extension ability.

**Since:** 10

<!--Device-unnamed-declare class BackupExtensionAbility--><!--Device-unnamed-declare class BackupExtensionAbility-End-->

**System capability:** SystemCapability.FileManagement.StorageService.Backup

## ExtensionAbility Usage Restrictions

To ensure system security and stability, BackupExtensionAbility is restricted from abusing system resources. The system controls its capabilities and does not support referencing some modules. For details, see [Appendix](#appendix).

## Modules to Import

```TypeScript
import { BackupExtensionAbility, BundleVersion } from '@kit.CoreFileKit';
```

## getBackupCompatibilityInfo

```TypeScript
getBackupCompatibilityInfo(extInfo: string) : Promise<string>
```

Callback to be called when getting application backup compatibilityInfo. Developer could override this method to provide the backup compatibilityInfo.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-BackupExtensionAbility-getBackupCompatibilityInfo(extInfo: string) : Promise<string>--><!--Device-BackupExtensionAbility-getBackupCompatibilityInfo(extInfo: string) : Promise<string>-End-->

**System capability:** SystemCapability.FileManagement.StorageService.Backup

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| extInfo | string | Yes | Information about the capabilities of the peer. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Return backup compatibilityInfo, support promise. |

## getBackupInfo

```TypeScript
getBackupInfo(): string
```

Callback to be called when getting application backupInfo. Developer could override this method to provide the backupInfo.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-BackupExtensionAbility-getBackupInfo(): string--><!--Device-BackupExtensionAbility-getBackupInfo(): string-End-->

**System capability:** SystemCapability.FileManagement.StorageService.Backup

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| string | Return the backup application's info. |

## getRestoreCompatibilityInfo

```TypeScript
getRestoreCompatibilityInfo(extInfo: string) : Promise<string>
```

Callback to be called when getting application restore compatibilityInfo. Developer could override this method to provide the restore compatibilityInfo.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

<!--Device-BackupExtensionAbility-getRestoreCompatibilityInfo(extInfo: string) : Promise<string>--><!--Device-BackupExtensionAbility-getRestoreCompatibilityInfo(extInfo: string) : Promise<string>-End-->

**System capability:** SystemCapability.FileManagement.StorageService.Backup

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| extInfo | string | Yes | Information about the capabilities of the peer. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Return restore compatibilityInfo, support promise. |

## Appendix

BackupExtensionAbility does not support referencing the following modules.

| Kit | Module |
| --- | --- |
| Ability Kit | [@ohos.abilityAccessCtrl](../../apis-ability-kit/arkts-apis/arkts-ability-abilityaccessctrl.md) |
| Ability Kit | [@ohos.app.ability.missionManager](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-missionmanager.md) |
| Ability Kit | [@ohos.app.ability.quickFixManager](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-quickfixmanager.md) |
| Form Kit | [@ohos.application.formError](../../apis-form-kit/arkts-apis/arkts-form-application-formerror.md) |
| Form Kit | [@ohos.application.formHost](../../apis-form-kit/arkts-apis/arkts-form-application-formhost.md) |
| Ability Kit | [@ohos.application.missionManager](../../apis-ability-kit/arkts-apis/arkts-ability-application-missionmanager.md) |
| Ability Kit | [@ohos.bundle.appControl](../../apis-ability-kit/arkts-apis/arkts-ability-bundle-appcontrol.md) |
| Ability Kit | [@ohos.bundle.bundleMonitor](../../apis-ability-kit/arkts-apis/arkts-ability-bundle-bundlemonitor.md) |
| Ability Kit | [@ohos.bundle.defaultAppManager](../../apis-ability-kit/arkts-apis/arkts-ability-bundle-defaultappmanager.md) |
| Ability Kit | [@ohos.bundle.distributedBundleManager](../../apis-ability-kit/arkts-apis/arkts-ability-bundle-distributedbundlemanager.md) |
| Ability Kit | [@ohos.bundle.freeInstall](../../apis-ability-kit/arkts-apis/arkts-ability-bundle-freeinstall.md) |
| Ability Kit | [@ohos.bundle.innerBundleManager](../../apis-ability-kit/arkts-apis/arkts-ability-bundle-innerbundlemanager.md) |
| Ability Kit | [@ohos.bundle.installer](../../apis-ability-kit/arkts-apis/arkts-ability-bundle-installer.md) |
| Ability Kit | [@ohos.bundle.launcherBundleManager](../../apis-ability-kit/arkts-apis/arkts-ability-bundle-launcherbundlemanager.md) |
| Background Tasks Kit | [@ohos.bundleState](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-bundlestate.md) |
| Ability Kit | [@ohos.distributedBundle](../../apis-ability-kit/arkts-apis/arkts-ability-distributedbundle.md) |
| Ability Kit | [@ohos.distributedMissionManager](../../apis-ability-kit/arkts-apis/arkts-ability-distributedmissionmanager.md) |
| MDM Kit | [@ohos.enterprise.adminManager](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-adminmanager.md) |
| Mdm Kit | [enterprise.dataTimeManager](../../apis-mdm-kit/arkts-apis/arkts-enterprise-datatimemanager.md) |
| Core File Kit | [@ohos.file.fileAccess](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fileaccess.md) |
| Location Kit | [@ohos.geolocation](../../apis-location-kit/arkts-apis/arkts-location-geolocation.md) |
| IME Kit | [@ohos.inputMethod](../../apis-ime-kit/arkts-apis/arkts-ime-inputmethod.md) |
| Audio Kit | [@ohos.multimedia.audio](../../apis-audio-kit/arkts-apis/arkts-audio-multimedia-audio.md) |
| Media Kit | [@ohos.multimedia.media](../../apis-media-kit/arkts-apis/arkts-media-multimedia-media.md) |
| Input Kit | [@ohos.multimodalInput.inputMonitor](../../apis-input-kit/arkts-apis/arkts-input-multimodalinput-inputmonitor.md) |
| Connectivity Kit | [@ohos.nfc.cardEmulation](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-nfc-cardemulation.md) |
| Basic Services Kit | [@ohos.power](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-power.md) |
| Background Tasks Kit | [@ohos.reminderAgent](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-reminderagent.md) |
| Background Tasks Kit | [@ohos.reminderAgentManager](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-reminderagentmanager.md) |
| Background Tasks Kit | [@ohos.resourceschedule.usageStatistics](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-resourceschedule-usagestatistics.md) |
| ArkUI | [@ohos.screen](../../apis-arkui/arkts-apis/arkts-arkui-screen.md) |
| Sensor Service Kit | [@ohos.sensor](../../apis-sensor-service-kit/arkts-apis/arkts-sensorservice-sensor.md) |
| ArkUI | [@ohos.screenshot](../../apis-arkui/arkts-apis/arkts-arkui-screenshot.md) |
| Basic Services Kit | [@ohos.update](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-update.md) |
| ArkUI | [@ohos.window](../../apis-arkui/arkts-apis/arkts-arkui-window.md) |
| Ability Kit | [UIAbilityContext](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext.md) |
| Ability Kit | [ServiceExtensionContext](../../apis-ability-kit/arkts-apis/arkts-ability-serviceextensioncontext.md) |
