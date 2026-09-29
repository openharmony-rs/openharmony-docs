# ExtensionAbilityType

```TypeScript
export enum ExtensionAbilityType
```

Enumerates the types of ExtensionAbility components.

<!--RP2--><!--RP2End-->

**Since:** 9

<!--Device-bundleManager-export enum ExtensionAbilityType--><!--Device-bundleManager-export enum ExtensionAbilityType-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## FORM

```TypeScript
FORM = 0
```

[FormExtensionAbility](../../apis-form-kit/arkts-apis/arkts-form-app-form-formextensionability-formextensionability-c.md): provides APIs for widget development.

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-ExtensionAbilityType-FORM = 0--><!--Device-ExtensionAbilityType-FORM = 0-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## WORK_SCHEDULER

```TypeScript
WORK_SCHEDULER = 1
```

[WorkSchedulerExtensionAbility](../../apis-background-tasks-kit/arkts-apis/arkts-backgroundtasks-workschedulerextensionability-c.md): provides extended capabilities related to deferred tasks, enabling applications to execute non-real-time tasks when the system is idle.

**Since:** 9

<!--Device-ExtensionAbilityType-WORK_SCHEDULER = 1--><!--Device-ExtensionAbilityType-WORK_SCHEDULER = 1-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## INPUT_METHOD

```TypeScript
INPUT_METHOD = 2
```

[InputMethodExtensionAbility](../../apis-ime-kit/arkts-apis/arkts-ime-inputmethodextensionability-c.md): provides extended capabilities related to input method applications.

**Since:** 9

<!--Device-ExtensionAbilityType-INPUT_METHOD = 2--><!--Device-ExtensionAbilityType-INPUT_METHOD = 2-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## SERVICE

```TypeScript
SERVICE = 3
```

ServiceExtensionAbility: provides extended capabilities related to background services.

**Since:** 9

<!--Device-ExtensionAbilityType-SERVICE = 3--><!--Device-ExtensionAbilityType-SERVICE = 3-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## ACCESSIBILITY

```TypeScript
ACCESSIBILITY = 4
```

AccessibilityExtensionAbility: provides extended capabilities related to accessibility services, supporting access and operation of the foreground UI.

**Since:** 9

<!--Device-ExtensionAbilityType-ACCESSIBILITY = 4--><!--Device-ExtensionAbilityType-ACCESSIBILITY = 4-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## DATA_SHARE

```TypeScript
DATA_SHARE = 5
```

DataShareExtensionAbility: provides extended capabilities related to data sharing, providing data reading and writing services.

**Since:** 9

<!--Device-ExtensionAbilityType-DATA_SHARE = 5--><!--Device-ExtensionAbilityType-DATA_SHARE = 5-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## FILE_SHARE

```TypeScript
FILE_SHARE = 6
```

FileShareExtensionAbility: provides extended capabilities related to file sharing between applications. This ability is reserved and supported only by system applications.

**Since:** 9

<!--Device-ExtensionAbilityType-FILE_SHARE = 6--><!--Device-ExtensionAbilityType-FILE_SHARE = 6-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## STATIC_SUBSCRIBER

```TypeScript
STATIC_SUBSCRIBER = 7
```

StaticSubscriberExtensionAbility: provides extended capabilities related to static broadcast, used to handle static events such as startup events.

**Since:** 9

<!--Device-ExtensionAbilityType-STATIC_SUBSCRIBER = 7--><!--Device-ExtensionAbilityType-STATIC_SUBSCRIBER = 7-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## WALLPAPER

```TypeScript
WALLPAPER = 8
```

WallpaperExtensionAbility: provides extended capabilities to implement wallpapers displayed on home screen. This ability is reserved and supported only by system applications.

**Since:** 9

<!--Device-ExtensionAbilityType-WALLPAPER = 8--><!--Device-ExtensionAbilityType-WALLPAPER = 8-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## BACKUP

```TypeScript
BACKUP = 9
```

[BackupExtensionAbility](../../apis-core-file-kit/arkts-apis/arkts-corefile-application-backupextensionability-backupextensionability-c.md): provides extended capabilities for data backup and restore.

**Since:** 9

