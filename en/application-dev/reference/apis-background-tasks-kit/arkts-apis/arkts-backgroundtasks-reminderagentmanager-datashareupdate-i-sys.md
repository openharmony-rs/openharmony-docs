# DataShareUpdate (System API)

Defines the parameter information used to update the database.

The data provider needs to set the ID, read/write permissions, and basic information of the table to be shared under **proxyData** in the **module.json5** file. For details about the configuration method, see [Data Provider Application Development](../../../database/share-data-by-silent-access-sys.md#data-provider-application-development)

**Since:** 11

**System capability:** SystemCapability.Notification.ReminderAgent

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { reminderAgentManager } from '@kit.BackgroundTasksKit';
```

## equalTo

```TypeScript
equalTo: Record<string, number | string | boolean>
```

Filter criteria. Currently, only **equalTo** is supported.

**Type:** Record&lt;string, number &#124; string &#124; boolean&gt;

**Since:** 11

**System capability:** SystemCapability.Notification.ReminderAgent

**System API:** This is a system API.

## uri

```TypeScript
uri: string
```

URI of the data, which is the unique identifier for cross-application data access.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.Notification.ReminderAgent

**System API:** This is a system API.

## value

```TypeScript
value: ValuesBucket
```

New data.

**Type:** [ValuesBucket](../../apis-arkdata/arkts-apis/arkts-arkdata-valuesbucket-t.md)

**Since:** 11

**System capability:** SystemCapability.Notification.ReminderAgent

**System API:** This is a system API.
