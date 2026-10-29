# NotificationBasicContent (System API)

```TypeScript
export interface NotificationBasicContent
```

Describes the basic text notification, which is used to display the title and body content. It serves as basic content structure for other notification types. Other notification types (such as long text, multi-line text, picture, and live view) inherit this API and extend their own specific fields on this basis.

**Since:** 7

<!--Device-unnamed-export interface NotificationBasicContent--><!--Device-unnamed-export interface NotificationBasicContent-End-->

**System capability:** SystemCapability.Notification.Notification

## structuredText

```TypeScript
structuredText?: Map<string, string>
```

Structured field of the notification. Currently, only service reminder SMS messages are supported for structured display in the [notification center](../../../notification/notification-glossary.md#notification-center). Empty by default. (The size of each key/value must not exceed 512 bytes; the excess part is truncated. A maximum of 3 pairs of structured data is supported, and the excess part is ignored.)

**Type:** Map&lt;string, string&gt;

**Since:** 21

<!--Device-NotificationBasicContent-structuredText?: Map<string, string>--><!--Device-NotificationBasicContent-structuredText?: Map<string, string>-End-->

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.