<!--Device-ExtensionAbilityType-BACKUP = 9--><!--Device-ExtensionAbilityType-BACKUP = 9-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## WINDOW

```TypeScript
WINDOW = 10
```

WindowExtensionAbility: provides extended capabilities that allow system applications to pull up and embed UIs of other applications.

**Since:** 9

<!--Device-ExtensionAbilityType-WINDOW = 10--><!--Device-ExtensionAbilityType-WINDOW = 10-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## ENTERPRISE_ADMIN

```TypeScript
ENTERPRISE_ADMIN = 11
```

[EnterpriseAdminExtensionAbility](../../apis-mdm-kit/arkts-apis/arkts-mdm-enterprise-enterpriseadminextensionability-enterpriseadminextensionability-c.md): provides extended capabilities for processing enterprise management events, such as application installation events on devices and events indicating too many incorrect screen-lock password attempts.

**Since:** 9

<!--Device-ExtensionAbilityType-ENTERPRISE_ADMIN = 11--><!--Device-ExtensionAbilityType-ENTERPRISE_ADMIN = 11-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## THUMBNAIL

```TypeScript
THUMBNAIL = 13
```

ThumbnailExtensionAbility: provides extended capabilities for offering thumbnails for files. This ability is reserved and supported only by system applications.

**Since:** 9

<!--Device-ExtensionAbilityType-THUMBNAIL = 13--><!--Device-ExtensionAbilityType-THUMBNAIL = 13-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## PREVIEW

```TypeScript
PREVIEW = 14
```

PreviewExtensionAbility: provides extended capabilities for file preview so that other applications can be embedded and displayed in the current application. This ability is reserved and supported only by system applications.

**Since:** 9

<!--Device-ExtensionAbilityType-PREVIEW = 14--><!--Device-ExtensionAbilityType-PREVIEW = 14-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## PRINT

```TypeScript
PRINT = 15
```

PrintExtensionAbility: provides extended capabilities for printing photos and documents in office scenarios. This ability is supported only by system applications.

**Since:** 10

<!--Device-ExtensionAbilityType-PRINT = 15--><!--Device-ExtensionAbilityType-PRINT = 15-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## SHARE

```TypeScript
SHARE = 16
```

[ShareExtensionAbility](arkts-ability-app-ability-shareextensionability-shareextensionability-c.md): provides sharing service templates based on the UIExtensionAbility.

**Since:** 10

<!--Device-ExtensionAbilityType-SHARE = 16--><!--Device-ExtensionAbilityType-SHARE = 16-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## PUSH

```TypeScript
PUSH = 17
```

PushExtensionAbility: provides extended capabilities for pushing scenario-specific messages. This ability is reserved and supported only by system applications.

**Since:** 10

<!--Device-ExtensionAbilityType-PUSH = 17--><!--Device-ExtensionAbilityType-PUSH = 17-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## DRIVER

```TypeScript
DRIVER = 18
```

[DriverExtensionAbility](../../apis-driver-development-kit/arkts-apis/arkts-driverdevelopment-app-ability-driverextensionability-driverextensionability-c.md): provides extended capabilities for the peripheral driver. When an application configures an ExtensionAbility of the driver type, it is recognized as a driver application. Driver applications do not differentiate between users during installation, uninstall, and recovery. Moreover, when a new user account is created, the existing driver applications on the device are installed for that user. For example, when a sub-user is created, the driver applications already installed by the primary user is automatically installed for the sub-user. If a driver application is uninstalled for a sub- user, it is also removed for the primary user.

**Since:** 10

<!--Device-ExtensionAbilityType-DRIVER = 18--><!--Device-ExtensionAbilityType-DRIVER = 18-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## ACTION

```TypeScript
ACTION = 19
```

[ActionExtensionAbility](arkts-ability-app-ability-actionextensionability-actionextensionability-c.md): provides custom action service templates based on the UIExtensionAbility.

**Since:** 10

<!--Device-ExtensionAbilityType-ACTION = 19--><!--Device-ExtensionAbilityType-ACTION = 19-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## ADS_SERVICE

```TypeScript
ADS_SERVICE = 20
```

AdsServiceExtensionAbility: provides background customized ad services for external systems. This ability is supported only by system applications.

