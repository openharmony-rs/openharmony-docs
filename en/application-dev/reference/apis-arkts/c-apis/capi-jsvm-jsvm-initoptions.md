# JSVM_InitOptions

```c
typedef struct JSVM_InitOptions {...} JSVM_InitOptions
```

## Overview

Init the JavaScript VM with init option.

**Since**: 11

**Related module**: [JSVM](capi-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| const intptr_t* externalReferences | Optional nullptr-terminated array of raw adddresses in the embedder that the VM can match against during serialization and use for deserialization. This array and its content must stay valid for the entire lifetime of the VM instance. |
| int* argc | Flags for the VM. IF removeFlags is true, recognized flags will be removed from (argc, argv). Note that these flags are specific to VM. They are mainly used for development. Do not include them in production as they might not take effect if the VM is different from the development environment. |
| char** argv | argv . |
| bool removeFlags | remove flags. |


