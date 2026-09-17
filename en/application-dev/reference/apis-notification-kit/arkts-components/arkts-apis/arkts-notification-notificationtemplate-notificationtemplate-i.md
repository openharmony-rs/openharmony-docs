# NotificationTemplate

This module defines the notification template, which is used to specify the template type for a notification.

> **NOTE:** 
> 
> The predefined system templates are supported. You only need to provide the template name and related data for
> the system to automatically render the notification style that complies with the specifications.
> Application scenario: Currently, only the upload and download scenarios are supported.

**Since:** 8

**System capability:** SystemCapability.Notification.Notification

## data

```TypeScript
data: Record<string, Object>
```

Template data.

- **title**: Download title. Mandatory field, with the value being a string type.  
- **fileName**: Download file name. Mandatory field, with the value being a string type.  
- **progressValue**: Download progress, with the value being a numeric type. The recommended value range is 0  
to 100, representing the percentage progress. When **progressValue** is less than or equal to 0, the progress is 0; when it is greater than or equal to 100, the progress ring disappears, indicating that the download is complete.

**Type:** Record&lt;string, Object&gt;

**Since:** 8

**System capability:** SystemCapability.Notification.Notification

## name

```TypeScript
name: string
```

Template name. Currently, only the progress bar notification template indicating download progress is supported, with the value **downloadTemplate**. The string length cannot exceed 202 bytes; any excess will be truncated. It cannot be an empty string.

**Type:** string

**Since:** 8

**System capability:** SystemCapability.Notification.Notification
