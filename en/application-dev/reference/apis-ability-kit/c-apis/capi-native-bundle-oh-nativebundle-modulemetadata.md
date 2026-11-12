# OH_NativeBundle_ModuleMetadata

```c
typedef struct OH_NativeBundle_ModuleMetadata {...} OH_NativeBundle_ModuleMetadata
```

## Overview

The struct describes the metadata of a module.

<!--Device-struct OH_NativeBundle_ModuleMetadata {...}--><!--Device-struct OH_NativeBundle_ModuleMetadata {...}-End-->

**System capability**: SystemCapability.BundleManager.BundleFramework.Core

**Since**: 20

**Related module**: [Native_Bundle](capi-ability-kit-native-bundle.md)

**Header file**: [native_interface_bundle.h](capi-native-interface-bundle-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| char* moduleName | Pointer to the module name.<br>**Since**: 20 |
| [OH_NativeBundle_Metadata*](capi-native-bundle-oh-nativebundle-metadata.md) metadataArray | Pointer to an array containing the module's metadata.<br>**Since**: 20 |
| size_t metadataArraySize | Size of the metadata array of the module. It must be used together with metadataArray and should be equal to the actual number of elements in the metadataArray array. An incorrect value may cause array out-of-bounds access or abnormal data access.<br>**Since**: 20 |


