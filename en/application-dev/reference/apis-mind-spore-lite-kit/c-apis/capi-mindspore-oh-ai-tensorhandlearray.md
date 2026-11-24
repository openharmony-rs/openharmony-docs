# OH_AI_TensorHandleArray

```c
typedef struct OH_AI_TensorHandleArray {...} OH_AI_TensorHandleArray
```

## Overview

Defines the tensor array structure, which is used to store the tensor array pointer and tensor array length.

<!--Device-struct OH_AI_TensorHandleArray {...}--><!--Device-struct OH_AI_TensorHandleArray {...}-End-->

**System capability**: SystemCapability.Ai.MindSpore

**Since**: 9

**Related module**: [MindSpore](capi-mind-spore-lite-kit-mindspore.md)

**Header file**: [model.h](capi-model-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| size_t handle_num | Number of tensor handles in the array.<br>**Since**: 9<br><!--Device-size_t handle_num--><!--Device-size_t handle_num-End--> |
| OH_AI_TensorHandle *handle_list | Pointer to the array of tensor handles.<br>**Since**: 9<br><!--Device-OH_AI_TensorHandle *handle_list--><!--Device-OH_AI_TensorHandle *handle_list-End--> |


