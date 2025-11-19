| 操作 | 旧版本 | 新版本 | d.ts文件 |
| ---- | ------ | ------ | -------- |
|新增API|NA|类名：global；<br>API声明：declare namespace notificationManager<br>差异内容：declare namespace notificationManager|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：notificationManager；<br>API声明：function publish(request: NotificationRequest, callback: AsyncCallback\<void>): void;<br>差异内容：function publish(request: NotificationRequest, callback: AsyncCallback\<void>): void;|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：notificationManager；<br>API声明：function publish(request: NotificationRequest): Promise\<void>;<br>差异内容：function publish(request: NotificationRequest): Promise\<void>;|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：notificationManager；<br>API声明：function cancel(id: number, callback: AsyncCallback\<void>): void;<br>差异内容：function cancel(id: number, callback: AsyncCallback\<void>): void;|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：notificationManager；<br>API声明：function cancel(id: number, label: string, callback: AsyncCallback\<void>): void;<br>差异内容：function cancel(id: number, label: string, callback: AsyncCallback\<void>): void;|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：notificationManager；<br>API声明：function cancel(id: number, label?: string): Promise\<void>;<br>差异内容：function cancel(id: number, label?: string): Promise\<void>;|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：notificationManager；<br>API声明：function cancelAll(callback: AsyncCallback\<void>): void;<br>差异内容：function cancelAll(callback: AsyncCallback\<void>): void;|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：notificationManager；<br>API声明：function cancelAll(): Promise\<void>;<br>差异内容：function cancelAll(): Promise\<void>;|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：notificationManager；<br>API声明：function addSlot(type: SlotType, callback: AsyncCallback\<void>): void;<br>差异内容：function addSlot(type: SlotType, callback: AsyncCallback\<void>): void;|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：notificationManager；<br>API声明：function addSlot(type: SlotType): Promise\<void>;<br>差异内容：function addSlot(type: SlotType): Promise\<void>;|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：notificationManager；<br>API声明：function getSlot(slotType: SlotType, callback: AsyncCallback\<NotificationSlot>): void;<br>差异内容：function getSlot(slotType: SlotType, callback: AsyncCallback\<NotificationSlot>): void;|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：notificationManager；<br>API声明：function getSlot(slotType: SlotType): Promise\<NotificationSlot>;<br>差异内容：function getSlot(slotType: SlotType): Promise\<NotificationSlot>;|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：notificationManager；<br>API声明：function getSlots(callback: AsyncCallback\<Array\<NotificationSlot>>): void;<br>差异内容：function getSlots(callback: AsyncCallback\<Array\<NotificationSlot>>): void;|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：notificationManager；<br>API声明：function getSlots(): Promise\<Array\<NotificationSlot>>;<br>差异内容：function getSlots(): Promise\<Array\<NotificationSlot>>;|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：notificationManager；<br>API声明：function removeSlot(slotType: SlotType, callback: AsyncCallback\<void>): void;<br>差异内容：function removeSlot(slotType: SlotType, callback: AsyncCallback\<void>): void;|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：notificationManager；<br>API声明：function removeSlot(slotType: SlotType): Promise\<void>;<br>差异内容：function removeSlot(slotType: SlotType): Promise\<void>;|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：notificationManager；<br>API声明：function removeAllSlots(callback: AsyncCallback\<void>): void;<br>差异内容：function removeAllSlots(callback: AsyncCallback\<void>): void;|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：notificationManager；<br>API声明：function removeAllSlots(): Promise\<void>;<br>差异内容：function removeAllSlots(): Promise\<void>;|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：notificationManager；<br>API声明：function isNotificationEnabled(callback: AsyncCallback\<boolean>): void;<br>差异内容：function isNotificationEnabled(callback: AsyncCallback\<boolean>): void;|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：notificationManager；<br>API声明：function isNotificationEnabled(): Promise\<boolean>;<br>差异内容：function isNotificationEnabled(): Promise\<boolean>;|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：notificationManager；<br>API声明：function getActiveNotificationCount(callback: AsyncCallback\<number>): void;<br>差异内容：function getActiveNotificationCount(callback: AsyncCallback\<number>): void;|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：notificationManager；<br>API声明：function getActiveNotificationCount(): Promise\<number>;<br>差异内容：function getActiveNotificationCount(): Promise\<number>;|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：notificationManager；<br>API声明：function getActiveNotifications(callback: AsyncCallback\<Array\<NotificationRequest>>): void;<br>差异内容：function getActiveNotifications(callback: AsyncCallback\<Array\<NotificationRequest>>): void;|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：notificationManager；<br>API声明：function getActiveNotifications(): Promise\<Array\<NotificationRequest>>;<br>差异内容：function getActiveNotifications(): Promise\<Array\<NotificationRequest>>;|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：notificationManager；<br>API声明：function cancelGroup(groupName: string, callback: AsyncCallback\<void>): void;<br>差异内容：function cancelGroup(groupName: string, callback: AsyncCallback\<void>): void;|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：notificationManager；<br>API声明：function cancelGroup(groupName: string): Promise\<void>;<br>差异内容：function cancelGroup(groupName: string): Promise\<void>;|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：notificationManager；<br>API声明：function isSupportTemplate(templateName: string, callback: AsyncCallback\<boolean>): void;<br>差异内容：function isSupportTemplate(templateName: string, callback: AsyncCallback\<boolean>): void;|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：notificationManager；<br>API声明：function isSupportTemplate(templateName: string): Promise\<boolean>;<br>差异内容：function isSupportTemplate(templateName: string): Promise\<boolean>;|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：notificationManager；<br>API声明：function requestEnableNotification(callback: AsyncCallback\<void>): void;<br>差异内容：function requestEnableNotification(callback: AsyncCallback\<void>): void;|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：notificationManager；<br>API声明：function requestEnableNotification(context: UIAbilityContext, callback: AsyncCallback\<void>): void;<br>差异内容：function requestEnableNotification(context: UIAbilityContext, callback: AsyncCallback\<void>): void;|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：notificationManager；<br>API声明：function requestEnableNotification(): Promise\<void>;<br>差异内容：function requestEnableNotification(): Promise\<void>;|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：notificationManager；<br>API声明：function requestEnableNotification(context: UIAbilityContext): Promise\<void>;<br>差异内容：function requestEnableNotification(context: UIAbilityContext): Promise\<void>;|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：notificationManager；<br>API声明：function isDistributedEnabled(callback: AsyncCallback\<boolean>): void;<br>差异内容：function isDistributedEnabled(callback: AsyncCallback\<boolean>): void;|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：notificationManager；<br>API声明：function isDistributedEnabled(): Promise\<boolean>;<br>差异内容：function isDistributedEnabled(): Promise\<boolean>;|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：notificationManager；<br>API声明：function setBadgeNumber(badgeNumber: number, callback: AsyncCallback\<void>): void;<br>差异内容：function setBadgeNumber(badgeNumber: number, callback: AsyncCallback\<void>): void;|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：notificationManager；<br>API声明：function setBadgeNumber(badgeNumber: number): Promise\<void>;<br>差异内容：function setBadgeNumber(badgeNumber: number): Promise\<void>;|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：notificationManager；<br>API声明：export enum SlotType<br>差异内容：export enum SlotType|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：SlotType；<br>API声明：UNKNOWN_TYPE = 0<br>差异内容：UNKNOWN_TYPE = 0|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：SlotType；<br>API声明：SOCIAL_COMMUNICATION = 1<br>差异内容：SOCIAL_COMMUNICATION = 1|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：SlotType；<br>API声明：SERVICE_INFORMATION = 2<br>差异内容：SERVICE_INFORMATION = 2|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：SlotType；<br>API声明：CONTENT_INFORMATION = 3<br>差异内容：CONTENT_INFORMATION = 3|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：SlotType；<br>API声明：LIVE_VIEW = 4<br>差异内容：LIVE_VIEW = 4|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：SlotType；<br>API声明：CUSTOMER_SERVICE = 5<br>差异内容：CUSTOMER_SERVICE = 5|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：SlotType；<br>API声明：OTHER_TYPES = 0xFFFF<br>差异内容：OTHER_TYPES = 0xFFFF|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：notificationManager；<br>API声明：export enum ContentType<br>差异内容：export enum ContentType|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：ContentType；<br>API声明：NOTIFICATION_CONTENT_BASIC_TEXT<br>差异内容：NOTIFICATION_CONTENT_BASIC_TEXT|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：ContentType；<br>API声明：NOTIFICATION_CONTENT_LONG_TEXT<br>差异内容：NOTIFICATION_CONTENT_LONG_TEXT|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：ContentType；<br>API声明：NOTIFICATION_CONTENT_PICTURE<br>差异内容：NOTIFICATION_CONTENT_PICTURE|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：ContentType；<br>API声明：NOTIFICATION_CONTENT_CONVERSATION<br>差异内容：NOTIFICATION_CONTENT_CONVERSATION|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：ContentType；<br>API声明：NOTIFICATION_CONTENT_MULTILINE<br>差异内容：NOTIFICATION_CONTENT_MULTILINE|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：ContentType；<br>API声明：NOTIFICATION_CONTENT_SYSTEM_LIVE_VIEW<br>差异内容：NOTIFICATION_CONTENT_SYSTEM_LIVE_VIEW|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：ContentType；<br>API声明：NOTIFICATION_CONTENT_LIVE_VIEW<br>差异内容：NOTIFICATION_CONTENT_LIVE_VIEW|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：notificationManager；<br>API声明：export enum SlotLevel<br>差异内容：export enum SlotLevel|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：SlotLevel；<br>API声明：LEVEL_NONE = 0<br>差异内容：LEVEL_NONE = 0|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：SlotLevel；<br>API声明：LEVEL_MIN = 1<br>差异内容：LEVEL_MIN = 1|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：SlotLevel；<br>API声明：LEVEL_LOW = 2<br>差异内容：LEVEL_LOW = 2|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：SlotLevel；<br>API声明：LEVEL_DEFAULT = 3<br>差异内容：LEVEL_DEFAULT = 3|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：SlotLevel；<br>API声明：LEVEL_HIGH = 4<br>差异内容：LEVEL_HIGH = 4|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：notificationManager；<br>API声明：export type BundleOption = _BundleOption;<br>差异内容：export type BundleOption = _BundleOption;|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：notificationManager；<br>API声明：export type NotificationActionButton = _NotificationActionButton;<br>差异内容：export type NotificationActionButton = _NotificationActionButton;|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：notificationManager；<br>API声明：export type NotificationBasicContent = _NotificationBasicContent;<br>差异内容：export type NotificationBasicContent = _NotificationBasicContent;|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：notificationManager；<br>API声明：export type NotificationContent = _NotificationContent;<br>差异内容：export type NotificationContent = _NotificationContent;|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：notificationManager；<br>API声明：export type NotificationLongTextContent = _NotificationLongTextContent;<br>差异内容：export type NotificationLongTextContent = _NotificationLongTextContent;|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：notificationManager；<br>API声明：export type NotificationMultiLineContent = _NotificationMultiLineContent;<br>差异内容：export type NotificationMultiLineContent = _NotificationMultiLineContent;|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：notificationManager；<br>API声明：export type NotificationPictureContent = _NotificationPictureContent;<br>差异内容：export type NotificationPictureContent = _NotificationPictureContent;|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：notificationManager；<br>API声明：export type NotificationSystemLiveViewContent = _NotificationSystemLiveViewContent;<br>差异内容：export type NotificationSystemLiveViewContent = _NotificationSystemLiveViewContent;|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：notificationManager；<br>API声明：export type NotificationRequest = _NotificationRequest;<br>差异内容：export type NotificationRequest = _NotificationRequest;|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：notificationManager；<br>API声明：export type DistributedOptions = _DistributedOptions;<br>差异内容：export type DistributedOptions = _DistributedOptions;|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：notificationManager；<br>API声明：export type NotificationSlot = _NotificationSlot;<br>差异内容：export type NotificationSlot = _NotificationSlot;|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：notificationManager；<br>API声明：export type NotificationTemplate = _NotificationTemplate;<br>差异内容：export type NotificationTemplate = _NotificationTemplate;|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：notificationManager；<br>API声明：export type NotificationUserInput = _NotificationUserInput;<br>差异内容：export type NotificationUserInput = _NotificationUserInput;|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：notificationManager；<br>API声明：export type NotificationCapsule = _NotificationCapsule;<br>差异内容：export type NotificationCapsule = _NotificationCapsule;|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：notificationManager；<br>API声明：export type NotificationButton = _NotificationButton;<br>差异内容：export type NotificationButton = _NotificationButton;|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：notificationManager；<br>API声明：export type NotificationTime = _NotificationTime;<br>差异内容：export type NotificationTime = _NotificationTime;|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：notificationManager；<br>API声明：export type NotificationProgress = _NotificationProgress;<br>差异内容：export type NotificationProgress = _NotificationProgress;|api/@ohos.notificationManager.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface ActionResult<br>差异内容：export interface ActionResult|api/@system.notification.d.ts|
|新增API|NA|类名：ActionResult；<br>API声明：bundleName: string;<br>差异内容：bundleName: string;|api/@system.notification.d.ts|
|新增API|NA|类名：ActionResult；<br>API声明：abilityName: string;<br>差异内容：abilityName: string;|api/@system.notification.d.ts|
|新增API|NA|类名：ActionResult；<br>API声明：uri: string;<br>差异内容：uri: string;|api/@system.notification.d.ts|
|新增API|NA|类名：global；<br>API声明：export interface ShowNotificationOptions<br>差异内容：export interface ShowNotificationOptions|api/@system.notification.d.ts|
|新增API|NA|类名：ShowNotificationOptions；<br>API声明：contentTitle?: string;<br>差异内容：contentTitle?: string;|api/@system.notification.d.ts|
|新增API|NA|类名：ShowNotificationOptions；<br>API声明：contentText?: string;<br>差异内容：contentText?: string;|api/@system.notification.d.ts|
|新增API|NA|类名：ShowNotificationOptions；<br>API声明：clickAction?: ActionResult;<br>差异内容：clickAction?: ActionResult;|api/@system.notification.d.ts|
|新增API|NA|类名：global；<br>API声明：export default class Notification<br>差异内容：export default class Notification|api/@system.notification.d.ts|
|新增API|NA|类名：Notification；<br>API声明：static show(options?: ShowNotificationOptions): void;<br>差异内容：static show(options?: ShowNotificationOptions): void;|api/@system.notification.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@ohos.notificationManager.d.ts<br>差异内容：NotificationKit|api/@ohos.notificationManager.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：api\@system.notification.d.ts<br>差异内容：NotificationKit|api/@system.notification.d.ts|
|新增kit|类名：global；<br>API声明：<br>差异内容：NA|类名：global；<br>API声明：kits\@kit.NotificationKit.d.ts<br>差异内容：NotificationKit|kits/@kit.NotificationKit.d.ts|
