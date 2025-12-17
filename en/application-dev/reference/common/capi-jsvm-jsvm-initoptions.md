# JSVM_InitOptions
<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou; @string_sz-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->

```c
typedef struct {...} JSVM_InitOptions
```

## Overview

Defines options for initializing a JavaScript VM.

**Since**: 11

**Related module**: [JSVM](capi-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| const intptr_t* externalReferences | (Optional) A raw address array with a **nullptr** at the end in the embedder, which can be matched with the VM during serialization and can be used for deserialization. This array and its contents must remain valid throughout the lifecycle of the VM instance.|
| int* argc | VM flag. If **removeFlags** is **true**, the identified flags are removed from **(argc, argv)**. Note that these flags are now only available to V8 VMs. They are mainly used for development. Do not use these flags in the production environment, as they may not take effect if the VM's configuration differs from the development environment.|
| char** argv | argv.|
| bool removeFlags | Whether to remove the identified flags from **(argc, argv)**. If this parameter is set to **true**, the identified flags will be removed.|
