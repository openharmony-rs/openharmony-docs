# OH_AI_ShapeInfo

```c
typedef struct OH_AI_ShapeInfo {...} OH_AI_ShapeInfo
```

## Overview

Defines the shape of tensor. The maximum shape size reserved is 32.

<!--Device-struct OH_AI_ShapeInfo {...}--><!--Device-struct OH_AI_ShapeInfo {...}-End-->

**System capability**: SystemCapability.Ai.MindSpore

**Since**: 9

**Related module**: [MindSpore](capi-mind-spore-lite-kit-mindspore.md)

**Header file**: [model.h](capi-model-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| size_t shape_num | Number of shape dimensions.<br>**Since**: 9<br><!--Device-size_t shape_num--><!--Device-size_t shape_num-End--> |
| int64_t shape[OH_AI_MAX_SHAPE_NUM] | Dimension information (shape) of the tensor<br>**Since**: 9<br><!--Device-int64_t shape[OH_AI_MAX_SHAPE_NUM]--><!--Device-int64_t shape[OH_AI_MAX_SHAPE_NUM]-End--> |


