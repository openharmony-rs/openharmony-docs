# ContactSyncMode

The type of contact synchronization mode.

**Since:** 26.0.0

**System capability:** SystemCapability.Applications.ContactsData

## MODE_INCREMENTAL

```TypeScript
MODE_INCREMENTAL = 1
```

Indicates that contacts differing between cloud and local will be inserted or updated in the database.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Applications.ContactsData

## MODE_CLOUD_BASED

```TypeScript
MODE_CLOUD_BASED = 2
```

Indicates that all local contacts will be replaced by cloud contacts.

When the cloud overwrite local mode is used for batch synchronization, all local contacts (excluding third-party contacts) are deleted during the first batch synchronization.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Applications.ContactsData
