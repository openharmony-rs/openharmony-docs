# JSVM_InitOptions

<!--Kit: ArkTS-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=21434ce8d323ecbd7d67463989a2ef075be92cec translatedAt=2026-08-27T03:48:36.271Z pushedAt=2026-08-27T06:40:31.975Z -->

```c
typedef struct {...} JSVM_InitOptions
```

## Overview

Defines options for initializing a JavaScript VM.

**Use scenario:** Initialization of an app that embeds the JavaScript engine, scenarios where JavaScript code needs to be executed in an app, and development and debugging scenarios that require custom VM configuration.

**System capability:** SystemCapability.ArkCompiler.JSVM

**Since**: 11

**Related module**: [JSVM](capi-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| const intptr_t* externalReferences | (Optional) A raw address array with a **nullptr** at the end in the embedder, which can be matched with the VM during serialization and can be used for deserialization. This array and its contents must remain valid throughout the lifecycle of the VM instance.|
| int* argc | VM flag. If **removeFlags** is **true**, the identified flags are removed from **(argc, argv)**. Note that these flags are now only available to V8 VMs. They are mainly used for development. Do not use these flags in the production environment, as they may not take effect if the VM's configuration differs from the development environment.|
| char** argv | Double pointer to the string array of command parameters, which is used together with **argc** to transfer VM configurations.|
| bool removeFlags | Whether to remove flags. If this parameter is set to **true**, the identified flags are removed from **(argc, argv)**. If this parameter is set to **false**, the identified flags are not removed from **(argc, argv)**.|