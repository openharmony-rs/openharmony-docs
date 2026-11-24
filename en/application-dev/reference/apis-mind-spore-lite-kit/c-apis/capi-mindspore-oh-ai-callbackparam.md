# OH_AI_CallBackParam

```c
typedef struct OH_AI_CallBackParam {...} OH_AI_CallBackParam
```

## Overview

Defines the operator information passed in a callback.

<!--Device-struct OH_AI_CallBackParam {...}--><!--Device-struct OH_AI_CallBackParam {...}-End-->

**System capability**: SystemCapability.Ai.MindSpore

**Since**: 9

**Related module**: [MindSpore](capi-mind-spore-lite-kit-mindspore.md)

**Header file**: [model.h](capi-model-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| char *node_name | Name of kernel node<br>**Since**: 9<br><!--Device-char *node_name--><!--Device-char *node_name-End--> |
| char *node_type | Type of kernel node.<br>**Since**: 9<br><!--Device-char *node_type--><!--Device-char *node_type-End--> |


