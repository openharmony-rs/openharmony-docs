# JSVM_InitOptions
<!--Kit: Common Basic Capability-->
<!--Subsystem: arkcompiler-->
<!--Owner: @yuanxiaogou; @string_sz-->
<!--Designer: @knightaoko-->
<!--Tester: @test_lzz-->
<!--Adviser: @fang-jinxu-->

## Overview

Options for initializing a JavaScript VM.

**Since**: 11

**Related module**: [JSVM](capi-jsvm.md)

**Header file**: [jsvm_types.h](capi-jsvm-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| const intptr_t* externalReferences | Optional. An array of original addresses ended with nullptr in the embedder. The VM can match the array during serialization and can use the array for deserialization. This array and its contents must remain valid throughout the lifecycle of the VM instance.|
| int* argc | VM flag. If removeFlags is set to true, the identified flags will be removed from (argc, argv). Note that these flags are now only available to V8 VMs. They are mainly used for development. Do not use them in the production environment because they may not take effect if the VM is different from the development environment.|
| char** argv | argv.|
| bool removeFlags | Whether to delete the identified flags from (argc, argv). If this parameter is set to true, the identified flags will be removed from (argc, argv).|