**Since:** 11

<!--Device-ExtensionAbilityType-ADS_SERVICE = 20--><!--Device-ExtensionAbilityType-ADS_SERVICE = 20-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## EMBEDDED_UI

```TypeScript
EMBEDDED_UI = 21
```

[EmbeddedUIExtensionAbility](arkts-ability-app-ability-embeddeduiextensionability-embeddeduiextensionability-c.md): provides extended capabilities for the embeddable UI across process.

**Since:** 12

<!--Device-ExtensionAbilityType-EMBEDDED_UI = 21--><!--Device-ExtensionAbilityType-EMBEDDED_UI = 21-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## INSIGHT_INTENT_UI

```TypeScript
INSIGHT_INTENT_UI = 22
```

InsightIntentUIExtensionAbility: provides extended capabilities that enable applications to be called by Celia intents so as to be displayed in windows.

**Since:** 12

<!--Device-ExtensionAbilityType-INSIGHT_INTENT_UI = 22--><!--Device-ExtensionAbilityType-INSIGHT_INTENT_UI = 22-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## FENCE

```TypeScript
FENCE = 24
```

[FenceExtensionAbility](../../apis-location-kit/arkts-apis/arkts-location-app-ability-fenceextensionability-fenceextensionability-c.md): provides geofence- related capabilities. It inherits from ExtensionAbility.

**Since:** 18

<!--Device-ExtensionAbilityType-FENCE = 24--><!--Device-ExtensionAbilityType-FENCE = 24-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## CALLER_INFO_QUERY

```TypeScript
CALLER_INFO_QUERY = 25
```

CallerInfoQueryExtensionAbility: provides the capability of querying incoming and outgoing call information.

**Since:** 19

<!--Device-ExtensionAbilityType-CALLER_INFO_QUERY = 25--><!--Device-ExtensionAbilityType-CALLER_INFO_QUERY = 25-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## ASSET_ACCELERATION

```TypeScript
ASSET_ACCELERATION = 26
```

AssetAccelerationExtensionAbility: provides extended capabilities of pre-downloading background resources when the device is idle.

**Since:** 18

<!--Device-ExtensionAbilityType-ASSET_ACCELERATION = 26--><!--Device-ExtensionAbilityType-ASSET_ACCELERATION = 26-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## FORM_EDIT

```TypeScript
FORM_EDIT = 27
```

[FormEditExtensionAbility](../../apis-form-kit/arkts-apis/arkts-form-app-form-formeditextensionability-formeditextensionability-c.md): provides extended capabilities related to widget editing. It inherits from UIExtensionAbility.

**Since:** 18

<!--Device-ExtensionAbilityType-FORM_EDIT = 27--><!--Device-ExtensionAbilityType-FORM_EDIT = 27-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## DISTRIBUTED

```TypeScript
DISTRIBUTED = 28
```

[DistributedExtensionAbility](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-application-distributedextensionability-distributedextensionability-c.md): provides extended capabilities for distributed services and lifecycle callbacks for creation, destruction, and connection of the DistributedExtensionAbility.

**Since:** 20

<!--Device-ExtensionAbilityType-DISTRIBUTED = 28--><!--Device-ExtensionAbilityType-DISTRIBUTED = 28-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## APP_SERVICE

```TypeScript
APP_SERVICE = 29
```

[AppServiceExtensionAbility](arkts-ability-app-ability-appserviceextensionability-appserviceextensionability-c.md): provides backend service capabilities for enterprise common applications.

**Since:** 20

<!--Device-ExtensionAbilityType-APP_SERVICE = 29--><!--Device-ExtensionAbilityType-APP_SERVICE = 29-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## LIVE_FORM

```TypeScript
LIVE_FORM = 30
```

[LiveFormExtensionAbility](../../apis-form-kit/arkts-apis/arkts-form-app-form-liveformextensionability-liveformextensionability-c.md): provides extended capabilities for interactive widgets, and provides lifecycle callbacks for creating and destroying interactive widgets.

**Since:** 20

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-ExtensionAbilityType-LIVE_FORM = 30--><!--Device-ExtensionAbilityType-LIVE_FORM = 30-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## SELECTION

