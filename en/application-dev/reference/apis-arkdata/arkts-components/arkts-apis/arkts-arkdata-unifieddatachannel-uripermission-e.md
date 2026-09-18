# UriPermission

URI authorization policy in drag-and-drop scenarios.

> **NOTE:** 
> &gt;This authorization policy takes effect only in drag-and-drop scenarios and does not take effect in other scenarios.

**Implementation mechanism** During drag-and-drop data transfer, the system grants temporary authorization to the target URI based on the UriPermission configuration. The authorization lifecycle is bound to the drag-and-drop session, and the temporary authorization is automatically cleared after the drag-and-drop is complete. When the receiving application accesses the URI, the system verifies the permission configuration to determine whether access is allowed. The PERSIST permission converts the temporary authorization into persistent authorization.

Four permission policies are supported: no authorization, read, write, and persist. They can be used in combination, and only the following combinations take effect:  
- NONE only: no file authorization is granted.  
- READ only: only one-time read-only authorization is granted.  
- WRITE only: one-time read and write authorization is granted (write authorization includes read authorization).  
- READ+WRITE: one-time read and write authorization is granted, with the same effect as using WRITE only.  
- READ+PERSIST: persistent read authorization is granted.  
- WRITE+PERSIST: grants persistent read and write authorization.  
- READ+WRITE+PERSIST: grants persistent read and write authorization.

Rules for applying the drag-and-drop authorization policy (in descending order of priority):  
- Single data level: The FileUri and HTML Unified Data Structures (UDS) and the File, Image, Video, Audio, Folder,  
and HTML Unified Data Content (UDC) structures support configuring authorization policy parameters, which take effect only for a single record at a time and have the highest priority.  
- UnifiedData level: The authorization parameters provided in UnifiedDataProperties take effect for a single  
drag-and-drop operation. If an authorization policy is configured for a piece of data, the configuration of that data takes precedence, with the next highest priority.  
- Default level: If no authorization policy is configured for either a single piece of data or  
UnifiedDataProperties, proxy authorization is performed according to the default drag-and-drop logic. The default logic is as follows:

- FileUri data (FileUri UDS or the File, Image, Video, Audio, and Folder UDC types): In the drag-and-drop  
scenario, the default authorization is READ+WRITE+PERSIST (read + write + persistent authorization).  
- HTML data: read authorization is granted only for the URIs under the img tag in the HTML text.

**Since:** 26.0.0

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## NONE

```TypeScript
NONE = 0
```

No permissions granted.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## READ

```TypeScript
READ = 1
```

Permission to read or view data.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## WRITE

```TypeScript
WRITE = 2
```

Permission to modify data.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core

## PERSIST

```TypeScript
PERSIST = 3
```

Permission to persist files.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.DistributedDataManager.UDMF.Core
