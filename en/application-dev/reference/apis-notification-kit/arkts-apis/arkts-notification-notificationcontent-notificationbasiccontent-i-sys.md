# NotificationBasicContent

Describes the basic text notification, which is used to display the title and body content. It serves as the basic content structure for other notification types. Other notification types (such as long text, multi-line text, picture, and live view) inherit this API and extend their own specific fields on this basis.

**Since:** 7

**System capability:** SystemCapability.Notification.Notification

## structuredText

```TypeScript
structuredText?: Map<string, string>
```

Structured notification. Currently, only service reminder messages can be displayed in structured format in the notification center. This parameter is left empty by default. (The size of key or value cannot exceed 512 bytes; otherwise, the excess part will be truncated. Only a maximum of three pairs of structured data are supported.)

**Type:** Map&lt;string, string&gt;

**Since:** 21

**System capability:** SystemCapability.Notification.Notification

**System API:** This is a system API.