```TypeScript
SELECTION = 31
```

SelectionExtensionAbility: provides extended capabilities for text selection popup.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-ExtensionAbilityType-SELECTION = 31--><!--Device-ExtensionAbilityType-SELECTION = 31-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## WEB_NATIVE_MESSAGING

```TypeScript
WEB_NATIVE_MESSAGING = 32
```

[WebNativeMessagingExtensionAbility](../../apis-arkweb/arkts-apis/arkts-arkweb-web-webnativemessagingextensionability-webnativemessagingextensionability-c.md): provides extended capabilities for web native message communication.

**Since:** 21

<!--Device-ExtensionAbilityType-WEB_NATIVE_MESSAGING = 32--><!--Device-ExtensionAbilityType-WEB_NATIVE_MESSAGING = 32-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## FAULT_LOG

```TypeScript
FAULT_LOG = 33
```

[FaultLogExtensionAbility](../../apis-performance-analysis-kit/arkts-apis/arkts-performanceanalysis-hiviewdfx-faultlogextensionability-faultlogextensionability-c.md): provides extended capabilities for delayed fault notifications.

**Since:** 21

<!--Device-ExtensionAbilityType-FAULT_LOG = 33--><!--Device-ExtensionAbilityType-FAULT_LOG = 33-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## NOTIFICATION_SUBSCRIBER

```TypeScript
NOTIFICATION_SUBSCRIBER = 34
```

[NotificationSubscriberExtensionAbility](../../apis-notification-kit/arkts-apis/arkts-notification-application-notificationsubscriberextensionability-notificationsubscriberextensionability-c.md): provides extended capabilities for notification subscription.

**Since:** 22

<!--Device-ExtensionAbilityType-NOTIFICATION_SUBSCRIBER = 34--><!--Device-ExtensionAbilityType-NOTIFICATION_SUBSCRIBER = 34-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## CRYPTO

```TypeScript
CRYPTO = 35
```

[CryptoExtensionAbility](../../../security/UniversalKeystoreKit/huks-extension-ability-support-dev.md): provides extended capabilities for external key management.

**Since:** 22

<!--Device-ExtensionAbilityType-CRYPTO = 35--><!--Device-ExtensionAbilityType-CRYPTO = 35-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## PARTNER_AGENT

```TypeScript
PARTNER_AGENT = 36
```

[PartnerAgentExtensionAbility](../../apis-connectivity-kit/arkts-apis/arkts-connectivity-fusionconnectivity-partneragentextensionability-partneragentextensionability-c.md): provides the device discovery and device offline notification functions based on Bluetooth.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-ExtensionAbilityType-PARTNER_AGENT = 36--><!--Device-ExtensionAbilityType-PARTNER_AGENT = 36-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## AGENT

```TypeScript
AGENT = 37
```

AgentExtensionAbility: provides extended capabilities for agents, including lifecycle callback APIs for agent service creation, destruction, connection and disconnection, as well as callback APIs for receiving data sent by clients and security authentication.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-ExtensionAbilityType-AGENT = 37--><!--Device-ExtensionAbilityType-AGENT = 37-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## AGENT_UI

```TypeScript
AGENT_UI = 38
```

AgentUIExtensionAbility: provides the Agent UI display capability on the access device.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-ExtensionAbilityType-AGENT_UI = 38--><!--Device-ExtensionAbilityType-AGENT_UI = 38-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## MODULAR_OBJECT

```TypeScript
MODULAR_OBJECT = 39
```

Indicates extension info with type of the modular object extension.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ExtensionAbilityType-MODULAR_OBJECT = 39--><!--Device-ExtensionAbilityType-MODULAR_OBJECT = 39-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

## UNSPECIFIED

```TypeScript
UNSPECIFIED = 255
```

The ability type is not specified. <!--Del-->It can be used in [queryExtensionAbilityInfo](arkts-ability-bundlemanager-queryextensionabilityinfo-f-sys.md) to obtain ExtensionAbility components of all types.<!--DelEnd-->

**Since:** 9

<!--Device-ExtensionAbilityType-UNSPECIFIED = 255--><!--Device-ExtensionAbilityType-UNSPECIFIED = 255-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core
