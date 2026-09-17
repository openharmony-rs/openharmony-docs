# NotifyType (System API)

Enumerates the notification types.

**Since:** 10

**Deprecated since:** 23

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

## NOTIFY_ADD

```TypeScript
NOTIFY_ADD = 0
```

File added.

See examples 2 and 3 of **registerObserver**.

**Since:** 10

**Deprecated since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

## NOTIFY_DELETE

```TypeScript
NOTIFY_DELETE = 1
```

File deleted.

See examples 1 and 2 of **unregisterObserver(uri: string, callback: Callback&lt;NotifyMessage&gt;)**.

**Since:** 10

**Deprecated since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

## NOTIFY_MOVED_TO

```TypeScript
NOTIFY_MOVED_TO = 2
```

File or directory moved in (for example, **rename()** is performed on a file or directory in this directory or a file or directory is moved to this directory).

See example 1 of **registerObserver** and example 1 of **unregisterObserver(uri: string)**.

**Since:** 10

**Deprecated since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

## NOTIFY_MOVED_FROM

```TypeScript
NOTIFY_MOVED_FROM = 3
```

File or directory moved out (for example, **rename()** is performed on a file or directory in this directory or a file or directory is moved out from this directory).

See example 1 of **registerObserver** and example 1 of **unregisterObserver(uri: string)**.

**Since:** 10

**Deprecated since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

## NOTIFY_MOVE_SELF

```TypeScript
NOTIFY_MOVE_SELF = 4
```

File moved (for example, the target file or directory is renamed or moved).

See example 1 of **registerObserver**.

**Since:** 10

**Deprecated since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

## NOTIFY_DEVICE_ONLINE

```TypeScript
NOTIFY_DEVICE_ONLINE = 5
```

Device goes online.

**Since:** 11

**Deprecated since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

## NOTIFY_DEVICE_OFFLINE

```TypeScript
NOTIFY_DEVICE_OFFLINE = 6
```

Device goes offline.

**Since:** 11

**Deprecated since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.
